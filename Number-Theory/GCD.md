## GCD
$$\gcd(a,b)=\gcd(b,a\bmod b)$$
```cpp
int gcd(int a, int b) {
    return a == 0 ? b : gcd(b, a % b);
}
```

## exGCD
求解 $ax+by=\gcd(a,b)$ 的一组特解 $\left\{\begin{aligned}x=x_0\\y=y_0\end{aligned}\right.$。
$$\mathrm{exgcd}(a,b)\rightarrow(d,x_0,y_0)$$
```cpp
void exgcd(int a, int b, int &d, int &x, int &y) {
    if (b == 0) d = a, x = 1, y = 0;
    else {
        exgcd(b, a % b, d, x, y);
        int t = x; x = y; y = t - a / b * y;
    }
}
```

<div style="page-break-after: always;"></div>

## 二元一次不定方程
求解 $ax+by=c$ 的一组特解 $\left\{\begin{aligned}x=x_0\\y=y_0\end{aligned}\right.$。

$$\begin{array}{rl}
            & \mathrm{exgcd}(a,b)\rightarrow(d,x_0,y_0)\\
\Rightarrow & ax_0+by_0=\gcd(a,b)\\
\Rightarrow & a\frac{x_0}{\gcd(a,b)}+b\frac{y_0}{\gcd(a,b)}y=1\\
\Rightarrow & a\frac{x_0c}{\gcd(a,b)}+b\frac{y_0c}{\gcd(a,b)}=c\\
\Rightarrow & \left\{\begin{aligned}x=\frac{x_0c}{\gcd(a,b)}\\y=\frac{y_0c}{\gcd(a,b)}\end{aligned}\right.
\end{array}$$

有解条件： $c \bmod \gcd(a,b) = 0$。

```cpp
bool linearEquation(int a, int b, int c, int &x, int &y) {
    int d; exgcd(a, b, d, x, y);
    if (c % d) return false;
    int t = c / d;
    x *= t, y *= t;
    return true;
}
```
<div style="page-break-after: always;"></div>

## 线性同余方程
求解 $ax\equiv b\pmod{c}$ 的最小正整数解。
$$\begin{array}{rl}
            & ax\equiv b\pmod{c}\\
\Rightarrow & ax+cy=b\\
\Rightarrow & \mathrm{linearEquation}(a,c,b) \rightarrow(x,y)
\end{array}$$

有解条件： $b \bmod \gcd(a,c) = 0$。

```cpp
int equiv(int a, int b, int c) {
    int x, y;
    if (linearEquation(a, c, b, x, y)) {
        int t = gcd(a, c);
        return (x % t + t) % t;
    } else return -1;
}
```
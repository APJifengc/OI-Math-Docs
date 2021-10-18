## 欧拉函数

### 性质

1.  **定义:** $\varphi(n)$ 为 $x\in[1,n]$ 当中 $n$ 与 $x$ 互质（$\gcd(n,x)=1$）的个数。
2.  **积性函数:** 若 $\gcd(a,b)=1$， 那么$\varphi(a) \times \varphi(b) = \varphi(a \times b)$。
3.  若 $n$ 为质数， 则 $\varphi(n) = n-1$。
4.  若 $x\bmod p^2 \ne 0$， 则 $\varphi(x\times p) = \varphi(x) \times (p-1)$，
    若 $x\bmod p^2 = 0$， 则 $\varphi(x\times p)=\varphi(x) \times p$。
5.  设 $x = p_1^{c_1}\times p_2^{c_2}\times \cdots \times p_n^{c_n}$， 则$\varphi(x)=x\times \prod_{i=1}^{n}(1-\frac{1}{p})$。
    ```cpp
    int phi(int x) {
        int ans = x;
        for (int i = 1; i * i <= x; i++)
            if (x % i == 0) {
                while (x % i == 0) x /= i;
                ans = ans / i * (i - 1);
            }
        if (x > 1) ans = ans / x * (x - 1);
        return ans;
    }
    ```
<div style="page-break-after: always;"></div>

### 线性筛求欧拉函数

根据性质4，我们可以用线性筛在 $\mathrm{O}(n)$ 的时间内求出 $x\in [1,n]$ 中的所有 $\varphi(x)$ 值。
```cpp
int pre(int n) {
    for (int i = 2; i <= n; i++) {
        if (!vis[i]) {
            pri[++cnt] = i;
            phi[i] = i - 1;
        }
        for (int j = 1; j <= cnt && i * pri[j] <= n; j++) {
            vis[i * pri[j]] = 1;
            if (i % pri[j] == 0) {
                phi[i * phi[j]] = phi[i] * pri[j];
                break;
            } else phi[i * pri[j]] = phi[i] * (pri[j] - 1);
        }
    }
}
```

<div style="page-break-after: always;"></div>

### 欧拉定理

$$x^b\equiv \begin{cases}
    x^{b\bmod \varphi(p)}, &\gcd(x,p)=1\\
    x^{b\bmod \varphi(p) + \varphi(p)}, &\gcd(x,p)\ne 1, b < \varphi(p)\\
    x^b, &\gcd(x,p)\ne 1, b \ge \varphi(p)
\end{cases} \pmod{p}
$$
## GCD
$$\gcd(x,y)=\gcd(y,x\bmod y)$$
```cpp
int gcd(int x, int y) {
    return x == 0 ? y : gcd(y, x % y);
}
```

## exGCD
$$\mathrm{exgcd}(x,y)\rightarrow(d,x_0,y_0)$$
```cpp
void exgcd(int a, int b, int &d, int &x, int &y) {
    if (b == 0) d = a, x = 1, y = 0;
    else {
        exgcd(b, a % b, d, x, y);
        int t = x; x = y; y = t - (a / b) * y;
    }
}
```
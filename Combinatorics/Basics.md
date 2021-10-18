## 排列数

1.  $\displaystyle \mathrm A_n^m=\frac{n!}{(n-m)!}$
2.  $\mathrm A_n^n = n!$

## 组合数

1.  $\displaystyle \binom{n}{m} = \frac{\mathrm A_n^m}{m!} = \frac{n!}{m!(n-m)!}$
2.  $\displaystyle \binom{n}{m} = \binom{n-1}{m} + \binom{n-1}{m-1}$
3.  $\displaystyle\sum_{i=0}^{n}\binom{n}{i} = 2^n$
4.  将 $n$ 个数分为 $m$ 组（无空组）： $\displaystyle\binom{n-1}{m}$
    将 $n$ 个数分为 $m$ 组（有空组）： $\displaystyle\binom{n+m-1}{m}$

## 二项式定理

$$(a+b)^n=\sum_{i=0}^{n}\binom{n}{i}a^ib^{n-i}$$

<div style="page-break-after: always;"></div>

## 多重组合数

将 $n$ 个数分为 $k$ 组， 每组大小为 $m_k$ 的方案数。
$$\binom{n}{m_1,m_2,\cdots,m_k}=\frac{n!}{\prod_{i=1}^k m_i}$$

## Lucas 定理

$$\binom{a}{b} \bmod p =\binom{a\bmod p}{b \bmod p} \times \binom{\lfloor\frac{a}{p}\rfloor}{\lfloor\frac{b}{p}\rfloor} \bmod p $$
$\tiny{\text{我拒绝写拓展卢卡斯定理}}$
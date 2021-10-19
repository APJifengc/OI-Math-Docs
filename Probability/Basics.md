## 概率

1.  $P(X)$ 表示 $X$ 的概率， $P(X|Y)$ 表示 $X$ 在 $Y$ 发生的情况下发生的概率。
2.  独立事件： $P(A\cap B)=P(A)P(B)$
3.  全概率公式： $\displaystyle P(B) = \sum_{i=1}^nP(A_i)P(B|A_i)$
4.  贝叶斯公式： $\displaystyle P(B_i|A)=\frac{P(B_i)P(A|B_i)}{\displaystyle \sum_{j=1}^n P(B_j)P(A|B_j)}$

## 期望

1.  $E(X)$ 表示 $X$ 的期望。 
    $$E(X)=\sum\limits_{\alpha \in I(X)} \alpha\cdot P(X=\alpha)=\sum\limits_{\omega\in S}X(\omega)P(\omega)$$
2.  全期望公式： $\displaystyle E(Y)=\sum\limits_{\alpha \in I(X)} P(X=\alpha)E(Y|(X=\alpha))$
3.  期望的线性性： $E(aX+bY)=aE(X)+bE(Y)$
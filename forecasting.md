---
description: 课本第9章
---

# 预测

## 条件期望

$$Y$$的条件概率密度函数：

$$
f_{Y|X}(y|x) = \frac{f_{X,Y}(x,y)}{f_X(x)}
$$

$$Y$$的条件期望：

$$
E(Y|X=x) = \int_{\mathbb{R}} y\ f_{Y|X}(y|x)\ \ dy
$$

### 条件数学期望的性质

$$
E(aY+bZ+c | X=x) = aE(Y|X=x) + bE(Z|X=x) + c
$$

$$
E[h(Y)|X=x] = \int_\mathbb{R} h(y) f_{Y|X}(y|x)\ dy \\
\Rightarrow\ E[h(X)|X=x)]= h(x) \\
\Rightarrow\ E[h(X,Y)|X=x] = E[h(x,Y)|X=x]
$$

如果$$X$$和$$Y$$是独立的，则有：

$$
E(Y|X) = E(Y)
$$

#### 全期望公式

* 定理

$$
E(E(Y|X)g(X)) = E(Yg(X))
$$

证明如下：

$$
\text{LHS} = \int_\mathbb{R} \huge(\normalsize \int_\mathbb{R} y\ f_{Y|X}(y|x)\ \ dy\huge)\normalsize g(x) f_X(x)\ dx \\
= \int_\mathbb{R} \int_\mathbb{R} y\ g(x)\ f_{X,Y}(x,y)\ dy dx = \text{RHS}
$$

{% hint style="info" %}
若对$$\forall g(X),\ E(h(X)g(X)) = E(Yg(X))$$都成立，则必有$$h(X) = E(Y|X)$$。
{% endhint %}

* 全期望公式

$$
E[E(Y|X)] = E(Y)
$$

令上方定理$$g(X) = 1$$即可。

* 推论

$$
E(g(X)Y|X) = g(X) E(Y|X)
$$

证明如下：

$$
E[h(X)f(X)] = E[[g(X)E(Y|X)]f(X)] = E[E(Y|X) \tilde{f}(X)] \\
= E[Y \tilde{f}(X)] = E[[Yg(X)]f(X)]  = E[\tilde{Y}f(X)], \quad \forall\ f(X) \\ \quad \\
\Rightarrow\ g(X)E(Y|X) = h(X) = E(\tilde{Y}|X) = E(g(X)Y|X)
$$

## 最小均方误差预测

找到$$X$$的一个线性函数$$h(X)$$，使得$$E[Y-h(X)]^2$$达到最小。

$$
\begin{align}
&E[Y-h(X)]^2 = E[E\{[Y-h(X)]^2|X\}] \\ \\
\Rightarrow\ &E\{[Y-h(X)]^2|X\} = E\{[Y-h(x)]^2|X=x\} \\
&= E[Y^2|X=x] - 2h(x) E[Y|X=x] + [h(x)]^2 \\
&= \{h(x) - E[Y|X=x]\}^2 + E[Y^2|X=x] - \{E[Y|X=x]\}^2 \\ \\
\Rightarrow\ &\hat{h}(x) = E[Y|X=x]
\end{align}
$$

在任意$$X = x$$给定的条件下均可得到上述结果，故有

$$
h(X) = E[Y|X]
$$

是基于所有关于$$X$$的函数所得的$$Y$$的最优预测。






























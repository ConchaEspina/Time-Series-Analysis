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

更一般地，如果用一个$$X_1, X_2, \cdots, X_n$$的函数来预测$$Y$$，则易证最小均方误差预测为

$$
E(Y|X_1, X_2, \cdots, X_n)
$$

### 时间序列的最小均方误差预测

基于时间序列可获得的历史数据$$Y_1, Y_2, \cdots, Y_t$$，预测未来$$l$$期的值$$Y_{t+l}$$，称时间$$t$$为预测起点，$$l$$为预测前置时间，得到最小均方误差预测值：

$$
\hat{Y}_t(l) = E(Y_{t+l}|Y_1, Y_2, \cdots, Y_t)
$$

## 确定性趋势

$$
Y_t = \mu_t + X_t
$$

其中$$X_t$$是方差为$$\gamma_0$$的白噪声。

$$
\begin{align}
\hat{Y}_t(l) &= E(\mu_{t+l}+X_{t+l}\ |\ Y_1, \cdots, Y_t) = E(\mu_{t+l}\ |\ Y_1, \cdots, Y_t) + E(X_{t+l}\ |\ Y_1, \cdots, Y_t) \\
&= \mu_{t+l} + E(X_{t+l}) = \mu_{t+l}
\end{align}
$$

### 趋势示例

#### 线性趋势

$$
\hat{Y}_t(l) = \mu_{t+l} = \beta_0 + \beta_1 (t+l)
$$

#### 季节模型

$$
\hat{Y}_t(l) = \mu_{t+l} = \mu_{t+s+l} = \hat{Y}_t(l+s)
$$

### 预测误差

$$
e_t(l) = Y_{t+l} - \hat{Y}_t(l) = \mu_{t+l} + X_{t+l} - \mu_{t+l} = X_{t+l}
$$

#### 预测误差的性质

* 期望：$$E(e_t(l)) = 0$$ → $$\hat{Y}_t(l)$$无偏
* 方差： $$\text{Var}(e_t(l)) = \gamma_0$$ 

## ARIMA预测

### $$\text{AR}(1)$$ 

#### $$l = 1$$ 

$$
Y_{t+1} - \mu = \phi(Y_t - \mu) + e_{t+1}
$$

对两边取条件期望，得：

$$
\hat{Y}_t(1) - \mu = \phi [E(Y_t | Y_1, \cdots, Y_t) - \mu] + E(e_{t+1} | Y_1, \cdots, Y_t) \\
= \phi (Y_t - \mu) + E(e_{t+1}) = \phi (Y_t - \mu) \\ \quad \\
\Rightarrow\ \hat{Y}_t(1) = \phi(Y_t - \mu) + \mu
$$

预测误差：

$$
e_t(1)  = Y_{t+1} - \hat{Y}_t(1) = Y_{t+1} - \mu - \phi(Y_t - \mu) = e_{t+1} \\ \quad \\
\Rightarrow\ E(e_t(1)) = 0,\ \text{Var}(e_t(1)) = \sigma_e^2
$$

#### 一般情况

$$
\hat{Y}_t(l) = \phi[E(Y_{t+l-1} | Y_1, \cdots, Y_t) - \mu] + E(e_{t+l-1} | Y_1, \cdots, Y_t) + \mu \\
= \phi [\hat{Y}_t(l-1) - \mu] + \mu = \phi^2 [\hat{Y}_t(l-2) - \mu] + \mu \\
= \cdots = \phi^{l-1} [\hat{Y}_t(1) - \mu] + \mu = \phi^l (Y_t - \mu) + \mu
$$

因为$$|\phi|<1$$，所以当$$l$$很大的时候，有$$\hat{Y}_t(l) \approx \mu$$。

预测误差：

$$
Y_t = \mu + e_t + \phi e_{t-1} + \phi^2 e_{t-2} + \cdots
$$

$$
\begin{align}
e_t(l) &= Y_{t+l} - \hat{Y}_t(l) = Y_{t+l} - \mu - \phi^l(Y_t - \mu) \\
&= (e_{t+l} + \phi e_{t+l-1} + \phi^2 e_{t+l-2} + \cdots) - \phi^l (e_t + \phi e_{t-1} + \phi^2 e_{t-2} + \cdots) \\
&= e_{t+l} + \phi e_{t+l-1} + \phi^2 e_{t+l-2} + \cdots + \phi^{l-1} e_{t+1}
\end{align} \\ \quad \\
\Rightarrow\ E(e_t(l)) = 0,\ \text{Var}(e_t(l)) = \frac{1-\phi^{2l}}{1-\phi^2} \sigma_e^2
$$

 由上面的结果可以推出如下结论：

* $$\hat{Y}_t(l)$$是无偏估计
* 当$$l$$很大时，有$$\text{Var}(e_t(l)) \approx \Large\frac{1}{1-\phi^2} \normalsize\sigma_e^2$$或 $$e_t(l) \approx Y_{t+l} \Rightarrow \text{Var}(e_t(l)) \approx \text{Var}(Y_{t+l}) = \gamma_0 = \Large\frac{1}{1-\phi^2} \normalsize\sigma_e^2$$ 

### $$\text{MA}(1)$$ 

#### $$l = 1$$ 

$$
Y_{t+1} = \mu + e_{t+1} - \theta e_t
$$

对两边取条件期望，得：

$$
\hat{Y}_t(1) = \mu + E(e_{t+1} | Y_1, \cdots, Y_t)- \theta E(e_t | Y_1, \cdots, Y_t) = \mu - \theta e_t
$$

其中 $$E(e_{t+1} | Y_1, \cdots, Y_t) = E(e_{t+1}) = 0,\ E(e_t | Y_1, \cdots, Y_t) = e_t$$（由可逆性得$$e_t$$为 $$Y_1, \cdots, Y_t$$ 的函数）

预测误差：

$$
e_t(1) = Y_{t+1} - \hat{Y}_t(1) = e_{t+1}
$$

#### 一般情况

$$
\hat{Y}_t(l) = \mu + E(e_{t+l} | Y_1, \cdots, Y_t) - \theta E(e_{t+l-1} | Y_1, \cdots, Y_t) \\
= \mu + E(e_{t+l}) - \theta E(e_{t+l-1}) = \mu, \qquad l>1
$$

### $$\text{ARMA}(p,q)$$

$$
\begin{align}
\hat{Y}_t(l) &= E(Y_{t+l} | Y_1, \cdots, Y_t) \\
&= \phi_1 \hat{Y}_t(l-1) + \phi_2 \hat{Y}_t(l-2) + \cdots + \phi_p\hat{Y}_t(l-p) + \theta_0 - \theta_1 E(e_{t+l-1} | Y_1, \cdots, Y_t) \\
&- \theta_2 E(e_{t+l-2} | Y_1, \cdots, Y_t) - \cdots - \theta_q E(e_{t+l-q} | Y_1, \cdots, Y_t) \\
&= \sum_{i=1}^p \phi_i \hat{Y}_t(l-i) + \theta_0 - \sum_{j=1}^q \theta_j E(e_{t+l-j} | Y_1, \cdots, Y_t)
\end{align}
$$

其中 $$E(e_{t+j} | Y_1, \cdots, Y_t) = \begin{cases} 0, \quad j >0 \\ e_{t+j}, \quad j \leq 0 \end{cases},\quad \hat{Y}_t(j) = \begin{cases} \hat{Y}_t(j), \quad j>0 \\ Y_{t+j},\quad j \leq 0   \end{cases}$$ 

#### 特例：$$\text{ARMA}(1,1)$$

$$
\hat{Y}_t(1) = \phi Y_t + \theta_0 - \theta e_t \\
\hat{Y}_t(2) = \phi \hat{Y}_t(1) + \theta_0 \\ \quad \\
\Rightarrow\ \hat{Y}_t(l) = \phi \hat{Y}_t(l-1) + \theta_0, \quad l \geq 2
$$

$$
\hat{Y}_t(l) - \frac{\theta_0}{1-\phi} = \phi [\hat{Y}_t(l-1) - \frac{\theta_0}{1-\phi}] \\
\Rightarrow\ \hat{Y}_t(l) - \mu = \phi [\hat{Y}_t(l-1) - \mu] = \phi^{l-1} [\hat{Y}_t(1) - \mu] = \phi^l (Y_t - \mu) - \phi^{l-1} e_t,\quad l \geq1
$$

### 截断线性过程









## 预测极限


























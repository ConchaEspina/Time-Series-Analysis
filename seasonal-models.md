---
description: 课本第10章
---

# 季节模型

## 季节ARIMA模型

### 季节$$\text{MA}(Q)$$模型

季节周期为$$s$$的$$Q$$阶季节$$\text{MA}(Q)$$模型：

$$
Y_t = e_t - \Theta_1 e_{t-s} - \Theta_2 e_{t-2s} - \cdots - \Theta_Q e_{t-Qs}
$$

季节MA特征多项式：

$$
\Theta(x) = 1 - \Theta_1 x^s - \Theta_2 x^{2s} - \cdots - \Theta_Q x^{Qs}
$$

{% hint style="info" %}
模型可逆的条件：$$\Theta(x) = 0$$所有根的绝对值都必须大于1
{% endhint %}

该序列总是平稳的，且其自相关系数只在$$0, s, 2s, \dots, Qs$$等季节滞后上非零。

季节滞后上的自相关系数：

$$
\rho_{ks} = \frac{-\Theta_k + \Theta_1\Theta_{k+1} + \Theta_2\Theta_{k+2} + \cdots + \Theta_{Q-k}\Theta_Q}{1 + \Theta_1^2 + \Theta_2^2 + \cdots + \Theta_Q^2}
$$

季节$$\text{MA}(Q)$$模型可以看作阶数$$q = Qs$$的非季节性MA模型的特例，但除了季节滞后$$s,2s,\dots,Qs$$处，所有$$\theta$$值都取零。

### 季节$$\text{AR}(P)$$模型

季节周期为$$s$$的$$P$$阶季节$$\text{AR}(P)$$模型：

$$
Y_t = \Phi_1 Y_{t-s} + \Phi_2 Y_{t-2s} + \cdots + \Phi_P Y_{t-Ps} + e_t
$$

季节AR特征多项式：

$$
\Phi(x) = 1 - \Phi_1 x^s - \Phi_2 x^{2s} - \cdots - \Phi_P x^{Ps}
$$

{% hint style="info" %}
模型平稳的条件：$$\Phi(x) = 0$$所有根的绝对值都必须大于1
{% endhint %}

该序列的自相关系数只在$$0, s, 2s, \dots, Ps$$等季节滞后上非零。

季节滞后上的自相关系数：

$$
\rho_{ks} = \Phi^k,\quad k=1,2,\cdots
$$

季节$$\text{AR}(P)$$模型可以看作阶数$$p = Ps$$的非季节性AR模型的特例，但除了季节滞后$$s,2s,\dots,Ps$$处，所有$$\phi$$值都取零。

## 乘法季节ARMA模型

季节周期为$$s$$的乘法季节$$\text{ARMA}(p,q)\times(P,Q)_s$$模型是AR特征多项式为$$\phi(x)\Phi(x)$$、MA特征多项式为$$\theta(x)\Theta(x)$$的模型，其中：

$$
\begin{cases}
\phi(x) = 1 - \phi_1 x - \phi_2 x^2 - \cdots - \phi_p x^p \\
\Phi(x) = 1 - \Phi_1 x^s - \Phi_2 x^{2s} - \cdots - \Phi_P x^{Ps}
\end{cases} \\ \quad \\
\begin{cases}
\theta(x) = 1 - \theta_1 x - \theta_2 x^2 - \cdots - \theta_q x^q \\
\Theta(x) = 1 - \Theta_1 x^s - \Theta_2 x^{2s} - \cdots - \Theta_Q x^{Qs}
\end{cases}
$$

模型中可能也会包含常数项$$\theta_0$$ 

#### 例子：$$q = P = 1,\ p = Q = 0,\ s = 12$$ 

$$
Y_t = \Phi Y_{t-12} + e_t - \theta e_{t-1}
$$

$$
\gamma_0 = \frac{1+\theta^2}{1-\Phi^2} \sigma_e^2 \\
\rho_{12k} = \Phi^k,\quad k \geq 1 \\
\rho_{12k-1} = \rho_{12k+1} = -\frac{\theta}{1+\theta^2}\Phi^k,\quad k = 0,1,\cdots
$$

## 非平稳季节ARIMA模型

时间序列周期为$$s$$的季节差分：

$$
\nabla_s Y_t = Y_t - Y_{t-s}
$$

季节周期为$$s$$，非季节（规则的）阶数为$$p,d,q$$，季节阶数为$$P,D,Q$$的乘法季节$$\text{ARIMA}(p,d,q)\times(P,D,Q)_s$$模型要求差分序列

$$
W_t = \nabla^d \nabla_s^D Y_t
$$

满足某季节周期为$$s$$的乘法季节$$\text{ARMA}(p,q)\times(P,Q)_s$$模型。

## 模型识别、拟合和检验

### 模型识别

观察样本ACF图在季节滞后处是否存在强自相关关系

### 模型拟合

直接应第7章的参数估计方法即可

### 诊断性检验

#### 残差的相关性

* 绘制标准残差图，观察残差的模式
* 绘制残差的ACF图，观察残差的自相关性
* Ljung-Box检验

#### 残差的正态性

* 通过残差的直方图或QQ图检验残差的正态性
* 通过Shapiro-Wilk检验判断残差是否服从正态分布

## 季节模型预测














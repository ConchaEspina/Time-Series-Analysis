---
description: 课本第12章
---

# 条件异方差时间序列模型

**研究对象：**时间序列的条件方差过程

→ 条件方差会随着现在和过去数值的变化而变化

## 金融时间序列的一些共同特征

> 以CREF日收益率数据为例

对数收益率： $$r_t = \log(p_t) - \log(p_{t-1})$$ 

有效市场的预期收益率（条件均值）应该为零，且收益率序列是一个白噪声序列

### 波动集群

波动集群：大量的持续的平静和波动相交替的模式

→ 波动集群的特征显示收益率不是独立同分布的，因为方差不是常数

波动集群是一种高阶相关结构

**如果收益率是独立同分布的白噪声，那么它的绝对值和平方值也是独立同分布的白噪声。**

### 波动率

波动率：条件标准差$$\sigma_t$$

波动率的普遍特征：

1. 存在波动率聚集，也就是说，波动率可能是在一些时间段上高，而在另一些时间段上低
2. 波动率以连续方式随时间变化，即波动率跳跃是很少见的
3. 波动率不发散到无穷，即波动率在固定的范围内变化；从统计学角度说，这意味着波动率往往是平稳的
4. 波动率对价格大幅上升和价格大幅下降的反应不同，这种现象称为杠杆效应

_（参考：Tsay.R.S.《金融时间序列分析》）_

### McLeod-Li检验

**McLeod-Li检验：**用残差或者数据平方构造的Box-Ljung统计量来判断ARCH效应的检验

> ARCH效应：即条件异方差性。
>
> McLeod-Li检验就是将Box-Ljung统计量$$\{Q(m)\}$$应用于残差的平方值所构成的序列。

如果在检验中使用平方数据的$$m$$个自相关系数，不存在ARCH时，检验统计量近似服从$$m$$个自由度的卡方分布。一般设置显著水平为5%，若显著，则说明序列数据具有ARCH特征。

### 收益率分布形状的度量

#### 正态性检验

* QQ图
* Shapiro-Wilk检验

#### 峰度与偏度

* 偏度

$$
\frac{E(Y-\mu)^3}{\sigma^3}
$$

正态分布偏度为0

* 峰度

$$
\frac{E(Y-\mu)^4}{\sigma^4} - 3
$$

正态分布峰度为0，一个正峰度的分布被称为厚尾分布，一个负峰度的分布被称为薄尾分布

#### 基于峰度与偏度的正态性检验——Jarque-Bera检验

假设$$Y_1, Y_2, \cdots, Y_n$$是一组独立同分布的数据，则Jarque-Bera检验定义为：

$$
JB = \frac{n g_1^2}{6} + \frac{n g_2^2}{24}
$$

其中$$g_1$$为样本偏度，$$g_2$$为样本峰度。

在正态性的零假设条件下，Jarque-Bera检验的统计数据分布近似服从**2个自由度的卡方分布**。如果统计量的值太大的话，Jarque-Bera检验拒绝正态性假设。

### 金融时间序列普遍特征总结

1. 均值不显著地不同于零
2. 基本不存在序列相关性（由样本的ACF、PACF和EACF可以得到）
3. 存在高阶相关结构（即波动集群），不独立同分布
4. 厚尾分布

## $$\text{ARCH}(1)$$模型

ARCH \(autoregressive conditional heteroscedasticity\)：自回归条件异方差模型

### 条件方差

一项金融资产的收益率数据（如$$\{r_t\}$$）通常是零均值序列无关的过程，即使它表现出波动集群。

→ 说明给定过去的收益率时$$r_t$$的条件方差并非常数

$$r_t$$**的条件方差（条件波动率）：** $$\sigma_{t|t-1}^2$$ ****

→ 下标$$t-1$$表示以$$t-1$$时刻前的收益率为条件

→ $$E(r_t^2) = \sigma_{t|t-1}^2$$ 

### $$\text{ARCH}(1)$$模型

$$
r_t = \sigma_{t|t-1} \epsilon_t \\
\sigma_{t|t-1}^2 = \omega + \alpha r_{t-1}^2
$$

其中$$\alpha$$和$$\omega$$是未知参数，$$\{\epsilon_t\}$$是具有**零均值和单位方差**的**独立同分布**随机变量，且$$\epsilon_t$$与 $$r_{t-j},\ j=1,2,\dots$$是相互独立的。

$$
E(r_t^2 | r_1, \cdots, r_{t-1}) = E(\sigma_{t|t-1}^2 \epsilon_t^2 | r_1, \cdots, r_{t-1}) \\
= \sigma_{t|t-1}^2 E(\epsilon_t^2 | r_1, \cdots, r_{t-1}) = \sigma_{t|t-1}^2 \cdot 1= \sigma_{t|t-1}^2
$$

#### 条件方差的替代表示

$$
\eta_t = r_t^2 - \sigma_{t|t-1}^2 \\
\Rightarrow\ r_t^2 = \sigma_{t|t-1}^2 + \eta_t = \omega + \alpha r_{t-1}^2 + \eta_t
$$

$$\eta_t$$的特征：

1. $$\{\eta_t\}$$是均值为零的不相关序列：$$E(\eta_t) = 0, \text{Cov}(\eta_t, \eta_{t-k}) = 0 $$ 
2. $$\eta_t$$与过去的收益率不相关：$$\text{Cov}(\eta_t, r_{t-k}) = 0$$ 

$$r_t^2 = \omega + \alpha r_{t-1}^2 + \eta_t$$形式的导出结论：

1. $$\omega \geq 0, \alpha \geq 0$$ 
2. 平稳条件为 $$0 \leq \alpha < 1$$，此时 $$\sigma^2 = \Large\frac{\omega}{1-\alpha}$$ 

#### $$\text{ARCH}(1)$$模型的厚尾分布特征

$$\text{ARCH}(1)$$模型的平稳分布始终为厚尾分布。

#### $$\text{ARCH}(1)$$模型的预测

* 1步向前条件方差

$$
\sigma_{t+1|t}^2 = \omega + \alpha r_t^2 = (1-\alpha) \sigma^2 + \alpha r_t^2
$$

* h步向前条件方差

$$
\begin{align}
\sigma_{t+h|t}^2 &= E(r_{t+h}^2 | r_t, r_{t-1}, \cdots) = E[E(\sigma_{t+h|t+h-1}^2 \epsilon_{t+h}^2 | r_{r+h-1}, r_{t+h-2}, \cdots) | r_t, r_{t-1}, \cdots] \\
&= E[\sigma_{t+h|t+h-1}^2 E(\epsilon_{t+h}^2) | r_t, r_{t-1}, \cdots] = E(\sigma_{t+h|t+h-1}^2 | r_t, r_{t-1}, \cdots) \\
&= E(\omega + \alpha r_{t+h-1}^2 | r_t, r_{t-1}, \cdots) = \omega + \alpha E(r_{t+h-1}^2 | r_t, r_{t-1}, \cdots) \\
&= \omega + \alpha \sigma_{t+h-1|t}^2

\end{align}
$$

在$$h<0$$的情况下，$$\sigma_{t+h|t}^2 = r_{t+h}^2$$ 。

### $$\text{ARCH}(q)$$模型

$$
\sigma_{t|t-1}^2 = \omega +\alpha_1 r_{t-1}^2 + \cdots + \alpha_q r_{t-q}^2
$$

## GARCH模型

### $$\text{GARCH}(p,q)$$模型

$$
\sigma_{t|t-1}^2 = \omega + \beta_1 \sigma_{t-1|t-2}^2 + \cdots + \beta_p \sigma_{t-p|t-p-1}^2 + \alpha_1 r_{t-1}^2 + \cdots + \alpha_q r_{t-q}^2 \\ \quad \\
\Rightarrow\ (1 - \beta_1 B - \cdots - \beta_p B^p) \sigma_{t|t-1}^2 = \omega + (\alpha_1 B + \cdots + \alpha_q B^q) r_t^2
$$

#### 条件方差的替代表示

$$
\begin{align}
&\eta_t = r_t^2 - \sigma_{t|t-1}^2 \\
&\Rightarrow\ r_t^2 = \sigma_{t|t-1}^2 + \eta_t \\
&= \omega + \beta_1 \sigma_{t-1|t-2}^2 + \cdots + 
\beta_p \sigma_{t-p|t-p-1}^2 + \alpha_1 r_{t-1}^2 + \cdots + \alpha_q r_{t-q}^2 + \eta_t \\
&= \omega + \beta_1 (r_{t-1}^2 - \eta_{t-1}) + \cdots + \beta_p (r_{t-p}^2 - \eta_{t-p}) + \alpha_1 r_{t-1}^2 + \cdots + \alpha_q r_{t-q}^2 + \eta_t \\
&= \omega + (\alpha_1 + \beta_1) r_{t-1}^2 + \cdots + (\alpha_k + \beta_k) r_{t-k}^2 + \eta_t - \beta_1 \eta_{n-1} - \cdots - \beta_p \eta_{n-p}
\end{align}
$$

其中$$k = \max \{p,q\} \geq p,\ \beta_k=0 (\forall k>p),\ \alpha_k=0(\forall k>q)$$

$$r_t^2 = \omega + (\alpha_1 + \beta_1) r_{t-1}^2 + \cdots + (\alpha_k + \beta_k) r_{t-k}^2 + \eta_t - \beta_1 \eta_{n-1} - \cdots - \beta_p \eta_{n-p}$$的形式蕴含了一个 $$\text{ARMA}(\max\{p,q\},\ p)$$模型。

#### $$\text{GARCH}(p,q)$$模型弱平稳的充要条件

$$
\begin{align}
\sigma^2 &= E(r_t^2) \\
&= E[\omega + (\alpha_1 + \beta_1) r_{t-1}^2 + \cdots + (\alpha_k + \beta_k) r_{t-k}^2 + \eta_t - \beta_1 \eta_{n-1} - \cdots - \beta_p \eta_{n-p}] \\
& = \omega + \sum_{i=1}^{\max\{p,q\}} (\alpha_i + \beta_i) \sigma^2 \\
&\Rightarrow\ \sigma^2 = \frac{\omega}{1 - \sum\limits_{i=1}^{\max\{p,q\}} (\alpha_i + \beta_i)}
\end{align}
$$

$$\text{GARCH}(p,q)$$模型弱平稳的充要条件为：$$\sum\limits_{i=1}^{\max\{p,q\}} (\alpha_i + \beta_i) < 1$$ 

### GARCH模型识别方法

1. 给出序列的平方值和绝对值的样本EACF矩阵来确定$$\max\{p,q\}$$和 $$p$$
2. 如果$$p>q$$，则$$q$$会无法识别，可先拟合$$\text{GARCH}(p,p)$$模型，再对所得到的ARCH系数估计量进行显著性检验，从而估计$$q$$

### $$\text{GARCH}(1,1)$$模型的预测

$$
\sigma_{t|t-1}^2 = \omega + \beta \sigma_{t-1|t-2}^2 + \alpha r_{t-1}^2
$$

平稳方差：

$$
\sigma^2 = \omega + (\alpha + \beta) \sigma^2 \\ \quad \\
\Rightarrow\ \sigma^2 = \frac{\omega}{1-\alpha-\beta}
$$

设定初始条件方差$$\sigma_{1|0}^2 = \sigma^2$$或$$\sigma_{1|0}^2 = r_1^2$$

$$
\begin{align}
\sigma_{t+h|t}^2 &= E(r_{t+h}^2 | r_t, r_{t-1} ,\cdots) \\
&= E[E(\sigma_{t+h|t+h-1}^2 \epsilon_{t+h}^2 | r_{t+h-1}, r_{t+h-2}, \cdots) | r_t, r_{t-1}, \cdots] \\
&= E(\sigma_{t+h|t+h-1}^2 | r_t, r_{t-1}, \cdots) \\
&= E(\omega + \beta \sigma_{t+h-1|t+h-2}^2 + \alpha r_{t+h-1}^2 | r_t, r_{t-1}, \cdots) \\
&= \omega + \beta \sigma_{t+h-1|t}^2 + \alpha \sigma_{t+h-1|t}^2 \\
&= \omega + (\beta  + \alpha) \sigma_{t+h-1|t}^2
\end{align}
$$

### $$\text{GARCH}(1,1)$$模型参数的极大似然估计

$$
\sigma_{t|t-1}^2 = \omega + \alpha r_{t-1}^2 + \beta \sigma_{t-1|t-2}^2
$$

其中 $$t \geq 2,\ \sigma_{1|0}^2 = \sigma^2 = \Large\frac{\omega}{1-\alpha-\beta}$$。

假定$$\epsilon_t = \Large\frac{r_t}{\sigma_{t|t-1}}\normalsize\ \text{i.i.d} \sim\ N(0,1)$$ ，有似然函数

$$
a = b
$$







### 模型诊断












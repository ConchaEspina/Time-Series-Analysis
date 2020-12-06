---
description: 课本第6章
---

# 模型识别

> 对于给定的时间序列，如何选取适当的$$p, d, q$$值

## 样本自相关函数的性质

$$
r_k = \hat{\rho}_k = \frac{\sum\limits_{t=k
+1}^n (Y_t - \bar{Y})(Y_{t-k} - \bar{Y})}{\sum\limits_{t=1}^n (Y_t - \bar{Y})^2}, \quad k=1,2,\cdots
$$

$$
E(r_k) = \rho_k
$$

### 白噪声

$$
\text{Var}(r_k) \approx \frac{1}{n},\ \text{Corr}(r_k, r_j) \approx 0\ (k \neq j)
$$

### $$\text{AR}(1)$$过程

$$
\text{Var}(r_k)  \approx \frac{1}{n} \huge[\normalsize \frac{(1+\phi^2)(1-\phi^{2k})}{1-\phi^2} - 2k\phi^{2k} \huge]
$$

#### 特例

* $$k = 1$$时的方差 

$$
\text{Var}(r_1) \approx \frac{1-\phi^2}{n}
$$

{% hint style="info" %}
$$\phi$$越接近$$\pm 1$$，对$$\rho_1$$的估计就越精确。
{% endhint %}

* $$k$$较大时的方差

$$
\text{Var}(r_k) \approx \frac{1}{n} \huge[\normalsize \frac{1+\phi^2}{1-\phi^2} \huge]
$$

{% hint style="info" %}
$$\phi$$接近$$\pm 1$$意味着$$r_k$$有较大的方差。
{% endhint %}

* $$r_1$$和 $$r_2$$的相关系数

$$
\text{Corr}(r_1, r_2) \approx 2\phi \sqrt{\frac{1-\phi^2}{1+2\phi^2-3\phi^4}}
$$

### $$\text{MA}(q)$$过程

$$
\text{Var}(r_k) = \frac{1}{n} \huge[\normalsize 1 + 2\sum_{j=1}^q \rho_j^2 \huge]\normalsize, \quad k>q
$$

在模型检验中可以用$$r$$来代替$$\rho$$以得到对$$r_k$$的估计。对时间序列是$$\text{MA}(q)$$的假设的验证可以通过**把**$$r_k$$**与正负2倍标准误差相比**来完成。当且仅当$$r_k$$落在这个范围外拒绝零假设。

## 偏自相关函数和扩展的自相关函数

\*\*\*\*$$k$$**阶滞后偏自相关系数：**消除中间介入变量$$Y_{t-1}, Y_{t-2}, \cdots, Y_{t-k+1}$$的影响后 $$Y_t$$和$$Y_{t-k}$$的的相关系数函数。

### 偏自相关函数的两种更精确定义

#### 基于正态分布

$$
\phi_{kk} = \text{Corr}(Y_t, Y_{t-k}\ |\ Y_{t-1}, Y_{t-2}, \cdots, Y_{t-k+1})
$$

 即$$\phi_{kk}$$二元分布 $$Y_t$$和$$Y_{t-k}$$的以 $$Y_{t-1}, Y_{t-2}, \cdots, Y_{t-k+1}$$为条件的相关系数。

#### 基于中间变量对$$Y_t$$的预测








































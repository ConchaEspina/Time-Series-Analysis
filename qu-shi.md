---
description: 课本第3章
---

# 趋势

## 常数均值的估计

$$
Y_t = \mu + X_t
$$

其中 $$E(X_t) = 0$$ 

$$\mu$$的无偏估计：

$$
\bar{Y} = \frac{1}{n} \sum_{t=1}^n Y_t
$$

 性质：（假设 $$\{Y_t\} $$ 或等价地 $$\{X_t\} $$ 是平稳时间序列）

1. $$E(\bar{Y}) = \mu$$ 
2. $$\text{Var}(\bar{Y}) =  \Large\frac{\gamma_0}{n} [\normalsize \sum\limits^{n-1}_{k=-n+1} (1 - \Large\frac{|k|}{n} \normalsize)\rho_k \Large] \normalsize =  \Large\frac{\gamma_0}{n} [\normalsize 1 + 2 \sum\limits^{n-1}_{k=1} (1 - \Large\frac{k}{n} \normalsize)\rho_k \Large]$$ 

## 回归方法

### 时间的线性趋势和二次趋势

线性趋势：

$$
\mu_t = \beta_0 + \beta_1 t
$$

估计方法：古典最小二乘

$$
\begin{align}
&Q(\beta_0, \beta_1) = \sum_{t=1}^n [Y_t - (\beta_0 + \beta_1 t)]^2 \\

\Rightarrow &\hat{\beta}_0 =  \bar{Y} - \hat{\beta}_1 \bar{t} \\
&\hat{\beta}_1 = \frac{\sum\limits_{t=1}^n (Y_t - \bar{Y})(t-\bar{t})}{\sum\limits_{t=1}^n (t-\bar{t})^2}
\end{align}
$$

### 周期性或季节性趋势

$$
Y_t = \mu_t + X_t
$$

其对所有 $$t$$，$$E(X_t) = 0,\ \mu_t = \mu_{t-k}$$，$$|k|$$ 为周期

## 残差分析

无法观测的随机项 $$\{X_t\}$$ 可以通过残差来估计或预测：

$$
\hat{X_t} = Y_t - \hat{\mu}_t
$$

### 残差的特性

* 如果趋势模型恰当，残差应当基本上像真实随机项那样变化
* 如果随机项是白噪声，那么残差在行为上应该大致类似于均值为0、标准差为一有限正数的独立（正态）随机变量

### 残差分析步骤

一般先对残差做标准化

1. 观察残差的时间序列图 → 是否为没有明显模式的矩形散点图？
2. 观察残差与估计的相应趋势 →残差的大小与拟合的趋势值的大小有没有相关关系？
3. 观察残差的直方图/QQ图 → 残差是否具有显著正态性？












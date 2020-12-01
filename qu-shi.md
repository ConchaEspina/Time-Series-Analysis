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














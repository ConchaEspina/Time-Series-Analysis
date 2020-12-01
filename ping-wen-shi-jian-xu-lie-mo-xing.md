---
description: 课本第4章
---

# 平稳时间序列模型

## 一般线性过程

$$
Y_t = e_t + \psi_1 e_{t-1} + \psi_2 e_{t-2} + \cdots \\
\quad \\
s.t.\ \sum_{i=1}^\infty \psi_i^2 < \infty,\ \psi_0 = 1
$$

### 特例：$$\psi$$为指数递减形式

$$\psi_j = \phi^j, \quad -1<\phi<1$$ 

$$
Y_t = e_t + \phi e_{t-1} + \phi^2 e_{t-2} + \cdots
$$

#### 指数递减形式一般线性过程的性质

* 均值：$$E(Y_t) = 0$$ 
* 方差：$$\text{Var}(Y_t) = \Large\frac{\sigma^2_e}{1-\phi^2}$$ 
* 协方差：$$\text{Cov}(Y_t, Y_{t-k}) = \Large\frac{\phi^k \sigma^2_e}{1-\phi^2}$$ → 只与 $$k$$ 有关，说明该过程平稳
* 自相关函数： $$\text{Corr}(Y_t, Y_{t-k}) = \phi^k$$ 

### 一般线性过程的性质

* 均值：$$E(Y_t) = 0$$ 
* 方差：$$\text{Var}(Y_t) = \sigma^2_e \sum\limits_{i=0}^\infty \psi_i^2$$ 
* 协方差：$$\text{Cov}(Y_t, Y_{t-k}) = \sigma^2_e \sum\limits_{i=0}^\infty \psi_i \psi_{i+k},\quad k\geq0$$ → 只与 $$k$$ 有关，说明该过程平稳

## 滑动平均过程

**q阶滑动平均过程** $$\text{MA}(q)$$**：**

$$
Y_t = e_t - \theta_1 e_{t-1} - \theta_2 e_{t-2} - \cdots - \theta_q e_{t-q}
$$

### 一阶滑动平均过程

$$
Y_t = e_t - \theta e_{t-1}
$$

#### 一阶滑动平均模型的性质

* 均值：$$E(Y_t) = 0$$ 
* 方差：$$\gamma_0 = (1+\theta^2)\sigma^2_e$$ 
* 协方差：$$\gamma_k = \begin{cases}  -\theta\sigma^2_e,\quad k=1 \\   0, \quad k\geq2 \end{cases}$$ 
* 自相关函数：$$\rho_k = \begin{cases}  -\frac{\theta}{1+\theta^2},\quad k=1 \\   0, \quad k\geq2 \end{cases}$$ 

> 当连续观测值密切正相关时，如果一个观测值高于序列平均值，那么下一个观测值往往也高于平均值，图形随时间的变化较为平滑，偶尔有大的波动。当连续观测值密切负相关时，如果一个观测值高于序列平均值，那么下一个观测值往往会低于平均值，图形随时间的推移呈锯齿状，围绕均值来回震荡。

### 二阶滑动平均过程

$$
Y_t = e_t - \theta_1 e_{t-1} - \theta_2 e_{t-2}
$$

#### 二阶滑动平均模型的性质

* 均值：$$E(Y_t) = 0$$ 
* 方差：$$\gamma_0 = (1+\theta_1^2+\theta_2^2)\sigma^2_e$$ 
* 协方差：$$\gamma_k = \begin{cases}  (-\theta_1+\theta_1\theta_2)\sigma^2_e, \quad k=1 \\ -\theta_2 \sigma_e^2, \quad k=2\\    0, \quad k\geq3 \end{cases}$$ 
* 自相关函数：$$\rho_k = \begin{cases}  \frac{-\theta_1+\theta_1\theta_2}{1+\theta_1^2+\theta_2^2},\quad k=1 \\  \frac{-\theta_2}{1+\theta_1^2+\theta_2^2}, \quad k=2 \\   0, \quad k\geq3 \end{cases}$$ 

### 一般$$\text{MA}(q)$$过程

$$
Y_t = e_t - \theta_1 e_{t-1} - \theta_2 e_{t-2} - \cdots - \theta_q e_{t-q}
$$

#### q阶滑动平均模型的性质

* 均值：$$E(Y_t) = 0$$ 
* 方差：$$\gamma_0 = (1+\theta_1^2+\theta_2^2+\cdots+\theta_q^2)\sigma^2_e$$ 
* 协方差：$$\gamma_k = \begin{cases}  (-\theta_k+\theta_1\theta_{k+1}+\theta_2\theta_{k+2}+\cdots+\theta_{q-k}\theta_q)\sigma^2_e, \quad k=1,\dots,q \\ 0, \quad k>q \end{cases}$$ 
* 自相关函数：$$\rho_k = \begin{cases}  \large\frac{-\theta_k+\theta_1\theta_{k+1}+\theta_2\theta_{k+2}+\cdots+\theta_{q-k}\theta_q}{1+\theta_1^2+\theta_2^2+\cdots+\theta_q^2}, \quad \normalsize k=1,\dots,q \\ 0, \quad k>q \end{cases}$$  → 自相关函数在滞后q期“截尾”

## 自回归过程


















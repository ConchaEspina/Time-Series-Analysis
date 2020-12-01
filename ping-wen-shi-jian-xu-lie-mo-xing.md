---
description: 课本第4章
---

# 平稳时间序列模型

## 一般线性过程

$$
Y_t = e_t + \psi_1 e_{t-1} + \psi_2 e_{t-2} + \cdots \\
\quad \\
s.t.\ \sum_{I=1}^\infty \psi_i^2 < \infty
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









## 滑动平均过程



























## 自回归过程


















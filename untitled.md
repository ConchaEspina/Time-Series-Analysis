# 基本概念

## 均值、方差和协方差

对随机过程$$\{Y_t\}$$ ，有：

* 均值函数： $$\mu_t = E(Y_t)$$ 
* 自协方差函数： $$\gamma_{t,s} = Cov(Y_t, Y_s)$$ 
* 自相关函数： $$\rho_{t,s} = Corr(Y_t, Y_s) = \Large\frac{\gamma_{t,s}}{\sqrt{\gamma_{t,t} \gamma_{s,s}}}$$ 

_均值、自协方差、自相关的性质_

### 随机游动

$$e_1, e_2, \dots$$ 为均值是0，方差是 $$\sigma^2_e$$ 的独立同分布的随机变量序列

随机游动过程：

$$
\begin{cases}
\begin{align}
Y_1 &= e_1 \\
Y_2 &= e_1 +e_2 \\
&\vdots \\
Y_t &= e_1 + e_2 + \cdots + e_t
\end{align}
\end{cases}
$$

或写作

$$
Y_t = Y_{t-1} + e_t
$$

性质：

* 均值： $$\mu_t = E(Y_t) = 0$$ 
* 方差： $$\text{Var}(Y_t) = t\sigma^2_e$$ 
* 协方差： $$\gamma_{t,s} = t\sigma^2_e \quad (1\leq t \leq s)$$ 
* 自相关函数： $$\rho_{t,s} = \Large\sqrt{\frac{t}{s}} \normalsize\quad (1\leq t \leq s)$$ 

### 滑动平均

$$
Y_t = \frac{e_t + e_{t-1}}{2}
$$

性质：

* 均值： $$\mu_t = E(Y_t) = 0$$ 
* 方差与协方差： $$\gamma_{t,s} =  \begin{cases}  0.5\sigma^2_e,\quad |t-s|=0 \\ 0.25\sigma_e^2, \quad |t-s| = 1 \\ 0, \quad |t-s| >1 \end{cases}$$ 
* 自相关函数： $$\rho_{t,s} =  \begin{cases}  1,\quad |t-s|=0 \\ 0.5, \quad |t-s| = 1 \\ 0, \quad |t-s| >1 \end{cases}$$ 
















---
description: 课本第7章
---

# 参数估计

> 如何估计一个识别的$$\text{ARIMA}(p,d,q)$$模型的参数

## 矩估计

令样本矩等于相应的原点矩

### 自回归模型

#### $$\text{AR}(1)$$模型

$$
\hat\phi = r_1
$$

#### $$\text{AR}(2)$$模型

$$
\begin{cases}
\rho_1 = \phi_1 + \rho_1\phi_2 \\
\rho_2 = \rho_1\phi_1 + \phi_2
\end{cases}
 \\ \quad \\
\Rightarrow\ \begin{cases}
\phi_1 = \Large\frac{\rho_1(1-\rho_2)}{1-\rho_1^2} \\
\phi_2 = \Large\frac{\rho_2-\rho_1^2}{1-\rho_1^2}
\end{cases} \\ \quad \\
\Rightarrow\ \begin{cases}
\hat{\phi}_1 = \Large\frac{r_1(1-r_2)}{1-r_1^2} \\
\hat{\phi}_2 = \Large\frac{r_2-r_1^2}{1-r_1^2}
\end{cases}
$$

#### $$\text{AR}(p)$$模型

Yule-Walker估计：

$$
\begin{cases}
\phi_1 + r_1 \phi_2 + r_2 \phi_3 + \cdots + r_{p-1} \phi_p = r_1 \\
r_1 \phi_1 + \phi_2 + r_1 \phi_3 + \cdots + r_{p-2} \phi_p = r_2 \\
\qquad \qquad \qquad \qquad \vdots \\
r_{p-1} \phi_1 + r_{p-2} \phi_2 + r_{p-3} \phi_3 + \cdots + \phi_p = r_p
\end{cases} \\ \quad \\
\Rightarrow\ \hat\phi_1, \hat\phi_2, \dots, \hat\phi_p
$$

可用[Durbin-Levinson方程](model-specification.md#yang-ben-pian-zi-xiang-guan-han-shu)求解，但如果解接近平稳域的边界，则会产生较大的舍入误差。

### 滑动平均模型

#### $$\text{MA}(1)$$模型

$$
\rho_1 = -\frac{\theta}{1+\theta^2} \\ \quad \\
\Rightarrow\ r_1 = -\frac{\hat\theta}{1+\hat\theta^2} \\ \quad \\
\Rightarrow\ \hat\theta = -\frac{1}{2r_1} \pm \sqrt{\frac{1}{4r_1^2}-1}
$$

其中可逆解为 $$\hat\theta = \Large\frac{-1+\sqrt{1-4r_1^2}}{2r_1}$$ 

{% hint style="warning" %}
当$$|r_1| > 0.5$$时无法通过矩估计法得出$$\theta$$的估计量。
{% endhint %}

#### $$\text{MA}(q)$$模型

高度非线性，通过矩估计法很难求解。

采用矩估计法估计MA模型一般效果较差。

### 混合模型

$$\text{ARMA}(1,1)$$ 模型：

$$
\rho_k = \frac{(1-\theta\phi)(\phi-\theta)}{1-2\theta\phi+\theta^2} \phi^{k-1},\quad k \geq 1 \\ \quad \\
\Rightarrow\ \phi = \frac{\rho_2}{\rho_1} \\ \quad \\
\Rightarrow\ \hat\phi = \frac{r_2}{r_1}
$$

$$
r_1 = \frac{(1-\theta\hat{\phi})(\hat{\phi}-\theta)}{1-2\theta\hat{\phi}+\theta^2} \\ \quad \\
\Rightarrow \hat{\theta}
$$

若解存在，仅保留其中的可逆解。

### 噪声方差估计

估计$$\gamma_0 = \text{Var}(Y_t)$$：

$$
s^2 = \frac{1}{n-1} \sum_{t=1}^n (Y_t - \bar{Y})^2
$$

#### $$\text{AR}(p)$$模型

$$
\gamma_0 = \text{Var}(Y_t) = \text{Cov}(Y_t,\ \phi_1 Y_{t-1} + \cdots + \phi_p Y_{t-p} + e_t) \\
= \phi_1 \gamma_1 + \cdots + \phi_p \gamma_p + \sigma_e^2 = (\phi_1 \rho_1 + \cdots + \phi_p \rho_p) \gamma_0 + \sigma_e^2 \\ \quad \\
\Rightarrow\ \sigma_e^2 = (1 - \phi_1 \rho_1 - \cdots - \phi_p \rho_p) \gamma_0 \\ \quad \\
\Rightarrow\ \hat{\sigma}_e^2 = (1 - \hat{\phi}_1 r_1 - \cdots - \hat{\phi}_p r_p) s^2
$$

对$$\text{AR}(1)$$过程： $$\hat{\sigma}_e^2 = (1 - r_1^2)s^2$$ 

#### $$\text{MA}(q)$$模型

$$
\gamma_0 = \text{Var}(Y_t) = \text{Var}(e_t - \theta_1 e_{t-1} - \cdots - \theta_q e_{t-q}) = (1 + \theta_1^2 + \cdots + \theta_q^2) \sigma_e^2 \\ \quad \\
\Rightarrow\ \hat{\sigma}_e^2 = \frac{s^2}{1 + \hat{\theta_1}^2 + \cdots + \hat{\theta}_q^2}
$$

#### $$\text{ARMA}(1,1)$$模型

$$
\gamma_0 = \text{Var}(Y_t) = \text{Var}(\phi Y_{t-1} + e_t -\theta e_{t-1}) = \phi^2 \gamma_0 + (1  - 2\phi\theta + \theta^2) \sigma_e^2 \\ \quad \\
\Rightarrow\ \sigma_e^2 = \frac{1 - \phi^2}{1  - 2\phi\theta + \theta^2} \gamma_0 \\ \quad \\
\Rightarrow\ \hat{\sigma}_e^2 = \frac{1 - 
\hat{\phi}^2}{1  - 2\hat{\phi} \hat{\theta} + \hat{\theta}^2} s^2
$$

## 最小二乘估计

### 自回归模型















### 滑动平均模型













### 混合模型













## 极大似然与无条件最小二乘






















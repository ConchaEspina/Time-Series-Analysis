---
description: 课本第10章
---

# 季节模型

## 干预分析

假设干预是通过改变时间序列的**均值函数或趋势**而对过程施加影响的。

$$
Y_t = m_t + N_t
$$

其中$$m_t$$代表均值函数的变化，$$N_t$$代表未受干预影响的基础时间序列，称作自然过程或无扰过程。

**预干预数据：**假设在$$T$$之前，$$m_t$$与0无异，称时间序列 $$\{Y_t,\ t<T\}$$ 为预干预数据。

### 阶梯函数与脉冲函数

阶梯函数：

$$
S_t^{(T)} = I(t \geq T) = 
\begin{cases}
1,\quad t \geq T \\
0,\quad \text{otherwise}
\end{cases}
$$

阶梯函数在预干预期间为0，干预之后为1。

脉冲函数：

$$
P_t^{(T)} = S_t^{(T)} - S_{t-1}^{(T)} =  I(t = T) = 
\begin{cases}
1,\quad t=T \\
0,\quad \text{otherwise}
\end{cases}
$$

$$P_t^{(T)}$$是干预发生时间的指示器或虚拟标志变量。

$$
P_t^{(T)} = (1-B) S_t^{(T)}  \\
S_t^{(T)} = \frac{1}{1-B} P_t^{(T)}
$$

### 偏移

即时偏移：

$$
m_t = \omega S_t^{(T)}
$$

延迟偏移：

$$
m_t = \omega S_{t-d}^{(T)}
$$

### 常见干预模型

#### 阶梯响应干预示例

$$
m_t = \delta m_{t-1} + \omega S_{t-1}^{(T)} = 
\begin{cases} 
\omega \Large\frac{1 - \delta^{t-T}}{1 - \delta}\normalsize,\quad t > T   \\
0,\quad \text{otherwise}
\end{cases}
$$

其中 $$m_0=0$$（后续示例同假设）。

* $$0<\delta<1$$：$$m_t \to \Large\frac{\omega}{1-\delta}$$ ​即均值函数的最终变化量
* $$\delta = 1$$：$$m_t = \omega(T-t), \quad t \geq T$$ 

#### 脉冲响应干预示例

只在某一时点产生影响的干预效应：

$$
m_t = \omega P_t^{(T)}
$$

逐渐消失且无延迟的干预效应：

$$
m_t = \delta m_{t-1} + \omega P_t^{(T)} = \omega \delta^{T-t} I(t \geq T)
$$

逐渐消失且有延迟的干预效应：

$$
m_t = \delta m_{t-1} + \omega P_{t-1}^{(T)} \\ \quad \\
\Rightarrow\ m_t = \delta B m_t + \omega B P_t^{(T)} = \frac{\omega B}{1 - \delta B} P_t^{(T)}
$$

#### 均值函数变化的ARMA类型表达式

$$
m_t = \frac{\omega(B)}{\delta(B)} P_t^{(T)}
$$

用阶梯虚拟变量来表示也可。

## 异常值

### 可加异常值与新息异常值

| 可加异常值（AO） | 新息异常值（IO） |
| :---: | :---: |
| 基础过程受到可叠加性的扰动 | 误差（新息）受到扰动 |
| $$Y_t^\prime = Y_t + \omega_A P_t^{(T)} \\ = \begin{cases}Y_T + \omega_A,\quad t=T \\ Y_t,\quad t \neq T \end{cases}$$  | $$e_t^\prime = e_t + \omega_I P_t^{(T)} \\ =  \begin{cases}e_T + \omega_I,\quad t=T \\ e_t,\quad t \neq T \end{cases}$$  |
| $$m_t = \omega_A P_t^{(T)}$$  | $$Y_t^\prime = Y_t + \psi_{t-T} \omega_I$$  |
| 只在时刻$$T$$的观测值受到影响 | 时刻$$T$$及其后的所有观测值都受到影响 |

### 异常值类型的识别

#### 新息异常值（IO）的识别

**残差：**

$$
a_t = Y_t^\prime - \pi_1 Y_{t-1}^\prime - \pi_2 Y_{t-2}^\prime - \cdots
$$

假设过程均值为0且所有参数已知（未知的参数用样本估计量替代）

如果序列只在时刻$$T$$有IO：

$$
a_t = \begin{cases}
a_T + \omega_I,\quad t=T \\
a_t,\quad t \neq T
\end{cases}
$$

$$\omega_I$$可用$$\tilde{\omega}_I = a_T$$来估计。

**时刻**$$T$$**上IO的检验统计量：**

$$
\lambda_{1,T} = \frac{a_T}{\sigma}\ \dot\sim\ N(0,1)
$$

**假设：**

* **零假设：**无异常值 → 此时检验统计量近似服从标准正态分布
* **备择假设：**在$$T$$时刻存在异常值

**检验方法：**Bonfferoni律

$$
\lambda_1 = \max_{1 \leq t \leq n} |\lambda_{1,t}|
$$

假设$$\lambda_{1,t}$$的最大值在$$t = T$$时取到，如果$$\lambda_1 > Z_{1-\frac{\alpha}{2n}}$$，那么认为第$$T$$个观测值必然是IO。（误判率不大于$$\alpha$$）

{% hint style="info" %}
异常值可能导致$$\sigma$$的极大似然估计值偏大，因此可以采取一种对于噪声标准差的稳健估计来代替极大似然估计。
{% endhint %}

#### 可加异常值（AO）的识别

假设过程只在时刻$$T$$上存在AO，在其他时点上无异常值。

$$
a_t = - \omega_A \pi_{t-T} + e_t = 
\begin{cases}
e_t,\quad t<T \\
\omega_A + e_T,\quad t=T \\
 - \omega_A \pi_{t-T} + e_t,\quad t>T
\end{cases}
$$

其中 $$\pi_j = \begin{cases}-1,\quad j=0 \\ 0,\quad j<0 \end{cases}$$。

\*\*\*\*$$\omega_A$$**的最小二乘估计：**

$$
\tilde{\omega}_{T,A} = - \rho^2 \sum_{t=1}^n \pi_{t-T} a_t
$$

其中$$\rho^2 = (1 + \pi_1^2 + \pi_2^2 + \cdots + \pi_{n-T}^2)^{-1},\ \text{Var}(\tilde{\omega}_{T,A}) = \rho^2\sigma^2$$ 

**时刻**$$T$$**上AO的检验统计量：**

$$
\lambda_{2,T} = \frac{\tilde{\omega}_{T,A}}{\rho\sigma} \to N(0,1)
$$

**假设：**

* **零假设：**无异常值 → 此时检验统计量渐近服从标准正态分布
* **备择假设：**在$$T$$时刻存在异常值

**检验方法：**通常$$T$$未知，需要重复对每个时间点进行检验，再次用Bonfferoni律来控制总体误差。**当在时间**$$T$$**上检验到异常值时，如果**$$|\lambda_{1,T}| > |\lambda_{2,T}|$$**，则可将观测值归类到IO，否则就是AO。**

{% hint style="info" %}
当找出一个异常之后，可将其纳入模型中，然后反复对修正的模型进行异常值检验，直到不再发现异常值为止。
{% endhint %}

## 伪相关











## 预白化与随机回归
















---
description: 课本第11章
---

# 时间序列回归模型

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
| $$a = b$$  |  |
|  |  |








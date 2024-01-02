

# 随机过程课程作业-**Week15**

**作者**：48-丁力-202328015926048  
**日期**：今天

---

## 目录

- [泊松过程](#马尔科夫过程)
  - [题目1](#题目1)
  - [题目2(#题目2)

---

## 二阶矩过程、平稳过程和随机分析

### 1.设 $X_n=\sum_{k=1}^N \sigma_k \sqrt{2} \cos \left(\alpha_k n-U_k\right)$, 其中 $\sigma_k$ 和 $\alpha_k$ 为正常数, $U_k \sim U(0,2 \pi)$, 且相互独立, $k=1,2, \cdots, N$, 试计算 $\left\{X_n, n=0, \pm 1, \cdots\right\}$ 的均值函数和相关函数, 并说明其是否是平稳过程。

> 首先尝试计算其均值函数:
> $$
> \begin{align}
> E(X_n) &= E( \sum_{k=1}^N \sigma_k \sqrt{2} \cos \left(\alpha_k n-U_k\right) )\\
> &= \sum_{k=1}^N \sigma_k \sqrt{2} E(  \cos \left(\alpha_k n-U_k\right) )\\
> &= \sum_{k=1}^N \sigma_k \sqrt{2} E( \cos(\alpha_kn) \cos(U_k)+\sin(\alpha_kn) \sin(U_k)+ )\\
> &= 0
> \end{align}
> $$
> 然后尝试计算其相关函数:
> $$
> \begin{align}
> R_x(m,n) &= E([\sum_{k=1}^N \sigma_k \sqrt{2} \cos \left(\alpha_k m-U_k\right)][\sum_{k=1}^N \sigma_k \sqrt{2} \cos \left(\alpha_k n-U_k\right)])\\
> & =2 \sum_{i=1}^N \sum_{j=1}^N \sigma_i \sigma_j E\left\{\cos \left(\alpha_i n-U_i\right) \cos \left(\alpha_j m-U_j\right)\right\}\\
> &= 2 \sum_{i=1}^N \sigma_i^2 E\left\{\cos \left(\alpha_i n-U_i\right) \cos \left(\alpha_i m-U_i\right)\right\}\\
> &=\sum_{i=1}^N \sigma_i^2 \cos \left[\alpha_i(n-m)\right]
> 
> 
> 
> \end{align}
> $$
> 由于其期望是常数，并且自相关函数是只依赖于时间间隔，所以其为平稳过程。







### 2.设有随机过程 $X(t)=A \cos (\omega t+\pi \eta(t))$, 其中 $\omega>0$ 为常数, $\{\eta(t), t \geq 0\}$ 是泊松过程, $A$ 是与 $\eta(t)$ 独立的随机变量, 且 $P\{A=-1\}=P\{A=1\}=1 / 2$ 。
(1)试画出此过程的样本函数, 并问样本函数是否连续?
(2)试求此过程的相关函数, 并问该过程是否均方连续?

> - (1)
>
> 泊松过程 $\eta(t)$ 是一个以离散跳跃形式增长的过程，这意味着 $\eta(t)$ 在跳跃点上不连续。由于 $X(t)$ 依赖于 $\eta(t)$，所以当 $\eta(t)$ 发生跳跃时，$X(t)$ 也会不连续。因此，这个过程的样本函数不是连续的。
>
> 借助于下述`Python`代码，我可以给出其样本函数:
>
> ```python
> import numpy as np
> import matplotlib.pyplot as plt
> # 设置参数
> omega = 1  # 频率omega
> time = np.linspace(0, 10, 1000)  # 时间范围为0到10秒，共1000个点
> # 生成泊松过程
> rate = 1  # 泊松过程的速率（跳跃频率），假设为每秒1次
> poisson_process = np.random.poisson(rate, time.shape)
> # 生成随机变量A的值
> A = np.random.choice([-1, 1], time.shape)
> # 计算随机过程X(t)
> X_t = A * np.cos(omega * time + np.pi * np.cumsum(poisson_process))
> # 绘制样本函数
> plt.figure(figsize=(12, 6))
> plt.plot(time, X_t)
> plt.title("Sample Function of the Random Process $X(t) = A \cos(\omega t + \pi \eta(t))$")
> plt.xlabel("Time (t)")
> plt.ylabel("$X(t)$")
> plt.grid(True)
> plt.show()
> 
> ```
>
> ![Output image](https://files.oaiusercontent.com/file-9DLB3ODiORn8sW8YDJwRz63k?se=2023-12-07T12%3A51%3A55Z&sp=r&sv=2021-08-06&sr=b&rscc=max-age%3D3599%2C%20immutable&rscd=attachment%3B%20filename%3De0bc1bed-5115-443f-97f8-67791cd2dd98&sig=jWoy1LEoYm45Nl/oP5D0hyaCmnMJ7w1Xrq7/aSKMzpE%3D)
>
> 从图中也能看出，其为不连续的。
>
> - (2)
>
> 现在我们来求其自相关函数如下:
> $$
> \begin{align}
> R(s,t)&= E(A \cos (\omega t+\pi \eta(s))\times A \cos (\omega t+\pi \eta(t)))\\ 
> &= A^2E(\cos (\omega s+\pi \eta(s))\cos (\omega t+\pi \eta(t)))\\
> &= \frac{A^2}{2}E(\cos(\omega (t+s)+\pi(\eta(s)+\eta(t)) + \cos(\omega (s-t) +\pi(\eta(s)-\eta(t))))\\
> &=\frac{A^2}{2} [E(\cos(\omega (t+s) +\pi(\eta(s)+\eta(t))) + 
> E(\cos(\omega (s-t) + \pi(\eta(s)-\eta(t))))
> ]\\
> & =\frac{1}{2} \sum_{k=0}^{\infty}(-1)^k\left\{\cos \left[\omega\left(t+s\right)\right]+\cos \left[\omega\left(s-t\right)\right]\right\} \cdot \frac{\left[\lambda\left(s-t\right)\right]^k}{k !} \cdot e^{-\lambda\left(s-t\right)} \\
> & =\frac{1}{2}\left\{\cos \left[\omega\left(s+t\right)\right]+\cos \left[\omega\left(s-t\right)\right]\right\} \cdot e^{-2 \lambda\left(s-t\right)} \\
> &= \cos \omega t \cos \omega s \cdot e^{-2 \lambda\left(s-t\right)}
> 
> 
> 
> \end{align}
> $$
> 在给定的随机过程$X(t) = A \cos(\omega t + \pi \eta(t))$ 中，我们发现相关函数 $ R_X(s, t) $ 在 $s$ 趋近于 $t$ 时，趋向于 $\cos^2 \omega t$，这表明即使时间点非常接近，随机过程在这两点上的值仍然有较强的相关性。这种特性表明了过程是均方连续的——即使考虑了随机变量的波动，随机过程在时间上仍然展现出一定程度的平滑性。

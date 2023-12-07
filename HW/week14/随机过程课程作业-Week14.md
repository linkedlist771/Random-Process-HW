

# 随机过程课程作业-**Week14**

**作者**：48-丁力-202328015926048  
**日期**：今天

---

## 目录

- [泊松过程](#马尔科夫过程)
  - [题目7](#题目1)
  - [题目8](#题目2)
  - [题目9](#题目3)

---

## 泊松过程

### 7. 某商场为调查客源情况, 考察男女顾客到达商场的人数。假设 $[0, t)$ 时间内男女顾客到达商场的人数分别独立地服从参数为 $\lambda$ 和 $\mu$ 的泊松过程。问:

(1) $[0, t)$ 时间内到达商场的总人数应该服从什么分布?
(2) 在已知 $[0, t)$ 时间内商场到达 $n$ 位顾客的条件下, 其中有 $k$ 位是女顾客的概率为何？平均有多少位女顾客？

> - (1)
>
> 假设$W(t)$和$M(t)$ 分别为$[0,t)$内到达的男顾客和女顾客人数。那么对于两者的总和的概率分布有:
> $$
> \begin{align}
> P(W(t)+M(t)=k) &= \sum_{i=0}^k P(W(t)=i) P(M(t)=k-i) \\
> &=  \sum_{i=0}^k    \frac{(\lambda t)^i}{i!}e^{-\lambda t} \frac{(\mu t)^{k-i}}{(k-i)!}e^{-\mu t}\\
> &=  \frac{((\lambda+\mu) t)^k}{k!}e^{-(\lambda+\mu) t}
> \end{align}
> $$
> 所以其服从参数为$\lambda+\mu$的泊松分布。
>
> - (2)
>
> 该概率为:
> $$
> \begin{align}
> 
> 
> P(W(t)=k|W(t)+M(t)=n) &= \frac{P(W(t)+M(t)=n, W(t)=k)}{P(W(t)+M(t)=n)}\\
> &= \frac{P(M(t)=n-k, W(t)=k)}{P(W(t)+M(t)=n)}\\
> &由于两者独立\\
> &= \frac{P(M(t)=n-k)P(W(t)=k)}{P(W(t)+M(t)=n)}\\
> &= \frac{    \frac{(\lambda t)^k}{k!}e^{-\lambda t} \frac{(\mu t)^{n-k}}{(n-k)!}e^{-\mu t}    }{ \frac{((\lambda+\mu) t)^n}{n!}e^{-(\lambda+\mu) t}}\\
> &= \frac{n\mu}{\mu+\lambda}
> 
> 
> 
> 
> \end{align}
> $$



### 8. 设在时间区间 $(0, t]$ 到达某商店的顾客数 $N(t), t \geq 0$ 是强度为 $\lambda>0$ 的齐次泊松过程， $N(0)=0$, 且每个顾客购买商品的概率 $p>0$, 没有买商品的概率为 $q=1-p$, 分别以 $X(t)$ 和 $Y(t)$ 表示 $(0, t]$ 所有购买商品的顾客数和所有没有购买商品的顾客数, $t \geq 0$ 。证明 $X(t)$ 和 $Y(t)$ 分别是服从参数为 $\lambda p$ 和 $\lambda q$ 的泊松过程, 并且是相互独立的。进一步求 $X(t)$ 和 $Y(t)$ 的均值函数 $m(t)$ 和相关函数 $R(s, t)$ 。
> 由题，我们可以知道:
> $$
> N(t) = X(t)+Y(t)
> $$
> 所以有：
> $$
> \begin{gathered}
> P\{X(t)=n, Y(t)=m\}=\sum_{k=0}^{\infty} P\{X(t)=n, Y(t)=m \mid N(t)=k\} P\{N(t)=k\} \\
> \quad=P\{X(t)=n, Y(t)=m \mid N(t)=n+m\} P\{N(t)=n+m\} \\
> \quad=C_{n+m}^n p^n q^m \frac{(\lambda t)^{n+m}}{(n+m) !} e^{-\lambda t}=\frac{(\lambda p t)^n}{n !} e^{-\lambda p t} \cdot \frac{(\lambda q t)^m}{m !} e^{-\lambda q t}
> \end{gathered}
> $$
> 首先求$X(t)$的分别，同理可得$Y(t)$的分布。
> $$
> \begin{align}
> P(X(t)=n) &= \sum_{m=0}^{\infty} P\{X(t)=n, Y(t)=m\} \\
> &=\sum_{m=0}^{\infty}\left[\frac{(\lambda p t)^n}{n !} e^{-\lambda p t} \cdot \frac{(\lambda q t)^m}{m !} e^{-\lambda q t}\right]\\
> &=\frac{(\lambda p t)^n}{n !} e^{-\lambda p t}
> 
> \end{align}
> $$
>
> 同理可得$Y(t)$的分布：
> $$
> \begin{align}
> P(Y(t)=m) 
> &=\frac{(\lambda p t)^m}{m !} e^{-\lambda q t}
> 
> \end{align}
> $$
> 所以有:
> $$
> P\{X(t)=n, Y(t)=m\} =P(X(t)=n) \times P(Y(t)=m)
> $$
> 所以两者独立，并且服从参数为$\lambda p, \lambda q$的泊松过程。
>
> 由泊松过程的性质可得：
> $$
> \begin{equation}
> \begin{aligned}
> & m_X(t)=E\{X(t)\}=\lambda p t, \quad t \geq 0, \quad m_Y(t)=E\{Y(t)\}=\lambda q t, \quad t \geq 0 \\
> & R_X(s, t)=E\{X(s) X(t)\}=(\lambda p)^2 s t+(\lambda p) \min \{s, t\}, \quad s, t \geq 0 \\
> & R_Y(s, t)=E\{Y(s) Y(t)\}=(\lambda q)^2 s t+(\lambda q) \min \{s, t\}, \quad s, t \geq 0
> \end{aligned}
> \end{equation}
> $$
> 





### 9. 在某公共汽车起点站, 有甲、乙两路公交车。设乘客到达甲、乙两路公交车的人数分别为参数 $\lambda_1 、 \lambda_2$ 的齐次 Poisson 过程, 且它们是相互独立的。假设 $t=0$ 时, 两路公交车同时开始接受乘客上车。

(1) 如果甲车在时刻 $t$ 发车, 计算在 $[0, t]$ 内到达甲车的乘客等待开车时间总和的期望值;
(2) 如果当甲路车上有 $n$ 个乘客时, 甲路车发车; 当乙路车上有 $m$ 个乘客时, 乙路车发车。求甲路车比乙路车发车早的概率。(写出表达式即可)

> - (1)
>
> 
>
> 乘客到站的时间为齐次 Poisson 过程中的阶跃点，其间隔服从指数分布。对于 Poisson 过程，事件间的时间间隔服从参数为
>
> $\lambda_1$, 指数分布的期望值为$\frac{1}{\lambda_1}$, 在时间内，每个乘客到达的时间可看作均匀分布在$[0,t]$所以其平均到达时间为:
> $$
> \frac{t}{2}
> $$
> 总时间为:
> $$
> k \times \frac{t}{2} = \frac{kt}{2}
> $$
> 
>
> 
>
> - (2)
>
> 假设$[0,t]$时刻到达甲车的人数为$M(t)$, 那么由于其满足泊松过程，那么我们有：
> $$
> \begin{align}
> P(M(t)=k) = \frac{(\lambda t)^k}{k!}e^{-\lambda_1 t}
> \end{align}
> $$
> 其期望为:
> $$
> m_M(t) = \lambda_1 t
> $$
> 假设第$i$个人，在第$S_i$个时刻降临，那么$[0,t]$时刻内到达甲车的乘客总等待时间为:
> $$
> \sum_{i=1}^{M(t)} (t-S_i)
> $$
> 当$M(t)=k$时：
> $$
> E(\sum_{i=1}^{M(t)} (t-S_i)|M(t)=k) = \frac{kt}{2}
> $$
> 那么其期望值为:
> $$
> E(S(t)) = \sum_{k=0}^\infty \frac{kt}{2} P(M(t)=k) = \frac{t}{2} E(M(t)) = \frac{\lambda_1 t^2}{2}
> $$
>
> - (2)
>
> $$
> P\left\{S_n<S_m\right\}=\int_0^{+\infty} d t_2 \int_0^{t_2} \frac{\left(\lambda_1 t_1\right)^{n-1}}{(n-1) !} \lambda_1 e^{-\lambda_1 t_1} \cdot \frac{\left(\lambda_2 t_2\right)^{m-1}}{(m-1) !} \lambda_2 e^{-\lambda_2 t_2} d t_1
> $$




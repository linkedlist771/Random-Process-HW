

# 随机过程课程作业-**Week8**

**作者**：48-丁力-202328015926048  
**日期**：今天

---

## 目录

- [马尔科夫过程](#马尔科夫过程)
  - [题目13](#题目1)
  - [题目14](#题目2)
  - [题目15](#题目3)
  - [题目16](#题目4)

---

## 马尔科夫过程

### 13、设有一生灭过程 $\{\xi(t) ; t \geq 0\}$, 其中参数 $\lambda_n=\lambda, \mu_n=n \mu, \lambda$ 和 $\mu$ 均为大于零的常数, 其起始状态为 $\xi(0)=0$ 。试求:

(a) 该过程的 $Q$ 矩阵;
(b)列出福克一普朗克微分方程;
(c) 其均值函数 $M_{\xi}(t)=E\{\xi(t)\}$;
(d) 证明 $\lim _{t \rightarrow \infty} p_0(t)=\exp \{-\lambda / \mu\}$ 。

> (a):
>
> 在过程$Q$矩阵中，其满足如下条件：
>
> - 描述是极小时间内发生的事情，所以只能发生一个单元的跳变， 也只能发生如下转变：
>   - $P_{n, n-1} = n\mu $ (灭过程) 
>   - $P_{n, n} = -(\lambda + n\mu )$ (离开$n$状态的负概率) 
>   - $P_{n, n+1} =  \lambda$ (生过程)
>   - $P_{其他情况} = 0 $
>
> 如上，我们可以求得$Q$矩阵为:
> $$
> Q = Q=\left[\begin{array}{cccccc}
> -\lambda & \lambda & 0 & 0 & \cdots & 0 \\
> \mu & -(\mu+\lambda) & \lambda & 0 & \cdots & 0 \\
> 0 & 2 \mu & -(2 \mu+\lambda) & \lambda & \cdots & 0 \\
> \vdots & \vdots & \vdots & \vdots & \vdots & \vdots \\
> \cdots & \cdots & n \mu & -(n \mu+\lambda) & \lambda & \cdots \\
> \vdots & \vdots & \vdots & \vdots & \vdots & \vdots
> \end{array}\right]
> $$
>
>
> (b):
>
> 对于生灭过程的$K-F$方程，其一般表达形式为：
> $$
> \frac{d P_n(t)}{d t}=\sum_m\left[W_{n, m} P_m(t)-W_{m, n} P_n(t)\right]
> $$
>
> 其中:
> - $P_n(t)$ 是在时间 $t$ 时系统处于状态 $n$ 的概率。
> - $W_{n, m}$ 是从状态 $m$ 转移到状态 $n$ 的转移率。
> - $W_{m, n}$ 是从状态 $n$ 转移到状态 $m$ 的转移率。
>
> - 从状态 $n$ 到 $n+1$ 的转移率是 $\lambda$ 。
> - 从状态 $n$ 到 $n-1$ 的转移率 (对 $n>0$ ) 是 $n \mu$ 。
>
> 因此，对于这个生灭过程，$K-F$可以写为:
> $$
> \frac{d P_n(t)}{d t}=\lambda P_{n-1}(t)+(n+1) \mu P_{n+1}(t)-(\lambda+n \mu) P_n(t)
> $$
> - 第一项 $\lambda P_{n-1}(t)$ 表示由状态 $n-1$ “生”到状态 $n$ 的概率流入。
> - 第二项 $(n+1) \mu P_{n+1}(t)$ 表示由状态 $n+1$ “灭”到状态 $n$ 的概率流入。
> - 第三项 $(\lambda+n \mu) P_n(t)$ 表示从状态 $n$ 流出到其他状态的概率。
>
> 当然，对于$0$状态，由于不存在$-1$这个状态，所以其$K-F$方程为：
> $$
> \frac{dP_0(t)}{dt} = \mu P_{1}(t) - \lambda P_0(t)
> $$
> 综上所述，方程可以表达为：
>
> $$
> \frac{dP_n(t)}{dt} = 
> \begin{cases} 
> \mu P_{1}(t) - \lambda P_0(t) & \text{if } n = 0 \\
> \lambda P_{n-1}(t) + (n+1) \mu P_{n+1}(t) - (\lambda + n \mu) P_n(t) & \text{if } n > 0
> \end{cases}
> $$
>
> 这里：
>
> - 当 $ n = 0 $ 时，方程考虑的是从状态 0 到状态 1 的转移（“生”）和从状态 1 到状态 0 的转移（“灭”）。
> - 当 $ n > 0 $ 时，方程考虑的是从状态 $ n-1 $ 到状态 $ n $ 的转移（“生”）、从状态 $ n+1 $ 到状态 $ n $ 的转移（“灭”）以及从状态 $ n $ 到其他状态的转移。
>
> (c):
>
> 由定义可以得到:
> $$
> \begin{align}
> M_{\xi}(t)&=E\{\xi(t)\} \\
> &=\sum_{n}^\infty  n\times P_n(t)
> \end{align}
> $$
> 直接求解比较困难， 所以这里考虑先求导，然后转换求导， 因为我们在(c)中给出了其对时间求导的关系式：
> $$
> \begin{align}
> \frac{\partial M_{\xi}(t)}{\partial t}&=\frac{E\{\xi(t)\}}{\partial t} \\
> &=\sum_{n=1}^\infty  n\times \frac{P_n(t)}{\partial t} \\
> &= \sum_{n=1}^\infty  n\times (\lambda P_{n-1}(t) + (n+1) \mu P_{n+1}(t) - (\lambda + n \mu) P_n(t)) \\
> & = \sum_{n=1}^\infty  n\lambda P_{n-1}(t) + \sum_{n=1}^\infty  n(n+1) \mu P_{n+1}(t) - \sum_{n=1}^\infty  n(\lambda + n \mu) P_n(t)
> \end{align}
> $$
> 这里需要一点技巧了， 
> $$
> \begin{align}
> \sum_{n=1}^\infty  n\lambda P_{n-1}(t) &= \sum_{m=0}^\infty  (m+1)\lambda P_{m}(t)\\
> &= \sum_{n=1}^\infty  (n+1)\lambda P_{n}(t) - \lambda P_0(t)
> \end{align}
> $$
>
> $$
> \begin{align}
> \sum_{n=1}^\infty  n(n+1) \mu P_{n+1}(t) &= \sum_{m=2} (m-1)m\mu P_{m}(t)\\
> &=\sum_{n=1} (n-1)n\mu P_{n}(t) - 2\mu P_2 (t)
> 
> \end{align}
> $$
>
> 回带，得到原式为：
> $$
> \begin{align}
>  \sum_{n=1}^\infty  n\lambda P_{n-1}(t) + \sum_{n=1}^\infty  n(n+1) \mu P_{n+1}(t) - \sum_{n=1}^\infty  n(\lambda + n \mu) P_n(t) &= \\  
>   \sum_{n=1}^\infty  (n+1)\lambda P_{n}(t) - \lambda P_0(t)  +  \sum_{n=1} (n-1)n\mu P_{n}(t) - 2\mu P_2 (t)- \\\sum_{n=1}^\infty  n(\lambda + n \mu) P_n(t)\\
>   &= \lambda -\mu M_{\xi}(t)
> \end{align}
> $$
> 那么可以求得:
> $$
> M_{\xi}(t) = exp(-\mu t)M_{\xi}(0) +\int_0^t exp(-\mu(t-s)) \lambda ds = \frac{1-exp(-\mu t)}{\mu} \lambda
> $$
> (d):
> $$
> \lim _{t \rightarrow \infty} p_0(t)=\lim _{t \rightarrow \infty} e^{-\frac{\lambda}{\mu}\left(1-e^{-\mu t}\right)}=e^{-\frac{\lambda}{\mu}}
> $$

### 14、有一个细菌群体, 在一段时间内假定可以通过分裂等方式产生新的细菌, 并不会死去。假设在长为 $\Delta t$ 的一段时间内, 一个细菌分裂为两个, 即产生新细菌的概率为 $\lambda \Delta t+o(\Delta t)$, 令 $X(t)$ 表示时刻 $t$ 的细菌群体的大小。
(a) 试说明 $\{X(t), t \geq 0\}$ 是生灭过程;
(b) 试证 $\lambda_i=i \lambda, \mu_i=0$, 并列出其前进方程和后退方程;
(c) 验证 $p_{k j}(t)=C_{j-1}^{j-k}\left(e^{-\lambda t}\right)^k\left(1-e^{-\lambda t}\right)^{j-k}, j \geq k \geq 1$ 是上述方程的解, 并计算
$$
E\{X(s+t)-X(s) \mid X(s)=m\} 。
$$
> (a):
>
> 同13,容易得知 $\{X(t), t \geq 0\}$ 是生灭过程是显然的, 其 $Q$ 矩阵为
> $$
> Q=\left(\begin{array}{ccccc}
> -\lambda & \lambda & & & \\
> & -2 \lambda & 2 \lambda & & \\
> & & -3 \lambda & 3 \lambda & \ldots \\
> & & & \ddots & \ddots \\
> & & & & \ddots
> \end{array}\right)
> $$
> (b):
>
> 
>
> (c):
>
> 



### 15、在一个线性生灭过程中, 假定人口中每个人在间隔 $(t, t+\Delta t)$ 内以概率 $\lambda \Delta t+o(\Delta t)$ 生一个儿女, 假定这些人是统计独立的, 则如果在时刻 $t$ 人口中有 $n$ 个人,在 $(t, t+\Delta t)$ 中出生的概率是 $n \lambda \Delta t+o(\Delta t)$ 。同样地, 如果在 $(t, t+\Delta t)$ 内一个人死亡的概率是 $\mu \Delta t+o(\Delta t)$, 则如果在 $t$ 时刻有 $n$ 个人活着, 在 $(t, t+\Delta t)$ 内死亡的概率是 $n \mu \Delta t+o(\Delta t), X(t)$ 表示 $t$ 时刻人口的数目, 且已知 $X(0)=n_0$, 则 $X(t)$ 是一马氏过程。

(a) 试写出过程的状态空间及 $Q$ 矩阵, 求 $p_n(t)=P\{X(t)=n\}$ 满足的微分方程;

(b) 试导出 $m_X(t)=E\{X(t)\}$ 满足的微分方程;
(c) 求解 $m_X(t)$ 。

> (a):
>
> 当 $\lambda_n=n \lambda+a, \mu_n=n \mu \quad(\lambda, \mu, a>0)$ 时,可以得到此过程的 $Q$ 矩阵:
>
> 令:
> $$
> \begin{gathered}
> p_j(t)=P\{\xi(t)=j\} \\
> \vec{p}(t)=\left(p_0(t), p_1(t), p_2(t), \cdots, p_n(t), \cdots\right)
> \end{gathered}
> $$
>
> 写出福克一普朗克方程:
>
> 初始条件: $p_{n_0}(0)=1, p_j(0)=0 \quad\left(j \neq n_0\right)$ 。
> (b):
>
> 由数学期望的定义: $E\{\xi(t)\} \hat{=} M_{\xi}(t)=\sum_{n=0}^{\infty} n p_n(t)=\sum_{n=1}^{\infty} n p_n(t)$, 由此, 我们有:
> $$
> \begin{aligned}
> & \frac{d M_{\xi}(t)}{d t}=\frac{d}{d t} \sum_{n=1}^{\infty} n p_n(t)=\sum_{n=1}^{\infty} n \frac{d p_n(t)}{d t}= \\
> & \left.=\sum_{n=1}^{\infty} n\{(n-1) \lambda+a] p_{n-1}(t)-[n(\lambda+\mu)+a] p_n(t)+(n+1) \mu p_{n+1}(t)\right\} \\
> & =\sum_{n=1}^{\infty} n a p_{n-1}(t)-\sum_{n=1}^{\infty} n a p_n(t)+ \\
> & \quad \quad+\sum_{n=1}^{\infty} n\left[(n-1) \lambda p_{n-1}(t)-n(\lambda+\mu) p_n(t)+(n+1) \mu p_{n+1}(t)\right] \\
> & =\sum_{n=0}^{\infty} a p_n(t)+\sum_{n=1}^{\infty} n\left[(n-1) \lambda p_{n-1}(t)-n(\lambda+\mu) p_n(t)+(n+1) \mu p_{n+1}(t)\right] \\
> & =a+(\lambda-\mu) \sum_{n=1}^{\infty} n p_n(t)=a+(\lambda-\mu) M_{\xi}(t)
> \end{aligned}
> $$
>
> 即可得到描写 $M_{\xi}(t)$ 的微分方程:
> $$
> \left\{\begin{array}{l}
> \frac{d M_{\xi}(t)}{d t}=a+(\lambda-\mu) M_{\xi}(t) \\
> M_{\xi}(0)=n_0
> \end{array}\right.
> $$
> 
>
> (c):
>
> 解上面的微分方程, 我们有:
> $$
> M_{\xi}(t)=n_0 e^{(\lambda-\mu) t}+\frac{a}{\mu-\lambda}\left[1-e^{(\lambda-\mu) t}\right]
> $$
>
> 以上得求解当 $a=0$ 时即是所要得解。



### 16、一条电路供给 $m$ 个焊工用电, 每个焊工均是间断地用电。现假设 (1) 若一焊工在 $t$ 时刻用电, 而在 $(t, t+\Delta t)$ 内停止用电的概率为 $\mu \Delta t+o(\Delta t)$; (2) 若一焊工在 $t$ 时刻没有用电, 而在 $(t, t+\Delta t)$ 内用电的概率为 $\lambda \Delta t+o(\Delta t)$ 。每一焊工的工作情况是相互独立的。设 $\xi(t)$ 表示在 $t$ 时刻正在用电的焊工数。
(a) 试写出此过程的状态空间及 $Q$ 矩阵;
(b) 设 $\xi(0)=0$, 写出福克一普朗克方程;
(c) 当 $t \rightarrow+\infty$ 时, 求极限分布 $P_n$ 。

> (a):
>
> 令 $\xi(t)$ 表示 $t$ 时刻系统中正在用电的焊工数, 则 $\{\xi(t), t \geq 0\}$ 是一马氏过程,其状态空间为: $S=\{0,1,2, \cdots, m\}$ 。
> $Q$ 矩阵为:
> $$
> Q=\left(\begin{array}{cccccc}
> -m \lambda & m \lambda & 0 & 0 & \cdots & 0 \\
> \mu & -[\mu+(m-1) \lambda] & (m-1) \lambda & 0 & \cdots & 0 \\
> 0 & 2 \mu & -[2 \mu+(m-2) \lambda] & (m-2) \lambda & \cdots & 0 \\
> \vdots & \vdots & \ddots & \ddots & \cdots & \vdots \\
> 0 & 0 & 0 & 0 & m \mu & -m \mu
> \end{array}\right)
> $$
> (b):
>
> 令: $p_j(t)=P\{\xi(t)=j\}$
> $$
> \vec{p}(t)=\left(p_0(t), p_1(t), p_2(t), \cdots, p_m(t)\right), \vec{p}(0)=(1,0,0, \cdots, 0)
> $$
>
> 写出福克－普朗克方程:
> $$
> \left\{\begin{array}{l}
> \frac{d \vec{p}(t)}{d t}=\vec{p}(t) Q \\
> \vec{p}(0)=(1,0,0, \cdots, 0)_{1 \times(m+1)}
> \end{array}\right.
> $$
> (c):
>
> (c) 画出状态转移率图, 可得 $t \rightarrow \infty$ 时的平衡方程:
> $$
> \left\{\begin{array}{l}
> m \lambda p_0=\mu p_1 \\
> {[(m-1) \lambda+\mu] p_1=m \lambda p_0+2 \mu p_2} \\
> \quad \vdots \\
> {[(m-n) \lambda+n \mu] p_n=(m-n+1) \lambda p_{n-1}+(n+1) \mu p_{n+1}} \\
> \quad \vdots \\
> \lambda p_{m-1}=m \mu p_m \\
> \sum_{n=0}^m p_n=1
> \end{array}\right.
> $$
>
> 由此可得：
> $$
> \begin{aligned}
> & (m-n) \lambda p_n-(n+1) \mu p_{n+1}=(m-n+1) \lambda p_{n-1}-n \mu p_n=\cdots= \\
> & m \lambda p_0-\mu p_1=0
> \end{aligned}
> $$
>
> 即有:
> $$
> \begin{gathered}
> (m-n) \lambda p_n-(n+1) \mu p_{n+1}=0 \\
> p_{n+1}=\frac{(m-n)}{(n+1)} \cdot \frac{\lambda}{\mu} \cdot p_n, \quad n=0,1,2, \cdots, m
> \end{gathered}
> $$
>
> 由此可以求得:
> $$
> p_n=\frac{(m-n+1)}{n} \cdot \frac{(m-n)}{n-1} \cdots \cdots \frac{m}{1} \cdot\left(\frac{\lambda}{\mu}\right)^n \cdot p_0=C_m^n\left(\frac{\lambda}{\mu}\right)^n p_0, \quad n=0,1, \cdots, m
> $$
>
> 由 $\sum_{n=0}^m p_n=1$, 即可确定 $p_0$, 最终得到所要的结果。
>
> 
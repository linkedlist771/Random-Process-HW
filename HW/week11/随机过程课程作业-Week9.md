

# 随机过程课程作业-**Week8**

**作者**：48-丁力-202328015926048  
**日期**：今天

---

## 目录

- [马尔科夫过程](#马尔科夫过程)
  - [题目9](#题目1)
  - [题目10](#题目2)
  - [题目11](#题目3)
  - [题目12](#题目4)

---

## 马尔科夫过程

###  9、考虑三个状态的齐次马氏链, 其转移概率矩阵为


$$
P=\left(\begin{array}{lll}

p_{00} & p_{01} & p_{02} \\

p_{10} & p_{11} & p_{12} \\

p_{20} & p_{21} & p_{22}

\end{array}\right)=\left(\begin{array}{lll}

1 & 0 & 0 \\

p & q & r \\

0 & 0 & 1

\end{array}\right)
$$


其中: $p, q, r>0, p+q+r=1$,

（a）假定过程从状态 1 出发, 试求过程被状态 0 （或 2）吸收的概率;

> 首先，为了计算被吸收的概率，我们首先要画出其状态转移图：
>
> ```mermaid
> graph TD
>     0 -->|1| 0
>     1 -->|p| 0
>     1 -->|q| 1
>     1 -->|r| 2
>     2 -->|1| 2
> 
> ```
>
> 然后我们进行如下定义：
>
> - $P\left\{C_0 \mid 1\right\}$ 表示从状态1被状态0吸收的概率。
> - $p_{11} P\left\{C_0 \mid 1\right\}$ 表示从状态转移到状态1的概率，然后再被状态 0 吸收的概率。
> - $p_{10}$ 是从状态 1 直接转移到状态 0 的概率。
>
> - $P\left\{C_2 \mid 1\right\}$ 表示从状态1被状态2吸收的概率。
> - $p_{12} P\left\{C_2 \mid 1\right\}$ 表示从状态2转移到状态1的概率，然后再被状态 1 吸收的概率。
> - $p_{12}$ 是从状态 1 直接转移到状态2的概率。
>
> 那么，我们可以列出如下表达式:
> $$
> \begin{cases}
> P\left\{C_0 \mid 1\right\} = p_{11} P\left\{C_0 \mid 1\right\} + p_{10}\\
> P\left\{C_2 \mid 1\right\} = p_{11} P\left\{C_2 \mid 1\right\} + p_{12}\\
> \end{cases}
> $$
> 然后，我们知道：
> $$
> \begin{cases}
> p_{10} = p\\
> p_{11} = q \\ 
> p_{12} = r
> \end{cases}
> $$
> 带入上式子，我们可以得到：
> $$
> \begin{cases}
> P\left\{C_0 \mid 1\right\} = \frac{p}{1-q} \\
> P\left\{C_2 \mid 1\right\} = \frac{r}{1-q}
> \end{cases}
> $$
> 

（b）试求过程进入吸收态而永远停留在那里所需的平均时间。

> 我们假设这个时间为$T$, 那么该期望由三部分组成：
>
> 1. 从1进入0， 然后停留。
> 2. 从1进入2，然后停留。
> 3. 从1进入1，此时$T+1$, 然后重复1,2,3 过程，
>
> 那么我可以求得其递推关系式为：
> $$
> T = p \times 1 + r \times 1 + q \times (T+1)
> $$
> 那么，我们可以求得$T$为：
> $$
> T = \frac{p+r+q}{1-q} = \frac{1}{1-q}
> $$

### 10、设齐次马氏链 $\left\{X_n, n \geq 0\right\}, S=\{1,2,3,4\}$, 一步转移概率矩阵如下:


$$
P=\left(\begin{array}{cccc}

0 & 0 & 1 / 2 & 1 / 2 \\

0 & 0 & 1 / 2 & 1 / 2 \\

1 / 2 & 1 / 2 & 0 & 0 \\

1 / 2 & 1 / 2 & 0 & 0

\end{array}\right)
$$

(1) 写出切普曼一柯尔莫哥洛夫方程 $(C-K$ 方程);

> 定理：对于 $m$ 步转移概率有如下的 $\mathbf{C}-\mathbf{K}$ 方程:
> $$
> p_{i j}^{(m+r)}(n)=\sum_{k \in S} p_{i k}^{(m)}(n) p_{k j}^{(r)}(n+m) \quad(i, j \in S)
> $$
>
> 对于齐次马氏链, 此方程为:
> $$
> p_{i j}^{(m+r)}=\sum_{k \in S} p_{i k}^{(m)} p_{k j}^{(r)} \quad(i, j \in S) \quad(\mathbf{C}-\mathbf{K} \text { 方程 })
> $$

(2) 求 $n$ 步转移概率矩阵;

> 其$n$步转移概率矩阵，可以通过$P^n$ 求得，对于该题而言，显然是分别求其$P^2,P^3,P^4,..$ 地推出$P^n$的表达式。
> $$
> \begin{align}
> P^2 &= P\times P = \left(\begin{array}{cccc}
> 
> 1 / 2 & 1 / 2 & 0 & 0 \\
> 
> 1 / 2 & 1 / 2 & 0 & 0 \\
> 0 & 0 & 1 / 2 & 1 / 2 \\
> 
> 0 & 0 & 1 / 2 & 1 / 2 \\
> 
> 
> \end{array}\right) \\
> P^3&=P^2\times P = \left(\begin{array}{cccc}
> 
> 0 & 0 & 1 / 2 & 1 / 2 \\
> 
> 0 & 0 & 1 / 2 & 1 / 2 \\
> 
> 1 / 2 & 1 / 2 & 0 & 0 \\
> 
> 1 / 2 & 1 / 2 & 0 & 0
> 
> \end{array}\right) = P
> 
> \end{align}
> $$
> 不难看出：
> $$
> P^n = \begin{cases}
> P =  \left(\begin{array}{cccc}
> 
> 0 & 0 & 1 / 2 & 1 / 2 \\
> 
> 0 & 0 & 1 / 2 & 1 / 2 \\
> 
> 1 / 2 & 1 / 2 & 0 & 0 \\
> 
> 1 / 2 & 1 / 2 & 0 & 0
> 
> \end{array}\right) , \text{$n$ is odd} \\
> P^2 = \left(\begin{array}{cccc}
> 
> 1 / 2 & 1 / 2 & 0 & 0 \\
> 
> 1 / 2 & 1 / 2 & 0 & 0 \\
> 0 & 0 & 1 / 2 & 1 / 2 \\
> 
> 0 & 0 & 1 / 2 & 1 / 2 \\
> 
> 
> \end{array}\right) , \text{$n$ is even} \\
> 
> 
> 
> \end{cases}
> $$
> 

(3) 试问此马氏链是平稳序列吗? 为什么?

> 画出其状态转移图如下：
>
> ```mermaid
> graph TD
>     1 -->|0.5| 3
>     1 -->|0.5| 4
>     2 -->|0.5| 3
>     2 -->|0.5| 4
>     3 -->|0.5| 1
>     3 -->|0.5| 2
>     4 -->|0.5| 1
>     4 -->|0.5| 2
> 
> ```
>
> 从(2)中可以看出，其$n$步转移矩阵只具有两个状态，也就是说此马氏链具有两个不可约子链，它们是互不通讯的，导致整个链不具有遍历性，不是平稳序列。

### 11、某车间有两台独立工作的机器, 每台机器有两种状态: 正常工作和故障修理。知正常工作的机器在某天出故障的概率为 $a$, 机器处于故障修理状态在某天恢复正常工作的概率为 $b$, 其中 $0<a, b<1$ 。令 $X_n$ 表示第 $n$ 天车间正常工作的机器数, 试求:

(1) 证明 $\left\{X_n ; n=1,2, \cdots\right\}$ 是一齐次马氏链, 并写出其一步转移概率矩阵;

> 由于该车间只有两台机器，所以$X_n$的状态空间为：
> $$
> S = \{0,1,2\}
> $$
> 由题意可知，当天机器是否出问题只和前一天有关，所以其为一齐次马氏链， 并且我们也容易知道。
> $$
> \begin{align}
> &P_{X_{n-1}=0,X_{n}=0} = (1-b)^2\\
> &P_{X_{n-1}=0,X_{n}=1} = \binom{2}{1}(1-b)\times b = 2b(1-b)\\
> &P_{X_{n-1}=0,X_{n}=2} = b^2\\
> 
> &P_{X_{n-1}=1,X_{n}=0} = a(1-b)\\
> &P_{X_{n-1}=1,X_{n}=1} = (1-b)(1-a)+ba\\
> &P_{X_{n-1}=1,X_{n}=2} = b(1-a)\\
> 
> 
> &P_{X_{n-1}=2,X_{n}=0} = a^2\\
> &P_{X_{n-1}=2,X_{n}=1} = \binom{2}{1}(1-a)a\times = 2a(1-a)\\
> &P_{X_{n-1}=2,X_{n}=2} = (1-a)^2\\
> 
> 
> \end{align}
> $$
>
> 那么我们可以得到其状态矩阵：
> $$
> P=\left[\begin{array}{ccc}
> (1-b)^2 & 2 b(1-b) & b^2 \\
> a(1-b) & (1-b)(1-a)+b a & b(1-a) \\
> a^2 & 2 a(1-a) & (1-a)^2
> \end{array}\right]
> $$

(2) 此马氏链是否存在极限分布? 存在的话, 计算其平稳分布;

> 由于$0<a,b<1$ , 所以$P>0$ , 所以该马氏链存在， 设其平稳分布的表达为:
> $$
> \pi = [p_0 , p_1, p_2]
> $$
> 并且有$p_0+p_1+p_2=1$，由其定义，我们可以得到:
> $$
> \pi P = \pi
> $$
> 计算得到:
> $$
> p_0=\frac{a^2}{(a+b)^2}, \quad p_1=\frac{2 a b}{(a+b)^2}, \quad p_2=\frac{b^2}{(a+b)^2}
> $$
> 上述内容即为所求的平稳分布， 不难看出，其为参数为$\frac{b}{a+b}$ 的二项分布。

(3) 若车间里有 $m$ 台独立工作的机器, 假设条件不变, 问其平稳分布是什么?

> 由于(2)中为两台机器的分布，为二项分布， 所以$m$独立机器的平稳分布为伯努利分布，为:
> $$
> p_i =\binom{m}{i} (\frac{b}{a+b})^i  (\frac{a}{a+b})^{m-i}
> $$
> 

### 12、



设 $\left\{X_n ; n \geq 0\right\}$ 是一齐次马氏链, 状态空间为 $\bar{S}=S_0 \cup S$, 其中: $S=\{1,2, \cdots, m\}$为瞬时态集, $S_0=\{0\}$ 为吸收态集, 且转移矩阵为 $\widetilde{P}=\left[\begin{array}{cc}P & P_0 \\ 0 & 1\end{array}\right]$, 其中 $P_0=(I-P) \cdot \vec{e}$,$\vec{e}=(1,1, \cdots 1)^\tau$ 。定义从瞬时态集到吸收态集的首达时间为:


$$
\tau=\inf \left\{n: n \geq 0, X_n \in S_0\right\} 
$$


令: $\vec{\pi}(0)=\left(\alpha_0, \alpha_1, \cdots, \alpha_m\right)$ 为马氏链的初始分布, 记: $\vec{\alpha}=\left(\alpha_1, \cdots, \alpha_m\right)$, 且满足:
$$
\alpha_k \geq 0(k=0,1, \cdots, m), \sum_{k=0}^m \alpha_k=1 
$$




令: $g_k=P\{\tau=k\}$ (称为 Phase-Type 分布), $G(\lambda)=E\left\{\lambda^\tau\right\}=\sum_{k=0}^{+\infty} g_k \lambda^k$ 。试证明:

(a) 对于任意 $k \in N$, 有: $g_0=\alpha_0, g_k=\vec{\alpha} P^{k-1} P_0=\vec{\alpha} P^{k-1}(I-P) \vec{e}$;

> 用数学归纳法证明
> 当 $k=0$ 时, $g_0=P\{\tau=0\}=P\left\{X_0=0\right\}=\alpha_0$ ；
> 当 $k=1$ 时, $g_1=P\{\tau=1\}=P\left\{X_0 \in S, X_1=0\right\}=\sum_{i \in S} \alpha_i p_{i 0}=\vec{\alpha} P_0$ ；
> 当 $k=2$ 时,
> $$
> \begin{aligned}
> g_2 & =P\{\tau=2\}=P\left\{X_0 \in S, X_1 \in S, X_2=0\right\}= \\
> & =\sum_{i \in S} \sum_{j \in S} P\left\{X_0=i, X_1=j, X_2=0\right\}=\sum_{i \in S} \sum_{j \in S} \alpha_i p_{i j} p_{j 0}=\vec{\alpha} P^{2-1} P_0
> \end{aligned}
> $$
>
> 假设当 $k=n$ 时结论成立, 即 $g_n=\vec{\alpha} P^{n-1} P_0=\vec{\alpha} P^{n-1}(I-P) \vec{e}$, 则当 $k=n+1$ 时, 作如下分解, (1) 从初始状态 $i$ 转移一步到状态 $j$; (2) 以 $j$ 作为初始状态转移 $n$ 步被吸收, 结合归纳假设, 我们有:
> $$
> g_{n+1}=P\{\tau=n+1\}=\vec{\alpha} P \cdot P^{n-1} P_0=\vec{\alpha} P^{(n+1)-1} P_0
> $$
>
> 即当 $k=n+1$ 时结论成立。
> 因此, 对于任意 $k \in N$, 有: $g_0=\alpha_0, g_k=\vec{\alpha} P^{k-1} P_0=\vec{\alpha} P^{k-1}(I-P) \vec{e}$ 。

(b) 对于任意 $0 \leq \lambda \leq 1$, 有: $G(\lambda)=\alpha_0+\lambda \vec{\alpha}(I-\lambda P)^{-1}(I-P) \vec{e}$ 。

> 注意到 $S$ 为瞬时态集, 因此有
> $$
> \lim _{n \rightarrow+\infty} P^{n}=0
> $$
> 因此, 当 $n$ 充分大时, 有: 
> $$
> \operatorname{det}\left(I-P^{n}\right)=\left|I-P^{n}\right| \neq 0
> $$
> 
>
> 由于:
> $$
> (I-P)\left(I+P+P^{2}+\cdots+P^{n-1}\right)=I-P^{n}
> $$
> 
>
> 因此当 $n$ 充分大时, 有
> $$
> |I-P| \cdot\left|I+P+P^{2}+\cdots+P^{n-1}\right| \neq 0
> $$
> 
>
> 
>
> 于是 
> $$
> |I-P| \neq 0
> $$
> 
>
> 即 
>
> $(I-P)^{-1}$存在,
>
>  在 (A) 式中左右两边乘以  $(I-P)^{-1}$ , 令 $n \rightarrow+\infty$, 则有
> $$
> (I-P)^{-1}=\sum_{k=0}^{\infty} P^{k}
> $$
> 
>
> 将 $g_{k}$ 的表达式代入, 利用上面的结论, 有
> $$
> \begin{aligned}
> 
> G(\lambda) &= E\left\{\lambda^{\tau}\right\} \\
> 
> &= \sum_{k=0}^{+\infty} g_{k} \lambda^{k} \\
> 
> &= \alpha_{0}+\sum_{k=1}^{+\infty} \vec{\alpha} P^{k-1} P_{0} \lambda^{k} \\
> 
> &= \alpha_{0}+\lambda \vec{\alpha}\left[\sum_{k=1}^{+\infty}(\lambda P)^{k-1}\right] P_{0} \\
> 
> &= \alpha_{0}+\lambda \vec{\alpha}(I-\lambda P)^{-1} P_{0} \\
> 
> &= \alpha_{0}+\lambda \vec{\alpha}(I-\lambda P)^{-1}(I-P) \vec{e}
> 
> \end{aligned}
> $$


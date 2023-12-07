

# 随机过程课程作业-**Week12**

**作者**：48-丁力-202328015926048  
**日期**：今天

---

## 目录

- [马尔科夫过程](#马尔科夫过程)
  - [题目4](#题目1)
  - [题目5](#题目2)
  - [题目6](#题目3)

---

## 泊松过程

### 4、设 $Y(t)=X(-1)^{N(t)}, t \geq 0$, 其中 $\{N(t) ; t \geq 0\}$ 为强度为 $\lambda>0$ 的 Poisson 过程, 随机变量 $X$ 与此 Poisson 过程独立, 且有如下分布:

$$
P\{X=-a\}=P\{X=a\}=1 / 4, \quad P\{X=0\}=1 / 2, \quad a>0
$$

试求随机过程 $Y(t), t \geq 0$ 的均值函数和相关函数。

> - (1)
>
> $$
> \begin{align}
> E(Y(t)) &= E(X(-1)^{N(t)}) \\
> &由于X和Possion过程独立，那么有\\
> &= E(X) E((-1)^{N(t)})\\
> &= ((a-a)\times \frac{1}{4}+0\times\frac{1}{2})E((-1)^{N(t)})\\
> &=0
> \end{align}
> $$
>
> - (2)
>
> $$
> \begin{align}
> R_Y(t_1,t_2) &= E(X^2(-1)^{N(t_1)+N(t_2)})\\
> &=E(X^2) E((-1)^{N(t_1)+N(t_2)})\\
> &= ((a^2+a^2)\times \frac{1}{4}+0\times\frac{1}{2}) E((-1)^{N(t_1)+N(t_2)})\\
> &=\frac{a^2}{2} E((-1)^{N(t_1)+N(t_2)})\\
> &= \frac{a^2}{2} E((-1)^{2N(t_1)+N(t_2)-N(t_1)})\\
> &= \frac{a^2}{2} E((-1)^{N(t_2)-N(t_1)})\\
> &= \frac{a^2}{2} \sum_{n=0}^\infty  E((-1)^{N(t_2)-N(t_1)}|N(t_2)-N(t_1)=n)P(N(t_2)-N(t_1)=n)\\
> &=\frac{a^2}{2} \sum_{n=0}^\infty  (-1)^n \frac{(\lambda(t_2-t_1))^n e^{-\lambda (t_2-t_1)}}{n!}\\
> &= \frac{a^2}{2} e^{-2\lambda(t_2-t_1)}
> \end{align}
> $$
>
> 





### 5、设 $\{N(t), t \geq 0\}$ 是一强度为 $\lambda$ 的泊松过程, $S_0=0, S_n$ 为第 $n$ 个事件发生的时刻, 求:
(1) $\left(S_2, S_5\right)$ 的联合概率密度函数;
(2) $E\left\{S_1 \mid N(t) \geq 1\right\}$;
(3) $\left(S_1, S_2\right)$ 在 $N(t)=1$ 条件下的条件概率密度函数。

> - (1)
>
> 令: $0<t_2<t_5$, 取充分小的 $h>0$, 使得:
> $$
> t_2-\frac{h}{2}<t_2<t_2+\frac{h}{2}<t_5-\frac{h}{2}<t_5<t_5+\frac{h}{2}
> $$
>
> 由
> $$
> \begin{aligned}
> \left\{t_2-\right. & \left.\frac{h}{2}<S_2 \leq t_2+\frac{h}{2}, t_5-\frac{h}{2}<S_5 \leq t_5+\frac{h}{2}\right\}= \\
> & \left\{N\left(t_2-\frac{h}{2}\right)=1, N\left(t_2+\frac{h}{2}\right)-N\left(t_2-\frac{h}{2}\right)=1,\right. \\
> & \left.N\left(t_5-\frac{h}{2}\right)-N\left(t_2+\frac{h}{2}\right)=2, N\left(t_5+\frac{h}{2}\right)-N\left(t_5-\frac{h}{2}\right)=1\right\} \cup H_n
> \end{aligned}
> $$
>
> 其中
> $$
> \begin{aligned}
> & H_n=\left\{N\left(t_2-\frac{h}{2}\right)=1, N\left(t_2+\frac{h}{2}\right)-N\left(t_2-\frac{h}{2}\right)=1,\right. \\
> & \left.\quad N\left(t_5-\frac{h}{2}\right)-N\left(t_2+\frac{h}{2}\right)=2, N\left(t_5+\frac{h}{2}\right)-N\left(t_5-\frac{h}{2}\right) \geq 2\right\}
> \end{aligned}
> $$
>
> 因此有
> $$
> \begin{aligned}
> & P\left\{t_2-\frac{h}{2}<S_2 \leq t_2+\frac{h}{2}, t_5-\frac{h}{2}<S_5 \leq t_5+\frac{h}{2}\right\}= \\
> & \quad=\lambda\left(t_2-\frac{h}{2}\right) e^{-\lambda\left(t_2-\frac{h}{2}\right)} \cdot(\lambda h) e^{-\lambda h} \cdot \frac{1}{2}\left[\lambda\left(t_5-t_2-h\right)\right]^2 e^{-\lambda\left(t_5-t_2-h\right)} \cdot(\lambda h) e^{-\lambda h}+o\left(h^2\right)
> \end{aligned}
> $$
>
> 由此可得 $\left(S_2, S_5\right)$ 的联合概率密度函数为
> $$
> \begin{aligned}
> & g\left(t_2, t_5\right)=\lim _{h \rightarrow 0} \frac{P\left\{t_2-\frac{h}{2}<S_2 \leq t_2+\frac{h}{2}, t_5-\frac{h}{2}<S_5 \leq t_5+\frac{h}{2}\right\}}{h^2} \\
> & =\frac{\lambda^5}{2} t_2\left(t_5-t_2\right)^2 e^{-\lambda t_5}, \quad 0<t_2<t_5
> \end{aligned}
> $$
>
> - (2)
>
>   
>
>    由于 $\{N(t) \geq 1\}=\left\{S_1 \leq t\right\}$, 由泊松过程与指数分布的关系可知, 在 $\left\{S_1 \leq t\right\}$ 条件下， $S_1$ 的分布密度函数为
>   $f(x)=\frac{\lambda e^{-\lambda x}}{1-e^{-\lambda t}}, \quad 0 \leq x \leq t$
>   因此有:
>
> $$
> E\left\{S_1 \mid N(t) \geq 1\right\}=E\left\{S_1 \mid S_1 \leq t\right\}=\int_0^t x \cdot \frac{\lambda e^{-\lambda x}}{1-e^{-\lambda t}} d x=\frac{1}{\lambda}+\frac{1-t e^{-\lambda t}}{1-e^{-\lambda t}}
> $$
>
> - (3)
>
> 由于 $\{N(t)=1\}=\left\{S_1 \leq t<S_2\right\}$, 令: $0<t_1 \leq t<t_2$, 取充分小的 $h_1, h_2>0$,使得: $t_1-h_1<t_1 \leq t<t_2-h_2<t_2$, 由
> $$
> \begin{aligned}
> & \left\{t_1-h_1<S_1 \leq t_1, t_2-h_2<S_2 \leq t_2\right\}= \\
> & \quad=\left\{N\left(t_1-h_1\right)=0, N\left(t_1\right)-N\left(t_1-h_1\right)=1,\right. \\
> & \left.\quad N\left(t_2-h_2\right)-N\left(t_1\right)=0, N\left(t_2\right)-N\left(t_2-h_2\right)=1\right\} \cup H_n
> \end{aligned}
> $$
>
> 其中
> $$
> \begin{aligned}
> & H_n=\left\{N\left(t_1-h_1\right)=0, N\left(t_1\right)-N\left(t_1-h_1\right)=1,\right. \\
> & \left.\quad N\left(t_2-h_2\right)-N\left(t_1\right)=0, N\left(t_2\right)-N\left(t_2-h_2\right) \geq 2\right\}
> \end{aligned}
> $$
>
> 因此
> $$
> \begin{aligned}
> & P\left\{t_1-h_1<S_1 \leq t_1, t_2-h_2<S_2 \leq t_2\right\}= \\
> & \quad=e^{-\lambda\left(t_1-h_1\right)} \cdot\left(\lambda h_1\right) \cdot e^{-\lambda h_1} \cdot e^{-\lambda\left(t_2-h_2-t_1\right)} \cdot\left(\lambda h_2\right) \cdot e^{-\lambda h_2}+o\left(h_1 h_2\right)
> \end{aligned}
> $$
>
> 由此可得在 $N(t)=1$ 的条件下 $\left(S_1, S_2\right)$ 的联合概率密度函数为
> $$
> \begin{aligned}
> & g\left(t_1, t_2 \mid N(t)=1\right)= \\
> & \quad=\lim _{h_1, h_2 \rightarrow 0} \frac{P\left\{t_1-h_1<S_1 \leq t_1, t_2-h_2<S_2 \leq t_2\right\}}{h_1 h_2 P\{N(t)=1\}}=\frac{\lambda}{t} e^{-\lambda\left(t_2-t\right)}, \quad 0<t_1 \leq t<t_2
> \end{aligned}
> $$





### 6、设 $\{N(t), t \geq 0\}$ 是一强度为 $\lambda$ 的泊松过程, 设 $T$ 为第一个事件出现的时间, $N(T / a)$ 为第一个事件后, 在 $T / a$ 时间间隔内出现的事件数, 其中 $a$ 为正常数。试计算:
(1) $E\{T N(T / a)\}$;
(2) $E\left\{[T N(T / a)]^2\right\}$ 。

> - (1)
>
> 由题可知$T$满足参数为$\lambda$的指数分布，也就是有：
> $$
> E(N(t)) = \lambda t
> $$
>
> $$
> \begin{align}
> E\{T N(T / a)\} &= \int_0^\infty E(TN(T/a)|T=t) f_T(t) dt \\
> &=  \int_0^\infty E(TN(T/a)|T=t) \lambda e^{-\lambda t}dt \\
> &=  \int_0^\infty E(tN(t/a)) \lambda e^{-\lambda t}dt\\
> &= \int_0^\infty t \lambda \frac{t}{a} \lambda e^{-\lambda t}dt\\
> &= \frac{2}{a\lambda}
> \end{align}
> $$
>
> - (2)
>
> $$
> \begin{align}
> E\left\{[T N(T / a)]^2\right\} &=  \int_0^\infty E([TN(T/a)]^2|T=t) f_T(t) dt\\
> &=  \int_0^\infty E([TN(T/a)]^2|T=t) \lambda e^{-\lambda t} dt\\
> &= \int_0^\infty E([tN(t/a)]^2) \lambda e^{-\lambda t} dt\\
> &= \int_0^\infty t^2 E([N(t/a)]^2) \lambda e^{-\lambda t} dt\\
> &= \int_0^\infty t^2 (D(N(t/a))+E(N(t/a)^2)) \lambda e^{-\lambda t} dt\\
> &= \int_0^\infty t^2 (\lambda t/a+\frac{\lambda^2 t^2}{a^2})) \lambda e^{-\lambda t} dt\\
> &= \frac{6a+24}{a^2\lambda^2}
> \end{align}
> $$
>
> 




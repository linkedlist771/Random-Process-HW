

# 随机过程课程作业-**Week12**

**作者**：48-丁力-202328015926048  
**日期**：今天

---

## 目录

- [马尔科夫过程](#马尔科夫过程)
  - [题目1](#题目1)
  - [题目2](#题目2)
  - [题目3](#题目3)

---

## 泊松过程

### 1. 设 $\{N(t), t \geq 0\}$ 是一强度为 $\lambda$ 的齐次泊松过程, 而 $X(t)=N(t) / 2-1, t \geq 0$ 。对 $s>0$,试求:
(1) 计算 $E\{N(t) N(t+s)\}$ 及 $E\{N(s+t) \mid N(s)\}$ 的分布律;
(2) 证明过程 $X(t), t \geq 0$ 是马氏过程并写出转移概率 $p(s, i ; t, j)$, 其中 $s \leq t$ 。

> - (1)
>
> 由于$N(t)$是齐次泊松过程，那么可以得到$X(t)$的状态空间为：
> $$
> S=\{\frac{k-2}{2}\} , k=0,1,2,3..
> $$
> 现在让我们来计算第一个的期望：
> $$
> \begin{align}
> E\{N(t) N(t+s)\} = 
> & E\{N(t) (N(t+s) -N(t) +N(t))\}\\
> =&E\{N(t)^2\} + E\{N(t) (N(t+s)-N(t))\}\\
> =& D(N(t)) + (E\{N(t)\}) ^2 + E\{N(t) (N(t+s)-N(t))\}\\
> & 由于[0,t] 与[t, t+s]的泊松过程是独立的，所以有\\
> =& \lambda t+(\lambda t)^2 + E\{N(t)\} \lambda(s)\\
> =&  \lambda t+(\lambda t)^2 + \lambda t \lambda s\\
> =& \lambda^2t(t+s) +\lambda t
> \end{align}
> $$
>
> ---
>
> $$
> \begin{align}
> E\{N(s+t) \mid N(s)=n\} &=  E\{(N(s+t)-N(s)+N(s) \mid N(s)=n\}\\
> &=  E\{(N(s+t)-N(s) \mid N(s)=n\} +   E\{(N(s) \mid N(s)=n\}\\
> &由上可知，前一项的条件概率是不相关的\\
> &=E\{(N(s+t)-N(s)\}  + n \\
> &\lambda t +n\\
> & \lambda t + N(s)
> \end{align}
> $$
>
> 那么，其分布列为:
> $$
> P\{E\{N(s+t) \mid N(s)\}=n+\lambda t\}=P\{N(s)=n\}=\frac{(\lambda s)^n}{n !} e^{-\lambda s}
> $$
>
> - (2)
>
> 由泊松过程的独立增量性可知过程 $X(t)$ 也是独立增量的, 又因为 $X(0)=-1$, 因此可知过程 $X(t)$ 是一马氏过程, 其转移概率为:
> $$
> \begin{align}
> p(s, i ; t, j)&= \frac{P(X(t)=j, X(s)=i)}{P(X(t)=j)}\\
> &= \frac{P(N(t)=2(j+1), N(s)=2(i+1))}{P(N(t)=2(j+1))}\\
> &=\frac{P(N(t)=2(j+1))P(N(t-s)=2(j-i))}{P(N(t)=2(j+1))}\\
> &=\frac{(\lambda (t-s)^{2(j-i)}}{2(j-i)!}e^{-\lambda (t-s)} 
> 
> \end{align}
> $$
> 



### 2. 设 $\{X(t) ; t \geq 0\}$ 与 $\{Y(t) ; t \geq 0\}$ 是相互独立, 参数分别为 $\lambda_1$ 与 $\lambda_2$ 的 Poisson 过程。定义随机过程 $Z(t)=X(t)-Y(t), t \geq 0$, 且令: $p_n(t)=P\{Z(t)=n\}$ 。
(1) 试求随机过程 $\{Z(t) ; t \geq 0\}$ 的均值函数 $E\{Z(t)\}$ 和二阶矩 $E\left\{Z^2(t)\right\}$;
(2)试证明: $\sum_{n=-\infty}^{+\infty} p_n(t) u^n=\exp \left\{-\left(\lambda_1+\lambda_2\right) t\right\} \cdot \exp \left\{\lambda_1 u t+\lambda_2 u^{-1} t\right\} 。$

> - (1)
>
> $$
> \begin{align}
> E\{Z(t)\} &= E(X(t)-Y(t)) \\
> &由于X(t) 和Y(t)相互独立\\
> &= E(X(t)) - E(Y(t)) \\
> &= (\lambda_1-\lambda_2)t
> \end{align}
> $$
>
> $$
> \begin{align}
> E\left\{Z^2(t)\right\} &=E\left\{(X(t)^2-2X(t)Y(t) +Y(t)^2)\right\}\\
> &= E(X(t)^2) - 2E(X(t)Y(t)) + E(Y(t)^2)\\
> &由于X(t)与Y(t)相互独立，E(X(t)Y(t)) =E(X(t))E(Y(t))\\
> &= (E(X(t))^2+D(X(t))) +(E(Y(t))^2+D(Y(t))) - 2\lambda_1 \lambda_2 t^2\\
> &= (\lambda_1 t)^2 + \lambda_1 t+(\lambda_2 t)^2 + \lambda_2 t - 2\lambda_1 \lambda_2 t^2 \\
> &= (\lambda_1-\lambda_2)^2 t^2+(\lambda_1+\lambda_2)t
> 
> \end{align}
> $$
>
> - (2)
>
> $$
> \begin{aligned}
> \Phi_{Z(t)}(u) & =\sum_{n=-\infty}^{+\infty} p_n(t) u^n=\Phi_{X(t)-Y(t)}(u)=\Phi_{X(t)+(-Y(t))}(u)=\Phi_{X(t)}(u) \Phi_{-Y(t)}(u) \\
> & =\exp \left\{-\left(\lambda_1+\lambda_2\right) t\right\} \cdot \exp \left\{\lambda_1 u t+\lambda_2 u^{-1} t\right\}
> \end{aligned}
> $$

### 3. 设 $\left\{N_1(t) ; t \geq 0\right\}$ 和 $\left\{N_2(t) ; t \geq 0\right\}$ 是相互独立的 Poisson 过程, 其参数分别为 $\lambda_1$ 和 $\lambda_2$. 若 $N_0(t)=N_1(t)-N_2(t)$, 问:
(1) $\left\{N_0(t) ; t \geq 0\right\}$ 是否为 Poisson 过程, 请说明理由;
(2) $\left\{N_0(t) ; t \geq 0\right\}$ 是否为平稳过程, 请说明理由。

> - (1):
>
> 有题可以得到其状态空间为:
> $$
> S=\{0,\pm 1,\pm 2. \pm 3,...,\pm k    \}
> $$
> 所以其不为计数过程，所以其不为Poisson过程。
>
> - (2):
>
> 首先，我们求解其期望:
> $$
> \begin{align}
> E(N_0(t)) &= E(N_1(t)-N_2(t))\\
> &= (\lambda_1-\lambda_2)t
> \end{align}
> $$
> 其期望不为常数，所以其不为平稳过程。
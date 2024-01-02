

# 随机过程课程作业-**Week16**

**作者**：48-丁力-202328015926048  
**日期**：今天

---

## 目录

- [泊松过程](#马尔科夫过程)
  - [题目3](#题目1)
  - [题目4](#题目2)
  - [题目5](#题目1)
  - [题目6](#题目2)

---

## 二阶矩过程、平稳过程和随机分析

### 3、设 $\{X(t), t \geq 0\}$ 是一实的零初值正交增量过程, 且 $X(t) \sim N\left(\mu, \sigma^2 t\right)$ 。令 $Y(t)=2 X(t)-1, t \geq 0$ 。试求过程 $\{Y(t), t \geq 0\}$ 的相关函数 $R_Y(s, t)$ 。

> 由相关函数的定义，我们可以得到：
> $$
> \begin{align}
> 
> R_Y(s,t) &= E(Y(s)Y(t)) \\
> &=E((2X(t)-1)(2X(s)-1)) \\ 
> &=E(4X(t)X(s)-2X(s)-2X(t)+1)\\
> &=4E(X(t)X(s))-2E(X(s))-2E(X(t))+1\\
> &=4E(X(t)X(s))-4\mu +1 \\
> \end{align}
> $$
> 现在，我们来计算$E(X(t)X(s))$, 也就是$R_X(s,t)$, 由于$X(t)$是初值为0的正交增量过程，所以有：
> $$
> \begin{align}
> E(X(t)X(s)) &= E(X(s)[X(t)-X(s)+X(s)])\\
> &=E(X(s)[X(t)-X(s)]) +E(X^2(s))\\
> &\text{由于X(t)是正交增量过程，}\\
> &\text{所以E(X(s)[X(t)-X(s)])= $\mu$E(X(t)-X(s))=0 }\\
> &=E(X^2(s))\\
> &=D(X(s)) + E^2(X(s))\\
> &=\sigma^2 t + \mu^2
> \end{align}
> $$
> 在这里的话，我们假设是$t\geq s$, 同理可得$t<s$, 此时原式子为:
> $$
> \sigma^2s+\mu^2
> $$
> 所以：
> $$
> E(X(t)X(s)) = \max(s,t)\sigma^2+\mu^2
> $$
> 所以得到：
> $$
> R_Y(s,t) =4E(X(t)X(s))-4\mu +1 = 4 \max(s,t)\sigma^2+4\mu^2-4\mu +1
> $$
> 



### 4、设有随机过程 $X(t)=2 Z \sin (t+\Theta),-\infty<t<+\infty$, 其中 $Z$ 、 $\Theta$ 是相互独立的随机变量, $Z \sim N(0,1), P(\Theta=\pi / 4)=P(\Theta=-\pi / 4)=1 / 2$ 。问过程 $X(t)$ 是否均方可积过程? 说明理由。

> 首先我们求其期望函数和自相关函数来判断其为什么过程：
> $$
> \begin{align}
> 
> E(X(t))  &= 2E(Z \sin (t+\Theta))\\
> & \text{由题，两者不相关，所以有}\\
> &=2E(Z)E(\sin(t+\Theta))\\
> &=0
> \end{align}
> $$
> 然后我们来求其自相关函数:
> $$
> \begin{align}
> R_X(s,t) &= E(X(s)X(t))\\
> &= 4E(Z^2 \sin(t+\Theta)\sin(s+\Theta))\\
> &= 4E(Z^2)E(\sin(t+\Theta)\sin(s+\Theta))\\
> &= 4(D(Z)+E^2(Z)) E(\sin(t+\Theta)\sin(s+\Theta))\\
> &=4E(\sin(t+\Theta)\sin(s+\Theta))\\
> &=4\frac{E(\sin(t+\frac{\pi}{4})\sin(s+\frac{\pi}{4})+E(\sin(t-\frac{\pi}{4})\sin(s-\frac{\pi}{4}))}{2}\\
> &= 2 E(\cos(t-\frac{\pi}{4})\cos(s-\frac{\pi}{4})+E(\sin(t-\frac{\pi}{4})\sin(s-\frac{\pi}{4}))\\
> &=2E(\cos(t-s))\\
> &=2\cos(t-s)
> \end{align}
> $$
> 由于其期望值为常数，其相关函数只与$t-s$的间隔相关，所以该过程为平稳过程，所以其是均方可积过程。



### 5、设随机过程 $\xi(t)=X \cos 2 t+Y \sin 2 t,-\infty<t<+\infty$, 其中随机变量 $X$ 和 $Y$ 独立同分布。
（1）如果 $X \sim U(0,1)$, 问过程 $\xi(t)$ 是否平稳过程? 说明理由;
（2）如果 $X \sim N(0,1)$, 问过程 $\xi(t)$ 是否均方可微？说明理由。

> 判断是否平稳和均方可微都可以转换成对其期望以及自相关函数的计算结果的判断。
>
> - (1):
>
> 首先我们来其自相关函数:
> $$
> \begin{align}
> R_{\xi}(s,t)&= E(\xi(t)\xi(s))\\
> &= E(X^2\cos(2t)\cos(2s)+ Y^2\sin(2t)\sin(2s)+XY(\sin(2s+2t)))\\
> &由于X和Y独立同分布\\
> &= E(X^2) E(\cos(2t)\cos(2s)) + E(Y^2)E(\sin(2t)\sin(2s)) +E(X)E(Y) E(\sin(2s+2t))\\
> &= E(\cos(2(t-s)))\frac{1}{3} + \frac{1}{4} \sin(2(t+s))\\
> &=\frac{\cos(2(t-s))}{3}+\frac{\sin(2(t+s))}{4}
> \end{align}
> $$
> 由于其自相关函数和$t+s$有关，故其不是平稳过程。
>
> - (2):
>
> 此时， 我们有：
> $$
> E(X^2) =E(Y^2) =  E^2(X) +D(X) = 1, E(X) = E(Y)=0 
> $$
> 所以:
> $$
> R_{\xi}(s,t) = \cos(2(t-s)), E(\xi(t)) = 0
> $$
> 其为平稳过程，所以其均方可微。



### 6、设随机过程 $\{X(t) ;-\infty<t<+\infty\}$ 是一实正交增量过程, 并且 $E\{X(t)\}=0$, 及满足:

$$
E\left\{[X(t)-X(s)]^2\right\}=|t-s|, \quad-\infty<s, t<+\infty ;
$$

令: $Y(t)=X(t)-X(t-1),-\infty<t<+\infty$, 试证明 $Y(t)$ 是平稳过程。

> 这一题和上面的还是一样的，还是分别求其期望和自相关函数然后进行分析：
> $$
> E(Y(t)) = E(X(t-1))= E(X(t-1)) = 0-0= 0
> $$
> 其期望容易求得，现在我们来求其自相关函数：
> $$
> \begin{align}
> R_Y(t,s) &= E(Y(t)Y(s))\\
> &= E([X(t)-X(t-1)][(X(s)-X(s-1))])\\
> = & \frac{1}{2}\left[E\left\{[X(t)-X(s-1)]^2\right\}-E\left\{[X(t)-X(s)]^2\right\}\right. \\
> & \left.+E\left\{[X(t-1)-X(s)]^2\right\}-E\left\{[X(t-1)-X(s-1)]^2\right\}\right] \\
> = & \frac{1}{2}[|t-(s-1)|-|t-s|+|(t-1)-s|-|(t-1)-(s-1)|]\\
> & = \begin{cases}1-|t-s|, & \text { if }|t-s| \leq 1 \\
> 0, & \text { if }|t-s|>1\end{cases}
> \end{align}
> $$
> 所以其为平稳过程。

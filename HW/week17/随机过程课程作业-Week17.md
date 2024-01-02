

# 随机过程课程作业-**Week16**

**作者**：48-丁力-202328015926048  
**日期**：今天

---

## 目录

- [泊松过程](#马尔科夫过程)
  - [题目7](#题目1)
  - [题目8](#题目2)
  - [题目9](#题目1)
  - [题目10](#题目2)

---

## 二阶矩过程、平稳过程和随机分析

###  7、设 $\xi(t)=X \sin (Y t) ; t \geq 0$, 而随机变量 $X 、 Y$ 是相互独立且都服从 $[0,1]$ 上的均匀分布,试求此过程的均值函数及相关函数。并问此过程是否是平稳过程, 是否连续、可导?

> - 首先求其均值函数:
>
> $$
> \begin{align}
> 
> E(\xi(t)) &= E(X\sin(Yt)) \\
> & 由于X和Y独立\\
> &= E(X) E(\sin(Yt))\\
> &= \frac{1}{2} \int _0^1 Y\sin(Yt)dY\\
> &= \frac{1}{2} \frac{t-t\cos(t)}{t^2}\\
> &=\frac{1-\cos(t)}{2t}
> \end{align}
> $$
>
> - 然后求其相关函数：
>
> $$
> \begin{align}
> R(s,t) &=E(\xi(s)\xi(t))\\
> &=E(X^2\sin(Yt)\sin(Ys))\\
> &=E(X^2) E(\sin(Yt)\sin(Ys))\\
> &= \frac{1}{3} E(\frac{\cos(Y(t-s)-\cos(Y(t+s)))}{2} )\\
> &= \frac{1}{6}\left(\frac{t \cos (t) \sin (s)-s \cos (s) \sin (t)}{s^2-t^2}\right)
> \end{align}
> $$
>
> 由于其期望不是常数，并且相关函数不是只与$t-s$有关，所以该过程不是平稳过程, 并且不连续，不可导。



### 8、设 $\{X(t), t \in R\}$ 是连续平稳过程, 均值为 $m$, 协方差函数为 $C_X(\tau)=a e^{-b|\tau|}$, 其中: $\tau \in R, a, b>0$ 。对固定的 $T>0$, 令 $Y=T^{-1} \int_0^T X(s) d s$, 证明: 

$$
E\{Y\}=m, \operatorname{Var}(Y)=2 a\left[(b T)^{-1}-(b T)^{-2}\left(1-e^{-b T}\right)\right]
$$

> 题干要求所求的内容为期望与方差，那么我们一个个的开始计算：
> $$
> \begin{align}
> E(Y) &= E(T^{-1} \int_0^T X(s) d s)\\
> &=T^{-1}\int_0^T E(X(s)) ds\\
> &=T^{-1}\int_0^T m ds\\
> &= m
> \end{align}
> $$
> Q.E.D
>
> - 然后我们来计算其方差：
>
> $$
> \begin{align}
> Var(Y) &= E(Y^2)-E^2(Y)\\
> &=E(Y^2)-m^2\\
> &=E([T^{-1} \int_0^T X(s) d s]^2)-m^2\\
> &=T^{-2}\int_0^T\int_0^T E(X(s)X(u)) ds du -m^2\\
> &= T^{-2} \int_0^T\int_0^T R_X(s-u)ds du -m^2\\
> &= T^{-2} \int_0^T\int_0^T  [C_X(s-u)+m^2] ds du -m^2\\
> &= T^{-2} \int_0^T\int_0^T  ae^{-b|\tau|} ds du\\
> &= 2 a\left[(b T)^{-1}-(b T)^{-2}\left(1-e^{-b T}\right)\right]
> 
> 
> 
> \end{align}
> $$
>
> Q.E.D
>
> 



### 9、设 $(X, Y) \sim N\left(0,0, \sigma_1^2, \sigma_2^2, \rho\right)$, 令 $X(t)=X+t Y$, 以及 $Y(t)=\int_0^t X(u) d u$, $Z(t)=\int_0^t X^2(u) d u$, 对于任意 $0 \leq s \leq t$,

（1）求 $E\{X(t)\}, E\{Y(t)\}, E\{Z(t)\}, \operatorname{Cov}(X(s), X(t)), \operatorname{Cov}(Y(s), Y(t))$;

（2）证明 $X(t)$ 在 $t>0$ 上均方连续、均方可导

（3）求 $Y(t)$ 及 $Z(t)$ 的均方导数。

> - (1)
>
> ---
>
> - 首先来求 $X(t)$的期望：
>
> $$
> \begin{align}
> E(X(t)) &= E(X+tY)\\
> &=  E(X) + E(tY)\\
> &= 0 + 0\\
> &= 0
> 
> 
> 
> \end{align}
> $$
>
> ---
>
> - 再来求$Y(t)$的期望：
>
> $$
> \begin{align}
> E(Y(t)) &= E(\int_0^t X(u) d u)\\
> &=  E(\int_0^t X+uY d u)\\
> &=  \int_0^t E(X)+E(uY) d u\\
> &= 0+0\\
> &=0
> 
> \end{align}
> $$
>
> ---
>
> - 再来求$Z(t)$的期望:
>
> $$
> \begin{align}
> E(Z(t)) &= E(\int_0^t X^2(u) d u)\\
> &=E( \int_0^t [X+uY]^2 d u) \\
> &= E(\int_0^t X^2+ 2uXY + u^2Y^2 d u )\\
> &= E(X^2u+u^2XY+\frac{u^3}{3}Y^2 \mid_0^t)\\
> &= E(X^2t+t^2XY+\frac{t^3}{3}Y^2)\\
> &= t\sigma_1^2+ t^2\rho\sigma_1\sigma_2 + \frac{t^3}{3} \sigma_2^2
> 
> \end{align}
> $$
>
> 
>
> ---
>
> - 然后我们再来求其的协方差：
>
> $$
> \begin{align}
> \operatorname{Cov}(X(s), X(t)) &= R_X(s,t) \\
> &= E(X(s)X(t))\\
> &= E([X+sY][X+tY])\\
> &= E(X^2+tXY+sXY+stY^2)\\
> &= E^2(X)+D(X) + (t+s)E(XY) + st E(Y^2)\\
> &= \sigma_1^2+(s+t)\rho \sigma_1\sigma_2 +st\sigma_2^2
> \end{align}
> $$
>
> ---
>
> - 然后我们再来求$Y$的自相关函数：
>
> $$
> \begin{align}
> \operatorname{Cov}(Y(s), Y(t)) &= R_Y(s,t) \\
> &= E(Y(s)Y(t))\\
> &= E(\int_0^t X(u) d u\int_0^s X(u) d u)\\
> &= E(\int_0^t [X+uY] d u\int_0^s [X+uY] d u)\\
> &= E([tX+\frac{t^2}{2}Y][sX+\frac{s^2}{2}Y] )\\
> &= E(stX^2+[\frac{ts^2+t^2s}{2}XY + \frac{s^2t^2}{4} Y^2])\\
> &= st\sigma_1^2 + \frac{ts^2+t^2s}{2} \rho\sigma_1\sigma_2 + \frac{s^2t^2}{4} \sigma_2^2\\
> &= st\sigma_1^2 + \frac{t+s}{2} ts\rho\sigma_1\sigma_2 + \frac{s^2t^2}{4} \sigma_2^2
> \end{align}
> $$
>
> - (2)
>
> 因为由：
> $$
> R_X(s, t)=\sigma_1^2+(s+t) \rho \sigma_1 \sigma_2+s t \sigma_2^2
> $$
>   可知, $X(t)$ 在 $t>0$ 上均方连续、均方可导。
>
> - (3)
>
> $$
> R_Y(s, t)=\sigma_1^2 s t+\frac{1}{2} \rho \sigma_1 \sigma_2 s t(s+t)+\frac{1}{4} \sigma_2^2 s^2 t^2,
> $$
>
> 可知, $Y(t)$ 在 $t>0$ 上均方可导。其均方导数 $Y^{\prime}(t)$ 的均值函数和相关函数分别为
> $$
> \begin{gathered}
> \mu_{Y^{\prime}}=E\left\{Y^{\prime}(t)\right\}=0 \\
> R_{Y^{\prime}}(s, t)=\frac{\partial^2 R_Y(s, t)}{\partial s \partial t}=\sigma_1^2+\rho \sigma_1 \sigma_2(s+t)+\sigma_2^2 s t
> \end{gathered}
> $$





### 10、设随机过程 $\{X(t) ;-\infty<t<+\infty\}$ 是均值为零、自相关函数为 $R_X(\tau)$ 的实平稳正态过程。设 $X(t)$ 通过线性全波检波器后, 其输出为 $Y(t)=|X(t)|$, 试求:
（1）随机过程 $Y(t)$ 的相关函数 $R_Y(\tau)$, 并说明其是否为平稳过程;
（2）随机过程 $Y(t)$ 的均值和方差;
（3）随机过程 $Y(t)$ 的一维概率分布密度函数 $f_Y(y)$ 。

> - (1)设 $X, Y$ 是服从均值为零的正态分布二维随机变量, 其联合概率密度为:
>   $$
>   f(x, y)=\frac{1}{2 \pi \sigma_1 \sigma_2 \sqrt{1-r^2}} \exp \left\{-\frac{1}{2\left(1-r^2\right)}\left[\frac{x^2}{\sigma_1^2}-\frac{2 r x y}{\sigma_1 \sigma_2}+\frac{y^2}{\sigma_2^2}\right]\right\}
>   $$
>
>   则有:
>   $$
>   E\{|X Y|\}=\frac{2 \sigma_1 \sigma_2}{\pi}[\varphi \sin \varphi+\cos \varphi]
>   $$
>
>   其中: $\sin \varphi=r,-\frac{\pi}{2}<\varphi<\frac{\pi}{2}$ 。
>   因为 $X(t+\tau)$ 与 $X(t)$ 是联合正态分布的, 且各自的均值为零, 方差为 $R_X(0)$, 相关系数为
>   $$
>   r=\frac{E\{X(t+\tau) E(t)\}}{\sqrt{E\left\{X^2(t+\tau)\right\}} \sqrt{E\left\{X^2(t)\right.}}=\frac{R_X(\tau)}{R_X(0)}
>   $$
>
>   由此, 我们有:
>   $$
>   R_Y(\tau)=E\{|X(t+\tau)||X(t)|\}=\frac{2 R_X(0)[\varphi \sin \varphi+\cos \varphi]}{\pi}
>   $$
>
>   其中: $\sin \varphi=\frac{R_X(\tau)}{R_X(0)},-\frac{\pi}{2}<\varphi<\frac{\pi}{2}$ 。
>   $$
>   m_Y=E\{Y(t)\}=\int_{-\infty}^{+\infty}|x| f_X(x) d x=2 \int_0^{+\infty} x \frac{1}{\sqrt{2 \pi R_X(0)}} \exp \left\{-\frac{x^2}{2 R_X(0)}\right\} d x=\sqrt{\frac{2 R_X(0)}{\pi}}
>   $$
>
>   由此可知, 随机过程 $Y(t)$ 是平稳过程。
>
>   - (2) 均值计算如上 (1), 方差计算如下:
>
>   $$
>   \begin{gathered}
>   E\left\{Y^2(t)\right\}=E\left\{X^2(t)\right\}=R_X(0) \\
>   \sigma_Y^2=E\left\{Y^2(t)\right\}-m_Y^2=\left(1-\frac{2}{\pi}\right) R_X(0)
>   \end{gathered}
>   $$
>   - (3) 因为 $X(t)$ 的一维分布为正态分布, 其分布密度函数为:
>
> $$
> f_X(x)=\frac{1}{\sqrt{2 \pi R_X(0)}} \exp \left\{-\frac{x^2}{2 R_X(0)}\right\}, \quad-\infty<x<+\infty
> $$
>
> 因此, 我们有:
> $$
> f_Y(y)=\left[f_X(y)+f_X(-y)\right]=\frac{2}{\sqrt{2 \pi R_X(0)}} \exp \left\{-\frac{y^2}{2 R_X(0)}\right\}, \quad y>0
> $$

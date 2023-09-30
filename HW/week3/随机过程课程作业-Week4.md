

# 随机过程课程作业-**Week3**

**作者**：48-丁力-202328015926048  
**日期**：今天

---

## 目录

- [随机过程及其分类](#随机过程及其分类)
  - [题目1](#题目1)
  - [题目2](#题目2)
  - [题目3](#题目3)
  - [题目4](#题目4)

---

## 随机过程及其分类

### 题目1

12、考察两个谐波随机信号 $X(t)$ 和 $Y(t)$, 其中:
$$
X(t)=A \cos \left(\omega_c t+\phi\right), \quad Y(t)=B \cos \left(\omega_c t\right)
$$
式中 $A$ 和 $\omega_c$ 为正的常数; $\phi$ 是 $[-\pi, \pi]$ 内均匀分布的随机变量, $B$ 是标准正态分布的 随机变量。
  (a) 求 $X(t)$ 的均值、方差和相关函数;
（b）若 $\phi$ 与 $B$ 独立, 求 $X(t)$ 与 $Y(t)$ 的互相关函数。


> **答案**：
>
> - (a):
>
> 下面，我们将一个个计算这些值：
>
> **期望:**
> $$
> \begin{align}
> E(X(t)) &= E(A\cos(\omega_ct+\phi))\\
> &由于其中A为常数\\
> &= AE(\cos(\omega_ct+\phi))\\
> &=AE(\cos(\omega_ct)\cos(\phi)-\sin(\omega_ct)\sin(\phi))\\
> &=A(E(\cos(\omega_ct)\cos(\phi))-  E(\sin(\omega_ct)\sin(\phi)))\\
> &由于\int_{-\pi}^\pi\cos(\phi)d\phi =\int_{-\pi}^\pi\sin(\phi)d\phi = 0\\ 
> &= A(0-0)\\
> &=0
> \end{align}
> $$
> **方差:**
> $$
> \begin{align}
> D(X(t)) &= E(X^2(t))- E^2(X(t)) \\
> &=  E(X^2(t)) \\
> &=  E(A^2\cos^2(\omega_ct+\phi))\\
> &=A^2 E(\cos^2(\omega_ct+\phi))\\
> &= A^2 E(\frac{1+\cos(2(\omega_ct+\phi))}{2})\\
> &= A^2(E(\frac{1}{2})+E(\frac{\cos(2(\omega_ct+\phi)}{2}))\\
> &= A^2(\frac{1}{2}+0)\\
> &= \frac{A^2}{2}
> \end{align}
> $$
> **相关函数:**
> $$
> \begin{align}
> R_{XX}(X(t_1), X(t_2))&= E(X_{t_1}X_{t_2})\\
> &=E(A^2\cos(\omega_ct_1+\phi)\cos(\omega_ct_2+\phi))\\
> &= A^2E(\cos(\omega_ct_1+\phi)\cos(\omega_ct_2+\phi))\\
> &由积化和差公式：\\
> &=  A^2E(\cos(w_c(t_1+t_2))+\cos(w_c(t_1-t_2)))\\
> &= A^2\int_{-\pi}^\pi \cos(w_c(t_1+t_2+2\phi))+\cos(w_c(t_1-t_2)) \frac{1}{2\pi}d\phi\\
> &因为2\pi 是周期性的，所以前一项直接变为0，那么也就是求 \\
> &= A^2\int_{-\pi}^\pi \cos(w_c(t_1-t_2)) \frac{1}{2\pi}d\phi\\
> &=A^2\cos(w_c(t_1-t_2))
> \end{align}
> $$
>
> - (b):
>
> 现在让我们来求这个互相关函数：
> $$
> \begin{align}
> R(X(t), Y(t)) &=  E(X(t)Y(t)) \\
> &= E(A \cos \left(\omega_c t+\phi\right)B \cos \left(\omega_c t\right))\\
> &= AE(\cos \left(\omega_c t+\phi\right)B \cos \left(\omega_c t\right))\\
> &= A\int_{-\pi}^\pi \frac{1}{2\pi} d\phi \int_{-\infty}^\infty \cos \left(\omega_c t+\phi\right) \cos \left(\omega_c t\right) B \frac{1}{\sqrt{2\pi}} e^{-\frac{B^2}{2}} dB\\
> &由于其为奇函数,所以在对称区间积分为0，也就是\\
> &= 0
> \end{align}
> $$
> 也就是说，这个互相关函数为0。

13、设 $\xi(t)=X \sin (Y t) ; t \geq 0$, 而随机变量 $X 、 Y$ 是相互独立且都服从 $[0,1]$ 上的均匀分布, 试求此过程的均值函数及相关函数。

> **答案**：
>
> 同上，我们会一个个的计算这两个函数：
>
> - 均值函数：
>
> 求其对应的均值函数也就是求其期望，也即
> $$
> E(\xi(t)) &= \int_{0}^1 dY \int_{0}^1 X\sin(Yt) dX \\
> &= \frac{1}{2} \int_{0}^1 \sin(Yt)  dY\\
> &= \frac{1-\cos t}{2t},\quad t\geq0
> $$
>
> - 相关函数
>
> $$
> \begin{align}
> R(\xi(t_1),\xi(t_2)) &= E(\xi(t_1)\xi(t_2))\\
> &= E(X^2 \sin (Y t_1) \sin (Y t_2))\\
> &由积化和差公式可以得到\\
> &=E(X^2\frac{1}{2}(\cos(Y(t_1-t_2)-\cos(Y(t_1+t_2)))\\
> &=E(X^2\frac{1}{2}(\cos(Y(t_1-t_2)))) - E(X^2\frac{1}{2}(\cos(Y(t_1+t_2)))\\
> &= \frac{1}{2}(E(X^2(\cos(Y(t_1-t_2)))) - E(X^2(\cos(Y(t_1+t_2))))\\
> &=\frac{1}{2}(\int_{0}^1 dY \int_{0}^1 X^2\cos(Y(t_1-t_2)) dX-\int_{0}^1 dY \int_{0}^1 X^2\cos(Y(t_1-t_2)) dX)\\
> &= \frac{1}{6}(\int_0^1 \cos(Y(t_1-t_2))dY- \int_0^1 \cos(Y(t_1+t_2))dY) \\
> &=\frac{1}{6}(\frac{\sin(t_1-t_2)}{t_1-t_2}-\frac{\sin(t_1+t_2)}{t_1+t_2})
> \end{align}
> $$
>
> 
>
> 

### 题目3

15、设 $X \sim N\left(\mu, \sigma^2\right), Y$ 满足参数为 $p$ 的几何分布, 即 $P\{Y=k\}=(1-p)^{k-1} p$, 其中: $0<p<1, k=1,2, \cdots, X$ 与 $Y$ 独立。令 $X(t)=X+e^{-t} Y$, 试求:
(1) $X(t)$ 在 $t>0$ 的一维概率密度函数;
(2) $E\{X(t)\}, \operatorname{Cov}(X(s), X(t))(0 \leq s \leq t)$;

> **答案**： 
>
> - (1):
>
> 首先，我们先求其对应的概率分布函数， 由定义，我们可以得到：
> $$
> \begin{align}
> F_{X(t)}(u) &= P_{X(t)} (X(t)\le u)\\
> &= P_{X(t)}(X+e^{-t} Y\leq u)\\
> &= \sum_{k=1}^\infty P(X+e^{-t}Y\leq u|Y=k) p(1-p)^{1-k} \\
> &= \sum_{k=1}^\infty  P(X\leq u-e^{-t}k) p(1-p)^{1-k} \\
> &= \sum_{k=1}^\infty \int_{-\infty}^{u-e^{-t}k}  \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x-\mu)^2}{2\sigma^2}} p(1-p)^{k-1} dx \\
> \end{align}
> $$
> 那么，现在我们求解概率密度函数，也就是对概率分布函数进行求导得到：
> $$
> \begin{align}
> f_{X(t)}(u) &= \frac{\partial F_{X(t)}(u)}{\partial u}\\
> &= \sum_{k=1}^\infty \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(u-e^tk-\mu)^2}{2\sigma^2}} p(1-p)^{k-1}
> \end{align}
> $$
>
>
> - (2)
>
> 下面，我们将一个个求解这些变量：
>
> -  $E(X(t))$
>
> 
> $$
> \begin{align}
> E(X(t)) &= E(X+e^{-t}Y)\\
> &= E(X)+ E(e^{-t}Y)\\
> &= \mu + \frac{1}{pe^t}
> \end{align}
> $$
>
> - $ \operatorname{Cov}(X(s), X(t))(0 \leq s \leq t)$
>
> $$
> \begin{align}
> \operatorname{Cov}(X(s), X(t))&=  E(X(s)X(t))- E(X(s)) E(X(t))\\
> &=  E((X+e^{-s}Y)(X+e^{-t}Y))-  (\mu^2+\frac{\mu}{p}(\frac{1}{e^t}+\frac{1}{e^s})+\frac{1}{p^2e^{s+t}})\\ 
> &=  E(X^2+XY(e^{-s}+e^{-t})+Y^2e^{-(t+s)})-  (\mu^2+\frac{\mu}{p}(\frac{1}{e^t}+\frac{1}{e^s})+\frac{1}{p^2e^{s+t}})\\ 
> &=  E^2(X) + D(X) +(\frac{1}{e^t}+\frac{1}{e^s})\sum_{k=1}^\infty E(X|Y) p(1-p)^{k-1} +(E^2(Y)+D(Y))\frac{1}{e^{t+s}}- (\mu^2+\frac{\mu}{p}(\frac{1}{e^t}+\frac{1}{e^s})+\frac{1}{p^2e^{s+t}}) \\
> &由于X和Y独立\\
> &= \mu^2+\sigma^2+(\frac{1}{e^t}+\frac{1}{e^s})\sum_{k=1}^\infty E(X) p(1-p)^{k-1}+(\frac{1}{p^2}+\frac{1-p}{p^2})\frac{1}{e^{t+s}}- (\mu^2+\frac{\mu}{p}(\frac{1}{e^t}+\frac{1}{e^s})+\frac{1}{p^2e^{s+t}}) \\
> &= \mu^2+\sigma^2+(\frac{1}{e^t}+\frac{\mu}{p}(\frac{1}{e^t}+\frac{1}{e^s})+(\frac{1}{p^2}+\frac{1-p}{p^2})\frac{1}{e^{t+s}}- (\mu^2+\frac{\mu}{p}(\frac{1}{e^t}+\frac{1}{e^s})+\frac{1}{p^2e^{s+t}}) \\
> &= \sigma^2+ \frac{1-p}{p^2e^{s+t}}
> \end{align}
> $$
>
> 

---

### 题目4

17、设随机过程 $\xi(t)=X \cos 2 t+Y \sin 2 t,-\infty<t<+\infty$, 其中随机变量 $X$ 和 $Y$ 独立同分布。
（1）如果 $X \sim U(0,1)$, 试求过程 $\xi(t)$ 的均值函数和相关函数;
（2） 如果 $X \sim N(0,1)$, 试求过程 $\xi(t)$ 的均值函数和相关函数;

> **答案**：
>
> - (1):
>
>   下面，我们将一个个的求解这些内容：
>
>   - $E(\xi(t))$
>
>   $$
>   \begin{align}
>   E(\xi(t))&= E(X\cos2t+Y\sin2t)\\
>   &= \cos2tE(X) + \sin2tE(Y) \\
>   &= \frac{\cos2t+\sin 2t\quad}{2}, t\in R
>   \end{align}
>   $$
>
>   - $R(\xi(t), \xi(s))$
>
>   $$
>   \begin{align}
>   R(\xi(t), \xi(s)) &= E(\xi(t) \xi(s))\\
>   &= E((X\cos2t+Y\sin2t)\times (X\cos2s+Y\sin2s))\\
>   &= E(X^2\cos2t\cos2s+XY(\sin2s\cos2t+\sin2t\cos2s)+Y^2\sin2s\sin2t)\\
>   &= \cos2t\cos2sE(X^2) + \sin(2s+2t)E(XY) + \sin2s\sin2tE(Y^2)\\
>   &= (\sin2t\sin2s+\cos2t\cos2s)(\frac{1}{12}+(\frac{1}{2})^2) + \sin(2s+2t)E(X)E(Y)\\
>   &= \frac{1}{3} \cos(2t-2s) +\frac{1}{4}\sin(2t+2s)
>   \end{align}
>   $$
>
> - (2):
>
>   同上，我们可以简单的计算得到这些内容，与上面不同的是，此时的两者期望值和方程分别变成:
>   $$
>   E(X)= 0, D(X) = 1,E(X^2) = D(X) +E^2(X) = 1
>   $$
>   
>
> ​		所以，简单替换，便可以得到：
>
> - $E(\xi(t))$
>
> $$
> \begin{align}
> E(\xi(t))&= E(X\cos2t+Y\sin2t)\\
> &= \cos2tE(X) + \sin2tE(Y) \\
> &= 0
> \end{align}
> $$
>
> - $R(\xi(t), \xi(s))$
>
> $$
> \begin{align}
> R(\xi(t), \xi(s)) &= E(\xi(t) \xi(s))\\
> &= E((X\cos2t+Y\sin2t)\times (X\cos2s+Y\sin2s))\\
> &= E(X^2\cos2t\cos2s+XY(\sin2s\cos2t+\sin2t\cos2s)+Y^2\sin2s\sin2t)\\
> &= \cos2t\cos2sE(X^2) + \sin(2s+2t)E(XY) + \sin2s\sin2tE(Y^2)\\
> &= (\sin2t\sin2s+\cos2t\cos2s)\\
> &=  \cos(2t-2s) 
> \end{align}
> $$
>
> 

---



### 问题5

20、设随机变量 $X$ 与随机变量 $\Theta$ 独立, 且都服从均匀分布, 即 $X \sim U[2,4], \Theta \sim U[1,3]$ 。 令: $Z=X e^{\Theta \ln 2}$, 试求随机变量 $Z$ 的分布密度函数。思考: 若给定随机过程: $Z(t)=X e^{\Theta \ln t}(t>0)$, 则其一维分布如何确定?

> 首先，令$Y=e^{\Theta\ln2}$, 然后我们来求其对应的概率分布：
>$$
>\begin{align}
>F_Y(y)&= P_Y(Y\leq y) \\
>&= P_Y(e^{\theta \ln 2}\leq y)\\
>&=  P_Y(\theta\leq \frac{\ln y}{\ln 2})\\
>&= \int_1^{\frac{\ln y}{\ln 2}} f_{\Theta}(\theta) d \theta\\
>&=\frac{\ln y}{2\ln2},\quad y \in [2,8]
>\end{align}
>$$
>那么，我们可以得到其对应的概率密度函数：
>$$
>\begin{align}
>f_Y(y) &= \frac{F_Y(y)}{dy} \\
>&= \frac{1}{(2\ln2) y},\quad y\in [2,8]
>\end{align}
>$$
>那么，进行变换，我们可以得到$Z$的新的表达式。
>$$
>Z = XY
>$$
>由公式，我们可以得到：
>$$
>f_Z(z)= \int_{-\infty}^\infty \frac{1}{\mid x\mid} f_X(x) f_Y(\frac{z}{x}) dx
>$$
>又有:
>$$
>y = \frac{z}{x} \in [2,8] \rightarrow x\in[\frac{z}{8}, \frac{z}{2}]
>$$
>又因为：
>$$
>x\in[2,4], z\in[4,32]
>$$
>这里我们需要讨论z的取值范围：
>$$
>\begin{cases}
>z/2\geq2, z/2\leq4\\
>z/2\geq4, z/8\leq2\\
>z/8\geq2
>\end{cases}
>$$
>也就是:
>$$
>\begin{cases}
>4\leq z \leq 8\\
>8\leq z \leq 16\\
>16\leq z \leq 32
>\end{cases}
>$$
>其对应的x的积分区间为：
>$$
>\begin{cases}
>2\leq x \leq z/2 \\
>2\leq z \leq 4\\
>z/8 \leq z \leq 4
>\end{cases}
>$$
>
>$$
>f_Z(z)= \int_{-\infty}^\infty \frac{1}{\mid x\mid} f_X(x) f_Y(\frac{z}{x}) dx = \frac{1}{(4\ln2)}\int_{-\infty}^\infty\frac{1}{z} dx
>$$
>那么，我们容易求得其概率密度函数在不同区间的函数：
>$$
>f_z(Z) = \begin{cases}
>\frac{1}{(4\ln2)}(\frac{1}{2}-\frac{2}{z}),4\leq z \leq 8\\
>\frac{1}{(2\ln2)z},8\leq z \leq 16\\
>\frac{1}{(4\ln2)}(\frac{4}{z}-\frac{1}{8}),16\leq z \leq 32
>\end{cases}
>$$
>
>- **$Z(t)=X e^{\Theta \ln t}(t>0)$, 则其一维分布如何确定?**
>
>> 其实可以用和上面相同的算法来计算：
>>
>> - $t=1$时，
>>
>>   此时， $Z(t)=X\thicksim U[2,4]$。
>>
>> - $t\neq1$时，
>>
>>    此时，我们同样令$Y=e^{\Theta\ln t}$, 那么可以得到其概率密度函数为：
>>
>>   - $t>1$时
>>
>>   $$
>>   f_y(Y) = \frac{1}{(2\ln t )y}, y\in [t, t^3]
>>   $$
>>
>>   所以：
>>   $$
>>   z\in[2t,4t^3]
>>   $$
>>   
>>
>>   同上：
>>   $$
>>   y = \frac{z}{x} \in [t, t^3] \rightarrow x\in[\frac{z}{t^3},\frac{z}{t}] \rightarrow x\in[\frac{2}{t^2}. 4t^2]
>>   $$
>>   进行讨论可以得到如下区间：
>>   $$
>>   \begin{cases}
>>   z\leq \min(2t^3,4t)\\
>>   2t^3\leq z \leq 4t\\
>>    4t\leq z \leq  2t^3\\
>>    \max(2t^3,4t) \leq z
>>   \end{cases}
>>   $$
>>   所以对于$t$的划分，可以分为:
>>   $$
>>   \begin{cases}
>>   2t^3>4t\\
>>   2t^3\leq 4t
>>   \end{cases} \rightarrow \begin{cases}
>>   t\geq \sqrt{2}\\
>>   1<t< \sqrt{2} 
>>   \end{cases}
>>   $$
>>   $t\geq \sqrt{2}$时：
>>
>>   > $$
>>   > \begin{cases}
>>   > z\leq 4t\\
>>   > 
>>   >  4t\leq z \leq  2t^3\\
>>   >  2t^3 \leq z 
>>   > \end{cases}\xrightarrow{积分区间} \begin{cases}
>>   > [2,\frac{z}{t}]\\
>>   > 
>>   > [2,4]\\
>>   > [\frac{z}{t^3},4]
>>   > \end{cases}
>>   > $$
>>   >
>>   > 所以，此时可以得到其对应的概率密度为：
>>   > $$
>>   > f_z(Z(t)) = \begin{cases}
>>   > \frac{1}{(4\ln t)}(\frac{1}{t}-\frac{2}{z}),z\in [2t,4t]\\
>>   > \frac{1}{(2\ln t)z},z\in [4t,2t^3]\\
>>   > \frac{1}{(4\ln t)}(\frac{4}{z}-\frac{1}{t^3}), z\in [2t^3,4t^3]
>>   > \end{cases}
>>   > $$
>>   > 
>>
>>   $1<t< \sqrt{2} $时：
>>
>>   > 容易知道，此时概率密度函数相同，但是取值范围不同：
>>   > $$
>>   > f_z(Z(t)) = \begin{cases}
>>   > \frac{1}{(4\ln t)}(\frac{1}{t}-\frac{2}{z}),z\in [2t,2t^3]\\
>>   > \frac{1}{(2\ln t)z},z\in [2t^3,4t]\\
>>   > \frac{1}{(4\ln t)}(\frac{4}{z}-\frac{1}{t^3}), z\in [4t,4t^3]
>>   > \end{cases}
>>   > $$
>>   > 
>>
>>   - $t<1$时
>>
>>   $$
>>   f_y(Y) = -  \frac{1}{(2\ln t )y},y\in[t^3,t]
>>   $$
>>
>>   所以：
>>   $$
>>   z\in[2t^3,4t]
>>   $$
>>   
>>
>>   同上:
>>   $$
>>   y = \frac{z}{x} \in [t^3, t] \rightarrow x\in[\frac{z}{t},\frac{z}{t^3}] \rightarrow x\in[2t^2. \frac{4}{t^2}]
>>   $$
>>
>>   - $t<1$时
>>
>>     对于这种情况，我们已经知道 $f_Y(y) = -\frac{1}{(2\ln t)y}$，且 $y$ 的取值范围为 $[t^3,t]$。
>>
>>     同样地，我们可以得到 $z$ 的取值范围为 $[2t^3,4t]$。
>>
>>     由于 $y = \frac{z}{x}$，我们可以得到 $x$ 的取值范围为 $[2t^2, \frac{4}{t^2}]$。
>>
>>     接下来，我们可以使用卷积公式来求解 $Z$ 的概率密度函数。
>>
>>     1. 对于 $2t^3 \leq z \leq 2t$ 的情况：
>>       $$
>>       f_{Z}(z(t)) = \frac{2t - z}{4z \ln t}
>>       $$
>>       
>>
>>     2. 对于 $2t \leq z \leq 4t$ 的情况：
>>       $$
>>       f_{Z}(z(t)) = \frac{1}{2z \ln t} 
>>       $$
>>       
>>     
>>     3. 对于 $4t \leq z \leq 4t^3$ 的情况：
>>       $$
>>        f_{Z}(z(t)) = \frac{4t^3 - z}{4z \ln t} 
>>       $$
>>       
>>     
>>     我们有：
>>     $$
>>     f_Z(z(t)) = 
>>     \begin{cases} 
>>     \frac{2t - z}{4z \ln t}, & 2t^3 \leq z \leq 2t \\
>>     \frac{1}{2z \ln t}, & 2t \leq z \leq 4t \\
>>     \frac{4t^3 - z}{4z \ln t}, & 4t \leq z \leq 4t^3 
>>     \end{cases}
>>     $$
>
>结论：
>
>对于随机变量 $Z(t) = X e^{\Theta \ln t}$，其一维分布可以根据 $t$ 的不同值进行划分。具体来说：
>
>1. 当 $t=1$ 时，$Z(t)$ 的分布与 $X$ 相同，即 $Z(t) \sim U[2,4]$。
>2. 当 $t \neq 1$ 时，$Z(t)$ 的分布会受到 $t$ 的值的影响，具体如下：
>   - 当 $t > 1$ 时，$Z(t)$ 的概率密度函数为：
>     $$
>     f_Z(z(t)) = 
>     \begin{cases} 
>     \frac{1}{(4\ln t)}(\frac{1}{t}-\frac{2}{z}), & z \in [2t,4t] \\
>     \frac{1}{(2\ln t)z}, & z \in [4t,2t^3] \\
>     \frac{1}{(4\ln t)}(\frac{4}{z}-\frac{1}{t^3}), & z \in [2t^3,4t^3]
>     \end{cases}
>     $$
>   - 当 $1 < t < \sqrt{2}$ 时，$Z(t)$ 的概率密度函数为：
>     $$
>     f_Z(z(t)) = 
>     \begin{cases} 
>     \frac{1}{(4\ln t)}(\frac{1}{t}-\frac{2}{z}), & z \in [2t,2t^3] \\
>     \frac{1}{(2\ln t)z}, & z \in [2t^3,4t] \\
>     \frac{1}{(4\ln t)}(\frac{4}{z}-\frac{1}{t^3}), & z \in [4t,4t^3]
>     \end{cases}
>     $$
>   - 当 $t < 1$ 时，$Z(t)$ 的概率密度函数为：
>     $$
>     f_Z(z(t)) = 
>     \begin{cases} 
>     \frac{2t - z}{4z \ln t}, & z \in [2t^3,2t] \\
>     \frac{1}{2z \ln t}, & z \in [2t,4t] \\
>     \frac{4t^3 - z}{4z \ln t}, & z \in [4t,4t^3]
>     \end{cases}
>     $$
>
>








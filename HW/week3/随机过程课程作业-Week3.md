

# 随机过程课程作业-**Week3**
**作者**：56-丁力-202328015926048  
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

设二维随机变量 $ (X, Y) $ 的联合密度函数为
$$
f(x, y) = 
\begin{cases} 
\frac{4}{7}(1+y+xy), & 0 < x < 1, 0 < y < 1 \\
0, & \text{其他}
\end{cases}
$$
试求随机变量 $ Y(1+X) $ 的密度函数。

> **答案**：
>
> 首先，我们需要找到满足 $ z = y(1+x) $ 的 $ (x,y) $ 对的范围。
>
> 对于随机变量 $ (X, Y) $ 的取值范围，我们可以将其分为两个区域。在区域A中，$ y $ 的取值范围是 $ (0, 1) $，而 $ x $ 的取值范围是 $ (0, z-1) $。在区域B中，$ y $ 的取值范围是 $ (0, \frac{z}{x+1}) $，而 $ x $ 的取值范围是 $ (z-1, 1) $。
>
> 接下来，我们可以分别对这两个区域进行积分。
> 首先，我们考虑区域A的积分：
> $$
> g_A(z) = \int_{0}^{z-1} \int_{0}^{1} \frac{4}{7}(1+y+xy) \, dy \, dx
> $$
> 
>
> 然后，我们考虑区域B的积分：
> $$
> g_B(z) = \int_{z-1}^{1} \int_{0}^{\frac{z}{x+1}} \frac{4}{7}(1+y+xy) \, dy \, dx
> $$
> 经过计算，我们得到区域A的积分 $ g_A(z) $ 为：
> $$
> g_A(z) = \frac{6(-1 + z)}{7} + \frac{(-1 + z)^2}{7} 
> $$
> 
>
> 区域B的积分 $ g_B(z) $ 为：
> $$
>  g_B(z) = \frac{-2z(2+z)\ln\left(\frac{z}{2}\right)}{7}
> $$
> 
>
> 因此，总的分布函数 $ g(z) $ 为：
> $$
> g(z) = \frac{-5 + 4z + z^2 - 2z(2 + z)\ln\left(\frac{z}{2}\right)}{7}
> $$
> 对其求导，便可以得到概率密度函数:
> $$
> f(z) = \frac{4(z+1)(ln(2)-ln(z))}{7}, (0<z<2)
> $$
> 

---

### 题目2

设 $ X_1, X_2 , X_3 $ 为独立同分布的随机变量, 且服从标准正态分布。令:
$$
Y=\frac{X_1+X_2 X_3}{\sqrt{1+X_3^2}}
$$
(a) 试求随机变量 $ Y $ 的分布密度函数;  
(b) 试问有限个独立正态分布随机变量经过非线性变换是否可以服从正态分布?

> **答案**：
>
> - (a):
>
> 由定义，可以得到：
> $$
> \begin{align}
> F(Y) &= P(Y\leq y)\\
> &= P(\frac{X_1+X_2 X_3}{\sqrt{1+X_3^2}}\leq y)\\
> &=\int_{-\infty}^\infty P(\frac{X_1+X_2 X_3}{\sqrt{1+X_3^2}}\leq y|X_3 )f_(x_3)dx_3\\
> \end{align}
> $$
> 在给定$X_3$的情况下，$\frac{X_1+X_2 X_3}{\sqrt{1+X_3^2}}$ 中的$X_3$可以看成一个常数，所以有：
> $$
> \frac{X_1+X_2 X_3}{\sqrt{1+X_3^2}} = \frac{1}{\sqrt{1+X_3^2}} X_1 + \frac{X_3}{\sqrt{1+X_3^2}} X_1
> $$
> 由题干，我们知道，$X_1,X_2$是独立同分布的标准正态分布，所以我们有:
> $$
> \frac{X_1+X_2 X_3}{\sqrt{1+X_3^2}} \thicksim N(0,1)
> $$
> 所以有：
> $$
> \begin{align}
> \int_{-\infty}^\infty P(\frac{X_1+X_2 X_3}{\sqrt{1+X_3^2}}\leq y|X_3 )f_(x_3)dx_3 &= \int_{-\infty}^\infty \Phi(y) f_(x_3)dx_3\\ 
> &= \Phi(y)
> \end{align}
> $$
> 所以$Y$也为标准正态分布，其概率密度函数为:
> $$
> f_Y(y) = \frac{1}{\sqrt{2}\pi}e^{-\frac{y^2}{2}}, y \in R
> $$
>
> - (b):
>
> 可以，其实这点我们从(a)不难看出可以实现， 假设有`m`个独立同分布的标准正态分布变量$X_1,X_2,X_3,...,X_n$。
>
> 那么按照(a)中的变换，令
> $$
> X_{1^\prime} = \frac{X_1+X_2 X_3}{\sqrt{1+X_3^2}}
> $$
> 则:
> $$
> X_{1^\prime} \thicksim N(0,1)
> $$
> 并且也与其他变量独立同分布。
>
> 那么上述`m`个独立同分布标准正态可以变为`m-2`个:
> $$
> X_{1^\prime},X_4,...,X_n
> $$
> 如此操作，最后可以得到2或3个变量。如果是2两个那么直接通过
> $$
> X_{1^\prime} = \frac{X_1+X_2}{\sqrt{2}}
> $$
> 变换即可，所以我们可以证明`有限个独立正态分布随机变量经过非线性变换可以服从正态分布。`
>
> Q.E.D

### 题目3

设 $ \left\{\xi_n, n \geq 1\right\} $ 为独立同分布连续型随机变量序列, 令:
$$
\tau=\min \left\{n: n \geq 2, \xi_n>\xi_1\right\}, \sigma=\min \left\{n: n>m

, \xi_n>\max _{1 \leq k \leq m}\left\{\xi_k\right\}\right\}
$$

试回答以下问题:  
(a) 求随机变量 $ \tau $ 的分布函数, 并确定随机变量 $ \tau $ 的数学期望是否存在;  
(b) 求概率 $ P\{\sigma>n\}(n \geq m+1) $。

> **答案**： 
>
> - (a):
>
>   从$\tau$的定义可以得到，$\tau=2$时，其概率为$\xi_2>\xi_1$的概率，也就是
>   $$
>   P(\tau=2) = P(\xi_2>\xi_1)
>   $$
>   
>
> 此时，我们令:
> $$
> p = P(\xi_2\leq \xi_1)
> $$
> 由于$ \left\{\xi_n, n \geq 1\right\} $独立同分布，所以:
> $$
> p = P(\xi_{n}\leq \xi_{1})
> $$
>    当$\tau=3$是，就是$\xi_2\leq \xi_1$, 并且$\xi_3$，也就是：
> $$
> P(\tau=3) = P(\xi_2\leq \xi_1) P(\xi_3>\xi_2) = (1-p)p
> $$
> 如此类推，可以得到：
> $$
> P(\tau = n) = p^{n-2}(1-p), n\geq2
> $$
> 这边是其分布函数，下面我们计算并探讨其数学期望是否存在：
>
> 由定义，我们可以得到:
> $$
> E(\tau) = \sum_{n=2}^\infty n\times p^{n-2}(1-p)
> $$
> 判断其期望是否存在，也就是判断该极限是否存在？
>
> 很显然，这是一个类似等比级数求和的数列，可以通过和差化积来求得，通过等比数列求和的性质，我们可以知道当$p<1$时，该级数和收敛，由于$p$为概率，所以$0<p<1$，所以该级数收敛
>
> ，也就是其存在期望。
>
> 现在，我们来求解该期望的值，首先，我们有：
> $$
> \begin{align}
> E(\tau) &= \sum_{n=2}^\infty n\times p^{n-2}(1-p) \\
> &= \frac{1-p}{p} \sum_{n=2}^\infty n\times p^{n-1}\\
> &=\frac{1-p}{p} (\sum_{n=2}^\infty  p^{n})^\prime  \\
> & = \frac{1-p}{p} (\frac{p^2}{1-p})^\prime\\
> &= \frac{1-p}{p} \frac{p(2-p)}{(1-p)^2}\\
> & = \frac{2-p}{1-p}
> \end{align}
> $$
> 
>
> - (b):
>
> 由$\sigma$的定义，我们可以知道，$P(\sigma=n)$为$\xi_n$ 大于前$m$个数中最大值的概率，由于$\xi_n$独立同分布，也就是每一个都有可能是最大的，所以其对应的概率都是$1-p$, 一共有$n-(m+1)+1= n-m$个，所以其概率分布函数可以表示为：
> $$
> P(\sigma > n) = (1-p)^{n-m}, n\geq1
> $$
> ​                                         

---

### 题目4

设 $ \xi_1, \xi_2, \cdots \xi_n $ 与 $ \eta $ 为随机变量, $ \eta \sim U[0,1] $, 而 $ \xi_i(i=1,2, \cdots n) $ 均以下述条件概率取 1 和 0 两个, 即: $ P\left\{\xi_i=1 \mid \eta=p\right\}=p, P\left\{\xi_i=0 \mid \eta=p\right\}=1-p $; 并且条件独立, 即对于 $ i=1,2, \cdots, n $, 均有 $ x_i=0,1 $ 时, 有
$$ P\left\{\xi_1=x_1, \cdots, \xi_n=x_n \mid \eta\right\}=P\left\{\xi_1=x_1 \mid \eta\right\} \cdots P\left\{\xi_n=x_n \mid \eta\right\} $$
试回答以下问题:
（a） 试求 $ P\left\{\xi_1=x_1, \cdots, \xi_n=x_n\right\} $;
（b） 试求随机变量 $ S_n=\xi_1+\cdots+\xi_n $ 的分布;
（c） 试求条件分布 $ P\left\{\eta \leq p \mid S_n=x\right\} $, 并求出密度函数, 其中: $ x=x_1+\cdots x_n $;
（d） 试问分布 $ P\left\{\eta \leq p \mid S_n=x_1+\cdots x_n\right\} $ 与 $ P\left\{\eta \leq p \mid \xi_1=x_1, \cdots, \xi_n=x_n\right\} $ 是否相同, 其中: $ p \in(0,1) $ 。

> **答案**：
>
> - (a):
>
> 根据全概率公式:
> $$
> \begin{align}
> P\left\{\xi_1=x_1, \cdots, \xi_n=x_n\right\} &= \int_{0}^1P\left\{\xi_1=x_1, \cdots, \xi_n=x_n\right|\eta = p\} f_{\eta}(p) dp  \\
> &= \int_0^1P\left\{\xi_1=x_1 \mid \eta\right\} \cdots P\left\{\xi_n=x_n \mid \eta\right\} \times 1 dp \\
> \end{align}
> $$
> 记$x_1,x_2,x_3,x_4....x_n$中为1的个数为$x$,那么有$x=x_1+x_2+..+x_n$, 那么其中为0的个数为$n-x$个。所以，继续写原式，化为：
> $$
> =  \int_0^1 p^{x}(1-p)^{n-x} dp \\
> = \frac{1}{(n+1)\binom{n}{k}}
> $$
>
> - (b):
>
>   ​	由定义，可以得到：
>   $$
>   \begin{align}
>   P(S_n)&= P(\xi_1+\cdots+\xi_n)\\
>   	&= \int_0^1 P(\xi_1+\cdots+\xi_n|\eta = p)f_\eta(p) dp\\
>   	\end{align}
>   $$
>   假设$\xi_1,\xi_2,...,\xi_n$中有$k$个为1，那么上式可以表示为:
>
>   
>   $$
>   \begin{align}
>   \int_0^1 \binom{n}{k} &p^k(1-p)^{n-k}\times 1 dp\\
>   &= \binom{n}{k} \int_0^1  p^k(1-p)^{n-k}\times  dp\\
>   & = \binom{n}{k}  \frac{1}{(n+1)\binom{n}{k}}\\
>   &= \frac{1}{n+1}
>   
>   \end{align}
>   $$
>
> - (c):
>
> 由贝叶斯公式，可以得到：
> $$
> \begin{align}
> f_\eta(\eta\leq p| S_n=x) &= \frac{P(S_n=x| \eta=p)\times f(\eta)}{P(S_n=x)}\\
> &= \frac{ \binom{n}{k} p^x(1-p)^{n-x}}{\frac{1}{n+1}}\\
> &=(n+1) \binom{n}{k} p^x(1-p)^{n-x}
> \end{align}
> $$
> 
>
> - (d):
>
> 同(c):
> $$
> \begin{align}
>  f_\eta\left\{\eta \leq p \mid \xi_1=x_1, \cdots, \xi_n=x_n\right\}  &= \frac{P(\xi_1=x_1, \cdots, \xi_n=x_n| \eta=p)\times f(\eta)}{P(\xi_1=x_1, \cdots, \xi_n=x_n)}\\
> &= \frac{   p^{x}(1-p)^{n-x}}{\frac{1}{(n+1)\binom{n}{k}}}\\
> &=(n+1) \binom{n}{k} p^x(1-p)^{n-x}
> \end{align}
> $$
> 由于两者的概率密度函数相同，所以两者的分布也相同。
>
> 

---
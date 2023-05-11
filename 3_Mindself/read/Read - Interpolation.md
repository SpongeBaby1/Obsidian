---
alias: Interpolation（插值）
year: 2023
sort: Finite difference method
nation: 
crew: 
rate: 
info: Chapter 5
date: 2023-04-08-Saturday 20:40:47
update: 2023-04-23-Sunday 20:05:43
tags: [read/year2023, read/month04]
id: read20230408204047
---
---

```ad-info
title: Lagrange interpolation
1. $n$次拉格朗日插值多项式:
$$ P(x) = \sum_{i=0}^{n} y_i \ell_i(x) $$
其中，$\ell_i(x)$是$n$次拉格朗日基函数，定义为：
$$ \ell_i(x) = \prod_{j=0,j\ne i}^{n} \frac{x-x_j}{x_i-x_j} $$
对于任意一个数据点 $(x_k,f(x_k))$，都有$\ell_i(x_k) = 
\begin{cases}
1, & i = k \\
0 & i \neq k  \\
\end{cases}$
且$P(x_k) = f(x_k)$

2. 拉格朗日公式还可以写成：
$$P(x)= \sum_{i=0}^n \dfrac{\omega(x)}{(x-x_i)\omega^{'}(x_i)}y_i$$
其中，$$\omega(x)=\prod_{j=0}^{n}(x-x_j)$$

3. 余项：
$$R_{n}(x)=f(x)-P(x)=\dfrac{f^{(n+1)}(\xi)}{(n+1)!}\omega(x)$$
```



```ad-info
title: Newton's divided differences interpolation polynomial
1. 共有$n+1$个插值点，则
$$
P(x)=f(x_{0}) +\sum_{i=1}^{n} \left(b_{i} n_{i}(x) \right) 
$$
其中
$$
b_i=f[x_0,x_1,\cdots,x_{i}] (i>0)
$$
$$
n_i(x)=\prod_{j=0}^{i-1}(x-x_j) \left(i>0 \right)
$$
2. 余项：
$$R_{n}(x)=f[x_0,x_1,\cdots,x_n,x]\omega(x)$$

```





# 1. Introduction
## 1.1 Polynomial Interpolation（多项式插值）

```ad-info
title: Polynomial Interpolation
多项式插值是一种通过已知数据点来构造一个多项式函数，以便在给定插值点上近似原函数的方法。具体来说，给定$n+1$个不同的数据点$(x_0, y_0), (x_1, y_1), \cdots, (x_n, y_n)$，多项式插值的目标是构造一个$n$次多项式$P(x)$，满足$P(x_i) = y_i$，$i=0,1,\cdots,n$ .
```

## 1.2 Uniqueness（唯一性）

```ad-info
title: Uniqueness
对于任意给定的$n+1$个数据点$(x_0,y_0),(x_1,y_1),\cdots,(x_n,y_n)$，存在唯一的次数不超过$n$的多项式$P(x)$，满足$P(x_i) = y_i$，$i=0,1,\cdots,n$。
```


---

# 2. Lagrange Interpolation

## 2.1 The Theory of Lagrange Interpolation （拉格朗日插值定理）

```ad-info
title: Lagrange Extrapolation
1. 多项式插值的一个经典算法是拉格朗日插值法。假设我们已知$n+1$个数据点$(x_0, y_0), (x_1, y_1), \cdots, (x_n, y_n)$，则$n$次拉格朗日插值多项式可以表示为：
$$ P(x) = \sum_{i=0}^{n} y_i \ell_i(x) $$
其中，$\ell_i(x)$是$n$次拉格朗日基函数，定义为：

$$ \ell_i(x) = \prod_{j=0,j\ne i}^{n} \frac{x-x_j}{x_i-x_j} $$
对于任意一个数据点 $(x_k,f(x_k))$，都有$\ell_i(x_k) = 
\begin{cases}
1, & i = k \\
0 & i \neq k  \\
\end{cases}$
且$P(x_k) = f(x_k)$

2. 拉格朗日公式还可以写成：
$$P(x)= \sum_{i=0}^n \dfrac{\omega(x)}{(x-x_i)\omega^{'}(x_i)}y_i$$
其中，$$\omega(x)=\prod_{j=0}^{n}(x-x_j)$$

- 证明1：

等式两边取对数得
$$\omega^{'}(x)=\omega(x)\sum_{k=0}^n\frac{1}{x-x_k}$$
则
$$\omega^{'}(x_i)=\omega(x_i)\sum_{k=0}^n\frac{1}{x_i-x_k}$$
即
$$\omega^{'}(x_i)=(x_i-x_0)(x_i-x_1)\cdots(x_i-x_i)\cdots(x_i-x_n)[\frac{1}{x_i-x_0}+\cdots+\frac{1}{x_i-x_i}+\cdots+\frac{1}{x_i-x_n}]$$
在求和项中，只有第$i$项的$\dfrac{1}{x_i-x_i}$与$w(x_i)$的乘积不为0。

故

$$
\omega^{'}(x_i)=\prod_{j=0,j\ne i}^{n} (x_i-x_j)
$$

所以
$$\frac{\omega(x)}{(x-x_i)\omega^{'}(x_i)}y_i=\prod_{j=0,j\ne i}^{n} \frac{x-x_j}{x_i-x_j}=\ell_i(x) $$

- 证明2

$$\omega(x)=(x-x_i)\prod_{j=0,j\ne i}{(x-x_j)}$$
$$\omega^{'}(x)=\prod_{j=0,j\ne i}(x-x_j)+(x-x_i)\dfrac{\mathrm{d}}{\mathrm{d}x}\left(\prod_{j=0,j\ne i}^n(x-x_j)\right)$$
$$\omega^{'}(x_i)=\prod_{j=0,j\ne i}(x_i-x_j)$$
```

---

## 2.2 Example

### 2.2.1 Linear interpolation（线性插值）

```ad-info
title: linear interpolation
过两点$(x_0,y_0)$和$(x_1,y_1)$的直线为：
$P(x)=y_0+\dfrac{y_1-y_0}{x_1-x_0}(x-x_0)$ 
即 $P(x)=\dfrac{x-x_1}{x_0-x_1}y_0+\dfrac{x-x_0}{x_1-x_0}y_1$
为了便于推广，记$l_0(x)=\dfrac{x-x_1}{x_0-x_1},l_1(x)=\dfrac{x-x_0}{x_1-x_0}$ 
则 $$P(x)=l_0(x)y_0+l_1(x)y_1$$
```

已知两点$(1,1)$和$(3,2)$，求线性插值多项式，以及$x=1.5$时的值。

$$
\ell_{0}(x) = \frac{x-3}{1-3} , 
\ell_{1}(x) =\frac{x-1}{3-1} , 
P(x) = \ell_{0}(x) * 1 + \ell_{1}(x) * 2 = 0.5x + 0.5
$$

### 2.2.2 Parabolic interpolation（抛物线插值）

```ad-info
title: Parabolic interpolation
过三点$(x_0,y_0)$，$(x_1,y_1)$和$(x_2,y_2)$的抛物线为：
$P(x)=\ell_0(x)y_0+\ell_1(x)y_1+\ell_2(x)y_2$，
由 
$\left\{
\begin{array}{l}
\ell_0(x_0)=1 \\
\ell_0(x_1)=0 \\
\ell_0(x_2)=0
\end{array}\right.$
知 $\ell_0(x)=\dfrac{(x-x_1)(x-x_2)}{(x_0-x_1)(x_0-x_2)}$
同理 $\ell_1(x)=\dfrac{(x-x_0)(x-x_2)}{(x_1-x_0)(x_1-x_2)}$，$\ell_2(x)=\dfrac{(x-x_0)(x-x_1)}{(x_2-x_0)(x_2-x_1)}$
```

已知$f(x)$ 过三点$(1,1)$, $(3,2)$, $(2,-1)$，求抛物线插值多项式，以及$x=1.5$时的值。

$$
\ell_{0}(x) = \frac{(x-3)(x-2)}{(1-3)(1-2)} , 
\ell_{1}(x) =\frac{(x-1)(x-2)}{(3-1)(3-2)} , 
\ell_{2}(x) =\frac{(x-1)(x-3)}{(2-1)(2-3)} 
$$
$$
P(x) = \ell_{0}(x) * 1 + \ell_{1}(x) * 2 + \ell_{2}(x) *(-1)= 2.5x^{2} - 9.5x+8
$$

### 2.2.3 多点插值

下面以一个简单的例子来说明多项式插值的计算过程。假设我们要通过以下四个数据点$(0, 1), (1, 2), (2, 3), (3, 5)$来构造一个三次插值多项式。首先，我们可以计算出拉格朗日基函数：

$$\ell_{0}(x) = \frac{(x-1)(x-2)(x-3)}{(0-1)(0-2)(0-3)} = -\frac{1}{6}(x-1)(x-2)(x-3)
$$

$$\ell_{1}(x) = \frac{(x-0)(x-2)(x-3)}{(1-0)(1-2)(1-3)} = \frac{1}{2}x(x-2)(x-3) 
$$

$$\ell_{2}(x) = \frac{(x-0)(x-1)(x-3)}{(2-0)(2-1)(2-3)} = -\frac{1}{2}x(x-1)(x-3)  
$$

$$\ell_{3}(x) = \frac{(x-0)(x-1)(x-2)}{(3-0)(3-1)(3-2)} = \frac{1}{6}x(x-1)(x-2)
$$

$$P(x) = \ell_{0}(x)*1 + \ell_{1}(x)*2 + \ell_{2}(x)*3 + \ell_{3}(x)*5 
$$

$$P(x) = \frac{1}{6} x^{3} - \frac{1}{2} x^{2} + \frac{4}{3} x + 1
$$

---

## 2.3 Remainder in Lagrange Interpolation Formula （插值余项）

$$R(x)=f(x)-P(x)=\dfrac{f^{n+1}(\xi)}{(n+1)!}\omega(x)$$

![[Pasted image 20230413213353.png]]

![[Pasted image 20230413213602.png]]

---

## 2.4 Iterative Interpolation

- Aitken interpolation（埃特金逐次插值法）

![[Pasted image 20230413214216.png]]

---

## 2.5 反插值
.........

---

# 3. Newton Polynomial

```ad-success
title: Advantage
拉格朗日插值中的基函数和每一个插值点有关，因此，每增加一个插值点时，所有的基函数都要重新计算，这会造成计算量的浪费。迭代插值虽具有承袭性，但其计算式为递推型的，不便进行理论分析。牛顿插值是一种具有承袭性的插值。
```

## 3.1 牛顿插值的几何解释

[知乎-牛顿插值的几何解释](https://www.zhihu.com/question/22320408/answer/141973314?utm_campaign=shareopn&utm_content=group3_Answer&utm_medium=social&utm_oi=822814266133454848&utm_psn=1628456272298143744&utm_source=wechat_session)

1. 已知$f_1(x)$过两点$(x_0,f(x_0)),(x_1,f(x_1))$，求$f_1(x)$

$$f_1(x)=f_0(x)+b_1(x)(x-x_{0)}, b_1=\frac{f(x_1)-f(x_0)}{x_1-x_0}$$


2. 已知$f_2(x)$过三点$(x_0,f(x_0)),(x_1,f(x_1)),(x_2,f(x_2))$，求$f_2(x)$

假设 $f_2(x)=f_1(x)+b_2(x-x_0)(x-x_1)$，代入点$(x_2,f(x_2))$

$$
\begin{align*} & \implies b_2=& & \frac{[\frac{f(x_2) - f(x_1)}{x_2 - x_1}] - [\frac{f(x_1) - f(x_0)}{x_1 - x_0}]}{x_2 - x_0} \\
& \implies f_2(x) = & & f(x_0)+\frac{f(x_1)-f(x_0)}{x_1-x_0}(x-x_0) \\ 
& & & +\frac{[\frac{f(x_2) - f(x_1)}{x_2 - x_1}] - [\frac{f(x_1) - f(x_0)}{x_1 - x_0}]}{x_2 - x_0}(x-x_0)(x-x_1) 
\end{align*}
$$
[[Pasted image 20230411220110.png]]

3. 假设我们定义一阶差商为：

$$f[x_0,x_1]=\frac{f(x_1)-f(x_0)}{x_1-x_0}$$

则二阶差商为：

$$
f[x_0,x_1,x_2]=\frac{f[x_1,x_2]-f[x_0,x_1]}{x_2-x_0}
$$

同样，三阶差商为：

$$
f[x_0,x_1,x_2,x_3]=\frac{f[x_1,x_2,x_3]-f[x_0,x_1,x_2]}{x_3-x_0}
$$

若$m-1$阶差商存在，则$m$阶差商为：

$$
f[x_0,x_1,\cdots,x_m]=\frac{f[x_1,x_2,\cdots,x_m]-f[x_0,x_1,\cdots,x_{m-1}]}{x_m-x_0}
$$

![[Pasted image 20230411222946.png]]


4. Newton interpolation

$$
\begin{align*} f(x)= & f(x_0)+f[x_0,x_1](x-x_0) \\ 
& +f[x_0,x_1,x_2](x-x_0)(x-x_1) + \cdots \\
& +f[x_0,x_1,\cdots,x_{n-1},x_n](x-x_0)(x-x_1)\cdots(x-x_{n-1}) \\
& +f[x_0,x_1,\cdots,x_n,x](x-x_0)(x-x_1)\cdots(x-x_{n}) \\
\end{align*}
$$

---

## 3.2 Divided difference（差商）

```ad-info
title: Divided difference
n阶差商$f[x_0,x_1,\cdots,x_n]$是函数值（零阶差商）$f(x_0)$, $f(x_1)$,$\cdots$, $f(x_n)$的线性组合，即
$$
f[x_0,x_1,\cdots,x_n]=\sum_{i=0}^{n} \frac{f(x_i)}{\omega^{'}(x_i)}
$$
其中
$$
\omega^{'}(x_i)=\prod_{j=0,j\ne i}^n(x_i-x_j)
$$
```

---

## 3.3 Newton's Divided Differences Interpolation polynomial（牛顿差商形式的插值多项式）

```ad-info
title: Newton's divided differences interpolation polynomial
共有$n+1$个插值点，则
$$
\begin{align*}
P(x) =& b_{0} & \\
&+  b_1(x-x_0) & \\
&+ b_2(x-x_0)(x-x_1)+\cdots & \\
&+ b_n(x-x_0)(x-x_1)\cdots(x-x_{n-1}) &\\ 
\end{align*}
$$
$$
P(x)=f(x_{0}) +\sum_{i=1}^{n} \left(b_{i} n_{i}(x) \right) 
$$
其中
$$
b_i=f[x_0,x_1,\cdots,x_{i}] (i>0)
$$
$$
n_i(x)=\prod_{j=0}^{i-1}(x-x_j) \left(i>0 \right)
$$

```

```ad-info
title: Remainder in Newton interpolation formula（插值余项）
$$
R_{n}(x)=f[x_0,x_1,\cdots,x_n,x]\omega(x)
$$
```

![[Pasted image 20230414221010.png]]

![[Pasted image 20230414220837.png]]

---

## 3.4 Divided Difference and derivative（差商和导数）

$$
\begin{align*}
R(x) &= f(x)-P(x) \\\\
R(x_{i}) &= f(x_{i})-P(x_{i}) (i=0,1,2,\cdots,n)
\end{align*}
$$

故$R(x)$在区间$[x_{0},x_{n}]$上有$n+1$个零点。

由罗尔定理知：$\exists\ \xi\in [x_{0},x_{n}]$，使得$R^{(n)}(\xi)=0$

又
$$
\begin{align*}
R^{(n)}(x)&=f^{(n)}(x)-P^{(n)}(x) \\\\
P^{(n)}(x)&=\left(f(x_{0}) +\sum_{i=1}^{n}\left(b_{i} n_{i}(x)\right)\right)^{(n)} \\
&= \left(\sum\limits_{i=1}^{n}(x-x_{0})(x-x_{1}) \cdots (x-x_{i-1}) f[x_{0},x_{1},\cdots,x_{i}]\right)^{(n)}\\\\
&=\left( (x-x_{0})(x-x_{1}) \cdots (x-x_{n-1}) f[x_{0},x_{1},\cdots,x_{n}] \right)^{(n)}\\\\
&=n! \cdot f[x_{0},x_{1},\cdots,x_{n}]
\end{align*}
$$
且
$$
R^{(n)}(\xi)=f^{(n)}(\xi)-P^{(n)}(\xi)=0
$$
所以
$$
f[x_{0},x_{1},\cdots,x_{n}]=\frac{f^{(n)}(\xi)}{n!}\ (\xi\in [x_{0},x_{n}])
$$

---

# Appendix

1. [数学符号和公式的英文标准读法](https://blog.csdn.net/wanjiac/article/details/108654201)
2. 

---

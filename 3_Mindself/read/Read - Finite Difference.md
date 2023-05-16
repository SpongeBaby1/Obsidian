---
alias: 有限差分
year: 2023
sort: numeric
nation: Chinese
crew: Sponge
rate: 1st
info: Chapter 5
date: 2023-04-17-Monday 17:11:20
update: 2023-05-16-Tuesday 16:03:35
tags: [read/year2023, read/month04]
id: read20230417171120
---
---

```ad-summary
1. 

2. Finite Difference Formulas with equidistant points
	
	- forawrd difference
	
		difference: 
		
		$\Delta^{(n)}y_{i} = \Delta^{(n-1)}y_{i+1} - \Delta^{(n-1)}y_{i}$

		$\Delta^{(n)} y_{k} = \sum\limits_{i=0}^{n} (-1)^{i} \cdot C_{n}^{i} \cdot y_{k+n-i}$
		
		difference and divided difference: $\Delta^{(n)}y_{i} = n! h^{n} f[x_{0},x_{1},x_{2},\cdots,x_{n}]$
		
		divided difference and derivative: $f[x_{0},x_{1},\cdots,x_{n}] = \dfrac{f^{(n)}(\xi)}{n!}\ (\xi\in [x_{0},x_{n}])$
		
		difference and derivative: $\Delta^{(n)} y_{0} = n! \cdot h^{n} f^{(n)}(\xi)\cdot h^{n} (\xi\in [x_{0},x_{n}])$
	
	- backward difference
	
		difference: 
		
		$\nabla^{(n)}y_{i} = \nabla^{(n-1)}y_{i} - \nabla^{(n-1)}y_{i-1}$
		
		$\nabla^{(n)} y_{k} = \sum\limits_{i=0}^{n} (-1)^{i} \cdot C_{n}^{i} \cdot y_{k-i}$
		
		difference and divided difference: $\nabla^{(n)}y_{i} = n! h^{n} f[x_{0},x_{1},x_{2},\cdots,x_{n}]$
		
		divided difference and derivative: $f[x_{0},x_{1},\cdots,x_{n}] = \dfrac{f^{(n)}(\xi)}{n!}\ (\xi\in [x_{0},x_{n}])$
		
		difference and derivative: $\nabla^{(n)} y_{0} = n! \cdot h^{n} f^{(n)}(\xi)\cdot h^{n} (\xi\in [x_{0},x_{n}])$
	
	- central difference
	
		difference: 
		
		$\delta^{(n)}y_{i} = \delta^{(n-1)}y_{i+\frac{1}{2}} - \delta^{(n-1)}y_{i-\frac{1}{2}}$

		$\delta^{(n)} y_{k} = \sum\limits_{i=0}^{n} (-1)^{i} \cdot C_{n}^{i} \cdot y_{k+\frac{n}{2}-i}$
		
		difference and divided difference: $\delta^{(n)}y_{i} = n! h^{n} f[x_{0},x_{1},x_{2},\cdots,x_{n}]$
		
		divided difference and derivative: $f[x_{0},x_{1},\cdots,x_{n}] = \dfrac{f^{(n)}(\xi)}{n!}\ (\xi\in [x_{0},x_{n}])$
		
		difference and derivative: $\delta^{(n)} y_{0} = n! \cdot h^{n} f^{(n)}(\xi)\cdot h^{n} (\xi\in [x_{0},x_{n}])$

3. 

```


# 1 Definition

```ad-info
title: Finite Difference
A **finite difference** is a mathematical expression of the form ${\displaystyle{f(x+b) − f(x+a)}}$. If a finite difference is divided by ${\displaystyle{b-a}}$, one gets a **difference quotient**.
```

```ad-info
title: Finite Difference Method
In numerical analysis, **finite-difference methods (FDM)** are a class of numerical techniques for solving differential equations by approximating derivatives with finite differences.

**Details**: 将求解区域划分为若干个离散的网格点，然后在每个网格点上用差分公式逼近微分方程中的微分（偏微分）项，得到包含若干离散点函数值的代数方程组，最后再通过数值算法求解代数方程组，得到离散点上的函数值，从而求解原微分方程。
```

```ad-caution
title: Notion
有限差分法对网格的划分和差分格式的选择较为敏感，需要根据具体问题进行合理的选择，以保证数值解的精度和稳定性。
```


# 2 Basic Types and Higher-order Differences

## 2.1 Basic Types
1. Forward difference :
   ${\displaystyle{\Delta_{h} f(x) = f(x+h) - f(x)}}$
   
2. Backward difference :
    ${\displaystyle{\nabla_{h} f(x) = f(x) - f(x-h)}}$
    
3. Central difference :
    ${\displaystyle{\delta_{h} f(x) = f(x+h/2) - f(x-h/2)}}$
    
---

## 2.2 Second-order Differences
1. Second-order forward :
   ${\displaystyle{\Delta_{h}^{2} f(x) = f(x+2h)-2f(x+h)+f(x)}}$

2. Second-order backward :
   ${\displaystyle{\nabla_{h}^{2} f(x) = f(x)-2f(x-h)+f(x-2h)}}$

3. Second-order central :
   ${\displaystyle{\delta_{h}^{2} f(x) = f(x+h)-2f(x)+f(x-h)}}$
---

## 2.3 Nth Order Differences
1. Forward :
   ${\displaystyle{\Delta_{h}^{n} y_{k} = \sum\limits_{i=0}^{n} (-1)^{i} \cdot C_{n}^{i} \cdot y_{k+n-i} \quad (y_{k}=y(x_{k}))}}$
   推导 :$$
\begin{align*}
\Delta y_{k} & =  y_{k+1} - y_{k} = (-1)^{0} \cdot C_{1}^{0} \cdot y_{k+1} + (-1)^{1} \cdot C_{1}^{1} \cdot y_{k} \\\\
\Delta^{2} y_{k} & = y_{k+2} - 2y_{k+1} + y_{k} = (-1)^{0} \cdot C_{2}^{0} \cdot y_{k+2} + (-1)^{1} \cdot C_{2}^{1} \cdot y_{k+1} + (-1)^{2} \cdot C_{2}^{2} \cdot y_{k} \\\\
\Delta^{3} y_{k} & = y_{k+3} - 3y_{k+2} + 3y_{k+1} -y_{k} \\\\ & = (-1)^{0} \cdot C_{3}^{0} \cdot y_{k+3} + (-1)^{1} \cdot C_{3}^{1} \cdot y_{k+2} + (-1)^{2} \cdot C_{3}^{2} \cdot y_{k+1} + (-1)^{3} \cdot C_{3}^{3} \cdot y_{k} \\\\
\Delta^{n} y_{k} & =  (-1)^{0} \cdot C_{n}^{0} \cdot y_{k+n} + (-1)^{1} \cdot C_{n}^{1} \cdot y_{k+n-1} + (-1)^{2} \cdot C_{n}^{2} \cdot y_{k+n-2} + \cdots + (-1)^{n} \cdot C_{n}^{n} \cdot y_{k} \\\\
& = \sum\limits_{i=0}^{n} (-1)^{i} \cdot C_{n}^{i} \cdot y_{k+n-i}\\\\
\Delta^{n}y_{k} &=\Delta^{(n-1)}y_{k+1}-\Delta^{(n-1)}y_{k}
\end{align*}
$$

2. Backward :
   ${\displaystyle{\nabla_{h}^{n} y_{k} = \sum\limits_{i=0}^{n} (-1)^{i} \cdot C_{n}^{i} \cdot y_{k-i}\quad (y_{k}=y(x_{k}))}}$
   推导 :$$
\begin{align*}
\nabla y_{k} & =  y_{k} - y_{k-1} = (-1)^{0} \cdot C_{1}^{0} \cdot y_{k} + (-1)^{1} \cdot C_{1}^{1} \cdot y_{k-1} \\\\
\nabla^{2} y_{k} & = y_{k} - 2y_{k-1} + y_{k-2} = (-1)^{0} \cdot C_{2}^{0} \cdot y_{k} + (-1)^{1} \cdot C_{2}^{1} \cdot y_{k-1} + (-1)^{2} \cdot C_{2}^{2} \cdot y_{k-2} \\\\
\nabla^{3} y_{k} & = y_{k} - 3y_{k-1} + 3y_{k-2} -y_{k-3} \\\\ & = (-1)^{0} \cdot C_{3}^{0} \cdot y_{k} + (-1)^{1} \cdot C_{3}^{1} \cdot y_{k-1} + (-1)^{2} \cdot C_{3}^{2} \cdot y_{k-2} + (-1)^{3} \cdot C_{3}^{3} \cdot y_{k-3} \\\\
\nabla^{n} y_{k} & =  (-1)^{0} \cdot C_{n}^{0} \cdot y_{k} + (-1)^{1} \cdot C_{n}^{1} \cdot y_{k-1} + (-1)^{2} \cdot C_{n}^{2} \cdot y_{k-2} + \cdots + (-1)^{n} \cdot C_{n}^{n} \cdot y_{k-n} \\\\
& = \sum\limits_{i=0}^{n} (-1)^{i} \cdot C_{n}^{i} \cdot y_{k-i}\\\\
\nabla^{n}y_{k} &=\Delta^{(n-1)}y_{k}-\Delta^{(n-1)}y_{k-1}
\end{align*}
$$

3. Central :
   ${\displaystyle{\delta_{h}^{n} y_{k} = \sum\limits_{i=0}^{n} (-1)^{i} \cdot C_{n}^{i} \cdot y_{k+\frac{n}{2}-i} \quad (y_{k}=y(x_{k}))}}$
   推导 :$$
\begin{align*}
\delta y_{k} & =  y_{k+\frac{1}{2}} - y_{k-\frac{1}{2}} = (-1)^{0} \cdot C_{1}^{0} \cdot y_{k+\frac{1}{2}} + (-1)^{1} \cdot C_{1}^{1} \cdot y_{k-\frac{1}{2}} \\\\
\delta^{2} y_{k} & = y_{k+1} - 2y_{k} + y_{k-1}= (-1)^{0} \cdot C_{2}^{0} \cdot y_{k+1} + (-1)^{1} \cdot C_{2}^{1} \cdot y_{k} + (-1)^{2} \cdot C_{2}^{2} \cdot y_{k-1} \\\\
\delta^{3} y_{k} & = y_{k+\frac{3}{2}} - 3y_{k+\frac{1}{2}} + 3y_{k-\frac{1}{2}} - y_{k-\frac{3}{2}} \\\\
& = (-1)^{0} \cdot C_{3}^{0} \cdot y_{k+\frac{3}{2}} + (-1)^{1} \cdot C_{3}^{1} \cdot y_{k+\frac{1}{2}} + (-1)^{2} \cdot C_{3}^{2} \cdot y_{k-\frac{1}{2}} + (-1)^{3} \cdot C_{3}^{3} \cdot y_{k-\frac{3}{2}} \\\\
\delta^{n} y_{k} & =  (-1)^{0} \cdot C_{n}^{0} \cdot y_{k+\frac{n}{2}} + (-1)^{1} \cdot C_{n}^{1} \cdot y_{k+\frac{n}{2}-1} + (-1)^{2} \cdot C_{n}^{2} \cdot y_{k+\frac{n}{2}-2} + \cdots + (-1)^{n} \cdot C_{n}^{n} \cdot y_{k+\frac{n}{2}-n} \\\\
& = \sum\limits_{i=0}^{n} (-1)^{i} \cdot C_{n}^{i} \cdot y_{k+\frac{n}{2}-i}\\\\
\delta^{(n)}y_{k} &=\delta^{(n-1)}y_{k+\frac{1}{2}}-\delta^{(n-1)}y_{k-\frac{1}{2}}
\end{align*}
$$
---


# 3 Relation with Derivatives







对函数${\displaystyle{f(x)}}$进行三阶泰勒展开知 :

${\displaystyle{f(x+h) = f(x) + hf^{\prime}(x) + \frac{h^{2}}{2!}f^{\prime\prime}(x) + \frac{h^{3}}{3!}f^{\prime\prime\prime}(x) + \frac{h^{4}}{4!}f^{(4)}(x+\xi_{1})\quad (\xi_{1} \in (0, h))}}$
${\displaystyle{\implies f^{\prime}(x)=\frac{f(x+h)-f(x)}{h} + O(h)}}$ 

${\displaystyle{f(x-h) = f(x) - hf^{\prime}(x) + \frac{h^{2}}{2!}f^{\prime\prime}(x) - \frac{h^{3}}{3!}f^{\prime\prime\prime}(x) + \frac{h^{4}}{4!}f^{(4)}(x+\xi_{2})\quad (\xi_{2} \in (0, h))}}$

${\displaystyle{\implies f^{\prime}(x)=\frac{f(x)-f(x-h)}{h}+ O(h)}}$

将两次泰勒展开式相减得: ${\displaystyle{f^{\prime}(x)=\frac{f(x+h)-f(x-h)}{2h} + O(h^{2})}}$

---


# 4 Relation with Divided Difference



---


# 2 Examples
## 2.1
```ad-example
方程组$\begin{cases} u'(x) + u(x) = \sin(x) + \cos(x), \quad x \in [0, 2 \pi]; \\ u(x=0) = 0 \end{cases}$，求解微分方程
```

1. 设$\begin{cases} h=\dfrac{2 \pi}{N}\\ x_{i}=i\cdot \dfrac{2 \pi}{N}\\ u_{i}=u(x_{i}) \\ \end{cases}\quad$ 则$u'(x_{i})=\dfrac{u_{i+1}-u_{i}}{h}$

2. 将其代入方程组得：
$C_{i}u_{i}+u_{i+1}=F_{i}$，其中$\begin{cases}C_{i}=h-1 \\ F_{i}=\sin(x_{i}) + \cos(x_{i}) \end{cases}$

3. 写成矩阵并化简得：
$$\left( \begin{matrix} 1 & & & & & \\ C_{1} & 1 & & & & \\ & C_{2} & 1 & & & \\ & & \ddots & \ddots & & \\ & & & C_{N-2} & 1 & \\ & & & & C_{N-1} & 1 \end{matrix} \right) \left( \begin{matrix} u_{1} \\ u_{2} \\ u_{3} \\ \vdots \\ u_{N-1} \\ u_{N} \end{matrix} \right) = \left( \begin{matrix} F_{0} \\ F_{1} \\ F_{2} \\ \vdots \\ F_{N-2} \\ F_{N-1} \end{matrix} \right) $$

$$\implies \left( \begin{matrix} u_{1} \\ u_{2} \\ u_{3} \\ \vdots \\ u_{N-1} \\ u_{N} \end{matrix} \right) = \left( \begin{matrix} 1 & & & & & \\ C_{1} & 1 & & & & \\ & C_{2} & 1 & & & \\ & & \ddots & \ddots & & \\ & & & C_{N-2} & 1 & \\ & & & & C_{N-1} & 1 \end{matrix} \right)^{-1} \left( \begin{matrix} F_{0} \\ F_{1} \\ F_{2} \\ \vdots \\ F_{N-2} \\ F_{N-1} \end{matrix} \right) $$

4. Python Code

	```python
	from numpy import *
	
	h = 2*pi/N
	x = linspace(0, 2*pi, N+1)  %(0, 2*pi）含有$N+1$个等距离的点%
	A = zeros((N, N))
	F = zeros((N, 1))
	u = zeros((N+1, 1))
	for i in range(N):
	    A[i, i] = 1
	    if i > 0: A[i, i-1] = h-1 
	    F[i] = h*(sin(x[i]) + cos(x[i]))
	u[1:] = dot(linalg.inv(A), F)  求逆矩阵$A^{-1}$
	```

## 2.3 Appendix

- [微分方程数值求解——有限差分法 - 知乎](https://zhuanlan.zhihu.com/p/411798670)
- [[有限差分法工作原理.pdf]]

---


# 2 Forward difference（向前差分）

Finite Difference Formula at Equally Spaced points（等距节点的差分公式）


2. 后向差分：
The approximation of the partial derivative is represented as:

${\displaystyle{f'(x) \approx \frac{f(x) - f(x-h)}{h}}}$

3. 中心差分：
The approximation of the partial derivative is represented as:

${\displaystyle{f'(x) \approx \frac{f(x+h) - f(x-h)}{2h}}}$

4. 二阶中心差分：
The approximation of the second partial derivative is represented as:

${\displaystyle{f''(x) \approx \frac{f(x+h) - 2f(x) + f(x-h)}{h^2}}}$

### 2.1.1 Forward Difference of N Degree formula（n阶向前差分公式）

$$
\begin{align*}
\Delta y_{k} & =  y_{k+1} - y_{k} = (-1)^{0} \cdot C_{1}^{0} \cdot y_{k+1} + (-1)^{1} \cdot C_{1}^{1} \cdot y_{k} \\\\
\Delta^{2} y_{k} & = y_{k+2} - 2y_{k+1} + y_{k} = (-1)^{0} \cdot C_{2}^{0} \cdot y_{k+2} + (-1)^{1} \cdot C_{2}^{1} \cdot y_{k+1} + (-1)^{2} \cdot C_{2}^{2} \cdot y_{k} \\\\
\Delta^{3} y_{k} & = y_{k+3} - 3y_{k+2} + 3y_{k+1} -y_{k} \\\\ & = (-1)^{0} \cdot C_{3}^{0} \cdot y_{k+3} + (-1)^{1} \cdot C_{3}^{1} \cdot y_{k+2} + (-1)^{2} \cdot C_{3}^{2} \cdot y_{k+1} + (-1)^{3} \cdot C_{3}^{3} \cdot y_{k} \\\\
\Delta^{n} y_{k} & =  (-1)^{0} \cdot C_{n}^{0} \cdot y_{k+n} + (-1)^{1} \cdot C_{n}^{1} \cdot y_{k+n-1} + (-1)^{2} \cdot C_{n}^{2} \cdot y_{k+n-2} + \cdots + (-1)^{n} \cdot C_{n}^{n} \cdot y_{k} \\\\
& = \sum\limits_{i=0}^{n} (-1)^{i} \cdot C_{n}^{i} \cdot y_{k+n-i}\\\\
\Delta^{n}y_{k} &=\Delta^{(n-1)}y_{k+1}-\Delta^{(n-1)}y_{k}
\end{align*}
$$


### 2.1.2 Examples（例题）

![[Pasted image 20230417194355.png]]

### 2.1.3 Difference and Divided difference（差分与差商）

$$
\begin{align*}
& f[x_{0},x_{1}] =& \frac{\Delta y_{0}}{1!h} &\\\\
& f[x_{0},x_{1},x_{2}] =& \frac{\Delta^{2} y_{0}}{2!h^{2}} & \\\\
& f[x_{0},x_{1},x_{2},x_{3}] =& \frac{\Delta^{3} y_{0}}{3!h^{3}} & \\\\
& f[x_{0},x_{1},x_{2},\cdots,x_{n}] =& \frac{\Delta^{n} y_{0}}{n! \cdot h^{n}} \\\\
\end{align*}
$$

### 2.1.4 Divided Difference and derivative（差商与导数）

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
- 源自[[Read - Interpolation]]

### 2.1.5 Difference and derivative（差分与导数）

$$
\begin{align*}
\Delta^{n} y_{0} &= n! \cdot h^{n} f[x_{0},x_{1},x_{2},\cdots,x_{n}]\\\\
&=n!\cdot h^{n}\cdot\frac{f^{(n)}(\xi)}{n!}\\\\
&=f^{(n)}(\xi)\cdot h^{n}\ (\xi\in [x_{0},x_{n}])
\end{align*}
$$


---

## 2.2 Backward difference（向后差分）

### 2.2.1 Backward Difference of N Degree formula（n阶向后差分公式）

$$
\begin{align*}
\nabla y_{k} & =  y_{k} - y_{k-1} = (-1)^{0} \cdot C_{1}^{0} \cdot y_{k} + (-1)^{1} \cdot C_{1}^{1} \cdot y_{k-1} \\\\
\nabla^{2} y_{k} & = y_{k} - 2y_{k-1} + y_{k-2} = (-1)^{0} \cdot C_{2}^{0} \cdot y_{k} + (-1)^{1} \cdot C_{2}^{1} \cdot y_{k-1} + (-1)^{2} \cdot C_{2}^{2} \cdot y_{k-2} \\\\
\nabla^{3} y_{k} & = y_{k} - 3y_{k-1} + 3y_{k-2} -y_{k-3} \\\\ & = (-1)^{0} \cdot C_{3}^{0} \cdot y_{k} + (-1)^{1} \cdot C_{3}^{1} \cdot y_{k-1} + (-1)^{2} \cdot C_{3}^{2} \cdot y_{k-2} + (-1)^{3} \cdot C_{3}^{3} \cdot y_{k-3} \\\\
\nabla^{n} y_{k} & =  (-1)^{0} \cdot C_{n}^{0} \cdot y_{k} + (-1)^{1} \cdot C_{n}^{1} \cdot y_{k-1} + (-1)^{2} \cdot C_{n}^{2} \cdot y_{k-2} + \cdots + (-1)^{n} \cdot C_{n}^{n} \cdot y_{k-n} \\\\
& = \sum\limits_{i=0}^{n} (-1)^{i} \cdot C_{n}^{i} \cdot y_{k-i}\\\\
\nabla^{n}y_{k} &=\Delta^{(n-1)}y_{k}-\Delta^{(n-1)}y_{k-1}
\end{align*}
$$

### 2.2.2 Difference and Divided difference（差分与差商）

$$
\begin{align*}
& f[x_{0},x_{1}] =& \frac{\nabla y_{0}}{1!h} &\\\\
& f[x_{0},x_{1},x_{2}] =& \frac{\nabla^{2} y_{0}}{2!h^{2}} & \\\\
& f[x_{0},x_{1},x_{2},x_{3}] =& \frac{\nabla^{3} y_{0}}{3!h^{3}} & \\\\
& f[x_{0},x_{1},x_{2},\cdots,x_{n}] =& \frac{\nabla^{n} y_{0}}{n! \cdot h^{n}} \\\\
\end{align*}
$$


### 2.2.3 Difference and derivative（差分与导数）

$$
\begin{align*}
\nabla^{n} y_{0} &= n! \cdot h^{n} f[x_{0},x_{1},x_{2},\cdots,x_{n}]\\\\
&=n!\cdot h^{n}\cdot\frac{f^{(n)}(\xi)}{n!}\\\\
&=f^{(n)}(\xi)\cdot h^{n}\ (\xi\in [x_{0},x_{n}])
\end{align*}
$$


---

## 2.3 Central difference（中心差分）

### 2.3.1 Central Difference of N Degree formula（n阶中心差分公式）

$$
\begin{align*}
\delta y_{k} & =  y_{k+\frac{1}{2}} - y_{k-\frac{1}{2}} = (-1)^{0} \cdot C_{1}^{0} \cdot y_{k+\frac{1}{2}} + (-1)^{1} \cdot C_{1}^{1} \cdot y_{k-\frac{1}{2}} \\\\
\delta^{2} y_{k} & = y_{k+1} - 2y_{k} + y_{k-1}= (-1)^{0} \cdot C_{2}^{0} \cdot y_{k+1} + (-1)^{1} \cdot C_{2}^{1} \cdot y_{k} + (-1)^{2} \cdot C_{2}^{2} \cdot y_{k-1} \\\\
\delta^{3} y_{k} & = y_{k+\frac{3}{2}} - 3y_{k+\frac{1}{2}} + 3y_{k-\frac{1}{2}} - y_{k-\frac{3}{2}} \\\\
& = (-1)^{0} \cdot C_{3}^{0} \cdot y_{k+\frac{3}{2}} + (-1)^{1} \cdot C_{3}^{1} \cdot y_{k+\frac{1}{2}} + (-1)^{2} \cdot C_{3}^{2} \cdot y_{k-\frac{1}{2}} + (-1)^{3} \cdot C_{3}^{3} \cdot y_{k-\frac{3}{2}} \\\\
\delta^{n} y_{k} & =  (-1)^{0} \cdot C_{n}^{0} \cdot y_{k+\frac{n}{2}} + (-1)^{1} \cdot C_{n}^{1} \cdot y_{k+\frac{n}{2}-1} + (-1)^{2} \cdot C_{n}^{2} \cdot y_{k+\frac{n}{2}-2} + \cdots + (-1)^{n} \cdot C_{n}^{n} \cdot y_{k+\frac{n}{2}-n} \\\\
& = \sum\limits_{i=0}^{n} (-1)^{i} \cdot C_{n}^{i} \cdot y_{k+\frac{n}{2}-i}\\\\
\delta^{(n)}y_{k} &=\delta^{(n-1)}y_{k+\frac{1}{2}}-\delta^{(n-1)}y_{k-\frac{1}{2}}
\end{align*}
$$

### 2.3.2 Difference and Divided difference（差分与差商）

$$
\begin{align*}
& f[x_{0},x_{1}] =& \frac{\delta y_{0}}{1!h} &\\\\
& f[x_{0},x_{1},x_{2}] =& \frac{\delta^{2} y_{0}}{2!h^{2}} & \\\\
& f[x_{0},x_{1},x_{2},x_{3}] =& \frac{\delta^{3} y_{0}}{3!h^{3}} & \\\\
& f[x_{0},x_{1},x_{2},\cdots,x_{n}] =& \frac{\delta^{n} y_{0}}{n! \cdot h^{n}} \\\\
\end{align*}
$$


### 2.3.3 Difference and derivative（差分与导数）

$$
\begin{align*}
\delta^{(n)} y_{0} &= n! \cdot h^{n} f[x_{0},x_{1},x_{2},\cdots,x_{n}]\\\\
&=n!\cdot h^{n}\cdot\frac{f^{(n)}(\xi)}{n!}\\\\
&=f^{(n)}(\xi)\cdot h^{n}\ (\xi\in [x_{0},x_{n}])
\end{align*}
$$



---
# 3. Newton Polynomial at Equally Spaced points（等距节点的牛顿插值公式）

```ad-info
title: Newton polynomial
$$P(x)=y_{0}+\sum\limits_{i=1}^{n}f[x_{0},x_{1},\cdots,x_{i}] \prod\limits_{j=0}^{i-1}(x-x_{j})$$

$$
P(x)=P(x_{0}+th)
$$
```
---

## 3.1 牛顿向前插值多项式

1. 差商公式：$f[x_{0},x_{1},\cdots,x_{i}]=\dfrac{\Delta^{(i)}y_{0}}{i! \cdot h^{i}}$
2. 代入牛顿插值公式得：
$P(x)=y_{0}+\sum\limits_{i=1}^{n}C_{t}^{i}\Delta^{(i)}y_{0}$
3. 向前差分：$\Delta^{n}y_{i}=\Delta^{(n-1)}y_{i+1}-\Delta^{(n-1)}y_{i}$
4. 例题：![[Pasted image 20230420161109.png]]

	- 将$(x_{C},\Gamma_{C})$，$(x_{E},\Gamma_{E})$分别计为$(x_{0},y_{0})$，$(x_{1},y_{1})$，步长$h=\delta x_{e}$，求$(x_{\frac{1}{2}},y_{\frac{1}{2}})$，即$(x_{e},\Gamma_{e})$。
	
		$P(x)=y_{0}+t\Delta y_{0}= y_{0}+t(y_{1} - y_{0})$
		
		所以，$y_{\frac{1}{2}}=P(\frac{1}{2})=y_{0}+\frac{1}{2}\Delta y_{0}= y_{0}+\frac{1}{2}(y_{1} - y_{0})=\frac{1}{2}(y_{0} + y_{1})$
	
		$\implies \Gamma_{e}=y_{\frac{1}{2}}=\frac{1}{2}(\Gamma_{C}+\Gamma_{E})$

## 3.2 牛顿向后插值多项式

1. 差商公式：$f[x_{0},x_{1},\cdots,x_{i}]=\dfrac{\nabla^{(i)}y_{0}}{i! \cdot h^{i}}$
2. 代入牛顿插值公式得：
$P(x)=y_{0}+\sum\limits_{i=1}^{n}C_{t}^{i}\nabla^{(i)}y_{0}$
3. 向后差分：$\nabla^{n}y_{i}=\nabla^{(n-1)}y_{i}-\nabla^{(n-1)}y_{i-1}$
4. 例题：![[Pasted image 20230420161109.png]]

	- 将$(x_{C},\Gamma_{C})$，$(x_{E},\Gamma_{E})$分别计为$(x_{-1},y_{-1})$，$(x_{0},y_{0})$，步长$h=\delta x_{e}$，求$(x_{-\frac{1}{2}},y_{-\frac{1}{2}})$，即$(x_{e},\Gamma_{e})$。
	
		$P(x)=y_{0}+t\nabla y_{0}= y_{0}+t(y_{0} - y_{-1})$
		
		所以，$y_{-\frac{1}{2}}=P(-\frac{1}{2})=y_{0}-\frac{1}{2}\nabla y_{0}= y_{0}-\frac{1}{2}(y_{0} - y_{-1})=\frac{1}{2}(y_{-1} + y_{0})$
	
		$\implies \Gamma_{e}=y_{-\frac{1}{2}}=\frac{1}{2}(\Gamma_{C}+\Gamma_{E})$

---

## 3.3 牛顿中心插值多项式

1. 差商公式：$f[x_{0},x_{1},\cdots,x_{i}]=\dfrac{\delta^{(i)}y_{0}}{i! \cdot h^{i}}$
2. 代入牛顿插值公式得：
$P(x)=y_{0}+\sum\limits_{i=1}^{n}C_{t}^{i}\delta^{(i)}y_{0}$
3. 中心差分：$\delta^{n}y_{i}=\delta^{(n-1)}y_{i+\frac{1}{2}}-\delta^{(n-1)}y_{i-\frac{1}{2}}$
4. 例题：![[Pasted image 20230420161109.png]]

	- 将$(x_{C},\Gamma_{C})$，$(x_{E},\Gamma_{E})$分别计为$(x_{-\frac{1}{2}},y_{-\frac{1}{2}})$，$(x_{\frac{1}{2}},y_{\frac{1}{2}})$，步长$h=\delta x_{e}$，求$(x_{0},y_{0})$，即$(x_{e},\Gamma_{e})$。
	
		$P(x)=y_{0}+t\delta y_{0}= y_{0}+t(y_{\frac{1}{2}} - y_{-\frac{1}{2}})$
		
		所以，$y_{-\frac{1}{2}}=P(-\frac{1}{2})=y_{0}-\frac{1}{2}\delta y_{0}= y_{0}-\frac{1}{2}(y_{\frac{1}{2}} - y_{-\frac{1}{2}})$
	
		$\implies \Gamma_{C}=y_{-\frac{1}{2}}=y_{0}-\frac{1}{2}(y_{\frac{1}{2}} - y_{-\frac{1}{2}})=\Gamma_{e}-\frac{1}{2}(\Gamma_{E}-\Gamma_{C})$
		
		$\implies \Gamma_{e}=\frac{1}{2}(\Gamma_{C}+\Gamma_{E})$

---
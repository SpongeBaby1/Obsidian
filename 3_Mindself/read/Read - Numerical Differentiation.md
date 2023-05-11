---
alias: 数值微分
year: 2023
sort: numeric
nation: 
crew: 
rate: 
info: Chapter 6
date: 2023-04-21-Friday 14:23:40
update: 2023-04-21-Friday 22:19:30
tags: [read/year2023, read/month04]
id: read20230421142340
---
---

```ad-note
title: Numerical Differentiation
In [numerical analysis](https://en.wikipedia.org/wiki/Numerical_analysis "Numerical analysis"), **numerical differentiation** [algorithms](https://en.wikipedia.org/wiki/Algorithm "Algorithm") estimate the [derivative](https://en.wikipedia.org/wiki/Derivative "Derivative") of a [mathematical function](https://en.wikipedia.org/wiki/Mathematical_function "Mathematical function") or function [subroutine](https://en.wikipedia.org/wiki/Subroutine "Subroutine") using values of the function and perhaps other knowledge about the function.
```



# 1. Approximating the Derivative Using Newton's Difference quotient（差商型求导）


1. 由导数定义知
$f^{\prime}(x)=\lim\limits_{h \rightarrow 0} \dfrac{f(x+h)-f(x)}{h}$

2. 泰勒展开式
$f(x \pm h) = f(x) \pm h f^{\prime}(x) + \dfrac{h^{2}}{2!}f^{\prime \prime}(x) \pm \dfrac{h^{3}}{3!}f^{\prime \prime \prime}(x) + \cdots + \dfrac{(\pm h)^{n}}{n!}f^{(n)}(\xi)$

3. Forward difference quotient

	$f^{\prime}(x) \approx \dfrac{f(x+h)-f(x)}{h}$
	
	$R(x) = f^{\prime}(x)-\dfrac{f(x+h)-f(x)}{h}=-\dfrac{f^{\prime \prime}\left(x+\theta_{1} h\right)}{2} h=O(h)$


4. Backward difference quotient

	$f^{\prime}(x) \approx \dfrac{f(x)-f(x-h)}{h}$
	
	$R(x) = f^{\prime}(x)-\dfrac{f(x)-f(x-h)}{h}=\dfrac{f^{\prime \prime}\left(x-\theta_{2} h\right)}{2} h=O(h)$


5. Central difference quotient

	$f^{\prime}(x) \approx \dfrac{f(x+h)-f(x-h)}{2h}$

	$\begin{align*}R(x) &= f^{\prime}(x) - \dfrac{f(x+h)-f(x-h)}{2h} \\ \\ &=-\dfrac{h^{2}}{12} \left(f^{(3)} \left(x+\theta_{1} h\right) + f^{(3)} \left(x-\theta_{2} h\right) \right) \\ \\ &= O(h^{2}) \end{align*}$

一般的，对称的中心差商与中点处的斜率更接近，精度更高。在实际使用中，估计插值区间端点处导数值时多使用端点形式，其他时候更多使用中点形式。


---


# 2. Differentiation（插值型求导）

```ad-info
title: Differentiation

```
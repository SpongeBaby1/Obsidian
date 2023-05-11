---
alias: 数值积分
year: 2023
sort: numeric
nation: 
crew: 
rate: 
info: Chapter 6
date: 2023-04-21-Friday 18:47:10
update: 2023-04-28-Friday 22:12:50
tags: [read/year2023, read/month04]
id: read20230421184710
---
---

# Summary
1. **科特斯系数表：**
![[Pasted image 20230425205434.png]]

2. **科特斯系数具有的性质：**
	- 科特斯系数$C_{k}$之和为1。
	- 科特斯系数$C_{k}$具有对称性，$C_{k}=C_{n-k}$。
	- 科特斯系数$C_{k}$有时为负。

3. **等距节点的插值求积法则：区间$[a,b]$不大时，共有$n+1$个插值点，$n$阶插值函数。**

	| 区间    | $n+1$个插值点 | 相邻插值点之间的长度               | 阶数  | 等距节点的插值求积法则 |                                       公式实现                                       | 代数精度 |                             余项                             | 收敛性               |
	| ------- |:-------------:| ---------------------------------- | ----- | ---------------------- |:------------------------------------------------------------------------------------:| -------- |:------------------------------------------------------------:| -------------------- |
	| $[a,b]$ |       2       | ${\displaystyle{h=b-a}}$           | 一阶  | Trapezoidal rule       |                 ${\displaystyle{\frac{h}{2}\left[f(a)+f(b)\right]}}$                 | 1        | ${\displaystyle{- \frac{1}{12}h^{3}f^{\prime\prime}(\eta)}}$ | $A_{k}\gt 0$ 收敛    |
	| $[a,b]$ |       3       | ${\displaystyle{h=\frac{b-a}{2}}}$ | 二阶  | Simpson's rule         |        ${\displaystyle{\frac{h}{3}\left[f(a)+4f(\frac{a+b}{2})+f(b)\right]}}$        | 3        |     ${\displaystyle{- \frac{1}{90}h^{5}f^{(4)}(\eta)}}$      | $A_{k}\gt 0$ 收敛    |
	| $[a,b]$ |       5       | ${\displaystyle{h=\frac{b-a}{4}}}$ | 四阶  | Cotes rule             | ${\displaystyle{\frac{h}{90}\left[7f(a)+32f(a+h)+12f(a+2h)+32f(a+3h)+7f(b)\right]}}$ | 5        |     ${\displaystyle{- \frac{8}{945}h^{7}f^{(6)}(\eta)}}$     | $A_{k}\gt 0$ 收敛    |
	| $[a,b]$ |     $n+1$     | ${\displaystyle{h=\frac{b-a}{n}}}$ | $n$阶 | Newton-Cotes formulas  |             ${\displaystyle{(b-a)\sum\limits _{k=0}^{n} C_{k}f(x_{k})}}$             | $\ge n$  |                           $\cdots$                           | $A_{k} \&0$ 未必收敛 |


4. **低阶等距节点的复合插值求积法则：区间$[a,b]$较大时，将区间$[a,b]$进行$n^{\prime}$等分，每个区间的长度为$h^{\prime}$，此时，每个区间上共有$n+1$个插值点，其中部分节点会重复，相邻插值点之间的长度为$h^{\prime\prime}$。**

	| 区间    | $n^{\prime}$等分后每个区间的长度$h^{\prime}$         | 每个区间内相邻插值点之间的长度$h^{\prime\prime}$         | 阶数$n$ | **等距节点复合插值求解法则**   | 第$k$个区间$[x_{k},x_{k+1}]$ | 复合求积公式              | 代数精度 | 余项 | 收敛性 |
	| ------- | ---------------------------------------------------- | -------------------------------------------------------- | ------- | -------------------------- | ---------------------------- | ------------------------- | -------- | ---- | ------ |
	| $[a,b]$ | ${\displaystyle{h^{\prime}=\frac{b-a}{n^{\prime}}}}$ | ${\displaystyle{h^{\prime\prime}=h^{\prime}}}$ | 1       | Composite trapezoidal rule |    ${\displaystyle{t_{k}=\frac{h^{\prime\prime}}{2}\left[f(x_{k}+f(x_{k+1})\right]}}$                          | ${\displaystyle{T_{n^{\prime}}=\frac{h^{\prime\prime}}{2}\left[f(a)+2\sum\limits_{k=1}^{n^{\prime}-1}f(x_{k})+f(b)\right]}}$ |      1    |   ${\displaystyle{R_{T}=-\frac{n^{\prime}}{12} {h^{\prime\prime}}^{3} f^{\prime\prime}(\eta)=-\frac{b-a}{12} {h^{\prime}}^{2} f^{\prime\prime}(\eta) \quad a\leq \eta \leq b}}$   |  $A_{k}\gt 0$ 收敛   |
	| $[a,b]$ | ${\displaystyle{h^{\prime}=\frac{b-a}{n^{\prime}}}}$ | ${\displaystyle{h^{\prime\prime}=\frac{h^{\prime}}{2}}}$ | 2       | Composite Simpson's rule |    ${\displaystyle{s_{k}=\frac{h^{\prime\prime}}{3}\left[f(x_{k})+4f(x_{k+\frac{1}{2}})+f(x_{k+1})\right]}}$                          | ${\displaystyle{S_{n^{\prime}}=\frac{h^{\prime\prime}}{3}\left(f(a)-f(b)+\sum\limits_{k=1}^{n^{\prime}}\left[4f(x_{k-\frac{1}{2}})+2f(x_{k})\right]\right)}}$ |      3    |   ${\displaystyle{R_{S}=-\frac{n^{\prime}}{90} {h^{\prime\prime}}^{5} f^{(4)}(\eta)=-\frac{b-a}{2880} {h^{\prime}}^{4} f^{(4)}(\eta) \quad a\leq \eta \leq b}}$   |  $A_{k}\gt 0$ 收敛       |
	| $[a,b]$ | ${\displaystyle{h^{\prime}=\frac{b-a}{n^{\prime}}}}$ | ${\displaystyle{h^{\prime\prime}=\frac{h^{\prime}}{4}}}$ | 4       | Composite Cotes rule |    ${\displaystyle{c_{k}=\frac{h^{\prime\prime}}{90}\left[7f(x_{k})+32f(x_{k+\frac{1}{4}})+12f(x_{k+\frac{1}{2}})+32f(x_{k+\frac{3}{4}})+7f(x_{k+1})\right]}}$                          | ${\displaystyle{C_{n^{\prime}}=\frac{h^{\prime\prime}}{90} \left[7f(a) + 32\sum\limits _{k=0}^{n^{\prime}-1} f(x_{k+\frac{1}{4}}) + 12\sum\limits _{k=0}^{n^{\prime}-1} f(x_{k+\frac{1}{2}}) +32\sum\limits _{k=0}^{n^{\prime}-1} f(x_{k+\frac{3}{4}})+14\sum\limits _{k=1}^{n^{\prime}-1} f(x_{k})+ 7f(b)\right]}}$ |      5    |   ${\displaystyle{R_{C}=-\frac{8n^{\prime}}{945} {h^{\prime\prime}}^{7} f^{(6)}(\eta)=-\frac{2(b-a)}{945} (\frac{h^{\prime}}{4})^{6} f^{(6)}(\eta) \quad a\leq \eta \leq b}}$   |   $A_{k}\gt 0$ 收敛      |

---

# 1. Introduction

```ad-info
title: **Numerical Integration（数值积分）：**
将积分区间划分成若干个小区间，在每个小区间上，用简单函数**（本章主要使用代数插值多项式）**去代替复杂函数进行积分。

即：
${\displaystyle \int _{a}^{b}f(x)\,dx \approx \sum\limits_{k=0}^{n-1} \int _{x_{k}}^{x_{k+1}}P(x)dx}$
```

```ad-info
title: **Numerical Quadrature Rule（数值求积公式）：**
取积分区间若干个点$x_{k}$处的函数值$f(x_{k})$，进行加权求和。

即：${\displaystyle \int _{a}^{b}f(x)\,dx \approx \sum\limits_{k=0}^{n} A_{k}f(x_{k})}$

其中，$x_{k}$是求积节点，$A_{k}$是求积系数，也称作伴随节点$x_{k}$的权。
```

---

# 2. Quadrature Rules Based on Interpolating Functions（等距节点插值求积公式）

```ad-info
title: Quadrature Rules Based on Interpolating Functions（插值求积公式）：
使用代数插值多项式近似被积函数，用插值多项式的积分近似被积函数的积分。

即：

${\displaystyle {\begin{aligned} \int _{a}^{b} f(x)dx &\approx \int _{a}^{b}L(x)dx \\ &= \int _{a}^{b} \left(\sum\limits_{k=0}^{n} f(x_{k}) \ell_{k}(x) \right) dx \\ &= \sum\limits_{k=0}^{n} \left(f(x_{k}) \int _{a}^{b} \ell_{k}(x) dx \right) =\sum\limits_{k=0}^{n} f(x_{k}) A_{k} \\ &\implies A_{k}= \int _{a}^{b} \ell_{k}(x) dx \end{aligned}}}$

```

---

## 2.1 Trapezoidal rule（梯形公式）

- **Trapezoidal rule（梯形公式）**是一种低阶的数值积分方法。以过两点的直线代替曲线进行积分，从而得到所求积分的近似值。**具有一次代数精度**。

	${\displaystyle \int _{a}^{b}f(x)\,dx\approx (b-a)\left({\frac {f(a)+f(b)}{2}}\right).}$

---

## 2.2 Simpson's rule（辛普森公式）:
- **Simpson's rule（辛普森公式）**是一种数值积分方法，用于计算二次可积函数的定积分，**具有三次代数精度**。

	令$k=2$得：
	
	${\displaystyle{\begin{aligned} A_{0} =& \int _{a}^{b} \frac{(x-x_{1})(x-x_{2})}{(x_{0}-x_{1})(x_{0}-x_{2})} =& \frac{h}{2} \int _{0}^{2} (t-1)(t-2) dt &=\frac{b-a}{6} \\ A_{1} =& \int _{a}^{b} \frac{(x-x_{0})(x-x_{2})}{(x_{1}-x_{0})(x_{1}-x_{2})} =& -\frac{h}{2} \int _{0}^{2} t(t-2) dt =& \frac{4(b-a)}{6} \\ A_{2} =& \int _{a}^{b} \frac{(x-x_{0})(x-x_{1})}{(x_{2}-x_{0})(x_{2}-x_{1})} =& \frac{h}{2} \int _{0}^{2} t(t-1) dt =& \frac{b-a}{6} \end{aligned}}}$
	
	其中，${\displaystyle{x=x_{0}+ th, h=\frac{b-a}{2}}}$。
	
	因此，我们可以得到**辛普森公式**：
	
	${\displaystyle {\begin{aligned}\int _{a}^{b} f(x)dx &\approx \frac{h}{3}\left[f(a) + 4f\left(\frac{a+b}{2}\right)+ f(b)\right] \\\\ &= \frac{b-a}{6}\left[f(a) + 4f\left(\frac{a+b}{2}\right)+ f(b)\right].\end{aligned}}}$

---

## 2.3 Newton-cotes formulas（牛顿-柯特斯公式）


在求积公式中，${\displaystyle{A_{k}= \int _{a}^{b} \ell_{k}(x) dx= \int _{a}^{b} \prod\limits _{\substack{i=0 \\\\ i\ne k}}^{n} \frac{x-x_{j}}{x_{k}-x_{j}} dx}}$。

取系数${\displaystyle{C_{k}=\frac{A_{k}}{b-a}}}$，且插值节点等距时，将系数${\displaystyle{C_{k}}}$称作**柯特斯系数**。

**牛顿-科特斯公式：**
${\displaystyle {\int _{a}^{b}f(x)\,dx \approx (b-a) \sum\limits_{k=0}^{n} C_{k} f(x_{k})}}$

**柯特斯系数的计算：**
${\displaystyle{C_{k}= \frac{1}{b-a} \int _{a}^{b} \prod\limits _{\substack{i=0 \\\\ i\ne k}}^{n} \frac{x-x_{i}}{x_{k}-x_{i}} dx}}$


- **将积分区间${\displaystyle{[a,b]}}$进行$n$等分**，每一份的长度${\displaystyle{h=\frac{b-a}{n}}}$，等分点${\displaystyle{x_{k}=a+kh}}$ ，${\displaystyle{k=0,1,2,\cdots,n}}$，作变换${\displaystyle{x=a+th}}$，${\displaystyle{x_{i}=a+ih}}$，则：

	${\displaystyle{\begin{aligned}C_{k} &= \frac{1}{n \cdot h} \int _{0}^{n} \prod\limits  _{\substack{i=0 \\\\ i\ne k}}^{n} \frac{t-i}{k-i} \cdot h \cdot dt \\ &= \frac{1}{n} \int _{0}^{n} \prod\limits _{\substack{i=0 \\\\ i\ne k}}^{n} \frac{t-i}{k-i} \cdot dt \\\\ &= \frac{(-1)^{n-k}}{n\cdot k!\cdot (n-k)!} \int _{0}^{n} \prod\limits  _{\substack{i=0 \\\\ i\ne k}}^{n} (t-i)\,dt \\\\ &= \frac{(-1)^{n-k}}{n\cdot k!\cdot (n-k)!} \int _{0}^{n} \prod\limits _{i=0}^{n} \frac{t-i}{t-k}\,dt \quad k=0,1,2,\cdots,n \end{aligned}}}$

- 当$n=1$时：

	${\displaystyle{\begin{aligned}C_{0} &= \frac{(-1)^{1-0}}{1\cdot 0!\cdot 0!} \int _{0}^{1} \prod\limits _{i=0}^{1} \frac{t-i}{t}\,dt = -1 \int _{0}^{1} (t-1)\,dt = \frac{1}{2} \end{aligned}}}$
	
	由对称性知：${\displaystyle{C_{1}=\frac{1}{2}}}$，此时可以得到**梯形公式**。

- 当$n=2$时：

	${\displaystyle{\begin{aligned}C_{0} &= \frac{(-1)^{2-0}}{2!\cdot 0!\cdot 2!} \int _{0}^{2} \prod\limits _{i=0}^{2} \frac{t-i}{t}\,dt = \frac{1}{4} \int _{0}^{2} (t-1)(t-2)\,dt = \frac{1}{6}\\\\ C_{1} &= \frac{(-1)^{2-1}}{2\cdot 1!\cdot 1!} \int _{0}^{2} \prod\limits _{i=0}^{2} \frac{t-i}{t-1}\,dt = -1 \int _{0}^{1} (t-1)\,dt = \frac{2}{3} \end{aligned}}}$
	
	由对称性知：${\displaystyle{C_{2}=\frac{1}{6}}}$，此时可以得到**辛普森公式**。

- 以此类推，可以得到表6.2：
![[Pasted image 20230425205434.png]]


- 四阶($n=4$)牛顿-科特斯公式称作**科特斯公式**，即：
${\displaystyle {\int _{a}^{b} f(x)dx \approx \frac{b-a}{90}\left[7f(x_{0}) + 32f(x_{1} + 12f(x_{2}) + 32f(x_{3}) + 7f(x_{4})\right]}}$

- **在实际运用中，一阶（梯形），二阶（辛普森）和四阶（科特斯）牛顿-科特斯公式使用的比较多。**

- 科特斯系数具有的性质：
	1. 科特斯系数$C_{k}$之和为1。
	2. 科特斯系数$C_{k}$具有对称性，$C_{k}=C_{n-k}$。
	3.  科特斯系数$C_{k}$有时为负。



---

## 2.4 低阶求积公式的代数精度

- **代数精确度：**
求积公式${\displaystyle \int _{a}^{b}f(x)\,dx \approx \sum\limits_{k=0}^{n} A_{k}f(x_{k})}$具有$m$次代数精确度时，该公式对于 ${\displaystyle{f(x)=1,x,x^{2},\cdots,x^{m}}}$均准确成立，而对于${\displaystyle{f(x)=x^{m+1}}}$不能准确成立。代数精确度常简称为**代数精度**。

- **$n$阶牛顿-科特斯公式**至少具有**$n$次代数精度**。
- **当$n$为偶数时，牛顿-科特斯公式具有$n+1$次代数精度。**如**辛普森公式**具有**三次**代数精度，**科特斯公式**具有**$5$次**代数精度。

---

## 2.5 低阶求积公式的余项

```ad-info
title: Trapezoidal rule remainder（梯形公式余项）
设$f(x)$在$[a,b]$上有连续的二阶导数，则Trapezoidal rule（梯形公式）的余项为：
$$
R_{T}= -\frac{h^{3}}{12}f^{\prime\prime}(\eta)=-\frac{(b-a)^{3}}{12}f^{\prime\prime}(\eta) \quad a\leq \eta \leq b
$$

```


```ad-info
title: Simpson's rule remainder（辛普森公式余项）
设$f(x)$在$[a,b]$上有连续的四阶导数，则Simpson's rule（辛普森公式）的余项为：

$$
R_{S} = -{\frac {1}{90}}h^{5}f^{(4)}(\eta) = -\frac{(b-a)^{5}}{2880}f^{(4)}(\eta) \quad a\leq \eta \leq b
$$
```


```ad-info
title: Cotes rule remainder（辛普森公式余项）
设$f(x)$在$[a,b]$上有连续的六阶导数，则Cotes rule（科特斯公式）的余项为：

$$
R_{C}=-\frac{8}{945}h^{7}f^{(6)}(\eta)=-\frac{8}{945}\left(\frac{b-a}{4}\right)^{7}f^{(6)}(\eta) \quad a\leq \eta \leq b
$$
```

---


# 3. Composite quadrature（复合求积）

**梯形公式，辛普森公式和科特斯公式在区间$[a,b]$较大时，由余项公式可知其精度会显著下降。**并且高阶牛顿-科特斯公式也有其局限性。首先，他要求被积函数存在高阶导数，函数充分光滑；其次，科特斯系数有正有负，估计余项也有困难；最后，初始数据的误差会引起结果误差的扩大，造成求积公式不稳定。由此引入**复合求积法**。

- **将区间$[a,b]$进行$n$等分**，每个小区间的长度为：**${\displaystyle{h=\frac{b-a}{n}}}$**，：分点为：**${\displaystyle{x_{k}=a+kh \quad k=0,1,2,\cdots,n}}$**，其中$x_{0}=a\quad x_{n}=b$。
- **复合求积法**是利用定积分的区间累加性，将被积函数在区间$[a,b]$上的定积分划分为其在$n$个小区间上的定积分，再通过求积公式计算出其在$n$个小区间上定积分的近似值，得到被积函数在整个区间$[a,b]$上的定积分。

## 3.1 Composite Trapezoidal rule（复合梯形公式）

- 在子区间$[x_{k},x_{k+1}]$上使用梯形公式则有** Composite Trapezoidal rule（复合梯形公式）**：

	${\displaystyle{\begin{aligned}\int _{a}^{b}f(x)\,dx =  \sum\limits _{k=0}^{n-1} \int _{x_{k}}^{x_{k+1}} f(x)\,dx &\approx \sum\limits _{k=0}^{n-1} h \left({\frac {f(x_{k})+f(x_{k+1})}{2}}\right) \\ &= \frac{h}{2} \sum\limits _{k=0}^{n-1} [f(x_{k})+f(x_{k+1})] \\ &= \frac{h}{2} \left[f(a) + 2\sum\limits _{k=1}^{n-1}f(x_{k}) + f(b) \right] .\end{aligned}}}$

- **复合梯形公式余项**：

	${\displaystyle{R_{T}=-\frac{n}{12} {h}^{3} f^{\prime\prime}(\eta)=-\frac{b-a}{12} h^{2} f^{\prime\prime}(\eta) \quad a\leq \eta \leq b}}$

---

## 3.2 Composite Simpson's rule（复合辛普森公式）

- 在子区间$[x_{2k-2},x_{2k}]$上使用辛普森公式则有** Composite Simpson's rule（复合辛普森公式）**：

	${\displaystyle{\begin{aligned}\int _{a}^{b}f(x)\,dx &= \sum\limits _{k=1}^{n/2} \int _{x_{2k-2}}^{x_{2k}} f(x)\,dx \\ &\approx \sum\limits _{k=1}^{n/2} \frac{2h}{6} \left[f(x_{2k-2})+ 4f(x_{2k-1}) + f(x_{2k}) \right] \\ &= \frac{h}{3} \left[f(a) + 4\sum\limits _{k=1}^{n/2} f(x_{2k-1}) + 2\sum\limits _{k=1}^{n/2-1} f(x_{2k}) + f(b)\right]\quad (n=2i,i=1,2,\cdots).\end{aligned}}}$
	
	为了方便编程，可以将其改写为：${\displaystyle{\begin{aligned}S_{n} = \frac{h}{3} \left(f(a) - f(b) + \sum\limits _{k=1}^{n/2} \left[4f(x_{2k-1})+2f(x_{2k})\right]\right)\quad (n=2i,i=1,2,\cdots).\end{aligned}}}$

- **复合辛普森公式余项**：

	${\displaystyle{\begin{aligned}R_{S}=-\frac{n/2}{2880} (2h)^{5} f^{(4)}(\eta) &= -\frac{b-a}{180} h^{4} f^{(4)}(\eta) \quad (a\leq \eta \leq b \quad n=2i,i=1,2,\cdots).\end{aligned}}}$
	


---

## 3.3 Composite Cotes rule（复合科特斯公式）

- 在子区间$[x_{4k-4},x_{4k}]$上使用科特斯公式则有** Composite Cotes rule（复合科特斯公式）**：

	${\displaystyle{\begin{aligned}\int _{a}^{b}f(x)\,dx &= \sum\limits _{k=1}^{n/4} \int _{x_{4k-4}}^{x_{4k}} f(x)\,dx \\ &\approx \sum\limits _{k=1}^{n/4} \frac{4h}{90} \left[7f(x_{4k-4}) + 32f(x_{4k-3}) + 12f(x_{4k-2}) + 32f(x_{4k-1})+ 7f(x_{4k})\right] \\ &= \frac{2h}{45} \left[7f(a) + 32\sum\limits _{k=1}^{n/4} f(x_{4k-3}) + 12\sum\limits _{k=1}^{n/4} f(x_{4k-2}) +32\sum\limits _{k=1}^{n/4} f(x_{4k-1})+14\sum\limits _{k=1}^{n/4} f(x_{k})- 7f(b)\right]\quad( n=4i,i=1,2,\cdots).\end{aligned}}}$


- **复合科特斯公式余项**：

	${\displaystyle{\begin{aligned}R_{C}=-\frac{8\cdot n/4}{945} (4h)^{7} f^{(6)}(\eta) &= -\frac{8(b-a)}{945} \left(4h\right)^{6} f^{(6)}(\eta) \quad(a\leq \eta \leq b \quad n=4i,i=1,2,\cdots).\end{aligned}}}$

| 区间    | $n$等分后每个区间的长度$h$         | 求积法则对应的区间长度         | 阶数 | **等距节点复合插值求解法则**   | 第$k$个区间 | 复合求积公式              | 代数精度 | 余项 | 收敛性 |
| ------- | ---------------------------------------------------- | -------------------------------------------------------- | ------- | -------------------------- | ---------------------------- | ------------------------- | -------- | ---- | ------ |
| $[a,b]$ | ${\displaystyle{h=\frac{b-a}{n}}}$ | ${\displaystyle{1h}}$ | 1       | Composite trapezoidal rule |    ${\displaystyle{t_{k}= \frac{h}{2} \left[f(x_{k}) + f(x_{k+1}) \right]\quad[x_{k},x_{k+1}]}}$                          | ${\displaystyle{T_{n}= \frac{h}{2} \left[f(a) + 2\sum\limits _{k=1}^{n-1}f(x_{k}) + f(b) \right]}}$ |      1    |   ${\displaystyle{R_{T}=-\frac{n}{12} {h}^{3} f^{\prime\prime}(\eta)=-\frac{b-a}{12} h^{2} f^{\prime\prime}(\eta) \quad a\leq \eta \leq b}}$   |    $A_{k}\gt 0$ 收敛    |
| $[a,b]$ | ${\displaystyle{h=\frac{b-a}{n}}}$ | ${\displaystyle{2h}}$ | 2       | Composite Simpson's rule |    ${\displaystyle{s_{k}=\frac{2h}{6}\left[f(x_{2k-2})+4f(x_{2k-1})+f(x_{2k})\right]\quad[x_{2k-2},x_{2k}]}}$                          | ${\displaystyle{S_{n/2}=\frac{h}{3} \left[f(a) + 4\sum\limits _{k=1}^{n/2} f(x_{2k-1}) + 2\sum\limits _{k=1}^{n/2-1} f(x_{2k}) + f(b)\right] \quad (n=2i,i=1,2,\cdots)}}$ |      3    |   ${\displaystyle{R_{S}=-\frac{n/2}{2880} (2h)^{5} f^{(4)}(\eta)=-\frac{b-a}{180} h^{4} f^{(4)}(\eta) \quad a\leq \eta \leq b}}$   |  $A_{k}\gt 0$ 收敛      |
| $[a,b]$ | ${\displaystyle{h=\frac{b-a}{n}}}$ | ${\displaystyle{4h}}$ | 4       | Composite Cotes rule |    ${\displaystyle{c_{k}=\frac{4h}{90}\left[7f(x_{4k-4})+32f(x_{4k-3})+12f(x_{4k-2})+32f(x_{4k-1})+7f(x_{4k})\right]\quad[x_{4k-4},x_{4k}]}}$                          | ${\displaystyle{C_{n/4}=\frac{2h}{45} \left[7f(a) + 32\sum\limits _{k=1}^{n/4} f(x_{4k-3}) + 12\sum\limits _{k=1}^{n/4} f(x_{4k-2}) +32\sum\limits _{k=1}^{n/4} f(x_{4k-1})+14\sum\limits _{k=1}^{n/4} f(x_{4k})- 7f(b)\right]\quad (n=4i,i=1,2,\cdots)}}$ |      5    |   ${\displaystyle{R_{C}=-\frac{8\cdot n/4 }{945} (4h)^{7} f^{(6)}(\eta)=-\frac{8(b-a)}{945} (4h)^{6} f^{(6)}(\eta) \quad a\leq \eta \leq b}}$   |   $A_{k}\gt 0$ 收敛     |

---

# 4. Practice（练习题）

```ad-example
对于函数${\displaystyle{f(x)=\frac{\sin x}{x}}}$，给出$n=8$时的复合梯形公式和复合辛普森公式，计算积分：$$I=\int _{0}^{1}\frac{\sin x}{x}\,dx$$并估计误差。
```

解：

|  ${\displaystyle{x_{i}}}$   | 0   | ${\displaystyle{\frac{1}{16}}}$ | ${\displaystyle{\frac{1}{8}}}$ | ${\displaystyle{\frac{3}{16}}}$ | ${\displaystyle{\frac{2}{8}}}$ | ${\displaystyle{\frac{5}{16}}}$ | ${\displaystyle{\frac{3}{8}}}$ | ${\displaystyle{\frac{7}{16}}}$ | ${\displaystyle{\frac{4}{8}}}$ | ${\displaystyle{\frac{9}{16}}}$ | ${\displaystyle{\frac{5}{8}}}$ | ${\displaystyle{\frac{11}{16}}}$ | ${\displaystyle{\frac{6}{8}}}$ | ${\displaystyle{\frac{13}{16}}}$ | ${\displaystyle{\frac{7}{8}}}$ | ${\displaystyle{\frac{15}{16}}}$ | 1     |
|:---------------------------:| --- | ------------------------------- | ------------------------------ | ------------------------------- | ------------------------------ | ------------------------------- | ------------------------------ | ------------------------------- | ------------------------------ | ------------------------------- | ------------------------------ | -------------------------------- | ------------------------------ | -------------------------------- | ------------------------------ |:--------------------------------:| ----- |
| ${\displaystyle{f(x_{i})}}$ | 1   | 0.999                           | 0.997                          | 0.994                           | 0.990                          | 0.984                           | 0.977                          | 0.968                           | 0.959                          | 0.948                           | 0.936                          | 0.923                            | 0.909                          | 0.894                            | 0.877                          |              0.860               | 0.841 |


```ad-warning
${\displaystyle{\begin{aligned}I=S_{8}&=\frac{1}{3}\cdot \frac{1}{8}\cdot \frac{1}{2}\left(1-0.841+\sum\limits_{k=1}^{8}\left[4f(x_{k-\frac{1}{2}})+2f(x_{k})\right]\right)\\ &=\frac{1}{48}(0.1585 + 4\cdot 7.5702 + 2\cdot 7.486)\\ &=0.94608 \end{aligned}}}$
```

```ad-success
将区间$[a,b]$进行4等分，在每个区间上使用**辛普森公式**，可得：
${\displaystyle{\begin{aligned}I=S_{n/2}&=\frac{1}{3}\cdot \frac{1}{8}\left(1-0.841+\sum\limits_{k=1}^{4}\left[4f(x_{2k-1})+2f(x_{2k})\right]\right)\\ &=\frac{1}{24}(0.1585 + 15.14989 + 7.39758)\\ &=0.94608 \end{aligned}}}$

${\displaystyle{\begin{aligned}R_{S}=-\frac{b-a}{180}h^{4}f^{\prime\prime}(\eta)\le -\frac{1}{180}(\frac{1}{8})^{4}\frac{1}{5}=0.271\cdot 10^{-6} \end{aligned}}}$
```




---

# 5. （外推原理和龙贝格算法）







---


# 6. Gaussian quadrature（高斯求积）








---

# Appendix

- [数值计算方法 第六章 数值积分和数值微分 - 知乎](https://zhuanlan.zhihu.com/p/142583935)
- [数值积分与数值微分 - 华东师范大学](https://math.ecnu.edu.cn/~sfzhu/course/NumerAnal/NumerInt2.pdf)
- [https://quyanyun.xmu.edu.cn/pdf/cm04.pdf](https://quyanyun.xmu.edu.cn/pdf/cm04.pdf)
- [Simpson's Rule](https://courses.lumenlearning.com/calculus2/chapter/simpsons-rule/)

---
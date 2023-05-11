---
alias: SIMPLE algorithm（压力耦合方程组的半隐式方法）
year: 2023
sort: Numerical method
nation: 
crew: 
rate: 
info: SIMPLE
date: 2023-04-16-Sunday 20:27:49
update: 2023-04-16-Sunday 20:49:41
tags: [read/year2023, read/month04]
id: read20230416202749
---
---



SIMPLE algorithm 求解Navier-Stokes方程的基本流程如下：

1.  确定计算区域的网格划分，建立数值模型，并设置边界条件和初值条件。
    
2.  对于每个时间步，先通过速度场方程求解出速度场，然后再通过压力场方程求解出压力场，并更新速度场和压力场的值。
    
3.  对于速度场方程，可以采用以下的物理方程和数学方程：
    
    物理方程： $$ \rho\frac{\partial u}{\partial t}+\rho u\cdot\nabla u=-\nabla p+\mu\nabla^2u $$
    
    数学方程： $$ \frac{u^{n+1}-u^*}{\Delta t}+u\cdot\nabla u^{n+1}=-\frac{1}{\rho}\nabla(p^{n+1}-p^*)+\nu\nabla^2u^{n+1} $$ 其中，$u^{n+1}$表示时间步$n+1$时刻的速度场，$u^*$表示时间步$n$时刻的速度场，$p^{n+1}$表示时间步$n+1$时刻的压力场，$p^*$表示时间步$n$时刻的压力场，$\rho$表示流体密度，$\mu$表示流体粘度，$\nu=\frac{\mu}{\rho}$表示运动粘度，$\Delta t$表示时间步长。
    
4.  对于压力场方程，可以采用以下的物理方程和数学方程：
    
    物理方程： $$ \nabla\cdot u^{n+1}=0 $$
    
    数学方程： $$ \nabla\cdot u^{n+1}=0 $$
    
5.  对于压力场的修正，可以采用以下的物理方程和数学方程：
    
    物理方程： $$\nabla\cdot u^*=0 $$

	 数学方程： $$ \nabla\cdot u^*=\nabla\cdot u^{n+1} $$

6.  对于速度场的修正，可以采用以下的物理方程和数学方程：
    
    物理方程： $$ \frac{\partial u^{n+1}}{\partial t}+\frac{1}{\rho}\nabla(p^{n+1}-p^*)=\nu\nabla^2u^{n+1} $$
    
    数学方程： $$ \frac{u^{n+1}-u^*}{\Delta t}=-\frac{1}{\rho}\nabla(p^{n+1}-p^*) $$
    
7.  重复步骤2~6，直到速度场和压力场收敛。
    

需要注意的是，以上方程中的数学符号和物理符号可能存在差异，具体实现时需根据实际情况进行调整。在实际求解中，还需要注意一些问题，如时间步长的选择、数值格式的选取、边界条件的处理等。

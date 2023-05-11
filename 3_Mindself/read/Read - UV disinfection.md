---
alias: 紫外消毒
year: 20230113
sort: CFD
nation: 
crew: 
rate: 
info: 
date: 2023-01-14-Saturday 19:01:42
update: 2023-02-10-Friday 21:53:25
tags: [read/year2023, read/month01]
id: read20230114190142
---
---




## 1.1 First order kinetic for MS2
**$$LogI=kD$$**
where $k$ is the first order inactivation constant for challenge microorganisms.
and **$$LogI=log{\frac{N_{0}}{N}}$$**
so, **$$ N=N_{0}10^{-kD}$$**
or, **$$N=N_{0}e^{-ln10 kD}$$**
which is **$$N=N_{0} e^{-k_{m}D }$$**
where $k_{m}$ is the first-order inactivation rate constant for modeling microorganisms.

![[Pasted image 20230113223650.png]]

**Reference:** [[UV Reactor Performance Modeling by Eulerian and Lagrangian Methods.pdf]]

---

## 1.2 First order kinetic for challenge microorganisms

**$$LogI=k\left(D-D_{0}\right)$$**
where $k$ is the first order inactivation constant for challenge microorganisms, and $D_{0}$ is the intercept of the UV dose-response curve on the X axis.

and **$$LogI=log{\frac{N_{0}}{N}}$$**
so **$$N=N_{0}10^{-k\left(D-D_{0}\right)}$$**
or **$$N=N_{0}e^{-ln10\cdot k\left(D-D_{0}\right)}$$**
therefore, the average concentration of microorganisms at the effluent is **$$\overline{N}=\frac{1}{n_{p}}\Sigma^{i=n_{p}}_{i=1} N_{0} 10^{-k \left(D_{i}-D_{0}\right)}$$**
we can obtain **$$LogI= -log \left(\frac{1}{n_{p}} \Sigma^{n_{p}}_{i=1} 10^{-k \left(D_{i}-D_{0}\right)} \right)$$**
so, RED can be represented as follows **$$RED=-\frac{1}{k} log \left(\frac{1}{n_{p}} \Sigma^{n_{p}}_{i=1} 10^{-k \left(D_{i}-D_{0}\right)} \right) + D_{0}$$**


![[Pasted image 20230113235648.png]]

**Reference:** [[Configuration optimization of UV reactors for water disinfection with2.pdf]]

---

## 1.3 UV disinfection efficacy correlated to the  probability density function $f(D)$

The average concentration of microorganisms at the effluent can be writtern as follows 

**$$\overline{N}=\int f(D) N_{0} 10^{-k \left(D-D_{0} \right)} dD$$**
or
**$$\overline{N}=\int f(D) N_{0} e^{-k_{m} \left(D-D_{0} \right)} dD$$**
and the logrithmic inactivation can be calculated as follows
**$$LogI= -log \left(\int f(D)e^{-k_{m}\left( D-D_{0} \right)} dD \right)$$**
so, RED can be represented as follows
**$$RED= -\frac{1}{k} log \left(\int f(D)e^{-k_{m}\left( D-D_{0} \right)} dD \right) + D_{0}$$**

![[Pasted image 20230114005118.png]]

**Reference:** [[A systematic approach for the design of UV reactors using computational fluid.pdf]]

---

## 1.4 Advection-diffusion-reaction equation

The UV disinfection process convection, diffusion, and reaction.

![[Pasted image 20230114111655.png]]


### 1.4.1 Advection and convection
Advection is the transport of a substance or quantity by bulk motion of a fluid.



---

### 1.4.2 Diffusion

**Molecular diffusion $D_{m}$ :** 

**Viscosity :** the viscosity of a fluid is a measure of its resistance to deformation at a given rate.

**Dynamic viscosity $\mu$ :** 
$$[\mu]= \frac{Nm^{-2}\cdot m}{ms^{-1}}=Nm^{-2}\cdot s=Pa \cdot s$$
**Kinematic viscosity $\nu$ :** 
$$[\nu]= \frac{[\mu]}{[\rho]}=\frac{Nm^{-2}\cdot s}{kg \cdot m^{-3}}=m\cdot s^{-2}\cdot m\cdot s=m^{2}\cdot s^{-1} $$
**Code：**
![[Pasted image 20230115123815.png]]

---


### 1.4.3 Reaction
#### 1.4.3.1 Incident radiation(fluence rate)



#### 1.4.3.2 Source/sink term

The inactivation kinetic for chemical disinfectants is most commonly described by the first-order disinfection model of Chick and Waston and the same model can be applied for UV disinfection. Based on the first-order model, the linear relationship between log inactivation and the UV dose or fluence is described as: 
**$$log{\frac{N}{N_{0}}}=-k \cdot fluence=-k \cdot D$$**

The concentration of microorganisms can be writtern

****$$N=N_{0}e^{-ln10\cdot k\cdot D} $$**
Thus
**$$\frac{dN}{dt}=-k_{m} G N$$**

So, the sink term can be denoted as follows

![[Pasted image 20230130163534.png]]

By utilizing the subtantive derivative, we can obtain
**$$\frac{dN}{dt}=\frac{\partial N}{\partial t}+U_{j} \frac{\partial N}{\partial x_{j}}$$**




[[Developments in computational fluid dynamics-based modeling for disinfection3.pdf]]

**代码：**![[Pasted image 20230114200633.png]]

---




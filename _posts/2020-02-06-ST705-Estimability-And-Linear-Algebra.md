---
layout: post
comments: false
title: Example Problems on Linear Algebra and Estimability
description: ST705 Homework 5 on Linear Algebra and Estimability
tags: ST705 Linear-Algebra Estimability Statistics
category: ST705
---

* Do not remove this line (it will not be displayed)
{:toc}

# 1
**Prove that a (square) matrix that is both orthogonal and upper triangular must be a diagonal matrix.**

Recall that an upper diagonal matrix has its eigenvalues on its diagonal. Also recall that orthogonal matrices have no zero eigenvalues. Say $A$ looks like

$$
A = 
\begin{bmatrix}
	a_{11} & a_{12} & a_{13} & \dots a_{1n} \\
	0 & a_{22} & a_{23} & \dots a_{2n} \\
	\vdots & 0 & a_{33} & \dots a_{3n} \\
	\vdots & & & \\
	0 & \dots & & a_{nn}
\end{bmatrix}
$$


Since the columns are orthogonal, their inner products are zero.

$$
	\begin{align}
		\langle a_1 , a_2 \rangle & = a_{11} a_{12} + 0 a_{22} \\
			& = a_{11} a_{12} = 0 \Rightarrow a_{12} = 0 \\
		\langle a_2 , a_3 \rangle & = a_{12} a_{13} + a_{22} a_{23} \\
			& = 0 + a_{22} a_{23} = 0 \Rightarrow a_{23}  = 0 \\
			& \text{Since the diagonals can't be 0} \\
		\langle a_1 , a_3 \rangle & = a_11 a_13 = 0 \Rightarrow a_{13} = 0
	\end{align}
$$

If we continue with this process we will see that all of the off diagonals are 0 while all of the diagonals cannot be zero because of the properties mentioned previously. Thus, the matrix is diagonal.
# 2
**Suppose that $v_{1},\dots,v_{p} \in \mathbb{R}^{n}$ are a set of linearly independent vectors, and $w_{1},\dots,w_{p} \in \mathbb{R}^{n}$ are the orthogonal vectors obtained from $v_{1},\dots,v_{p}$ by the Gram-Schmidt process.  Furthermore, denote by $u_{1},\dots,u_{p}$ the normalized vectors corresponding to $w_{1},\dots,w_{p}$, and define the matrix $R \in \mathbb{R}^{p\times p}$ by**

$$
R_{ij} :=
\begin{cases}
\|w_{j}\| & \text{if } i=j \\
\langle v_{j}, u_i\rangle & \text{if } i<j \\
0 & \text{if } i>j \\
\end{cases}.
$$

**Prove that $V = UR$, where $V$ is the matrix with columns $v_{1},\dots,v_{p}$ and $U$ is the matrix with columns $u_{1},\dots,u_{p}$.**

Notice that 

$$
u_i = \frac{ w_i }{ ||w_i|| }.
$$


Then,

$$
\langle v_j , u_i \rangle = v_j ^T u_i = v_j^T \frac{ w_i }{ ||w_i|| } = \frac{ w_i^T v_j }{ || w_i || }
$$


Notice that 

$$
R = 
\begin{bmatrix}
	||w_1|| & \frac{ w_1^T v_2 }{ ||w_1|| } & \dots & \frac{ w_1^T v_n }{ ||w_1|| } \\
	0 & ||w_2|| & \dots & \frac{ w_2^T v_n }{ ||w_2|| } \\
	\vdots & 0 & \ddots & \dots \\
	0 & \dots & & ||w_n||
\end{bmatrix} = 
\begin{bmatrix}
	||w_1|| & 0 & \dots & 0 \\
	0 & ||w_2|| & \dots & 0 \\
	\vdots & 0 & \ddots & \dots \\
	0 & \dots & & ||w_n||
\end{bmatrix}
\begin{bmatrix}
	1  & \frac{ w_1^T v_2 }{ ||w_1||^2 } & \dots & \frac{ w_1^T v_n }{ ||w_1||^2 } \\
	0 & 1 & \dots & \frac{ w_2^T v_n }{ ||w_2||^2 } \\
	\vdots & 0 & \ddots & \dots \\
	0 & \dots & & 1
\end{bmatrix}
$$


Then,

$$
UR = [U_1, \dots , U_p] \begin{bmatrix}
	||w_1|| & 0 & \dots & 0 \\
	0 & ||w_2|| & \dots & 0 \\
	\vdots & 0 & \ddots & \dots \\
	0 & \dots & & ||w_n||
\end{bmatrix}
\begin{bmatrix}
	1  & \frac{ w_1^T v_2 }{ ||w_1||^2 } & \dots & \frac{ w_1^T v_n }{ ||w_1||^2 } \\
	0 & 1 & \dots & \frac{ w_2^T v_n }{ ||w_2||^2 } \\
	\vdots & 0 & \ddots & \dots \\
	0 & \dots & & 1
\end{bmatrix} = V.
$$


This is the same decomposition we got from the Gram-Schmidt process.

# 3
**In the notation of the previous problem, suppose that $p = n$.  Further, assume that $V = U_{1}R_{1} = U_{2}R_{2}$, where $U_{1}$ and $U_{2}$ are orthogonal matrices and $R_{1}$ and $R_{2}$ are upper triangular.  Prove that the matrix $R_{2}R_{1}^{-1}$ is orthogonal and diagonal.**

Since they are orthogonal, $U_i U_i ^T = I$.

$$
	\begin{align}
		R_1 & = U_1^T V \\
		R_2 & = U_2^T V \\ \\
		R_2 R_1^{-1} & = U_2^T V (U_1^T V)^{-1} \\
			& = U_2^T V V^T U_1 \\
			& = U_2^T U_1
	\end{align}
$$

Since this is the product of two orthogonal matrices, we know that $R_2 R_1^{-1}$ is also orthogonal.

Notice 

$$
	\begin{align}
		R_1^{-1} & = (U_1^T V)^{-1} \\
			& = V^T U_1 \\
			& = R_1^T U_1^T U_1 \\
			& = R_1^T.
	\end{align}
$$


Since $R_1$ is upper triangular, that means that $R_1^T  = R_1^{-1}$ is lower triangular. Thus, $R_2 R_1^{-1}$ is the product of a upper and lower triangular matrix, so it is diagonal.


# 4 (2.22)
**Householder matrices (a.k.a. elementary reflectors) take the form**


$$
\mathbf I = \mathbf I_n - \frac{ 2 }{ || \mathbf  u ||^2 } \mathbf u \mathbf u^T
$$


**where $\mathbf u$ is an $n \times 1$ nonzero vector.**


## a
**Show that $U$ is a symmetric, orthogonal matrix.**


Symmetry

$$
	\begin{align}
		U^T & = \Big( I - \frac{ 2 }{ ||u||^2 } u u^T \Big)^T \\
			& = I - \frac{ 2 }{ ||u||^2 } (u^T)^T (u)^T \\
			& = I - \frac{ 2 }{ ||u||^2 } u u^T \\
			& = U
	\end{align}
$$


Orthogonal

$$
	\begin{align}
		U U^T & = U U \\
			& = \Big( I - \frac{ 2 }{ ||u||^2 } u u^T \Big) \Big( I - \frac{ 2 }{ ||u||^2 } u u^T \Big) \\
			& = I I - I \frac{ 2 }{ ||u||^2 } u u^T - \frac{ 2 }{ ||u||^2 } u u^T I + \frac{ 4 }{ ||u||^4 } u u^T u u^T \\
			& = I - \frac{ 4 }{ ||u||^2 } u u^T + \frac{ 4 }{ ||u||^4 } u (u^T u) u^T \\
			& = I - \frac{ 4 }{ ||u||^2 } u u^T + \frac{ 4 ||u||^2 }{ ||u||^4 } u u^T \\
			& = I
	\end{align}
$$



## b
**Show that is $s = ||x||$, then choosing $u = x+ s e^{(1)}$ leads to $Ux = se^{(1)}$. This can be viewed as using $U$ to rotate space so that $x$ corresponds to the first dimension.**


Notice that

$$
	\begin{align}
		||u||^2 & = (x + ||x|| e^{(1)})^T (x + ||x|| e^{(1)}) \\
			& = x^T x + ||x|| (e^{(1)})^T x + ||x||^2 + x^T e^{(1)} ||x|| \\
			& = 2 ||x||(x + ||x|| e^{(1)}).
	\end{align}
$$


Then,

$$
	\begin{align}
		Ux & = x - \frac{ 2(x + ||x|| e^{(1)}) (x + ||x|| e^{(1)})^T}{ 2 ||x||(x + ||x|| e^{(1)})  } x  \\
			& = x - \frac{ (x + ||x|| e^{(1)})) (||x||^2 + ||x || e^{(1)})}{ 2 ||x||(x + ||x|| e^{(1)}) } \\ 
			& = x - x - ||x|| e^{(1)} \\
			& = -s e^{(1)}
	\end{align}
$$

# 5 (2.23)
**Now construct a matrix $U$ by partitioning as follows:**

$$
U = 
\begin{bmatrix}
	I_p & 0 \\
	0 & U_ *
\end{bmatrix}
\begin{matrix}
	p \\
	n-p
\end{matrix}

\text{and }

x = 
\begin{bmatrix}
	x_1 \\
	x_2
\end{bmatrix}
$$

**where $U_*$ is a Householder matrix constructed using (2.13) with $u_{\*} = x_2 + \|\|x_2\|\| e^{(1)}$.**

## a
**Show that $U$ is a symmetric, orthogonal matrix.**

Symmetry

$$
	\begin{align}
		U^T & = \begin{bmatrix}
				I_p & 0 \\
				0 & U_ *
			\end{bmatrix}^T \\
				& = \begin{bmatrix}
				I_p & 0 \\
				0 & U_* ^T
			\end{bmatrix} \\
		& = U
	\end{align}
$$


Orthogonality

$$
	\begin{align}
		U U^T & = U U \\
			& = \begin{bmatrix}
					I_p & 0 \\
					0 & U_ *
				\end{bmatrix} 
				\begin{bmatrix}
					I_p & 0 \\
					0 & U_ *
				\end{bmatrix} \\
			& = \begin{bmatrix}
					I_p I_p & 0 \\
					0 & U_* U_*
				\end{bmatrix} \\
			& = \begin{bmatrix}
					I_p & 0 \\
					0 & I_{n-p}
				\end{bmatrix} \\
			& = I_n
			
	\end{align}
$$


## b
**Show that**

$$
Ux = \begin{bmatrix}
	x_1 \\
	||x_2|| e^{(1)}
\end{bmatrix} 

\text{and }

U \begin{bmatrix}
	v \\
	0
\end{bmatrix} =
 \begin{bmatrix}
	v \\
	0
\end{bmatrix}
$$


$$
Ux = 
\begin{bmatrix}
	I_p & 0 \\
	0 & U_ *
\end{bmatrix}
\begin{bmatrix}
	x_1 \\
	x_2
\end{bmatrix} =
\begin{bmatrix}
	x_1 \\
	U_* x_2
\end{bmatrix} = 
\begin{bmatrix}
	x_1 \\
	||x_2|| e^{(1)}
\end{bmatrix}
$$


$$
U \begin{bmatrix}
	v \\
	0
\end{bmatrix} = 
\begin{bmatrix}
	I_p & 0 \\
	0 & U_ *
\end{bmatrix} 
 \begin{bmatrix}
	v \\
	0
\end{bmatrix} =
 \begin{bmatrix}
	Iv + 0  \\
	0 + 0 U_*
\end{bmatrix} =
 \begin{bmatrix}
	v \\
	0
\end{bmatrix}
$$


# 6 (2.24)
**Using the tools outlined in the two exercises above, for a design matrix $X$ we can construct a series of Householder matrices $U_1, \dots , U_p$ following (2.13) and (2.14) such that**

$$
U_p \dots U_2 U_1 X = \begin{bmatrix}
	R \\
	0
\end{bmatrix}
$$

**where $R$ is upper triangular.**

## a
**Show that $U_p \dots U_1$ is an orthogonal matrix.**


$$
(U_p \dots U_1) (U_p \dots U_1)^T = U_p \dots U_1 U_1^T \dots U_p^T = U_p \dots U_2 I U_2 ^T \dots U_p^T = I
$$


## b
**Show that $R^T R = X^T X$. (Note that $R$ constructed this way may differ from Gram-Schmidt by signs.**

$$
U_p \dots U_2 U_1 X = \begin{bmatrix}
	R \\
	0
\end{bmatrix}, \ 
(U_p \dots U_2 U_1 X)^T = \begin{bmatrix}
	R \\
	0
\end{bmatrix}^T
$$

$$
	\begin{align}
		(U_p \dots U_2 U_1 X) (U_p \dots U_2 U_1 X)^T & = \begin{bmatrix}
	R \\
	0
\end{bmatrix} \begin{bmatrix}
	R \\
	0
\end{bmatrix}^T \\
X^T U_1^T \dots U_p^T U_p \dots U_1 X & = R^T R \\
X^T X & = R^T R
	\end{align}
$$



# 7 (3.7)
**Consider the following cross-classified model without replicates:**

$$
y_{ij} = \mu + \alpha_i + \beta_j + e_{ijk}, \ E(e) = 0,
$$

**where $y$, $X$, and $b$ are as follows**

$$
	\begin{align}
		y = 
		\begin{bmatrix}
			y_{11} \\
			y_{12} \\
			y_{13} \\
			y_{21} \\
			y_{22} \\
			y_{23}
		\end{bmatrix}
		X = 
		\begin{bmatrix}
			1 & 1 & 0 & 1 & 0 & 0 \\
			1 & 1 & 0 & 0 & 1 & 0 \\
			1 & 1 & 0 & 0 & 0 & 1 \\
			1 & 0 & 1 & 1 & 0 & 0 \\
			1 & 0 & 1 & 0 & 1 & 0 \\
			1 & 0 & 1 & 0 & 0 & 1
		\end{bmatrix}
		b = 
		\begin{bmatrix}
			\mu \\
			\alpha_1 \\
			\alpha_2 \\
			\beta_1 \\
			\beta_2 \\
			\beta_3
		\end{bmatrix}.
	\end{align}
$$

## a
**What is $r = \text{rank}( X )$?**

The rank of $X$ is 4. 


## b
**Write out the normal equations and find all solutions.**

We need to solve $X^T X b = X^t y$.


$$
\begin{bmatrix}
	1 & 1 & 0 & 1 & 0 & 0 \\
	1 & 1 & 0 & 0 & 1 & 0 \\
	1 & 1 & 0 & 0 & 0 & 1 \\
	1 & 0 & 1 & 1 & 0 & 0 \\
	1 & 0 & 1 & 0 & 1 & 0 \\
	1 & 0 & 1 & 0 & 0 & 1
\end{bmatrix}^T \cdot
		\begin{bmatrix}
	1 & 1 & 0 & 1 & 0 & 0 \\
	1 & 1 & 0 & 0 & 1 & 0 \\
	1 & 1 & 0 & 0 & 0 & 1 \\
	1 & 0 & 1 & 1 & 0 & 0 \\
	1 & 0 & 1 & 0 & 1 & 0 \\
	1 & 0 & 1 & 0 & 0 & 1
\end{bmatrix}
\cdot 
\begin{bmatrix}
	\mu \\
	\alpha_1 \\
	\alpha_2 \\
	\beta_1 \\
	\beta_2 \\
	\beta_3
\end{bmatrix} = 
\begin{bmatrix}
	1 & 1 & 0 & 1 & 0 & 0 \\
	1 & 1 & 0 & 0 & 1 & 0 \\
	1 & 1 & 0 & 0 & 0 & 1 \\
	1 & 0 & 1 & 1 & 0 & 0 \\
	1 & 0 & 1 & 0 & 1 & 0 \\
	1 & 0 & 1 & 0 & 0 & 1
\end{bmatrix}^T \cdot 
\begin{bmatrix}
	y_{11} \\
	y_{12} \\
	y_{13} \\
	y_{21} \\
	y_{22} \\
	y_{23}
\end{bmatrix}
$$

Fix $\mu$ and $\beta_3$. Then we get,

$$
	\begin{align}
		\alpha_1 & = \frac{ y_{11} }{ 6 } + \frac{ y_{12} }{ 6 } + \frac{ 2y_{13} }{ 3 } - \frac{ y_{21} }{ 6 } - \frac{ y_{22} }{ 6 } + \frac{ y_{23} }{ 6 } - \beta_3 - \mu \\
		\alpha_2 & = -\frac{ y_{11} }{ 6 } - \frac{ y_{12} }{ 6 } + \frac{ y_{13} }{ 3 } + \frac{ y_{21} }{ 6 } + \frac{ y_{22} }{ 6 } + \frac{ 2 y_{23} }{ 3 }- \beta_3 - \mu \\
		\beta_1 & = \frac{ y_{11} }{ 2 } - \frac{ y_{13} }{ 2 } + \frac{ y_{21} }{ 2 } - \frac{ y_{23} }{ 2 } + \beta_3 \\
		\beta_2 & = \frac{ y_{12}}{ 2 } - \frac{ y_{13} }{ 2 } + \frac{ y_{22} }{ 2 } - \frac{ y_{23} }{ 2 } + \beta_3
	\end{align}
$$



## c
**Give a set of basis vectors for $\mathcal  N (X)$.**

We need to find the basis of vectors $a$ such that

$$
X a = 0.
$$


$$
	\begin{align}
		a_1 + a_2 + a_3 + a_4 + a_5 + a_6 & = 0 \\
		a_1 + a_2 + a_3 & = 0 \\
		a_4 + a_5 + a_6 & = 0 \\
		a_1 + a_4 & = 0 \\
		a_2 + a_5 & = 0 \\
		a_3 + a_6 & = 0 
	\end{align}
$$


Fix $a_5$ and $a_6$.

$$
	\begin{align}
		a_3 & = -a_6 \\
		a_2 & = -a_5 \\
		a_4 & = -a_5 - a_6 \\
		a_1 & = a_5 + a_6
	\end{align}
$$

So our basis vectors are

$$
\begin{bmatrix}
	1 \\
	-1 \\
	0 \\
	-1 \\
	1 \\
	0 \\
\end{bmatrix}

\begin{bmatrix}
	1 \\
	0 \\
	-1 \\
	-1 \\
	0 \\ 
	1
\end{bmatrix}.
$$



Another pair that would work are

$$
\begin{bmatrix}
	-1 \\
	0 \\
	0 \\
	1 \\
	1 \\
	1
\end{bmatrix}
\begin{bmatrix}
	-1 \\
	1 \\
	1 \\
	0 \\
	0 \\
	0
\end{bmatrix}.
$$

## d
**Give a list of $r$ linearly independent estimable functions $\lambda ^T b$.**

To do this we can find the $\text{ column }( X^T )$.

$$
X^T = 
\left(
\begin{array}{cccccc}
 1 & 1 & 1 & 1 & 1 & 1 \\
 1 & 1 & 1 & 0 & 0 & 0 \\
 0 & 0 & 0 & 1 & 1 & 1 \\
 1 & 0 & 0 & 1 & 0 & 0 \\
 0 & 1 & 0 & 0 & 1 & 0 \\
 0 & 0 & 1 & 0 & 0 & 1 \\
\end{array}
\right)
$$

Notice that this also has rank 4, so we need to choose 4 linearly independent columns. E.x. columns 1, 2, 5, and 6. 

## e
**Show that $\alpha_1 - \alpha_2$ is estimable and give its least squares estimator.**

Take $\lambda^T = [0, 1,-1, 0, 0, 0]$ such that 

$$
\lambda^T b = \alpha_1 - \alpha_2.
$$

Now we need to find $a$ such that

$$
a^T X = \lambda ^T.
$$


$$
[a_1, a_2, a_3, a_4, a_5, a_6] 		
\begin{bmatrix}
	1 & 1 & 0 & 1 & 0 & 0 \\
	1 & 1 & 0 & 0 & 1 & 0 \\
	1 & 1 & 0 & 0 & 0 & 1 \\
	1 & 0 & 1 & 1 & 0 & 0 \\
	1 & 0 & 1 & 0 & 1 & 0 \\
	1 & 0 & 1 & 0 & 0 & 1
\end{bmatrix}
= [0, 1, -1, 0, 0, 0]	
$$


$$
	\begin{align}
		a_1 + a_2 + a_3 + a_4 + a_5 + a_6 & = 0 \\
		a_1 + a_2 + a_3 & = 1 \\
		a_4 + a_5 + a_6 & = -1 \\
		a_1 + a_4 & = 0 \\
		a_2 + a_5 & = 0 \\
		a_3 + a_6 & = 0.
	\end{align}
$$


Now fix $a_5$ and $a_6$.


$$
	\begin{align}
		a_2 & = -a_5 \\
		a_3 & = -a_6 \\
		a_4 & = -1 + a_5 + a_6 \\
		a_1 & = 1 - a_5 - a_6
	\end{align}
$$


The least squares estimator would be

$$
\lambda^T \hat b = \frac{ y_{11} + y_{12} + y_{13}}{ 3  } + \frac{ y_{21} + y{22} + y{23} }{ 3 }.
$$


## f
**Show that $\beta_1 - 2\beta_2 + \beta_3$ is estimable and give its least squares estimator.**

Take $\lambda^T = [0, 0, 0, 1, -2, 1]$ such that 

$$
\lambda^T b = \beta_1 - 2 \beta_2 + \beta_3.
$$

Now we need to find $a$ such that

$$
a^T X = \lambda ^T.
$$



$$
[a_1, a_2, a_3, a_4, a_5, a_6] 		
\begin{bmatrix}
	1 & 1 & 0 & 1 & 0 & 0 \\
	1 & 1 & 0 & 0 & 1 & 0 \\
	1 & 1 & 0 & 0 & 0 & 1 \\
	1 & 0 & 1 & 1 & 0 & 0 \\
	1 & 0 & 1 & 0 & 1 & 0 \\
	1 & 0 & 1 & 0 & 0 & 1
\end{bmatrix}
= [0, 0, 0, 1, -2, 1]	
$$


$$
	\begin{align}
		a_1 + a_2 + a_3 + a_4 + a_5 + a_6 & = 0 \\
		a_1 + a_2 + a_3 & = 0 \\
		a_4 + a_5 + a_6 & = 0 \\
		a_1 + a_4 & = 1 \\
		a_2 + a_5 & = -2 \\
		a_3 + a_6 & = 1.
	\end{align}
$$


Now fix $a_5$ and $a_6$.

$$
	\begin{align}
		a_2 & = -2 - a_5 \\
		a_3 & = 1 - a_6 \\
		a_4 & = -a_5 - a_6 \\
		a_1 & = -a_2 - a_3 \\
			& = -(-2 - a_5) - (1-a_6) \\
			& = a_5 + a_6 + 1
	\end{align}
$$


## g
**Find all parameter vectors $b$ and $Xb$ = $(8,7,6,6,5,4)^T$.**

$$
	\begin{align}
		b_1 + b_2 + b_4 & = 8 \\
		b_1 + b_2 + b_5 & = 7 \\
		b_1 + b_2 + b_6 & = 6 \\
		b_1 + b_3 + b_4 & = 6 \\
		b_1 + b_3 + b_5 & = 5 \\
		b_1 + b_3 + b_6 & = 4
	\end{align}
$$

Fix $b_1$ and $b_2$.


$$
	\begin{align}
		b_4 & = 8 - b_1 - b_2 \\
		b_5 & = 7 - b_1 - b_2 \\
		b_6 & = 6 - b_1 - b_2 \\
		b_3 & = 6 - b_1 - b_4 \\
			& = 6 - b_1 - (8 - b_1 - b_2) \\
			& = b_2 - 2
	\end{align}
$$


The least squares estimator would be

$$
\lambda^T \hat b = \frac{ y_{11} + y_{21}}{ 2  } - 2 \cdot \frac{ y_{12} + y_{22} }{ 2 } + \frac{ y_{13} + y_{23} }{ 2 }.
$$
---
layout: post
comments: false
title: Example Problems on Linear Algebra and The Normal Equations
description: ST705 Homework 4 on Linear Algebra and The Normal Equations
tags: ST705 Linear-Algebra Normal-Equations Statistics
category: ST705
---

* Do not remove this line (it will not be displayed)
{:toc}


# 1 
**Let $X \in \mathbb{R}^{n\times p}$ and $u \in \text{column}(X)$.  Show that**

$$
\{\beta : X\beta = u\} = \{\beta : \beta = X^{g}u + (I_{p} - X^{g}X)z \text{ for some } z \in \mathbb{R}^{p}\}.
$$

Notice that

$$
	\begin{align}
		X \beta & = u \\
		X X^g X \beta & = X X^g u \\
		X \beta & = X X^g u \\
		u = X X^g u.
	\end{align}
$$

$\Leftarrow$

If $\{\beta : \beta = X^{g}u + (I_{p} - X^{g}X)z \text{ for some } z \in \mathbb{R}^{p}\}$, then

$$
	\begin{align}
		\beta & = X^{g}u + (I_{p} - X^{g}X)z \\
		X \beta & = X X^g u + X I_p z - X X^g X z \\
		X \beta & = u + X z - X z \\
		X \beta & = u.
	\end{align}
$$


$\Rightarrow$

If $\{\beta : X\beta = u\}$, then

$$
	\begin{align}
		\beta & = X^g u + \beta - X^g u \\
			& = X^g u + \beta - X^g X \beta \\
			& = X^g u + ( I_p - X^g X) \beta \\
			& \text{take } \beta = z \\
			& = X^g u + ( I_p - X^g X) z.
	\end{align}
$$

# 2 
**Let $X = QR$ where $Q$ has orthonormal columns.  Prove that if $\text{rank}(X) = \text{rank}(Q)$, then $P_{X} = QQ'$.**

Since $Q$ has the same rank as $X$ and it has orthonormal columns, it must have full column rank. Thus, $\text{ column }( Q ) = \text{ column }( X )$ and $P_U = P_X$.

$$
	\begin{align}
		P_X & = P_U \\
			& = U (U^T U)^g U^T \\
			& = U (I)^g U^T & \text{orthogonal} \\
			& = U U^T
	\end{align}
$$


# 3 (2.12)
**In Example 2.7 (Celsius to Fahrenheit), find $\gamma_0$ and $\gamma_1$ in terms of $\beta_0$ and $\beta_1$.**

We know that 

$$
	\begin{align}
		y_i & = \beta_0 + \beta_1 x_i + e_i \\
		y_i & = \gamma_0 + \gamma_1 w_i + e_i .
	\end{align}
$$

Where

$$
w_i = 1.8 x_i + 32.
$$


From this we get

$$
	\begin{align}
		\beta_0 & = \gamma_0 + 32 \gamma_1 \\
		\beta_1 & = 1.8 \gamma_1.
	\end{align}
$$


So,

$$
	\begin{align}
		\gamma_1 & = \frac{ \beta_1 }{ 1.8 } \\
		\gamma_0 & = \beta_0 - \frac{ 32 }{ 1.8 } \beta_1.
	\end{align}
$$

# 4 (2.13)
**Consider the simple linear regression model $y_i = \beta_0 + \beta_1 x_i + e_i$. Show that if the $x_i$ are equally spaced, that is, $x_i = s + t i$ for some values of $s$ and $t$, then $y_i = \gamma_0 + \gamma_1 i + e_i$ is an equivalent parameterization. Can you extend this to a quadratic or higher degree polynomial?**

$$
	\begin{align}
		y_i & = \beta_0 + \beta_1 x_i + e_i \\
			& = \beta_0 + \beta_1 (s + t i) + e_i \\
			& = \beta_0 + \beta_1 s + \beta_1 \cdot t \cdot i + e_i \\
	\end{align}
$$

Take $\gamma_0 = \beta_0 + \beta_1 s$ and $\gamma_1 = \beta_1 t$. The quadratic form looks like,


$$
	\begin{align}
		y_i & = \beta_0 + \beta_1 x_i + \beta_2 x^2 e_i \\
			& = \beta_0 + \beta_1 (s + t i) + \beta_2 (s + t i)^2 e_i \\
			& = \beta_0 + \beta_1 s + \beta_1 \cdot t i + \beta_2 s^2 + \beta_2 2 s t i + \beta_2 t^2 i^2 + e_i \\
			& = (\beta_0 + \beta_1 s + \beta_2 s^2) + (\beta_1 \cdot t + 2 \beta_2 s t) i + (\beta_2 t^2) i^2 + e_i.
	\end{align}
$$

Take $\gamma_0 =\beta_0 + \beta_1 s + \beta_2 s^2$, $\gamma_1 = \beta_1 \cdot t + 2 \beta_2 s t$, and $\gamma_2 = \beta_2 t^2$. This can be generalized to higher degree polynomials. You just have to expand the terms and then group them.


# 5 
**Let $A$ be an $m\times n$ matrix with rank $m$.  Prove that there exists an $n\times m$ matrix $B$ such that $AB = I_{m}$.**

Since $A$ has rank $m$, that means that the columns of $A$ form a basis for $\mathbb{R}^m$. If we take $b_i$ to be a column vector such that $A b_i = e_i$ and take $B = [b_1, \dots b_m]$, then $A B = I_m$.

# 6 
**Let $A \in \mathbb{R}^{n\times p}$ with rank$(A) = p$.  Further, suppose  $X \in \mathbb{R}^{n\times q}$ with $\text{column}(X) = \text{column}(A)$.  Show that there exists a unique matrix $S$ so that $X = AS$.**

Since $\text{ column }( X ) = \text{ column }( A )$, we know that all of the columns of $X$ exist in the column space of $A$. That is, $x_i = A s_i$. Take $S = [ s_1, \dots , s_q]$. Then, $X = A S$.

To show uniqueness, assume that are two matrices $S_1$ and $S_2$ such that $X = A S_1 = A S_2$. Then 

$$
A S_1 = A S_2 \Rightarrow 0 = A S_1 - A S_2 = A (S_1 - S_2).
$$

Since $A$ has full rank, know that $S_1 = S_2$.

# 7 (2.14)
**For $X$ and $W$ below, show $\mathcal C (X) = \mathcal C (W)$, by finding the matrices $S$ and $T$ so that $W = XT$ and $X = WS$:**


$$
X = 
\begin{bmatrix}
	1_{n_1} & 1_{n_1}& 0 & 0 \\
	1_{n_2} & 0 & 1_{n_2} & 0 \\
	1_{n_3} & 0 & 0 & 1_{n_3}
\end{bmatrix}, 
W = 
\begin{bmatrix}
	1_{n_1} & 1_{n_1} & 1_{n_1} \\
	1_{n_2} & 2 \cdot 1_{n_2} & 4 \cdot 1_{n_2} \\
	1_{n_3} & 3 \cdot 1_{n_3} & 9 \cdot 1_{n_3}
\end{bmatrix}
$$

**(Note: This shows the correspondence between ANOVA and a saturated polynomial regression.)**

$$
T = 
\begin{bmatrix}
	1 & 1 & 1 \\
	0 & 0 & 0 \\
	0 & 1 & 3 \\
	0 & 2 & 8
\end{bmatrix}
$$


We can use a shortcut to find $S$. Notice $X = W S = W W^{-1} X$.

$$
W^{-1} =
\left(
\begin{array}{ccc}
 \frac{3}{\text{n1}} & -\frac{3}{\text{n2}} & \frac{1}{\text{n3}} \\
 -\frac{5}{2 \text{n1}} & \frac{4}{\text{n2}} & -\frac{3}{2 \text{n3}} \\
 \frac{1}{2 \text{n1}} & -\frac{1}{\text{n2}} & \frac{1}{2 \text{n3}} \\
\end{array}
\right)

\Rightarrow

S = W^{-1} X = \left(
\begin{array}{cccc}
 1 & 3 & -3 & 1 \\
 0 & -\frac{5}{2} & 4 & -\frac{3}{2} \\
 0 & \frac{1}{2} & -1 & \frac{1}{2} \\
\end{array}
\right)
$$


# 8 
**Let $A$ be an $m\times n$ matrix and $B$ be an $n\times p$ matrix.  Prove that $AB$ can be written as a sum of $n$ matrices of rank at most one.  Hint: think about empirical covariance matrices.**

Notice that

$$
	\begin{align}
		\text{rank}( A ) & \leq \min(m,n) \\
		\text{rank}( B ) & \leq \min(n,p) \\
		\text{rank}( AB ) & \leq \min[ \text{rank}( A ), \text{rank}( B )] \\
			& = \min[ \min(m,n), \min(n,p)] \\
			& = \min(m,n,p).
	\end{align}
$$

Say that $\text{rank}( AB ) = k$, then take the first $k$ $U_i$'s to represent the $k$ linearly independent columns. That is,

$$
U_i = [ 0, \dots, (AB)_i, 0, \dots , 0 ].
$$

 This has rank 1. We can represent linearly dependent columns of $AB$ as

$$
U_j = [ 0, \dots (AB)_j, a \cdot (AB)_j, 0 \dots , 0, \dots 0].
$$

Where $a$ is a constant. This also has rank 1. We can add $k$ matrices of these forms together to get $AB$. Then we can make the remaining, if any, $n-k$ matrices the 0 matrix, which has rank 0. 

$$
AB =  \sum_{i=1}^{k}U_i +  \sum_{i=k+1}^{n} 0
$$

Notice that this will always work because $AB$ will have $n$ or fewer linearly independent columns.
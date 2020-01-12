---
layout: post
comments: false
title: Example Problems on Linear Algebra
description: ST705 Homework 1 on Linear Algebra
tags: ST705 Linear-Algebra Statistics
category: ST705
---


* Do not remove this line (it will not be displayed)
{:toc}

# 1
**Prove the following theorem.  Let $V$ be a vector space and $B = \{u_{1},\dots,u_{n}\}$ be a subset of $V$.  Then $B$ is a basis if and only if each $v \in V$ can be expressed _uniquely_ as**

$$
v = a_{1}u_{1} + \cdots + a_{n}u_{n}
$$

**for some set of scalars $\{a_{1},\dots,a_{n}\}$.**

_Proof:_

$\Rightarrow$

Take $B= \\{ b_1, b_2, \dots , b_n \\}$ to be a basis of $V$. Then, $B$ is linearly independent and generates $V$. So, for all $v\in V$

$$
v = x_1 \cdot b_1 + \dots + x_n \cdot b_n 
$$

for some scalars $x_1, \dots, x_n$, Now, let's check for uniqueness of the scalar multiples. Say there exists some scalars $y_1, \dots y_n$ such that,

$$
v = y_1 \cdot b_1 + \dots + y_n \cdot b_n.
$$


Then,

$$
	\begin{align}
		v & = v \\
		x_1 \cdot b_1 + \dots + x_n \cdot b_n & = y_1 \cdot b_1 + \dots + y_n \cdot b_n \\
		(x_1 - y_1) \cdot b_1 + \dots + (x_n - y_n) \cdot b_n & = 0.
	\end{align}
$$

Since $B$ is linearly independent, the only representation of the 0 vector is trivial. Thus each $x_i - y_i = 0 \Rightarrow x_i = y_i$. Thus, the scalars are unique.

$\Leftarrow$


Since $\forall v \in V$ can be expressed uniquely, we know that $\\{u_1, \dots, u_n\\}$ spans $V$. Since the 0 vector can be expressed uniquely, we know that $\\{u_1, \dots, u_n\\}$ is linearly independent. Satisfying these two conditions, we know that  $\\{u_1, \dots, u_n\\}$ forms a basis for $V$.

<div style="text-align: right"> 🐙 </div>



# 2
**Prove that the eigenvalues of an upper triangular matrix $M$ are the diagonal components of $M$.**


_Proof:_

Take $M$ to be an upper triangular matrix

$$
M = 
\begin{bmatrix}
	m_{11} & m_{12} & \dots & m_{1n} \\
	0 & m_{22} & \dots & \\
	\vdots & & \ddots & \\
	0 & \dots & & m_{nn}
\end{bmatrix}
$$

Then to find the eigenvalues, we must solve the $det\|M - \lambda I\| = 0$. This gives

$$
\begin{vmatrix}
	m_{11} - \lambda & m_{12} & \dots & m_{1n} \\
	0 & m_{22} - \lambda & \dots & \\
	\vdots & & \ddots & \\
	0 & \dots & & m_{nn} - \lambda
\end{vmatrix}
= 0.
$$

This is another upper triangular matrix. We know that the determinant of an upper triangular matrix is the product of the diagonal elements. So,

$$
(m_{11} - \lambda) \cdot (m_{22} - \lambda ) \cdot \dots \cdot (m_{nn} - \lambda) = 0.
$$

Thus, $\lambda = m\_{ii}$ with $i \in {1, \dots, n}$; the eigenvalues are equal to the elements on the diagonals.

<div style="text-align: right"> 🐙 </div>


<!--

**Write pseudo-code for an algorithm that exploits this fact for more efficiently computing the matrix exponential $e^{M}$ (recall the definition of the matrix exponential from your linear algebra course).**

We can use this to help us find the matrix exponential $e^{M}$. Recall,

$$
e^{M} = \sum_{k=0}^{\infty} \frac{ 1 }{ k! } M^k.
$$

Also recall,

$$
M^2 = M M, M^3 = M M^2.
$$


We can rewrite our matrix as $M = Q \Lambda Q^T$ where $Q$ is the matrix of eigenvectors and $\Lambda$ is the matrix with eigenvalues on the diagonal. We can find these with the trick from above. Then our sum is

$$
	\begin{align}
		e^{M} & = \sum_{k=0}^{\infty} \frac{ 1 }{ k! } Q\Lambda Q^T Q \Lambda Q^T \dots Q \Lambda Q^T \\
			& = \sum_{k=0}^{\infty} \frac{ 1 }{ k! } Q\Lambda^k Q^T Q.
	\end{align}
$$

Since $\Lambda$ has only the eigenvalues on the diagonal,

$$
\Lambda^k =
\begin{bmatrix}
	\lambda_1^k & 0 & \dots & \\
	0 & \lambda_2^k & 0 & \dots \\
	0 & & \ddots & \\
	0 & \dots & & \lambda_n^k
\end{bmatrix}.
$$


With this algorithm we only have to take the powers of the $\lambda$, which are just numbers, and performing two matrix multiplications rather than $k$ matrix multiplications. This is far more computationally efficient.

```
M = nxn upper-triangle matrix
rep = number of times to sum

# vector of eigenvalues
lambda = [][]


# read eigenvalues from diagonal
for i in range(1, n):
	lambda[i][i] = M[i][i]


eVector = eigenvector(M, lambda)

eM = 0

for i in range(1,rep):
	eM += 1 / factorial(k) * eVector^T * lambda * eVector

```
-->

# 3
**The defining property of a projection matrix $A$ is that $A^{2} = A$ (recall the definition of the square of a matrix from your linear algebra course).  Establish the following facts.**

## a
**If $A$ is a projection matrix, then all of its eigenvalues are either zero or one.**

Starting with the eigenvalue equation, we know

$$
A v = \lambda v.
$$

Where $v$ is an eigenvector and $\lambda$ and eigenvalue. If we take $v=0$ and $A \neq 0$, then it must be the case that $\lambda = 0$. Also,

$$
	\begin{align}
		A v & = \lambda v \\
		A A v & = A \lambda v \\
		A^2 v & = \lambda A v \\
		A v & = \lambda A v & \text{Projection} \\
		\lambda = 1.
	\end{align}
$$

Thus, $\lambda = 0$ or $\lambda = 1$.

## b
**If $A \in \mathbb{R}^{p\times p}$ is a projection and symmetric (i.e., an orthogonal projection matrix), then for every vector $v$ the projection $Av$ is orthogonal to $v - Av$.**

$$
	\begin{align}
		Av \cdot (v - Av) & = (Av)^T (v-Av) \\
			& = v^T A^T (v-Av) \\
			& = v^T A^T v - v^T A^T A v \\
			& = v^T A^T v - v^T A^T A^T v & \text{Symmetric} \\
			& = v^T A^T v - v^T (A^T)^2 v \\
			& = v^T A^T v - v^T A^T v & \text{Projection} \\
			& = 0
	\end{align}
$$


Since the dot product is 0, they are orthogonal.

## c
**$\text{tr}(A + B) = \text{tr}(A) + \text{tr}(B)$.**

$$
	\begin{align}
		\text{tr}(A+B) & = \sum_{i=1}^{n} a_ii + b_ii \\
			& = \sum_{i=1}^{n} (a_ii) + \sum_{i=1}^{n} (b_ii) \\
			& = \text{tr}(A) + \text{tr}(B)
	\end{align}
$$

## d
**$\text{tr}(AB) = \text{tr}(BA)$.**

$$
	\begin{align}
		\text{tr}(AB) & = \sum_{i=1}^n (AB)_{ii} \\
			& = \mathbf{a_{11} b_{11}} + a_{12} b_{21} + \dots a_{1n} b_{n1} \\
			& + \mathbf{a_{21} b_{12}} + a_{22} b_{22} + \dots a_{2n} b_{n2} \\
			& + \dots \\
			& + \mathbf{a_{n1} b_{1n}} + a_{n2} b_{2n} + \dots a_{nn} b_{nn} \\ \\
			& = a_{11} b_{11} + b_{12} a_{21} + \dots + b_{1n} a_{n1} \\
			& + \dots \\
			& + b_{n1} a_{1n} + b_{n2} a_{2n} + \dots + b_{nn} a_{nn} \\
			& = \text{tr}(BA)
	\end{align}
$$



# 4
**Let $A \in \mathbb{R}^{p\times p}$ be symmetric.  Use the spectral decomposition of $A$ to show that**

$$
\sup_{x\in\mathbb{R}^{p}\setminus\{0\}} \frac{x'Ax}{x'x} = \lambda_{\max}
$$

**where $\lambda_{\max}$ is the largest eigenvalue of $A$.  Observe that this is a special case of the Courant-Fischer theorem (see [https://en.wikipedia.org/wiki/Min-max_theorem](https://en.wikipedia.org/wiki/Min-max_theorem)).**

To show this equality we need to show both that $\lambda_{\max}$ is the supremum and also that the function attains this value.

Using the spectral theorem, 

$$
\frac{x^T A x}{x^T x}  = \frac{ x^T Q^T D Q x }{ x^T x }
$$

Where $D$ is a diagonal matrix with $\lambda_i$ on the $i$th diagonal and $Q$ is orthogonal.

$$
	\begin{align}
		\frac{x^TAx}{x^Tx} & = \frac{ x^T Q^T D Q x }{ x^T x } \\
			& = \frac{ (Qx)^T D (Qx) }{ x^T x } \\
			& = \frac{ v^T D v }{ x^T x } \\
			& = \frac{ \sum_{i=1}^{n} \lambda_i v_i^2 }{ x^T x } \\
			& = \frac{ \sum_{i=1}^{n} \lambda_i v_i^2 }{ x^T Q^T Q x } \text{Orthogonal} \\
			& = \frac{ \sum_{i=1}^{n} \lambda_i v_i^2 }{ v^T v } \\
			& \leq \lambda_{\max} \frac{ \sum_{i=1}^n v^2 }{ v^T v } \\
			& = \lambda_{\max}
	\end{align}
$$

We must now show that $\lambda_{\max}$ is attained by the function. Take $x = Q^T e_i$. Then,

$$
	\begin{align}
		\frac{x^TAx}{x^Tx} & = \frac{ e_i^T Q Q^T D Q Q^T e_i }{ e_i^T Q Q^T e_i } \\
			& = \frac{ e_i^T D e_i }{ e_i^T e_i }.
	\end{align}
$$

This has the effect of picking out the $i$th eigenvalue, so it will attain $\lambda_{\max}$.


# 5
**Let $x = (x_{1}, \dots, x_{p})' \in \mathbb{R}^{p}$.  Show that for $i \in \{1,\dots,p\}$,**

$$
|x_{i}| \le \|x\|_{2} \le \|x\|_{1},
$$

**where $\| \| \cdot \| \| \_{1}$ and $\| \| \cdot\|\| \_{2}$ are the $l\_{1}$ and $l\_{2}$ vector norms, respectively.**

$$
||x||_2 = \sqrt{x_1^2 + \dots + x_p^2} \leq \sqrt{x_1^2} + \dots + \sqrt{x_p^2} \leq |x_1| + \dots + |x_p| = ||x||_1
$$

Thus, $\|\|x\|\|_2 \leq \|\|x\|\|_1$.

$$
|x_i| = \sqrt{x_i^2} \leq \sqrt{ \sum x_i^2} = ||x||_2
$$
$\|\|x\|\|_2 \leq \|\|x\|\|_1$.


Thus, $\|x_i\| \leq \|\|x\|\|_2 \leq \|\|x\|\|_1$.



# 6
**Show that every eigenvalue of a real symmetric matrix is real.**

Take $A$ to be our real symmetric matrix with dimensions $p\times p$. By the spectral theorem we can say $A = QDQ^T$ where $D$ is a diagonal matrix of eigenvalues and $Q$ is the corresponding eigenvectors (also notice $$. Since $Q$ is linearly independent, it forms a basis of $\mathbb{R}^p$; all of its entries are real. Now notice $Q^T A Q = D$. Since all the entries in the left matrices are real and the real numbers are closed under addition and multiplication, that means all of the elements in $D$ must also be real. Thus, the eigenvalues are all real.

# 7
**Show that if $X \sim \text{N}_{p}(\mu, \Sigma)$ and $Y = X'AX$, then $E(Y) = \text{tr}(A\Sigma) + \mu'A\mu$.**

Notice that $E(Y)$ is a scalar, so $E(Y) = \text{tr}E(Y)$. Also notice that 

$$
Cov(X) = V(X) = E((X - E(X))(X-E(X))^T) = E(XX^T) - E(X)E(X^T)
$$

$$
	\begin{align}
		E(Y) & = E(X^T A X) \\
			& = \text{tr}( E(X^T A X)) \\
			& = E(\text{tr}( X^T A X)) \\
			& = E(\text{tr}( A X X^T )) \\
			& = \text{tr}( E(A E(X X^T)) ) \\
			& = \text{tr}( A \Big[ E(XX^T) - E(X) E(X^T) + E(X)E(X^T) \Big] ) \\
			& = \text{tr}( A ( \Sigma + \mu \mu^T) ) \\
			& = \text{tr}( A \Sigma + A \mu \mu^T ) \\
			& = \text{tr}( A \Sigma ) + \text{tr}( A \mu \mu^T ) \\
			& = \text{tr}( A \Sigma ) +  \text{tr}( \mu^T A \mu ) \\
			& = \text{tr}( A \Sigma ) + \mu^T A \mu
	\end{align}
$$


# 8
**Let $U$ and $V$ be random variables.  Establish the following inequalities.**


## a
**$P(|U+V| > a + b) \le P(|U| > a) + P(|V| > b)$ for every $a,b \ge 0$.**

From the triangle inequality we get

$$
P(|U+V| > a + b) \leq P(|U| + |V| > a + b).
$$

If we look at the set $\{ \|U\| + \|V\| > a + b \}$, its complement is $\{ \|U\| + \|V\| \leq a + b \}$. Notice

$$
{|U| + |V| \leq a + b} \subset \{|U| \leq a\} \cap \{|V| \leq b\}.
$$


Now if we take the complement again we get

$$
|U| + |V| > a + b  \subset \{ |U| > a \} \cup \{|V| > b \}.
$$


Thus,

$$
	\begin{align}
		P( |U| + |V| > a+b) & \leq P(|U| > a \cup |V| > b) \\
			& \leq P(|U| > a) + P(|V| > b).
	\end{align}
$$


## b
**$P(|UV| > a) \le P(|U| > a/b) + P(|V| > b)$ for every $a \ge 0$ and $b > 0$.**

Notice that $P(\|UV\| > a) = P(\|UV\| > \frac{ a }{ b } \cdot b)$ for $b>0$. Notice that the complements of $\{ \|UV\| > \frac{ a }{ b } \cdot b) \}$ is $\{ \|UV\| \leq \frac{ a }{ b } \cdot b) \}$. Then,

$$
\{ |UV| \leq \frac{ a }{ b } \cdot b) \} \subset \{ |U| \leq \frac{ a }{ b }\} \cap \{ |V| \leq b) \}
$$

Taking the complement again gives $\{ \|U\| > \frac{ a }{ b } \} \cup \{ \|V\| > b \}$. Thus,

$$
	\begin{align}
		P(|UV| > a) & \leq P(\{ |U| > \frac{ a }{ b } \} \cup \{ |V| > b \} ) \\
			& \leq P(|U| > \frac{ a }{ b }) + P(|V|>b).
	\end{align}
$$
---
layout: post
comments: false
title: Example Problems on Linear Algebra and The Normal Equations
description: ST705 Homework 3 on Linear Algebra and The Normal Equations
tags: ST705 Linear-Algebra Nomral-Equations Statistics
category: ST705
---

* Do not remove this line (it will not be displayed)
{:toc}



# 1
**Let $G(\beta) = (y - X\beta)'W(y - X\beta)$.  Derive $\partial{G} / \partial{\beta}$.**

$$
G(\beta) = (y - X\beta)'W(y - X\beta) = y^T W y - y^T W X \beta - \beta^T X^T W y + \beta^T X^T W X \beta
$$


$$
	\begin{align}
		\partial{G} / \partial{\beta} & = \partial/ \partial{\beta} \Big[ y^T W y - y^T W X \beta - \beta^T X^T W y + \beta^T X^T W X \beta \Big] \\
			& = 0 - (y^T W X) ^T - \partial/ \partial{\beta}  \Big[ \beta^T X^T W y \Big] + (X^TWX + (X^T W X)^T) \beta \\
			& =(y^T W X) ^T - \partial/ \partial{\beta}  \Big[ \beta^T X^T W y \Big] + (X^TWX + (X^T W X)^T) \beta \\
	\end{align}
$$


Notice that $\beta^T X^T W y - (\beta^T X^T W y)^T = y W^T X \beta$ because it's a scalar.

$$
	\begin{align}
		\partial{G} / \partial{\beta} & = (y^T W X) ^T - \partial/ \partial{\beta}  \Big[ y W^T X \beta\Big] + (X^TWX + (X^T W X)^T) \beta \\
			& = -X^T W^T y - X^T W y + (X^TWX + (X^T W X)^T) \beta
	\end{align}
$$

# 2
**Let $A \in \mathbb{R}^{n\times p}$**

## a
**Prove that if $A^{g}$ is a generalized inverse of $A$ (i.e., only satisfying $AA^{g}A = A$), then $(A^{g})'$ is a generalized inverse of $A'$.  Conclude from this fact that $P_{X} := X(X'X)^{g}X'$ is symmetric (this finishes the proof of a theorem about $P_{X}$ from lecture).**

 $$
	\begin{align}
		A A^g A & = A \\
		(A A^g A)^T & = A^T \\
		A^T (A^g)^T A^T & = A^T
	\end{align}
$$


Thus, $(A^g)^T = (A^T)^g$.

Notice that $P_X = P_X^T$.

$$
	\begin{align}
		P_X & = X (X^T X)^g X^T \\
			& = (X (X^T X)^g X^T )^T \\
			& = X ((X^T X)^g)^T X^T \\
			& = X ((X^T X)^T)^g X^T \\
			& = X (X^T X)^g X^T.
	\end{align}
$$

## b
**Prove the existence and uniqueness of the Moore-Penrose generalized inverse, usually denoted $A^{+}$, of $A$.**

From our work on the previous homework, we know that every matrix has a Moore-Penrose inverse via its SVD. Thus, we have existence.

Say we have two generalized inverses $A_1^+$ and $A_2^+$. In order to show uniqueness we need to show

$$
A_1^+ = A_1^+ A A_1^+ = A_1^+ A  A_2^+ = A_2^+ A A_2^+ = A_2^+.
$$

Thus, it is sufficient to show $A A_1^+ = A A_2^+$ and $A_1^+ A = A_2^+ A$. We will use our rules of Moore-Penrose inverses.

$$
	\begin{align}
		A A_1^+ & = A A_2^+ A A_1^+ & (1)\\
			& = (A A_2^+)^T (A A_1^+)^T & (3) \\
			& = (A_2^+)^T A^T (A_1^+)^T A^T \\
			& = (A_2^+)^T A^T & (1,3) \\
			& = (A A_2^+)^T & (3) \\
			& = A A_2^+
	\end{align}
$$


$$
	\begin{align}
		A_1^+ A & = A_1^+ A A_2^+ A & (1) \\
			& = (A_1^+ A)^T (A_2^+ A)^T & (3) \\
			& = A^T (A_1^+)^T A^T (A_2^+)^T \\
			& = A^T (A_2^+)^T & (1, 3) \\
			& = A_2^+ A & (3)
	\end{align}
$$


## c
**Show that if $A$ has full column rank, then $A^{+} = (A'A)^{-1}A'$.**

Notice that since $A$ is full column rank  $\text{rank}( A ) = \text{rank}( A^T A )$. So $ A^T A $ is square and has full column rank, so it is invertible. Now we need to show that the 4 conditions hold for the Moore-Penrose generalized inverse.

$$
	\begin{align}
		A A^+ A & = A (A'A)^{-1}A' A \\
			& =  A (A'A)^{-1} (A' A) \\
			& = A I \\
			& = A
	\end{align}
$$


$$
	\begin{align}
		A^+ A A^+ & =   (A'A)^{-1} A' A (A'A)^{-1}A' \\
			&  = (A'A)^{-1} (A' A) (A'A)^{-1}A' \\
			& = (A'A)^{-1}A' \\
			& = A^+
	\end{align}
$$


$$
	\begin{align}
		(A^+ A)^T & = ((A'A)^{-1}A' A)' \\
			& = A' (A')' (A'A)^{-1}\\
			& = A' A (A'A)^{-1}   \\
			& = (A' T A) (A'A)^{-1} \\
			& = I \\
			& = (A'A)^{-1} (A' A) \\
			& = A^+ A
	\end{align}
$$


$$
	\begin{align}
		(A A^+)^T & = (A (A'A)^{-1}A' )^T \\
			& = A (A'A)^{-1} A^T \\
			& = A A^+
	\end{align}
$$

## d
**Show that if $A$ has full row rank, then $A^{+} = A' (AA')^{-1}$.**
 
Since $A$ has full row rank, $A^T$ has full column rank. Thus, $A A^T$ is invertible. Now we need to verify the Moore-Penrose conditions.


$$
	\begin{align}
		A A^+ A & = A A^T (A A ^T )^{-1} A \\
			& = (A A^T) (A A ^T )^{-1} A \\
			& = A
	\end{align}
$$


$$
	\begin{align}
		A^+ A A^+ & = A^T (A A ^T )^{-1} A A^T (A A ^T )^{-1}  \\
			& = A^T (A A ^T )^{-1} (A A^T) (A A ^T )^{-1}  \\
			& = A^T (A A ^T )^{-1} \\
			& = A^+
	\end{align}
$$


$$
	\begin{align}
		(A A^+)^T & = (A A^T (A A ^T )^{-1})^T \\
			& = ((A A ^T )^{-1})^T A A^T \\
			& = I \\
			& = (A A^T) (A A ^T )^{-1} \\
			& = A A^+
	\end{align}
$$


$$
	\begin{align}
		(A^+ A)^T & = (A^T (A A ^T )^{-1} A )^T \\
			& = A^T (A A^T)^{-1} A \\
			& = A^+ A
	\end{align}
$$


# 3
**Let $S$ be a nonempty subset of an inner product space $V$.  The orthogonal complement to the set $S$ is defined as**

$$
S^{\perp} := \{x \in V : \langle x,y\rangle = 0 \text{ for every } y \in S\}.
$$


## a
**Show that $S^{\perp}$ is a subspace of $V$ for any $S \subseteq V$.**

In order to show that $S^{\perp}$ is a subspace we have to show three conditions:


1: That there is a zero element. Take $y \in S$. Then $\langle 0 , y \rangle = 0$ by the definition of the inner product. Thus, $0 \in S^{perp}$.


2: That the space is closed under vector addition. Take $a, b \in S^\perp$ and $y \in S$. Then $\langle a , y  \rangle = \langle b , y \rangle = 0$. Then, 

$$
\langle a + b, y \rangle = \langle a , y \rangle + \langle b , y \rangle = 0 + 0.
$$ 

Thus, $a + b \in S^\perp$.

3: That the space is closed under scalar multiplication. Take $x \in S^\perp$, $y \in S$ and $a \in F$. Then,

$$
\langle a x , y \rangle = a \langle x , y \rangle = a \cdot 0 = 0.
$$


Thus. $a x \in S^\perp$.


## b
**Let $W \subseteq V$ be a finite dimensional subspace, and let $y \in V$.  Show that there exist unique vectors $u \in W$ and $z \in W^{\perp}$ such that $y = u + z$.**

Take $\{ u_1, \dots u_k \}$ to be an orthonormal basis for $W$ (which is guaranteed to exist by Graham-Schmidt). Then define $u = \sum_{ i=1 }^{ k } = \langle y , u_i \rangle u_i$ and $z = y - u$. Then $y = u + z$. We need to show that $\langle u , z \rangle = 0$.

$$
	\begin{align}
		\langle u , z \rangle & = \langle u , y-u \rangle \\
			& = \langle u , y \rangle - \langle u , u \rangle \\
			& = \langle \sum_{ i=1 }^{ k }  \langle y , u_i \rangle u_i , y \rangle - \langle \sum_{ i=1 }^{ k }  \langle y , u_i \rangle u_i , \sum_{ i=1 }^{ k }  \langle y , u_i \rangle u_i \rangle \\
			& = \sum_{ i=1 }^{ k } \langle y , u_i \rangle^2 - \sum_{ i } \sum_{ j } \langle y , u_i \rangle \langle y , u_i \rangle \langle u_i , u_j \rangle \\
			& = \sum_{ i=1 }^{ k } \langle y , u_i \rangle^2 - \sum_{ i=1 }^{ k } \langle y , u_i \rangle^2 \\
			& = 0
	\end{align}
$$

Thus $y = \sum a_i v_i \rightarrow a_i = \langle y , v_i \rangle$ if the basis is orthonormal. By construction, $u \in W$. So now we must show that $z \in W^\perp$.

$$
	\begin{align}
		\langle v, z  \rangle & = \langle \sum a_i u_i , y - \sum \langle y , u_i \rangle u_i \rangle \\
		& = \langle \sum  a_i u_i , y \rangle - \langle \sum a_i u_i , \sum \langle y , u_i \rangle u_i  \rangle \\
		& = 0 & \text{same as above}
	\end{align}
$$

Thus, $z \in W^\perp$. Now to show uniqueness assume $u_1 + z_1 = u_2 + z_2 = y$. Then $u_1 - u_2 = z_2 - z_1$ where $u_1 - u_2 \in W$ and $z_2 - z_1 \in W^\perp$. Since they are equal and in the intersection, they must be 0. Thus, $u_1 = u_2 $ and $z_1 = z_2$.

## c
**Let $X \in \mathbb{R}^{n\times p}$.  Verify that column$(X)$ and null$(X')$ are orthogonal complements.**

Take $y \in \text{ column }( X )\rightarrow y = Xv$ and $W \in \mathcal N (X^T) \rightarrow X^T W = 0$.

$$
y^T W = v^T X^T W = v^T (0) = 0
$$


Thus, they are orthogonal. If $dim(A) = m$ and $\text{rank}( A )= \text{rank}( A^T ) = r$. Then $dim(\mathcal C (A)) = \text{rank}( A ) = r$ and $dim( \mathcal N (A^T) ) = m - \text{rank}( A^T ) - m-r$.

 
# 4 (2.8)

**Using $X$ and $P_X$ from Example 2.3, and $y^T = (1, 3, 5, 7)$:**

## a
**Construct all solutions to the normal equations.**

$$
	\begin{align}
		\begin{bmatrix}
			1 & 0 & 1 \\
			1 & 0 & 1 \\
			1 & 1 & 2 \\
			1 & 1 & 2
		\end{bmatrix}

		\begin{bmatrix}
			b_1 \\
			b_2 \\
			b_3
		\end{bmatrix}

		& = 
		\frac{ 1 }{ 2 }

		\begin{bmatrix}
			1 & 1 & 0 & 0 \\
			1 & 1 & 0 & 0 \\
			0 & 0 & 1 & 1 \\
			0 & 0 & 1 & 1
		\end{bmatrix}

		\begin{bmatrix}
			1 \\
			3 \\
			5 \\
			7
		\end{bmatrix} \\
		
		\begin{bmatrix}
			b_1 + b_3 \\
			b_1 + b_3 \\
			b_1 + b_2 + 2 b_3 \\
			b_1 + b_2 + 2 b_3
		\end{bmatrix} 
		& = 
		\begin{bmatrix}
			\frac{ 1 }{ 2 }(1+3) \\
			\frac{ 1 }{ 2 }(1+3) \\
			\frac{ 1 }{ 2 }(5+7) \\
			\frac{ 1 }{ 2 }(5+7)
		\end{bmatrix}
\end{align}
$$

Fix $b_1 = x$. Then $b_3 = 2-x$ and 

$$
	\begin{align}
		x + b_2 + 2 (2-x) & = 6 \\
		b_2 & = 2+x.
	\end{align}
$$






## b
**Construct all solutions to $Xb = P_X y$**

$$
	\begin{align}
		\begin{bmatrix}
			b_1 + b_3 \\
			b_1 + b_3 \\
			b_1 + b_2 + 2 b_3 \\
			b_1 + b_2 + 2 b_3
		\end{bmatrix} 
		& = 
		\begin{bmatrix}
			\frac{ 1 }{ 2 }(1+3) \\
			\frac{ 1 }{ 2 }(1+3) \\
			\frac{ 1 }{ 2 }(5+7) \\
			\frac{ 1 }{ 2 }(5+7)
		\end{bmatrix}
	\end{align}
$$

Set $b_1 = x$. Then,

$$
	\begin{align}
		x + b_3 & = \frac{ 1 }{ 2 }(y_1 + y_2) \\
		b_3 & = \frac{ 1 }{ 2 }(y_1 + y_2) - x \\ \\
		b_2 + x + 2 (\frac{ 1 }{ 2 }(y_1 + y_2) - x) & = \frac{ 1 }{ 2 }(y_3 + y_4) \\
		b_2 = \frac{ 1 }{ 2 } (y_3 + y_4) - \frac{ 1 }{ 2 }(y_1 + y_2) + x
	\end{align}
$$



# 5 (2.9)
**Using $P_X$ from Example 2.3, show that $1 \in \text{ column }( X )$. Also compute $P_X - P_1$.**

$1$ is in the column space of $X$ since the first column of $X$ is the $1$ vector itself.

$$
P_X - P_1 = \frac{ 1 }{ 2 } 
\begin{bmatrix}
	1 & 1 & 0 & 0 \\
	1 & 1 & 0 & 0 \\
	0 & 0 & 1 & 1 \\
	0 & 0 & 1 & 1
\end{bmatrix}
-
\frac{ 1 }{ 4 }

\begin{bmatrix}
	1 & 1 & 1 & 1 \\
	1 & 1 & 1 & 1 \\
	1 & 1 & 1 & 1 \\
	1 & 1 & 1 & 1
\end{bmatrix}

= \frac{ 1 }{ 4 }
\begin{bmatrix}
	1 & 1 & -1 & -1 \\
	1 & 1 & -1 & -1 \\
	-1 & -1 & 1 & 1 \\
	-1 & -1 & 1 & 1
\end{bmatrix}
$$


# 6 (2.11)
**A design matrix for a polynomial regression problem with only three design points takes the form**

$$
X = 
\begin{bmatrix}
	1 & -1 & 1 & -1 \\
	1 & 0 & 0 & 0 \\
	1 & 0 & 0 & 0 \\
	1 & 1 & 1 & 1 \\
	1 & 1 & 1 & 1
\end{bmatrix}
$$


## a
**What is the rank of $X$?**

There are 3 linearly independent rows and columns of $X$, so $\text{rank}( X ) = 3$.


## b
**What is the dimension of $\mathcal{C}(X)$ and a nonzero vector in it.**

The dimension of the column space of $X = \text{rank}( X ) = 3$. One vector in it is

$$
v = c_1
\begin{bmatrix}
	1 \\
	1 \\
	1 \\
	1 \\
	1
\end{bmatrix}
$$


## c
**What is the dimension of $\mathcal{N}(X)$ and a nonzero vector in it.**

$$
	\begin{align}
		dim(X) & = \text{rank}( X ) + dim(\mathcal N (X))  \\
		4 & = 3 + dim(\mathcal N (X))  \\
		dim(\mathcal N (X)) & = 1
	\end{align}
$$


One nonzero vector in is it:

$$
v = 
\begin{bmatrix}
	0 \\
	1 \\
	0 \\
	-1
\end{bmatrix}

\rightarrow

X v = 
\begin{bmatrix}
	0 + -1 \cdot 1 + 0 + -1 \cdot 1 \\
	0 \cdot 1+ 0 \\
	0 \cdot 1 + 0 \\
	0 \cdot 1 + 1 \cdot 1 + 0 \cdot 1 + 1 \cdot -1 \\
	0 \cdot 1 + 1 \cdot 1 + 0 \cdot 1 + 1 \cdot -1 
\end{bmatrix} = 
0
$$

## d
**Give the dimension of $\mathcal{ C }(X^T)$ and a nonzero vector in it.**

$\mathcal C (X^T) = \mathcal R(X) = 3$.

$$
v = r_1 = 
\begin{bmatrix}
	1 \\
	-1 \\
	1 \\
	-1
\end{bmatrix}
$$

## e
**Compute $X^T X$ and find a generalized inverse for it. (No need to check $AGA=A$).**

$$
X^T X = 
\begin{bmatrix}
	1 & 1 & 1 & 1 & 1\\
	-1 & 0 & 0 & 1 & 1 \\
	1 & 0 & 0 & 0 & 0 \\
	-1 & 0 & 0 & 1 & 1
\end{bmatrix}

\begin{bmatrix}
	1 & -1 & 1 & 1 \\
	1 & 0 & 0 & 0 \\
	1 & 0 & 0 & 0 \\
	1 & 1 & 1 & 1 \\
	1 & 1 & 1 & 1
\end{bmatrix} = 

\begin{bmatrix}
	5 & 1 & 3 & 1 \\
	1 & 3 & 1 & 3 \\
	1 & -1 & 1 & -1 \\
	1 & 3 & 1 & 3
\end{bmatrix}
$$
 
 
 We can use R to caculate the SVD and the Moore-Penrose generalized inverse.
 
 ```
 svd(X)
 $d
[1] 2.940034e+00 2.130947e+00 9.029217e-01 4.950053e-17

$u
          [,1]       [,2]        [,3]          [,4]
[1,] 0.6342573 -0.5271852 -0.56550283  8.681328e-18
[2,] 0.4242986  0.5634958 -0.04942893 -7.071068e-01
[3,] 0.4875030 -0.2949928  0.82177862  1.110223e-16
[4,] 0.4242986  0.5634958 -0.04942893  7.071068e-01

$v
           [,1]       [,2]       [,3]          [,4]
[1,] 0.09291154 -0.9146966  0.3933161  1.896487e-17
[2,] 0.21573128 -0.2473949 -0.6263033  7.071068e-01
[3,] 0.21573128 -0.2473949 -0.6263033 -7.071068e-01
[4,] 0.67018187  0.1430414  0.1743428 -1.051618e-16
[5,] 0.67018187  0.1430414  0.1743428 -1.051618e-16

library(MASS)
X_ginv = ginv(X)

 ```
 
 This gives
 
 $$
 A^+ = 
 \begin{bmatrix}
	0 & -0.25 & 0.5 & -0.25 \\
	0.5 & 0 & -0.5 & 0 \\
	0.5 & 0 & -0.5 & 0 \\
	0 & 0.125 & 0.25 & 0.125 \\
	0 & 0.125 & 0.25 & 0.125
\end{bmatrix}.
 $$
 
 Now we can check that this meets all of the requirements to be Moore-Penrose inverse.
 
$$
X X^+ X
$$
 
 ```
round(X %*% X_ginv %*% X, 3)
1	1   1	1   1
-1	0   0   1   1
1	0	0   1   1
-1	0	0   1	1
```

This is equal to $X$, so the first condition is met.


$$
X^+ X X^+
$$


```
round(X_ginv %*% X %*% X_ginv, 3)
0.0 -0.250  0.50 -0.250
0.5  0.000 -0.50  0.000
0.5  0.000 -0.50  0.000
0.0  0.125  0.25  0.125
0.0  0.125  0.25  0.125
```

This is equal to $X^+$, so the second condition is met.

Now we need to check that $X^+X$ and $X X^+$ are symmetric.

```
> round(X_ginv %*% X)
1	0   0	0   0
0   1   1   0   0
0   1   1   0   0
0   0   0   1   1
0   0	0   1	1

> round(t(X_ginv %*% X))
1    0    0    0    0
0    1    1    0    0
0    1    1    0    0
0    0    0    1    1
0    0    0    1    1

> round(X %*% X_ginv)
     [,1] [,2] [,3] [,4]
[1,]    1    0    0    0
[2,]    0    1    0    1
[3,]    0    0    1    0
[4,]    0    1    0    1
> round(t(X %*% X_ginv))
     [,1] [,2] [,3] [,4]
[1,]    1    0    0    0
[2,]    0    1    0    1
[3,]    0    0    1    0
[4,]    0    1    0    1
```
 
 These are indeed symmetric, so $X^+$ is the Moore-Penrose inverse of $X$.
 
## f
**Which of the following vectors could be $P_X y$ for an appropriate vector $y$?**

$$
\begin{bmatrix}
	3 \\
	1 \\
	1\\
	2\\ 
	2
\end{bmatrix}

\begin{bmatrix}
	1 \\
	-1 \\
	1\\
	-1\\ 
	1
\end{bmatrix}

\begin{bmatrix}
	1 \\
	0 \\
	0\\
	2\\ 
	2
\end{bmatrix}
$$

$$
\begin{bmatrix}
	3 \\
	1 \\
	1\\
	2\\ 
	2
\end{bmatrix}
$$

is an appropriate vector because it is in the column space of $X$. It is $c_1 + \frac{ 3 }{ 2 }c_3 - \frac{ 1 }{ 2 } c_2$.

## g
**Using the right-hand side you gave above in (f), find all solutions to the equations $Xb = P_X y$.**

$$
	\begin{align}
		Xb & = P_X y \\
		\begin{bmatrix}
			b_1 - b_2 + b_3 - b_4 \\
			b_1 \\
			b_1 \\
			b_1 + b_2 + b_3 + b_4 \\
			b_1 + b_2 + b_3 + b_4
		\end{bmatrix}
		
		& = \begin{bmatrix}
			3 \\
			1 \\
			1\\
			2\\ 
			2
		\end{bmatrix}
	\end{align}
$$

Then $b_1 = 1$ and take $b_2 = x$. Then,

$$
	\begin{align}
		b_1 - b_2 + b_3 - b_4 & = 3 \\
		1 - x + b_3 - b_4 & = 3 \\
		b_3 & = 2 + x + b_4 \\ \\
		b_1 + b_2 + b_3 + b_4 & = 2 \\
		1 + x + 2 + x + b_4 + b_4 & = 2 \\
		b_4 & = -1/2 -x \\
		b_3 & = 3/2 
	\end{align}
$$

## h
**Which of the following had the same column space as $X$?**

$$
U = 
\begin{bmatrix}
	1 & 0 & 0 \\
	0 & 1 & 0 \\
	0 & 1 & 0 \\
	0 & 0 & 1 \\
	0 & 0 & 1 \\
\end{bmatrix}

W = 
\begin{bmatrix}
	1 & 1 & 0 \\
	1 & 0 & 1 \\
	1 & 1 & 1 \\
	1 & 1 & 0 \\
	1 & 0 & 1 \\
\end{bmatrix}
$$

$U$ has the same column space as $X$. It's columns are linear combinations of columns in $X$.

$$
\frac{ 1 }{ 2 } (c_3 -  c_3) = \frac{ 1 }{ 2 } 
\begin{bmatrix}
	1 \\
	0 \\
	0 \\
	1 \\
	1
\end{bmatrix}
- \frac{ 1 }{ 2 } 
\begin{bmatrix}
	-1 \\
	0 \\
	0 \\
	1 \\
	1
\end{bmatrix} = 
\begin{bmatrix}
	1 \\
	0 \\
	0 \\
	0 \\
	0
\end{bmatrix} 
= u_1
$$


$$
c_1 - c_3  = 
\begin{bmatrix}
	1 \\
	1 \\
	1 \\
	1 \\
	1
\end{bmatrix}
- \begin{bmatrix}
	1 \\
	0 \\
	0 \\
	1 \\
	1
\end{bmatrix} =
\begin{bmatrix}
	0 \\
	1 \\
	1 \\
	0 \\
	0
\end{bmatrix}
= u_2
$$

$$
\frac{ 1 }{ 2 }(c_2 + c_3) = 
\frac{ 1 }{ 2 }
\begin{bmatrix}
	-1 \\
	0 \\
	0 \\
	1 \\
	1
\end{bmatrix} 
+ \frac{ 1 }{ 2 }
\begin{bmatrix}
	1 \\
	0 \\
	0 \\
	1 \\
	1 
\end{bmatrix} =
\begin{bmatrix}
	0 \\
	0 \\
	0 \\
	1 \\
	1
\end{bmatrix}
= u_3
$$

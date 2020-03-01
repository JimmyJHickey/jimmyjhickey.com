---
layout: post
comments: false
title: Example Problems on the Restricted Normal Equations
description: ST705 Homework 7 on the Restricted Normal Equations
tags: ST705 Linear-Algebra Restricted-Normal-Equations Statistics
category: ST705
---

* Do not remove this line (it will not be displayed)
{:toc}




# 1 (3.20)
**Consider the general unbalanced one-way ANOVA model with the (usual) (nonestimable) constraint $\sum_i n_i \alpha_i =0$. Write the constraint $Cb = 0$ as $C=(0, d^T)$ where $d_i = n_i, \ i=1 , \dots , a$. Show that**

$$
\Big( X^T X + C^T C \Big)^{-1} = 
\begin{bmatrix}
	\frac{ N + 1 }{ N^2 } & -\frac{ 1 }{ N^2 } 1_a^T \\
	-\frac{ 1 }{ N^2 }1_a & D^{-1} - \frac{ N-1 }{ N^2 }1_a 1_a^T
\end{bmatrix}
$$


**where $D = diag(n_i)$. Also find the solution to the normal equations using this result and show that it satisfies the constraint.**


Call the right had side matrix $R$. Let's write out some of the matrices that we know.

$$
	\begin{align}
		X^T X & = 
			\begin{bmatrix}
				N & n_1 & n_2 & \dots & n_a \\
				n_1 & n_1 & 0 & \dots & n_a \\
				\vdots & 0 & \ddots & & \vdots \\
				\vdots & & & \ddots & \vdots \\
				n_a& \dots & & & n_a
			\end{bmatrix} \\
		C^T C & = 
			\begin{bmatrix}
				0 & \dots & \dots &\dots  & 0\\
				\vdots & n_1^2 & n_1 n_2 & \dots & n_1 n_a\\
				\vdots & n_1 n_2 & n_2^2 &  \dots & n_2 n_a\\
				\vdots & & & \ddots &  \\
				0 & & & & n_a^2
			\end{bmatrix} \\
		X^T X + C^T C & = 
			\begin{bmatrix}
				N & n_1 & \dots & & n_a \\
				n_1 & n_1 + n_1^2 & n_1 n_2 & \dots \\
				\vdots  & n_1 n_2 & n_2 + n_2 ^2 & \dots \\
				& & & \ddots \\
				n_a & & & & n_a + n_a^2	
			\end{bmatrix}
	\end{align}
$$


Now let's look at a few elements of $R(X^T X + C^T C)$ to see that it's $I$. The (1, 1) element looks like,

$$
\frac{ N+1 }{ N^2 } N + \frac{ -1 }{ N^2 } n_1 + \frac{ -1 }{  N^2} n_2 = \frac{ N+1 }{ N} - \frac{ 1 }{ N^2 } \sum n_i = \frac{ N+1 }{ N } - \frac{ 1 }{ N } = 1.
$$


The (1,2) element (and all of the rest of the first row) looks like

$$
\frac{ N+1 }{ N^2 } n_1 - \frac{ 1 }{ N^2 }(n_1 + n_1 n_1) - \frac{ 1 }{ N^2 } n_1 n_2 - \dots = \frac{ N n_1 + n_1 }{ N^2 } - \frac{ n_1 }{ N^2 } - \frac{ n_1 }{ N^2 } \sum n_i = \frac{ N n_1 }{ N^2 } - \frac{ N n_1 }{ N^2 } = 0
$$


The other off diagonal elements look like (2,1).

$$
\frac{ -N }{ N^2 } + n_1( \frac{ 1 }{ n_1 } - \frac{ N-1 }{ N^2 }) + n_2 (-\frac{ N - 1 }{ N^2 }) + \dots = \frac{ -1 }{ N } + \frac{ n_1 }{ n_1 } - \frac{ N - 1 }{ N^2 } \sum n_i = \frac{ -1 }{ N } + 1 - \frac{ N-1 }{ N } = 0
$$


The rest of the diagonal elements look like (2,2).

$$
	\begin{align}
		(2,2) & = - \frac{ n_1 }{ N^2 } + (\frac{ 1 }{ n_1 } - \frac{ N-1 }{ N })(n_1 + n_1^2) + (-\frac{ N-1 }{ N^2 }) n_1 n_2 + (-\frac{ N-1 }{ N^2 }) n_1 n_2 + \dots \\
			& = - \frac{ n_1 }{ N^2 } + \frac{ n_1 + n_1^2 }{ n_1 } - \frac{ (n_1 + n_1^2)(N-1) }{ N^2 } + \frac{ -(N-1) n_1 }{ N^2 } \sum_{i \neq 1} n_i \\
			& = - \frac{ n_1 }{ N^2 } + 1 + n_1 - \frac{ (n_1 + n_1^2)(N-1) }{ N^2 } + \frac{ -(N-1) n_1 ( N - n_1) }{ N^2 } \\
			& = - \frac{ n_1 }{ N^2 } + 1 + n_1 - \frac{ n_1 N + n_1^2 N - n_1 - n_1^2 }{ N^2 } - \frac{ N^2 n_1 - N n_1^2 - N n_1 + n_1^2 }{ N^2 } \\
			& = -\frac{ n_1 }{ N } + 1 + n_1 - \frac{ n_1 N }{ N^2 } - \frac{ n_1^2 N }{ N^2 } + \frac{ n_1 }{ N^2 } + \frac{ n_1^2 }{ N^2 } - \frac{ N^2 n_1 }{ N^2 } + \frac{ N n_1^2 }{ N^2}  + \frac{ N n_1 }{N^2  } - \frac{ n_1^2 }{ N^2 } \\
			& = 1
	\end{align}
$$

The remaning diagonals and off diagonals will follow the same pattern as in the examples. This is the identity matrix.


We can see that both $(X^T X + C^T C)$ and $R$ are symmetric, so 

$$
I = R(X^T X + C^T C) = (R(X^T X + C^T C))^T = (X^T X + C^T C)^T R^T = (X^T X + C^T C) R
$$

Thus, $R$ is both a left and right inverse, so it is the inverse.


The solutions of the normal equations take the form

$$
	\begin{align}
		(X^T X + C^T C) b & = X^T y \\
		b & = R X^T y.
	\end{align}
$$



# 2 (3.24)
**Consider the general balanced cross-classified model from Section 3.5, $y_{ij} = \mu + \alpha_i + \beta_j + e_{ij}$, and partition the design matrix as below**

$$
X b = 
\begin{bmatrix}
	1_b & 1_b & 0 & \dots & 0 & I_b \\
	1_b &0 & 1_b & \dots & 0 & I_b \\
	\vdots & \vdots & \vdots & \vdots & \vdots & \vdots \\
	1_b & 0 & 0 & \dots & 0 & I_b \\
	1_b & 0 & 0 & \dots  & 1_b & I_b
\end{bmatrix}
\begin{bmatrix}
	\mu \\
	\alpha_1 \\
	\alpha_2 \\
	\vdots \\
	\alpha_a \\
	\beta_1 \\
	\beta_2 \\
	\vdots \\
	\beta_b
\end{bmatrix} = 
\begin{bmatrix}
	1_{ab} &  X_A & X_B
\end{bmatrix}
\begin{bmatrix}
	\mu \\
	\alpha^T s \\
	\beta^T s
\end{bmatrix}
$$

## a
**Show $P_{X_A} X_B = P_1 X_B$.**

We can expand the left hand side.

$$
	\begin{align}
		P_{X_A} X_B & = X_A (X_A^T X_A)^g X_A^T X_B \\ \\
		(X_A^T X_A)^{-1} & = 
			\begin{bmatrix}
				b & 0 & \dots & 0 \\
				0 & b &  &  \\
				\vdots  & & \ddots & \\
				0 &&& b\\
			\end{bmatrix} \\
			& = \frac{ 1 }{ b } I_{a} \\ \\
		\frac{ 1 }{ b }X_A X_A^T & = \frac{ 1 }{ b }
			\begin{bmatrix}
				1_b 1_b^T & 0 & \dots & 0 \\
				0 & 1_b 1_b^T & & \\
				& & \ddots & \\
				0 & & & 1_b 1_b^T
			\end{bmatrix} \\ \\
		\frac{ 1 }{ b }X_A X_A^T X_B & = \frac{ 1 }{ b }
			\begin{bmatrix}
				1_{ab} & 1_{ab} & \dots & 1_{ab}
			\end{bmatrix}
	\end{align}
$$

Notice that

$$
\begin{bmatrix} 1_{ab} & 1_{ab} & \dots & 1_{ab} \end{bmatrix} \in \mathbb{R}^{ab \times b}.
$$


We can expand the right hand side as well. Notice that $P_1 \in \mathbb{R}^{ab \times ab}$ and $X_B \in \mathbb{R}^{ab \times b}$.

$$
	\begin{align}
		P_1 X_B & = \frac{ 1 }{ ab } 
			\begin{bmatrix}
				1_{ab} & 1_{ab} & \dots & 1_{ab}
			\end{bmatrix}
			\begin{bmatrix}
				I_b \\
				I_b \\
				\vdots \\
				I_b
			\end{bmatrix}\\
			& = \frac{ a }{ ab } 
			\begin{bmatrix}
				1_{ab} & 1_{ab} & \dots & 1_{ab}
			\end{bmatrix} \\
			& = P_{X_A} X_B
	\end{align}
$$



## b
**Show that $P_{X_A} P_{X_B} = P_{1_{ab}}$.**

From above we know

$$
	\begin{align}
		P_{X_A} X_B & = P_1 X_B \\
		P_{X_A} X_B (X_B^T X_B)^g X_B^T & = P_1 X_B (X_B^T X_B)^g X_B^T \\
		P_{X_A} P_{X_B} & = P_1 X_B (X_B^T X_B)^g X_B^T \\
			& = \frac{1}{b} 
				\begin{bmatrix} 1_{ab} & 1_{ab} & \dots & 1_{ab} \end{bmatrix} (X_B^T X_B)^g X_B^T
	\end{align}
$$

Notice that $(X_B^T X_B)^g = (X_B^T X_B)^{-1} = \frac{ 1 }{ a }I_b$. Also notice that $X_B^T$ only has one $1$ in each column.

$$
	\begin{align}
		P_{X_A} P_{X_B} & = \frac{1}{b} 
				\begin{bmatrix} 1_{ab} & 1_{ab} & \dots & 1_{ab} \end{bmatrix} \frac{ 1 }{ a } X_B^T \\
				& = \frac{ 1 }{ ab } \begin{bmatrix} 1_{ab} & 1_{ab} & \dots & 1_{ab} \end{bmatrix} X_B^T \\
				& = \frac{ 1 }{ ab } 1_{ab} 1_{ab}^T \\
				& = 1_{ab} (1_{ab}^T 1_{ab})^-1 1_{ab}^T \\
				& = P_{1_{ab}}
	\end{align}
$$


## c
**Show that $P_X - P_{X_A} = P_{X_B} - P_1$**

Since $\text{ column }( X_A ) \subset \text{ column }( X )$ and $\text{ column }( 1 ) \subset \text{ column }( X_B )$, by theorem 2.2 we know that $P_X - P_{X_A}$ projects onto $\text{ column }( (I-P_{X_A})X )$ and that $P_{X_B} - P_1$ projects onto $\text{ column }( (I-P_1) X_B)$. Notice

$$
	\begin{align}
		(I-P_1) X_B & = X_B - P_1 X_B \\
			& = X_B - P_{X_A} X_B \\
			& = (I - P_{X_A})X_B
	\end{align}
$$

by part (a). These matrices project everything onto everything that is in the column spaces of $X$ and $X_B$, but not in the column space of $X_A$ respectively. Recall that 

$$X = \begin{bmatrix} 1_{ab} &  X_A & X_B \end{bmatrix}.$$

Since $1_{ab}$ is in the column space of $X_A$ (it can be made by adding all of the columns of $X_A$), these column spaces are going to be the same. And since projection matrices are unique,


$$
P_X - P_{X_A} = P_{X_B} - P_1.
$$

# 3 (3.26)
**Prove the result: let 
$\begin{bmatrix}
\hat{b}_H \\
\hat \theta_H
\end{bmatrix}^T$ 
and
$\begin{bmatrix}
	\widetilde b _H\\
	\widetilde \theta _H
\end{bmatrix}^T$ be two solutions to the RNE (3.10), then**

## a
**$X \hat b_H = X \widetilde b_H$, and**

Since $\hat b_H$ and $\widetilde b_H$ are both solutions to the RNE, they both minimize $Q(\beta)$ over $\beta \in \{ P^T \beta = \delta \}$. So,

$$
Q(\widetilde  b) = Q(\hat b_H) + || X(\hat b_H - \widetilde b_H) ||^2.
$$


By result 3.10, we know that $Q(\hat b_H) = Q(\widetilde b_H)$. So,

$$
|| X(\hat b_H - \widetilde b_H) ||^2 = 0.
$$

Thus, $\widehat b_H = \widetilde b_H$.


## b
**if $\lambda^T b$ is estimable in the restricted model, then $\lambda^T \hat b_H = \lambda^T \widetilde b_H$.**

Since $\lambda^T b$ is estimable, we know that

$$
\lambda  = X^T a + Pd.
$$

$$
	\begin{align}
		\lambda^T \widehat b_H & = (a^T X + d^T P^T) \widehat  b_H \\
			& = a^T X \widehat b_H + d^T P^T \widehat b_H \\
			& = a^T X \widetilde b_H + d^T \delta & (a)\\
			& = a^T X \widetilde b_H + d^T P^T \widetilde b_H \\
			& = (a^T X + d^T P^T) \widetilde  b_H \\
			& = \lambda^T \widetilde b_H
	\end{align}
$$


# 4
**Let $X$ be an $n\times p$ matrix with rank$(X) = r$, and let $C$ be a $(p-r)\times p$ matrix with**


* (i) rank$(C) = p-r$ and
* (ii) $\text{column}(X') \cap \text{column}(C') = \{0\}$.


**Show that $C(X'X + C'C)^{-1}C' = I_{p-r}$.**


Take

$$
z = 
\begin{bmatrix}
	X \\
	C
\end{bmatrix}.
$$

Notice that $P_Z z = z$. Then,

$$
	\begin{align}
		P_Z & = 
		\begin{bmatrix}
			X \\
			C
		\end{bmatrix} (X^T X + C^T C)^{-1}(X^T C^T) \\
		& = 
		\begin{bmatrix}
	X(X^TX + C^T C)^{-1} X^T & 0 \\
	0 & C (X^T X + C^T C)^{-1}C^T
\end{bmatrix}
	\end{align}
$$

Then,

$$
P_Z z =
\begin{bmatrix}
	X \\
	C (X^T X + C^T C)^{-1}C^T C
\end{bmatrix} =
\begin{bmatrix}
	X \\
	C
\end{bmatrix}.
$$

The last equation gives us

$$
0 = \Big[I -  C (X^T X + C^T C)^{-1}C^T \Big] C.
$$

Since we know that $C$ has full row rank, we know that $C \neq 0$. Thus,

$$
I -  C (X^T X + C^T C)^{-1}C^T  = 0 \rightarrow I =  C (X^T X + C^T C)^{-1}C^T 
$$


# 5
**Maximize the function $f(x) := \sum_{i=1}^{k}n_{i}\log(x_{i})$ subject to the constraints**

$$
\begin{align}
 \sum_{i=1}^{k}x_{i} = 1,\\
 x_{i} \ge 0,
\end{align}
$$

**with $\{n_{i}\}$ a set of fixed scalars.**

First let's re-write the constraint as $\sum x_i - 1 = 0$. Now we can use a Lagrange multiplier.

$$
	\begin{align}
		L(x, \lambda) & = \sum n_i \log(x_i) + \lambda (\sum x_i - 1) \\
		\frac{ \partial L }{ \partial \lambda } & = \sum x_i - 1 = 0\\
		\frac{ \partial L }{ \partial x_i } & = \frac{ n_i }{ x_i } + \lambda = 0 \\
		\Rightarrow \\
		x_i & = \frac{ n_i }{ -\lambda } \\
		\sum x_i & = 1 = \sum \frac{ n_i }{ -\lambda } \\
		-\lambda & = \sum n_i \\
		x_i & = \frac{ n_i }{ \sum n_i }
	\end{align}
$$


# 6 (4.1)
**Suppose that the random variable $Y_i$ represents the number of votes that a candidate receives in county $i$. A reasonable model would be that $Y_i, \ i = 1, \dots , N$ would be independent binomial random variables with parameters $n_i=$ number of voters in count $i$ and**

$$
p = Pr(\text{voter that correctly votes for candidate}).
$$

## a
**Write $E(Y_i)$ and $Var(Y_i)$.**

Since each $Y_i \sim Binom(n_i, p)$, we know that

$$
\mathbb E(Y_i) = n_i p \ V(Y_i) = n_i p (1-p)
$$


## b
**Write this as a linear model.**

We know that we want $E(Y_i) = X p$ and $V(Y_i) = n_i p(1-p)$. So we can build the following model,

$$
\begin{bmatrix}
	Y_1 \\ 
	\vdots \\
	Y_N
\end{bmatrix} = 
\begin{bmatrix}
	n_1 \\
	\vdots \\
	n_N
\end{bmatrix}
p + 
\begin{bmatrix}
	\sqrt{ n_1 p (1-p)} & 0 & \dots &  & 0 \\
	0 & \ddots & 0 & \dots & 0 \\
	\vdots & & \ddots & \\
	0 & \dots & & & \sqrt{ n_N p (1-p) }
\end{bmatrix}
\begin{bmatrix}
	e_1 \\ 
	\vdots \\
	e_N
\end{bmatrix}
$$

## c
**Find the BLUE of $p$ in this situation.**

If we look at our model from part (b) we will notice that our errors have mean 0 and are uncorrelated; however, they are not equal. So, we will need to rescale our model before getting the BLUE.

$$
	\begin{align}
		\widetilde Y & = \begin{bmatrix}
							\frac{ 1 }{ n_1 } & 0 & \dots & 0 \\
							0 & \frac{ 1 }{ n_2 } & 0 \cdots & \vdots \\
							0 & \dots & \ddots &  \\
							0 & \dots &  & \frac{ 1 }{ n_N }
						\end{bmatrix} 
						\begin{bmatrix}
							n_1 \\
							\vdots \\
							n_N
						\end{bmatrix}
						p + 
						\sqrt{ p (1-p) }
						\begin{bmatrix}
							e_1 \\ 
							\vdots \\
							e_N
						\end{bmatrix} \\
					& = \begin{bmatrix}
							1 \\
							\vdots \\
							1
						\end{bmatrix}
						p + 
						\sqrt{ p (1-p) }
						\begin{bmatrix}
							e_1 \\ 
							\vdots \\
							e_N
						\end{bmatrix}
	\end{align}
$$

Where 

$$
\widetilde Y = 
\begin{bmatrix}
	1/\sqrt{ n_1 }Y_1 \\
	\vdots \\
	1/\sqrt{N} Y_N
\end{bmatrix}.
$$


Now we have satisfied the last Gauss-Markov assumption, equal variances. Thus, our least squares estimator will be our BLUE.

$$
	\begin{align}
		\lambda^T \widehat p & = \widehat p \\
			& = \frac{ 1 }{ N } \sum_{i=1}^n \frac{ 1 }{ n_1 } y_i.
	\end{align}
$$

# 7 (4.2)
**Under that Gauss-Markov model, show that for $\lambda$ such that $\lambda^T b$ is estimable, $Var(\lambda^T b) = \sigma^2 \lambda^T (X^T X)^g \lambda$ does not depend on the choice of generalized inverse $(X^T X)^g$.**


Since $\lambda^T b$ is estimable, we can write $\lambda^T = a^T X$. 

$$
	\begin{align}
		V(\lambda^T b) & = \sigma^2 \lambda^T (X^T X)^g \lambda \\
			& = \sigma^2 a^T X (X^T X)^g X^T a \\
			& = \sigma^2 a^T P_X a
	\end{align}
$$

Since we have already shown that $P_X$ is invariant under the choice of generalized inverse, we can say that $V(\lambda^T b)$ is as well.
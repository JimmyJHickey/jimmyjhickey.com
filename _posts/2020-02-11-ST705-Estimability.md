---
layout: post
comments: false
title: Example Problems on Estimability
description: ST705 Homework 6 on Estimability
tags: ST705 Estimability Statistics
category: ST705
---


* Do not remove this line (it will not be displayed)
{:toc}

# 1
**Consider the following design matric for ANACOVA with two groups and one covariate.**


$$
y_{ij} = \mu + \alpha_i + \beta x_{ij} + e_{ij} \text{ where } \mathbf X =
\begin{bmatrix}
	1 & 1 & 0 & 1 \\
	1 & 1 & 0 & 2 \\
	1 & 1 & 0 & 3 \\
	1 & 1 & 0 & 4 \\
	1 & 0 & 1 & 1 \\
	1 & 0 & 1 & 2 \\
	1 & 0 & 1 & 3 \\
	1 & 0 & 1 & 4
\end{bmatrix}
\text{ and }
\mathbf b =
\begin{bmatrix}
	\mu \\
	\alpha_1 \\
	\alpha_2 \\
	\beta
\end{bmatrix}
$$

**so that $n_1 = 4$, $n_2 = 4$.**


## a
**What is the rank of $\mathbf X$?**

There are 3 linearly independent columns in $X$, so its rank is 3.



## b
**Find a generalized inverse of $X^T X$ and call it $G$.**

Need to find $G$ such that

$$
X^T X G X^T X = X^T X.
$$

Where,

$$
X^T X = 
\left(
\begin{array}{cccc}
 8 & 4 & 4 & 20 \\
 4 & 4 & 0 & 10 \\
 4 & 0 & 4 & 10 \\
 20 & 10 & 10 & 60 \\
\end{array}
\right).
$$


Then,

$$
G = 
\left(
\begin{array}{cccc}
 \frac{1}{3} & \frac{1}{6} & \frac{1}{6} & -\frac{1}{6} \\
 \frac{1}{6} & \frac{5}{24} & -\frac{1}{24} & -\frac{1}{12} \\
 \frac{1}{6} & -\frac{1}{24} & \frac{5}{24} & -\frac{1}{12} \\
 -\frac{1}{6} & -\frac{1}{12} & -\frac{1}{12} & \frac{1}{10} \\
\end{array}
\right).
$$

## c
**Compute $H = G X^T X$ and recall $H^T$ is a projection onto $\text{ column }( X^T ) = \text{ column }( X^T X )$.**

$$
H = (X^TX)^g X^T X = 
\left(
\begin{array}{cccc}
 \frac{1}{3} & \frac{1}{6} & \frac{1}{6} & -\frac{1}{6} \\
 \frac{1}{6} & \frac{5}{24} & -\frac{1}{24} & -\frac{1}{12} \\
 \frac{1}{6} & -\frac{1}{24} & \frac{5}{24} & -\frac{1}{12} \\
 -\frac{1}{6} & -\frac{1}{12} & -\frac{1}{12} & \frac{1}{10} \\
\end{array}
\right)
\left(
\begin{array}{cccc}
 8 & 4 & 4 & 20 \\
 4 & 4 & 0 & 10 \\
 4 & 0 & 4 & 10 \\
 20 & 10 & 10 & 60 \\
\end{array}
\right) =
\left(
\begin{array}{cccc}
 \frac{2}{3} & \frac{1}{3} & \frac{1}{3} & 0 \\
 \frac{1}{3} & \frac{2}{3} & -\frac{1}{3} & 0 \\
 \frac{1}{3} & -\frac{1}{3} & \frac{2}{3} & 0 \\
 0 & 0 & 0 & 1 \\
\end{array}
\right) = H^T
$$




## d
**Compute $(I - H)$ and recall that it is a projection onto $\mathcal N (X) = \mathcal N(X^T X)$.**


$$
I - H = \left(
\begin{array}{cccc}
 1 & 0 & 0 & 0 \\
 0 & 1 & 0 & 0 \\
 0 & 0 & 1 & 0 \\
 0 & 0 & 0 & 1 \\
\end{array}
\right) - 
\left(
\begin{array}{cccc}
 \frac{2}{3} & \frac{1}{3} & \frac{1}{3} & 0 \\
 \frac{1}{3} & \frac{2}{3} & -\frac{1}{3} & 0 \\
 \frac{1}{3} & -\frac{1}{3} & \frac{2}{3} & 0 \\
 0 & 0 & 0 & 1 \\
\end{array}
\right) =
\left(
\begin{array}{cccc}
 \frac{1}{3} & -\frac{1}{3} & -\frac{1}{3} & 0 \\
 -\frac{1}{3} & \frac{1}{3} & \frac{1}{3} & 0 \\
 -\frac{1}{3} & \frac{1}{3} & \frac{1}{3} & 0 \\
 0 & 0 & 0 & 0 \\
\end{array}
\right)
$$



## e
**Find a basis for $\mathcal C (X^T)$.**

Take columns $h_2, h_2, h_4$ of $H$ since it projects onto $\text{ column }( X^T )$. Notice that there are 3 vectors and  $\text{rank}( \mathcal C (X^T) ) = 3$.

## f
**Find a basis for $\mathcal N (X)$.**

By the rank nullity theorem there should only be one vector in this basis. Take it to be $(I-H)_1$ since $I-H$ forms a basis for $\mathcal N(X)$.

## g
**Compute $P_X$ and its trace.**

$$
P_X = X G X^T = \left(
\begin{array}{cccc}
 1 & 1 & 0 & 1 \\
 1 & 1 & 0 & 2 \\
 1 & 1 & 0 & 3 \\
 1 & 1 & 0 & 4 \\
 1 & 0 & 1 & 1 \\
 1 & 0 & 1 & 2 \\
 1 & 0 & 1 & 3 \\
 1 & 0 & 1 & 4 \\
\end{array}
\right) \left(
\begin{array}{cccc}
 \frac{1}{3} & \frac{1}{6} & \frac{1}{6} & -\frac{1}{6} \\
 \frac{1}{6} & \frac{5}{24} & -\frac{1}{24} & -\frac{1}{12} \\
 \frac{1}{6} & -\frac{1}{24} & \frac{5}{24} & -\frac{1}{12} \\
 -\frac{1}{6} & -\frac{1}{12} & -\frac{1}{12} & \frac{1}{10} \\
\end{array}
\right)
\left(
\begin{array}{cccccccc}
 1 & 1 & 1 & 1 & 1 & 1 & 1 & 1 \\
 1 & 1 & 1 & 1 & 0 & 0 & 0 & 0 \\
 0 & 0 & 0 & 0 & 1 & 1 & 1 & 1 \\
 1 & 2 & 3 & 4 & 1 & 2 & 3 & 4 \\
\end{array}
\right)
=
\frac{ 1 }{ 40 }

\left(
\begin{array}{cccccccc}
 19 & 13 & 7 & 1 & 9 & 3 & -3 & -9 \\
 13 & 11 & 9 & 7 & 3 & 1 & -1 & -3 \\
 7 & 9 & 11 & 13 & -3 & -1 & 1 & 3 \\
 1 & 7 & 13 & 19 & -9 & -3 & 3 & 9 \\
 9 & 3 & -3 & -9 & 19 & 13 & 7 & 1 \\
 3 & 1 & -1 & -3 & 13 & 11 & 9 & 7 \\
 -3 & -1 & 1 & 3 & 7 & 9 & 11 & 13 \\
 -9 & -3 & 3 & 9 & 1 & 7 & 13 & 19 \\
\end{array}
\right)
$$

# 2
**Consider the model $Y_{ijk} = \mu + \alpha_{i} + \beta_{j} + \theta_{ij} + U_{ijk}$, with $k \in \{1,\dots,m_{ij}\}$, $i \in \{1,\dots,n\}$, $j \in \{1,\dots,m\}$, and $E(U_{ijk}) = 0$.  Find necessary and sufficient conditions for which $\lambda'\gamma$ is estimable for**

$$
\gamma =
\begin{pmatrix}
\mu & \alpha_{1} & \cdots & \alpha_{n} & \beta_{1} & \cdots & \beta_{m} & \theta_{11} & \cdots & \theta_{nm} \\
\end{pmatrix}'.
$$


For some intuition, let's look at the example in the book before generalizing. Here they take $n=2$ and $m=3$. This is what their design matrix looks like.

$$
\begin{bmatrix}
1 & 1 & 0 & 1 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0\\
1 & 1 & 0 & 0 & 1 & 0 & 0 & 1 & 0 & 0 & 0 & 0\\
1 & 1 & 0 & 0 & 0 & 1 & 0 & 0 & 1 & 0 & 0 & 0\\
1 & 0 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0\\
1 & 0 & 1 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 1 & 0\\
1 & 0 & 1 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 1
\end{bmatrix}
$$

Notice that the first column is all 1s for the intercept. Then next 2 ($n$) columns are indicators for which $\alpha$ group the observation belongs. The next 3 ($m$) columns are indicators for which $\beta$ group the observation belongs. Finally, we have the last 6 ($mn$) columns which are indicators for the mixed term depending on which $\alpha$ and $\beta$ group the data belongs. The rank of this matrix is 6 which can be seen most quickly by looking at the last 6 columns and noticing that they are the standard basis vectors. Notice that if we add more rows, they will be replicates of rows we already have and thus will not add to the rank. So, we can consider the case where each class has 1 replicate without loss of generality. 


Our estimable functions live in the row space of $X$ (the column space of $X^T$). If we look at the entries each has a $\mu$, an $\alpha_i$, a $\beta_j$, and a $\theta_{ij}$ term. So we can estimate parameters, $\lambda^T \beta$, of the form $\mu + \alpha_i + \beta_j + \theta_{ij}$ and linear combinations of them.


Alternatively, can also try this going through the null space. The null space of our $2 \times 3$ example should have 

$$
\dim(\mathcal N(X))= \dim(X)- \text{rank}( \mathcal C(X) ) = 12 - 6 = 6
$$

basis vectors. We can construct them as follows.

$$
\left\{
\begin{bmatrix}
	−2 \\
	1 \\
	1 \\
	1 \\
	1 \\
	1 \\
	0 \\
	0 \\
	0 \\
	0 \\
	0 \\
	0 
\end{bmatrix},

\begin{bmatrix}
	0\\
	−1\\
	0\\
	0\\
	0\\
	0\\
	1\\
	1\\
	1\\
	0\\
	0\\
	0 
\end{bmatrix},

\begin{bmatrix}
	0\\
	0\\
	−1\\
	0\\
	0\\
	0\\
	0\\
	0\\
	0\\
	1\\
	1\\
	1 
\end{bmatrix},

\begin{bmatrix}
	0\\
	0\\
	0\\
	−1\\
	0\\
	0\\
	1\\
	0\\
	0\\
	1\\
	0\\
	0 
\end{bmatrix},

\begin{bmatrix}
	0\\
	0\\
	0\\
	0\\
	−1\\
	0\\
	0\\
	1\\
	0\\
	0\\
	1\\
	0 	
\end{bmatrix},

\begin{bmatrix}
	0\\
	0\\
	0\\
	0\\
	0\\
	−1\\
	0\\
	0\\
	1\\
	0\\
	0\\
	1 
\end{bmatrix}
\right\}
$$

Let's see if we can get any intuition on how these vectors were created, how we know that they are a basis for the null space, and how we can generalize them.

The first vector will always take -2 times 1 as we will always have an intercept term. Then it takes 1 times the second and third row entry in $X$. These correspond to the $\alpha$ levels, which we know are exlusive, i.e. exactly one will be 1. The next three 1s correspond to the $\beta$ levels, which we again know will a single element that is 1. Thus this will always map to 0.

The second vector have a -1 in the second row. This corresponds to the first alpha level. The 1s following all map to the interaction terms of $\alpha_1$ and $\beta_i$, which we know there will be exactly one of if we are in $\alpha_1$. Thus, this will map to 0. Also if we are not in $\alpha_1$, this will map to zero. 

The third vector does the same thing for the $\alpha_2$ level. The remaining vectors perform the same task but for each $\beta$ level. 

With all this information. we can begin to generalize. If $i \in \{1,\dots,n\}$, $j \in \{1,\dots,m\}$ our matrix will have $nm$ rows (one for each combination of $\alpha_i$ $\beta_j$) and $1 + n + m + nm$ columns (intercept + $\alpha$ level + $\beta$ level + interaction terms). We can again say that the interaction terms from a basis form $\mathbb{R}^{nm}$ and thus the rank is $nm$. We can also see that would need to drop one $\alpha_i$ and one $\beta_j$ to have a full rank model, so the rank would be 

$$
\text{rank}( X ) = 1 + (n-1)+ (m-1) + (n-1)(m-1) = 1 + n-1 + m-1 + nm - n -m + 1 = nm.
$$


Then the dimension of our null space will be

$$
\dim(\mathcal N(X)) = nm + n + m + 1 - nm = n + m + 1.
$$


This is what we would expect as before we saw one basis vector for the intercept, $n$ for the $\alpha$ levels, and $m$ for the $\beta$ levels. We will construct them in the same way for the general case.

$$
\left\{
\begin{bmatrix}
	-2 \\
	n \begin{cases}
		1 \\
		\vdots \\
		1
	\end{cases} \\
	m \begin{cases}
		1 \\
		\vdots \\
		1
	\end{cases} \\
	0 \\
	\vdots \\
	0
\end{bmatrix},

\begin{bmatrix}
  	0 \\
  	-1 \\
	n-1 \begin{cases}
		0 \\
		\vdots \\
		0
	\end{cases} \\
 	m \begin{cases}
		0 \\
		\vdots \\
		0
	\end{cases} \\
 	m \begin{cases}
		1 \\
		\vdots \\
		1
	\end{cases}\\
	nm-m \begin{cases}
		0 \\
		\vdots \\
		0
	\end{cases}
\end{bmatrix},

\dots ,

\begin{bmatrix}
	0 \\
	\mathbf 0_{n-1} \\
	-1 \\
	\mathbf 0_m \\
	\mathbf 0_{nm-m} \\
	\mathbf 1_m
\end{bmatrix},

\begin{bmatrix}
	0 \\ 
	\mathbf 0_{n} \\
	-1 \\
	\mathbf 0_{m-1} \\
	1 \\
	\mathbf 0_{n-1} \\
	1 \\
	\mathbf 0_{n-1} \\
	\vdots
\end{bmatrix}, 

\dots ,

\begin{bmatrix}
	0 \\ 
	\mathbf 0_{n} \\
	\mathbf 0_{m-1} \\
	-1 \\
	\mathbf 0_{n-1} \\
	1 \\
	\vdots
\end{bmatrix}


\right\}
$$


So that got _really_ messy really fast (sorry, I promise those vectors are all the same length), so let's review where the vectors came from.


The first vector has -2 for the intercept and 1 for each $\alpha$ and $\beta$ level, which we are guaranteed to have only one of each.

The second vector has -1 for the $\alpha_1$ level and a 1 for each $\theta_{1 j}$ level, which we are guaranteed to have only one of. The next $n-1$ vectors do the same for the other $\alpha_i$ levels.

The next vector has a -1 for the $\beta_1$ term and a 1 for all the $\theta_{i 1}$ terms, which we are guaranteed to have only one of (notice that this repeats in a pattern of 1 followed by $n-1$ 0's). The next $m-1$ vectors do the same thing for the other $\beta_j$ levels.


Thus, any $\lambda$ that is orthogonal to these vector will produce an estimable result.

# 3
**Prove the converse to Result 3.2 (recall that we saw two proofs of Result 3.2 in lecture).  That is, if the least squares estimator $\lambda'\widehat{\beta}$ is the same for all solutions $\widehat{\beta}$ to the normal equations, then $\lambda'\beta$ is estimable.**


We know that

$$
\lambda^T \beta_1 = \lambda^T \beta_2 \Rightarrow \lambda^T(\beta_1 - \beta_2) = 0.
$$


So we know that $\lambda$ is orthogonal to $\beta_1 - \beta_2$. And since $\beta_1$ and $\beta_2$ solve the normal equations, we know that

$$
X^T X \beta_1 = X^T X \beta_2 \rightarrow X^T X (\beta_1 - \beta_2) = 0.
$$


This means that $\beta_1  - \beta_2 \in \mathcal N(X^T X) = \mathcal N (X)$. Since $\mathcal N(X)$ and $\text{ column }( X^T )$ are orthogonal complements, we know that $\lambda \in \text{ column }( X^T )$ and thus is estimable.


# 4
**Let $V$ be a finite-dimensional inner product space over $\mathbb{C}$, and let $\{v_{1},\dots,v_{n}\}$ be an orthonormal basis for $V$.**


## a
**Show that for any $x,y \in V$,**

$$\langle x,y\rangle = \sum_{i=1}^{n}\langle x,v_{i} \rangle\overline{\langle y,v_{i} \rangle}.$$

**This is called Parseval's identity.**

Take $x = \sum a_1 v_i$ and $y = \sum b_i v_i$.

$$
	\begin{align}
		\sum_{i=1}^{n}\langle x,v_{i} \rangle\overline{\langle y,v_{i} \rangle} & = \sum_{i=1}^{n}\langle x,v_{i} \rangle \langle v_{i}, y \rangle \\
			& = \sum_{i=1}^{n}\langle a_1 v_1 + \dots + a_n v_n,v_{i} \rangle \langle v_{i}, b_1 v_1 + \dots + b_n v_n \rangle \\
	\end{align}
$$

Since the $v_i$'s are lineary independent, 

$$
\langle v_i , v_j \rangle =
\begin{cases}
	0 & i \neq j \\
	1 & i = j.
\end{cases}
$$


$$
	\begin{align}
		\sum_{i=1}^{n}\langle x,v_{i} \rangle\overline{\langle y,v_{i} \rangle} & = \sum_{i=1}^{n}\langle a_1 v_1 + \dots + a_n v_n,v_{i} \rangle \langle v_{i}, b_1 v_1 + \dots + b_n v_n \rangle \\ \\
			& = \sum_{i=1}^{n}\langle a_i v_i ,v_{i} \rangle \langle v_{i},  b_i v_i \rangle \\
			& = \sum_{i=1}^{n} a_i \overline{ b_i }  \langle v_i ,v_{i} \rangle \langle v_{i}, v_i \rangle \\
			& = \sum_{i=1}^{n} a_i \overline{ b_i } \\
			& = \langle x , y \rangle
	\end{align}
$$
## b
**For $V = \mathbb{R}^{2}$ use Parseval's identity to prove the Pythagorean theorem.  Generalize this result to $\mathbb{R}^{n}$.**

We are trying to show that for $a \perp b$,

$$
||a||^2 + ||b||^2 = ||a + b ||^2.
$$


Let's start with $a, b \in \mathbb{R}^2$


$$
	\begin{align}
		||a + b ||^2 & = \langle a + b , a+b \rangle \\
			& = \sum \langle a+b , v_i \rangle \langle v_i , a+b \rangle \\
			& = \sum \langle a_i v_i+b_i v_i , v_i \rangle \langle v_i , a_iv_i +b_i v_i \rangle \\
			& = \langle a_1 v_1 + b_1 v_1 , v_1 \rangle  \langle v_1, a_1 v_1 + b_1 v_1 \rangle + \langle a_2 v_2 + b_2 v_2 , v_2 \rangle \langle v_2, a_2 v_2 + b_2 v_2 \rangle \\
			& = (\langle a_1 v_1 , v_1 \rangle + \langle b_1 v_1 , v_1 \rangle)( \langle v_1 , a_1 v_1 \rangle + \langle v_1 , b_1 v_1 \rangle) + (\langle a_2 v_2 , v_2 \rangle + \langle b_2 v_2 , v_2 \rangle)( \langle v_2 , a_2 v_2 \rangle + \langle v_2 , b_2 v_2 \rangle) \\
			& = (a_1 + b_1)(\overline{ a_1 } + \overline{ b_1 }) + (a_2 + b_2) (\overline{ a_2 } + \overline{ b_2 }) \\
			& = a_1 \overline{ a_1 } + a_1 \overline{ b_1 } + b_1 \overline{ a_1 } + b_1 \overline{ b_1 } + a_2 \overline{ a_2 } + a_2 \overline{ b_2 } + b_2 \overline{ a_2 } + b_2 \overline{ b_2 } \\
			& = a_1 \overline{ a_1 } + a_2 \overline{ a_2 } + b_1 \overline{ b_1 } + b_2 \overline{ b_2 } \\
			& = \langle a,a  \rangle + \langle b , b \rangle \\
			& = ||a||^2 + ||b||^2
	\end{align}
$$


Notice that since $a \perp b$, all of the cross terms zeroed out. 

Notice that all of these steps hold for any dimension as long as $x_1 \perp x_2 \perp \dots \perp x_n$ so that the cross terms are 0.



# 5
**Let $V$ be an inner product space over $\mathbb{C}$, and let $\{v_{1},\dots,v_{n}\} \subset V$ be orthonormal.**


## a
**Prove that for any $x \in V$,**

$$
\|x\|^{2} \ge \sum_{i=1}^{n} |\langle x,v_{i}\rangle|^{2}.
$$

**This is called Bessel's inequality.**

Recall that a $\|\| \cdot \|\| \geq 0$.

$$
	\begin{align}
		0 & \leq || x - \sum_{i=1}^n \langle x , v_i \rangle v_i ||^2 \\
			& = ||x||^2 - 2 \sum_{i=1}^n | \langle x ,  v_i \rangle|^2 + \sum_{i=1}^n |\langle x , v_i \rangle | ^2 \\
			& = ||x||^2 - \sum_{i=1}^n | \langle x ,  v_i \rangle|^2 \\ \\
		\sum_{i=1}^n | \langle x ,  v_i \rangle|^2 &  \leq ||x||^2
	\end{align}
$$


## b
**Show that Bessel's inequality is an equality if and only if $x \in \text{span} \\{v_{1},\dots,v_{n}\\}$.**


$\Rightarrow$

Start with the inequality that we started with in a.

$$
0 \leq || x - \sum_{i=1}^n \langle x , v_i \rangle v_i ||^2 \\
$$

Since a norm is only zero when you are taking the norm of the zero element, for equality it must be the case that 

$$
x = \sum_{i=1}^n \langle x , v_i \rangle v_i .
$$

Now we see that $x$ is the sum of scalars multiplied by the $v_1, \dots v_n$. Thus, $x$ is in their span.


$\Leftarrow$

If $x \in \text{span} \\{v_{1},\dots,v_{n}\\}$, then $x = \sum a_i v_i$.

$$
	\begin{align}
		\sum_{i=1}^n | \langle x , v_i \rangle | ^2 & = \sum_{i=1}^n | \langle \sum a_j v_j , v_i \rangle | ^2 \\
		& = \sum_{i=1}^n | \langle \sum a_j v_j , v_i \rangle | ^2 \\
		& = \sum_{i=1}^n | a_i | ^2 \\ 
		& = ||x||^2
	\end{align}
$$

Notice that we again used the trick from 4,

$$
\langle v_i , v_j \rangle =
\begin{cases}
	0 & i \neq j \\
	1 & i = j.
\end{cases}
$$

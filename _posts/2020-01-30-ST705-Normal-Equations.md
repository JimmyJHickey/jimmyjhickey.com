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


# 2 
**Let $X = QR$ where $Q$ has orthonormal columns.  Prove that if $\text{rank}(X) = \text{rank}(Q)$, then $P_{X} = QQ'$.**


# 3 (2.12)
**In Example 2.7 (Celsius to Fahrenheit), find $\gamma_0$ and $\gamma_1$ in terms of $\beta_0$ and $\beta_1$.**


# 4 (2.13)
**Consider the simple linear regression model $y_i = \beta_0 + \beta_1 x_i + e_i$. Show that if the $x_i$ are equally spaced, that is, $x_i = s + t i$ for some values of $s$ and $t$, then $y_i = \gamma_0 + \gamma_1 i + e_i$ is an equivalent parameterization. Can you extend this to a quadratic or higher degreee polynomial?**


# 5 
**Let $A$ be an $m\times n$ matrix with rank $m$.  Prove that there exists an $n\times m$ matrix $B$ such that $AB = I_{m}$.**


# 6 
**Let $A \in \mathbb{R}^{n\times p}$ with rank$(A) = p$.  Further, suppose  $X \in \mathbb{R}^{n\times q}$ with $\text{column}(X) = \text{column}(A)$.  Show that there exists a unique matrix $S$ so that $X = AS$.**


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


# 8 
**Let $A$ be an $m\times n$ matrix and $B$ be an $n\times p$ matrix.  Prove that $AB$ can be written as a sum of $n$ matrices of rank at most one.  Hint: think about empirical covariance matrices.**



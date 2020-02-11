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





## b
**Find a generalized inverse of $X^T X$ and call it $G$.**


## c
**Compute $H = G X^T X$ and recall $H^T$ is a projection onto $\text{ column }( X^T ) = \text{ column }( X^T X )$.**




## d
**Compute $(I - H)$ and recall that it is a projection onto $\mathcal N (X) = \mathcal N(X^T X)$.**



## e
**Find a basis for $\mathcal C (X^T)$.**



## f
**Find a basis for $\mathcal N (X)$.**



## g
**Compute $P_X$ and its trace.**



# 2
**Consider the model $Y_{ijk} = \mu + \alpha_{i} + \beta_{j} + \theta_{ij} + U_{ijk}$, with $k \in \{1,\dots,m_{ij}\}$, $i \in \{1,\dots,n\}$, $j \in \{1,\dots,m\}$, and $E(U_{ijk}) = 0$.  Find necessary and sufficient conditions for which $\lambda'\gamma$ is estimable for**

$$
\gamma =
\begin{pmatrix}
\mu & \alpha_{1} & \cdots & \alpha_{n} & \beta_{1} & \cdots & \beta_{m} & \theta_{11} & \cdots & \theta_{nm} \\
\end{pmatrix}'.
$$




# 3
**Prove the converse to Result 3.2 (recall that we saw two proofs of Result 3.2 in lecture).  That is, if the least squares estimator $\lambda'\widehat{\beta}$ is the same for all solutions $\widehat{\beta}$ to the normal equations, then $\lambda'\beta$ is estimable.**



# 4
**Let $V$ be a finite-dimensional inner product space over $\mathbb{C}$, and let $\{v_{1},\dots,v_{n}\}$ be an orthonormal basis for $V$.**


## a
**Show that for any $x,y \in V$,**

$$\langle x,y\rangle = \sum_{i=1}^{n}\langle y,v_{i} \rangle\overline{\langle y,v_{i} \rangle}.$$




## b
**For $V = \mathbb{R}^{2}$ use Parseval's identity to prove the Pythagorean theorem.  Generalize this result to $\mathbb{R}^{n}$.**



# 5
**Let $V$ be an inner product space over $\mathbb{C}$, and let $\{v_{1},\dots,v_{n}\} \subset V$ be orthonormal.**


## a
**Prove that for any $x \in V$,**

$$
\|x\|^{2} \ge \sum_{i=1}^{n} |\langle x,v_{i}\rangle|^{2}.
$$

**This is called Bessel's inequality.**




## b
**Show that Bessel's inequality is an equality if and only if $x \in \text{span}\{v_{1},\dots,v_{n}\}$.**



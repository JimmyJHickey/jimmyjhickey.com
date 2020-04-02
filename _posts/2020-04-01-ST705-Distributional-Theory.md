---
layout: post
comments: false
title: Example Problems on Distributional Theory
description: ST705 Homework 10 Distributional Theory
tags: ST705 Linear-Algebra Distributional Statistics
category: ST705
---


* Do not remove this line (it will not be displayed)
{:toc}


# 5.9
**Find the density for the F-distribution.**



# 5.10
**Find the density of the noncentral Student's t-distribution. Also find its mean and variance.**



# 5.11
**Let $U \sim \chi^2_k (\phi)$; find its mean and variance. Confirm with Lemmas 4.1 and Result 4.6 (use $\sigma^2  =1$, $\gamma_3 = 0$, and $\gamma_4 = 3$).**



# 5.12
**Let $X \sim N_p( \mu, V)$ with $V$ nonsingular, and let $U = X^T A X$ for $A$ symmetric.**


## a
**Show that the mgf of $U$ is $m_U(t) = \| I - 2tAV \|^{-1/2} exp\\{-\frac{ 1 }{ 2 }[\mu^T V^{-1} \mu - \mu^T(V - 2t VAV)^{-1} \mu]\\}$**



## b
**Show that if $A \mu = 0$, then $m_U(t) = \|I-2tAV \|^{-1/2}$.**


# 5.14
**Using the result of Exercise 5.12, show that**

## a
$$Var(X^T A X) = 2 tr(AV)^2 + 4 \mu^T AVA \mu$$



## b
**(Easier) If $X \sim N_p(0, V)$, then $Var(X^TAX)=2 tr(AV)^2$.**



# 5.16
**Prove a converse to Result 5.16, assuming $V$ to be non-singular.**




# 5.23
**Let $X \sim N_p(\mu, V)$ with $V$ nonsingular, and partition as below:**


$$
X = \begin{bmatrix}
	X_1 \\
	X_2
\end{bmatrix},

\begin{array}{c}
	p_1 \\
	p_2 
\end{array},

\mu =
\begin{bmatrix}
	\mu_1 \\
	\mu_2
\end{bmatrix}
\begin{array}{c}
	p_1 \\
	p_2
\end{array},


V = 
\begin{bmatrix}
	V_{11} & V_{12} \\
	V_{21} & V_{22}
\end{bmatrix}
\begin{array}{c}
	p_1 \\
	p_2
\end{array}
$$

**Show that the conditional distribution of $X_1$ given $X_2 = x_2$ is multivariate normal with mean vector $\mu_1 + V_{12}V_{22}^{-1} (x_2 - \mu_2)$ and covariance matrix $V_{11} - V_{12}V_{22}^{-1}V_{21}$. Hint: Use the partitioned inverse result from Exercise A.74.**




# 5.25
**Show that $R^2$ given by (5.12) is also equal to the right-hand side of (5.11).**




# 5.27
**Prove Corollary 5.4.**
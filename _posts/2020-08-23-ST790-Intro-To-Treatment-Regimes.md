---
layout: post
comments: false
title: Example Problems an Introduction to Dynamic Treatment Regimes
description: ST790 Homework 1 an Introduction to Dynamic Treatment Regimes
tags: ST793 Likelihoods Statistics
category: ST790-Dynamic-Treatment-Regimes
---

* Do not remove this line (it will not be displayed)
{:toc}

Analytical Problems

# 1
**Suppose that there are two treatment options $\mathcal A = \\{ 0,1 \\}$, where $A$ is the treatment indicator. Suppose further that there is a single, binary baseline covariate, $X$, taking values 0 or 1; and the outcome, $Y$, is also binary, taking values 0 or 1. The joint distribution of the potential outcomes $Y^{\star}(1)$, $Y^\star(0), X$, and $A$ is given by**


$$
\begin{array}{c c c c c} 
Y^\star(1) & Y^\star(0) & X & A & \text{probability} \\ \hline
1	&	1	&	1	&	1	&	1/ 36	\\
1	&	1	&	1	&	0	&	1/ 18	\\
1	&	0	&	1	&	1	&	1/ 12	\\
1	&	0	&	1	&	0	&	1/ 6	\\
0	&	1	&	1	&	1	&	1/ 18	\\
0	&	1	&	1	&	0	&	1/ 9	\\
1	&	1	&	0	&	1	&	1/ 9	\\
1	&	1	&	0	&	0	&	1/ 18	\\
1	&	0	&	0	&	1	&	1/ 6	\\
1	&	0	&	0	&	0	&	1/ 12	\\
0	&	1	&	0	&	1	&	1/ 18	\\
0	&	1	&	0	&	0	&	1/ 36
\end{array}
$$

## a
**Show using direct calculations that the no unmeasured confounders assumptions (2.13) holds in this setting.**

Recall equation (2.7), if $Z_1 \perp Z_2 \| Z_3$ then

$$
p_{Z_1, Z_2|Z_3} (z_1, z_2 | z_3) = p_{Z_1 | Z_3}(z_1 | z_3) \cdot p_{Z_2|Z_3}(z_2 | z_3).
$$

Take $Z = \Big( Y^{\star}(0), Y^{\star}(1) \Big)$. Also notice that $P(X = 1) = P(X = 0) = 1/36 + 1/18 + 1/12 + 1/6 + 1/18 + 1/9 = 1/2$. So,

$$
\begin{align}
P(Z = (	B	,	C	), A = 	D	| X = 	x	) &=2 P( Z = (B,C) , A=D, X = x) \\
P(Z = (	B	,	C	) | X = 	x	)P(A = 	D	|X = 	x	) & =  4 P(Z = (	B	,	C	), X = 	x	)P(A = 	D, X = 	x	).
\end{align}
$$

Thus,

$$
\begin{array}{ c }
P(Z = (	1	,	1	), A = 	1	| X = 	1	) =  P(Z = (	1	,	1	) | X = 	1	)P(A = 	1	|X = 	1	)	\\
2\frac{ 1 }{ 36 } = \frac{ 1 }{ 18 }= 4 \left(\frac{1}{36}+\frac{1}{18}\right) \left(\frac{1}{36}+\frac{1}{12}+\frac{1}{18}\right) \\
P(Z = (	1	,	1	), A = 	1	| X = 	0	)=	P(Z = (	1	,	1	) | X = 	0	)P(A = 	1	|X = 	0	)	\\
2 \frac{ 1 }{ 9 } = \frac{ 2 }{ 9 } =4 (\frac{ 1 }{ 9 } + \frac{ 1 }{ 18 }) (\frac{ 1 }{ 18 } + \frac{ 1 }{ 6 } + \frac{ 1 }{ 9 }) \\
P(Z = (	1	,	1	), A = 	0	| X = 	1	)=	P(Z = (	1	,	1	) | X = 	1	)P(A = 	0	|X = 	1	)	\\
2 \frac{1}{9}  = \frac{ 2 }{ 9 } = 4 (\frac{ 1 }{ 36 } + \frac{ 1 }{ 18 })( \frac{ 1 }{ 9 } + \frac{ 1 }{ 6 } + \frac{ 1 }{ 18 }) \\ 
P(Z = (	1	,	1	), A = 	0	| X = 	0	)=	P(Z = (	1	,	1	) | X = 	0	)P(A = 	0	|X = 	0	)	\\
2 \frac{ 1 }{ 18 } = \frac{ 1 }{ 9 } = 4 (\frac{ 1 }{ 9 } +\frac{ 1 }{ 18 })(\frac{ 1 }{ 18 } + \frac{ 1 }{ 12 } + \frac{ 1 }{ 36 }) \\
P(Z = (	1	,	0	), A = 	1	| X = 	1	)=	P(Z = (	1	,	0	) | X = 	1	)P(A = 	1	|X = 	1	)	\\
2 \frac{ 1 }{ 12 } =\frac{ 1 }{ 6 } = 4 ( \frac{ 1 }{ 12 }+ \frac{ 1 }{ 6 })( \frac{1}{36}+\frac{1}{12}+\frac{1}{18} ) \\
P(Z = (	1	,	0	), A = 	1	| X = 	0	)=	P(Z = (	1	,	0	) | X = 	0	)P(A = 	1	|X = 	0	)	\\
2 \frac{ 1 }{ 6 } = \frac{ 1 }{ 3 }= 4 ( \frac{ 1 }{ 6 }+ \frac{ 1 }{ 12 })( \frac{ 1 }{ 18 } + \frac{ 1 }{ 6 } + \frac{ 1 }{ 9 } ) \\
P(Z = (	1	,	0	), A = 	0	| X = 	1	)=	P(Z = (	1	,	0	) | X = 	1	)P(A = 	0	|X = 	1	)	\\
2 \frac{ 1 }{ 6 } =\frac{ 1 }{ 3 }= 4 ( \frac{ 1 }{ 12 }+ \frac{ 1 }{ 6 })( \frac{ 1 }{ 9 } + \frac{ 1 }{ 6 } + \frac{ 1 }{ 18 } ) \\
P(Z = (	1	,	0	), A = 	0	| X = 	0	)=	P(Z = (	1	,	0	) | X = 	0	)P(A = 	0	|X = 	0	)	\\
2 \frac{ 1 }{ 12 } = \frac{ 1 }{ 6 }= 4 ( \frac{ 1 }{ 6 }+ \frac{ 1 }{ 12 })( \frac{ 1 }{ 18 }+ \frac{ 1 }{ 12 }+ \frac{ 1 }{ 36 }) \\
P(Z = (	0	,	1	), A = 	1	| X = 	1	)=	P(Z = (	0	,	1	) | X = 	1	)P(A = 	1	|X = 	1	)	\\
2 \frac{ 1 }{ 18 } = \frac{ 1 }{9  }= 4 ( \frac{ 1 }{ 18 }+ \frac{ 1 }{ 9 })( \frac{1}{36}+\frac{1}{12}+\frac{1}{18} ) \\
P(Z = (	0	,	1	), A = 	1	| X = 	0	)=	P(Z = (	0	,	1	) | X = 	0	)P(A = 	1	|X = 	0	)	\\
2 \frac{ 1 }{ 18 } = \frac{ 1 }{ 9 }= 4 ( \frac{ 1 }{ 18 }+ \frac{ 1 }{ 36 })( \frac{ 1 }{ 18 } + \frac{ 1 }{ 6 } + \frac{ 1 }{ 9 } ) \\
P(Z = (	0	,	1	), A = 	0	| X = 	1	)=	P(Z = (	0	,	1	) | X = 	1	)P(A = 	0	|X = 	1	)	\\
2 \frac{ 1 }{ 9 } = \frac{ 2 }{ 9 }= 4 ( \frac{ 1 }{ 18 }+ \frac{ 1 }{ 9 })( \frac{ 1 }{ 9 } + \frac{ 1 }{ 6 } + \frac{ 1 }{ 18 } ) \\
P(Z = (	0	,	1	), A = 	0	| X = 	0	)=	P(Z = (	0	,	1	) | X = 	0	)P(A = 	0	|X = 	0	)	\\
2 \frac{ 1 }{ 36 } = \frac{ 1 }{ 18 }= 4 ( \frac{ 1 }{ 18 }+ \frac{ 1 }{ 36 })(\frac{ 1 }{ 18 }+ \frac{ 1 }{ 12 }+ \frac{ 1 }{ 36 } ) \\



\end{array}
$$

## b
**In the rest of the problem, assume SUTVA given in (2.3) holds. Deduce the distribution of the observed data $(X,A,Y)$; that is, produce a table like that above with all with possible combinations of values $(X,A,Y)$ can take on together with their associated probabilities.**

SUTVA tells us that

$$
Y_i = Y_i^*(1) (A_i) + Y_i^*(0) (1 - A_i) , \ i =1, \dots , n
$$


$$
\begin{array}{c c c r } 
X & A & Y & \text{probability} \\ \hline
0	&	0	&	0	& 	\frac{ 1 }{ 36 } + \frac{ 1 }{ 18 } = \frac{ 1 }{ 12 }\\
0	&	0	&	1	&	\frac{ 1 }{ 12 } 	\\
0	&	1	&	0	&	 \frac{ 1 }{ 18 }\\
0	&	1	&	1	&	\frac{ 1 }{ 9 } + \frac{ 1 }{ 6 } = \frac{ 5 }{ 18 }\\
1	&	0	&	0	&	\frac{ 1 }{ 18 } + \frac{ 1 }{ 9 } = \frac{ 1 }{ 6 }	\\
1	&	0	&	1	&	 \frac{ 1 }{ 6 }	\\
1	&	1	&	0	&	 \frac{ 1 }{ 18 }	\\
1	&	1	&	1	&	\frac{ 1 }{ 36 } + \frac{ 1 }{ 12 } = \frac{ 1 }{ 9 }	\\
	
\end{array}
$$

As a sanity check, notice that

$$
 \frac{1}{12}+\frac{1}{12}+\frac{1}{18}+\frac{5}{18}+\frac{1}{6}+\frac{1}{6}+\frac{1}{18}+\frac{1}{9} = 1
$$

## c
**Find $E(Y \| A = 1), E \\{ Y^\star(1) \\}, E(Y\| A = 0)$, and $E \\{ Y^\star(0) \\}$ for these distributions.**



## d
**Verify that $E \\{ Y^\star(1) \\} = E \\{ E(Y \|X , A = 1) \\}$ and $E \\{ Y^\star(0) \\} = E \\{ E(Y \|X , A = 0) \\}$ for these distributions, where, as in the notes, the outer expectation is with respect to the distribution of $X$.**




# 2
**Assume that we have iid observed data $(X_i, A_i, Y_i), \ i = 1, \dots , n$, where there are two treatment options $\mathcal A = \\{ 0,1 \\}$, for which the SUTVA (2.3), the no unmeasured confounders (2.13), and the positivity assumption (2.17) hold. As in the notes, define**

$$
\pi(X) = P(A = 1 | X).
$$

**Prove that**

$$
\Big\{ \sum_{i=1}^n (1- A_i) \Big\}^{-1} \sum_{i=1}^n \Big[ A_i \frac{ \Big( 1 - \pi(X_i) \Big) }{ \pi(X_i) } Y_i \Big]
$$

**converges in probability to $E \\{ Y^\star(1) \| A = 0 \\}$, the expectation of $Y^\star(1)$ among those observed to receive treatment 0.**

# 3
**Consider again the joint distribution of the potential outcomes $Y^\star(1), Y^\star(0), X$, and $A$ given in Problem 1. Identifying $H_1 = X$, consider treatment regime $d$ with rule $d_1(h_1) = 1$ if $h_1 = 1$ and $d_1(h_1) = 0$ if $h_1 = 0$. Find $E \\{ Y^\star(d) \\}$.**




# 4
**Consider a fixed regime $d$ with true value $\mathcal V(d)$ and the "alternative" IPW estimator $\widehat{\mathcal{V}}_{IPW}(d)$ for the value of a fixed $d$ given in (3.14)**

## a
**Take the propensity $\pi_1(h_1)$ to be _known_. Under this condition, using M-estimation theory, find the limiting distribution of**

$$
n^{1/2} \{ \widehat{\mathcal{V}}_{IPW*}(d) - \mathcal V(d) \}
$$

**and give an expression for its variance.**

## b
**Now take the propensity $\pi_1(h_1)$ to be _unknown_ and modeled by a _correctly specified_ logistic regression model of the form**

$$
\pi_1(h_1; \gamma_1) = \frac{ \exp(\gamma_1^T \widetilde h_1) }{ 1 + \exp (\gamma_1^T \widetilde  h_1)}, \ \widetilde h_1 = (1, h_1^T)^T  
$$

**as in (3.12), and let $\widehat \gamma_1$ be the maximum likelihood estimator of $\gamma_1$.**

**Under this condition, using M-estimation theory, deriv the limiting distribution of (1) and give an expression for its variance. Show that the variance you found in (a) is at least as large as the variance here, thus demonstrating the counterintuitive result noted on Slide 134 and more generally that it is preferable on ground of efficiency to estimate the propensity even if it is known.**

**_Hint:_ You will find it useful to write $\widehat{\mathcal{V}}\_{IPW \star}(d)$ in the simpler form suggested on Slide 133. Then express $\widehat{\mathcal{V}}_{IPW\star}(d)$ equivalently as the solution to an estimating equation and "stack" it with the score equation for ML estimate $\gamma_1$ (e.g. see Slide 109).**
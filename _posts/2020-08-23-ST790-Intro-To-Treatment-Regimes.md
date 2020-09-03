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
1	&	0	&	1	&	\frac{ 1 }{ 18 } + \frac{ 1 }{ 9 } = \frac{ 1 }{ 6 }	\\
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

$$
\begin{align}
E(Y|A=1) & = \frac{\frac{5}{18}+\frac{1}{9}}{\frac{1}{18}+\frac{5}{18}+\frac{1}{18}+\frac{1}{9}} \\
    & = \frac{ 7 }{ 9 }\\ \\
E(Y^*(1)) & = \frac{1}{36}+\frac{1}{18}+\frac{1}{12}+\frac{ 1 }{ 6 } +\frac{1}{9}+\frac{1}{18}+\frac{1}{6}+\frac{1}{12} \\
    & = \frac{ 3 }{ 4 } \\ \\
E(Y|A=0) & = \frac{\frac{1}{12}+\frac{1}{6}}{\frac{1}{12}+\frac{1}{12}+\frac{1}{6}+\frac{1}{6}} \\
    & = \frac{ 1 }{ 2 }\\ \\
E(Y^*(0)) & =\frac{1}{36}+\frac{1}{18}+\frac{1}{18}+\frac{1}{9}+\frac{1}{9}+\frac{1}{18}+\frac{1}{18}+\frac{1}{36} \\
    & = \frac{ 1 }{ 2 }
\end{align}
$$


## d
**Verify that $E \\{ Y^\star(1) \\} = E \\{ E(Y \|X , A = 1) \\}$ and $E \\{ Y^\star(0) \\} = E \\{ E(Y \|X , A = 0) \\}$ for these distributions, where, as in the notes, the outer expectation is with respect to the distribution of $X$.**

Notice that $X$ is binary for $\mathbb I(X = 1) = X$ and $\mathbb I(X=0) = 1-X$.

$$
\begin{align}
E(E(Y|X, A = 1)) & = E\Big[ \mathbb  I(X= 1) E(Y | X = 1, A = 1) + \mathbb I(X=0) E(Y|X=0, A=1)\Big] \\
    & = E\Big[ \mathbb  I(X= 1) P(Y=1, X = 1, A = 1) + \mathbb I(X=0) P(Y=1, X=0, A=1)\Big] \\
    & = E\Big[ \mathbb  I(X= 1) \frac{ \frac{ 1 }{ 9 } }{ \frac{ 1 }{ 9 } + \frac{ 1 }{ 18 } } + \mathbb I(X=0) \frac{ \frac{ 5 }{ 18 } }{ \frac{ 5 }{ 18 } + \frac{ 1 }{ 18 } }\Big] \\
    & = E\Big[ \mathbb  I(X= 1) \frac{ \frac{ 1 }{ 9 } }{ \frac{ 1 }{ 9 } + \frac{ 1 }{ 18 } } + \mathbb I(X=0) \frac{ \frac{ 5 }{ 18 } }{ \frac{ 5 }{ 18 } + \frac{ 1 }{ 18 } }\Big] \\
    & = E\Big[ \frac{ 2 }{ 3 }\mathbb I(X= 1) + \frac{ 5 }{ 6 }\mathbb I(X=0) \Big] \\
    & = E\Big[ \frac{ 2 }{ 3 }X + \frac{ 5 }{ 6 }(1-X) \Big] \\
    & = E\Big[  \frac{ 5 }{ 6 }- \frac{ 1 }{ 6 }X \Big] \\
    & = \frac{ 5 }{ 6 } - \frac{ 1 }{ 6 } E(X) \\
    & = \frac{ 5 }{ 6 } - \frac{ 1 }{ 6 } (0\cdot P(X = 0) + 1 \cdot P(X=1)) \\
    & = \frac{5}{6}-\frac{1}{6} \left(\frac{1}{9}+\frac{1}{6}+\frac{1}{18}+\frac{1}{6}\right) \\
    & = \frac{ 3 }{ 4 } \\
    & = E(Y^*(1)) \\ \\
E(E(Y|X, A = 0)) & = E\Big[ \mathbb  I(X= 1) E(Y | X = 1, A = 0) + \mathbb I(X=0) E(Y|X=0, A=0)\Big] \\
    & = E\Big[ \mathbb  I(X= 1) P(Y=0, X = 1, A = 0) + \mathbb I(X=0) P(Y=0, X=0, A=0)\Big] \\
    & = E\Big[ \mathbb  I(X= 1) \frac{ \frac{ 1 }{ 6 } }{ \frac{ 1 }{ 6 } + \frac{ 1 }{ 6 } } + \mathbb I(X=0) \frac{ \frac{ 1 }{ 12 } }{ \frac{ 1 }{ 12 } + \frac{ 1 }{ 12 } }\Big] \\
    & = E\Big[ \mathbb  I(X= 1) \frac{ 1 }{ 2 } + \mathbb I(X=0) \frac{ 1 }{2}\Big] \\
    & = E\Big[ X \frac{ 1 }{ 2 } + (1-X) \frac{ 1 }{2}\Big] \\
    & = E\Big[ \frac{ 1 }{ 2 }\Big] \\
    & = \frac{ 1 }{ 2 } \\
    & = E(Y^*(0))
\end{align}
$$


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

We need to find this expression's expectation. Then we can apply the Weak Law of Large Numbers to find what it converges to.

$$
\begin{align}
\mathbb E(1-A) &= 1 - \mathbb E(A) \\
    & = 1 - P(A = 1) \\
    & = 1 - P(A = 1) \\
    & = 1 - \pi(X) \\
\mathbb E(A Y \frac{ 1 - \pi(X) }{ \pi(X) }) & = \mathbb E(A (Y^*(1)A + Y^*(0)(1-A)) \frac{ 1 - \pi(X) }{ \pi(X) })) & \text{SUTVA} \\
    & = \mathbb E( (Y^*(1)A^2 + Y^*(0)(1-A)A) \frac{ 1 - \pi(X) }{ \pi(X) })) \\
    & = \mathbb E(Y^*(1)A \frac{ 1 - \pi(X) }{ \pi(X) })) & A = \{0,1\} \\
    & = \mathbb E(Y^*(1) A \frac{ 1 }{ \pi(X)} - Y^{*}(1) A) \\
    & = \mathbb E(Y^*(1) \frac{ A }{ \pi(X)} ) - \mathbb E(Y^{*}(1) A) \\
    & = \mathbb E(Y^*(1) ) - \mathbb E(Y^{*}(1) A) \\
    & = \mathbb E(Y^*(1) (1-A)) \\
    & = \mathbb E \Big(\mathbb  E(Y^*(1) (1-A) |A) \Big) \\
    & = \mathbb E(Y^*(1) (1-A) |A = 1) P(A = 1) + \mathbb E(Y^*(1) (1-A) |A = 0) P(A = 0) \\
    & = \mathbb E(Y^*(1) (1-1) |A = 1) P(A = 1) + \mathbb E(Y^*(1) (1-0) |A = 0) (1 - P(A = 1)) \\
    & = \mathbb E(Y^*(1)|A = 0) (1 -\pi(X))
\end{align}
$$

Thus by WLLN and  $X_n \stackrel{ \text{p}}{\rightarrow} X, \ Y_n \stackrel{ \text{p}}{\rightarrow} Y \Rightarrow X_nY_n \stackrel{ \text{p}}{\rightarrow} XY$,

$$
\begin{align}
\Big\{ \sum_{i=1}^n (1- A_i) \Big\}^{-1} & \sum_{i=1}^n \Big[ A_i \frac{ \Big( 1 - \pi(X_i) \Big) }{ \pi(X_i) } Y_i \Big] \stackrel{ \text{p}}{\rightarrow} \\
	& \frac{ 1 }{ 1 - \pi(X) } \mathbb E(Y^*(1)|A = 0) (1 -\pi(X)) = \mathbb E(Y^*(1)|A = 0).
\end{align}
$$



# 3
**Consider again the joint distribution of the potential outcomes $Y^\star(1), Y^\star(0), X$, and $A$ given in Problem 1. Identifying $H_1 = X$, consider treatment regime $d$ with rule $d_1(h_1) = 1$ if $h_1 = 1$ and $d_1(h_1) = 0$ if $h_1 = 0$. Find $E \\{ Y^\star(d) \\}$.**


$$
\begin{align}
E(Y^*(d)) & =E\Big(Y^*(1) \mathbb  I(d_1(h_1)=1) \Big) + E\Big(Y^*(0) \mathbb I (d_1(h_1) = 0)\Big) & (3.1)\\
    & = \left(\frac{1}{36}+\frac{1}{18}+\frac{1}{12}+\frac{1}{6}\right)+\left(\frac{1}{9}+\frac{1}{18}+\frac{1}{18}+\frac{1}{36}\right) \\
    & = \frac{ 7 }{ 12 }
\end{align}
$$

# 4
**Consider a fixed regime $d$ with true value $\mathcal V(d)$ and the "alternative" IPW estimator $\widehat{\mathcal{V}}_{IPW\star}(d)$ for the value of a fixed $d$ given in (3.14)**

## a
**Take the propensity $\pi_1(h_1)$ to be _known_. Under this condition, using M-estimation theory, find the limiting distribution of**

$$
n^{1/2} \{ \widehat{\mathcal{V}}_{IPW*}(d) - \mathcal V(d) \}
$$

**and give an expression for its variance.**


Recall that $\mathcal V(d) = \mathbb E(Y^*(d))$and 

$$
\widehat{\mathcal V}_{IPW*}(d) = \Big[ \sum_{i=1}^n \frac{ \mathcal C_{d,i} }{ \pi_{d,1}(H_{i1}) }\Big]^{-1}  \sum_{i=1}^n \frac{ \mathcal C_{d,i} Y_i }{ \pi_{d,1}(H_{i1}) } , \ (3.14). 
$$

Where 

$$
C_d = \mathbb I(A = d(H)) = A\mathbb I(d(H_i) = 1) + (1 - A) \mathbb I(d(H_i) = 0).
$$


Now we want to show that $\widehat {\mathcal V}\_{IPW\star}(d)$ is consistent for $\mathcal V(d)$. Then, by CLT the limiting distribution will be normal, and we will find the estimator asymptotic variance for $\widehat{\mathcal V}\_{IPW\star}(d)$. We can get these properties from M-estimation.

 
Since we know the propensity, we also know that

$$
\mathbb E \Big[ \frac{ \mathcal C_{d} Y }{ \pi_{d,1}(H; \widehat \gamma_1) } \Big] = \mathbb E(Y^*(d))
$$

by slide 130. And 

$$
\begin{align}
\mathbb E \Big[ \frac{ \mathcal C_{d} }{ \pi_{d,1}(H; \widehat \gamma_1) } \Big] & = \mathbb E \Big[ \mathbb E(\frac{ \mathcal C_{d} }{ \pi_{d,1}(H; \widehat \gamma_1) }|H_{1i}) \Big]\\
	& = \mathbb E( \frac{ 1 }{ \pi_{d,1} } \mathbb E(C_{d,i} | H_{1i})) \\
	& = \mathbb E(\frac{ 1 }{ \pi_{d,1} } \cdot P(C_{d,i} = 1 | H_{1i})) \\
	& = \mathbb E(\frac{ 1 }{ \pi_{d,1} } \cdot \pi_{d,1}) \\
	& = 1.
\end{align}
$$


Consider the estimating equation

$$
M(Y_i, \widehat{ \mathcal V}) = (Y_i - \widehat{\mathcal V}) \frac{ C_{d,i} }{ \pi_{d,i} }.
$$


Now we need to check that the expectation is 0 (that it is unbiased for $\mathcal V$).

$$
\begin{align}
\mathbb E(M(Y_i, \mathcal V_0)) & = \mathbb E \Big[ (Y_i - \widehat{\mathcal V}) \frac{ C_{d,i} }{ \pi_{d,i} } \Big] \\
	& = \mathbb E \Big[ Y_i   \frac{ C_{d,i} }{ \pi_{d,i} } \Big] -\mathbb E \Big[ \widehat{\mathcal V} \frac{ C_{d,i} }{ \pi_{d,i} } \Big] \\
	& = \mathbb E(Y^*(d)) - \mathcal V_0 \\
	& = \mathcal V(d) - \mathcal V_0 
 \end{align}
$$

In order for this expectation to be 0, we need $\mathcal V(d) = \mathcal V_0$, which is what we wanted. Thus we have consistency and asymptotic normality. Now we need to find the asymptotic variance.

From the first order Taylor expansion, the sandwich formula says that the variance will be

$$
\Sigma = \mathbb E\Big[ \frac{ \partial  M(Y_i, \mathcal V(d)) }{\partial \mathcal V(D)} \Big]^{-1} \mathbb E \Big[ M(Y, \mathcal V(d)) M(Y, \mathcal V(d)) ^T \Big] \mathbb E\Big[ \frac{ \partial  M(Y_i, \mathcal V(d)) }{\partial \mathcal V(D)} \Big]^{-T}.
$$


Notice that in this case we are working with scalars. Now we can work out each piece.

$$
\begin{align}
\frac{\partial  M(Y_i, \mathcal V(d)) }{\partial \mathcal V(D)} & = \frac{ \partial  }{\partial \mathcal V(d)} \frac{ C_d Y }{ \pi_{d,1})H_1 } - \frac{ C_d \mathcal V(d) }{ \pi_{d,1})H_1 } \\
	& = -\frac{ C_{d} }{ \pi_{d,1}(H_1) } \\ \\
 E\Big[ \frac{ \partial  M(Y_i, \mathcal V(d)) }{\partial \mathcal V(D)} \Big] & = E\Big[ -\frac{ C_{d} }{ \pi_{d,1}(H_1) } \Big] \\
 	& = -1
\end{align}
$$

Thus our asymptotic variance will be 

$$
\frac{ 1 }{ (-1)^2 } \mathbb E\Big[ \Big( \frac{ C_d(Y-\mathcal V(d)) }{ \pi_{d,1}(H_1) } \Big)^2 \Big]
$$

## b
**Now take the propensity $\pi_1(h_1)$ to be _unknown_ and modeled by a _correctly specified_ logistic regression model of the form**

$$
\pi_1(h_1; \gamma_1) = \frac{ \exp(\gamma_1^T \widetilde h_1) }{ 1 + \exp (\gamma_1^T \widetilde  h_1)}, \ \widetilde h_1 = (1, h_1^T)^T  
$$

**as in (3.12), and let $\widehat \gamma_1$ be the maximum likelihood estimator of $\gamma_1$.**

**Under this condition, using M-estimation theory, derive the limiting distribution of (1) and give an expression for its variance. Show that the variance you found in (a) is at least as large as the variance here, thus demonstrating the counterintuitive result noted on Slide 134 and more generally that it is preferable on ground of efficiency to estimate the propensity even if it is known.**

**_Hint:_ You will find it useful to write $\widehat{\mathcal{V}}\_{IPW \star}(d)$ in the simpler form suggested on Slide 133. Then express $\widehat{\mathcal{V}}_{IPW\star}(d)$ equivalently as the solution to an estimating equation and "stack" it with the score equation for ML estimate $\gamma_1$ (e.g. see Slide 109).**

We can start with the same estimating equations above

$$
\sum_{i=1}^n \frac{ C_{d,i} Y_i }{ \pi_{d,1}(H_{1i}) } - \frac{ C_{d,i} \widehat{\mathcal V}_{IPV*}(d)}{ \pi_{d,1}(H_{1i}) }
$$


We can use the simplification given by (3.15).

$$
\pi(H_{1i}) = \pi_1(H_{i1})^{d_1(H_{1i})} \Big( 1- \pi_{1}(H_{i1}\Big)^{1-d_{1}(H_{1i})}
$$

Then we can set up the estimating equation for $\gamma$ using the MLE / score

$$
\begin{align}
\ell \lambda_{1i}(h_{1i}; \gamma_1) & = \sum_{i=1}^n \gamma_1^T \widetilde{h}_{1i} - \log(1 + \exp(\gamma_1^T \widetilde h_1)) \\
\frac{ \partial  \ell }{\partial \gamma_1} & = \sum_{i=1}^n \widetilde h_{1i} - \frac{ 1 }{ 1 + \exp(\gamma_1 \sum_{i=1}^n \widetilde h_{1i}) } \stackrel{\text{set}}{=}0
\end{align}
$$

We would then stack them together and find the variance.

After reading the slides and the Boos-Stefanski book, I am still having some trouble setting these problems up. Once I get the estimators, then I know it'll be consistent and asymptotically normal. Then I can proceed to find the variance.

As opposed to part a, in this problem we will be estimating both $\gamma$ and $\mathcal V$, so we will have a stacked vector of estimating equations and an asymptotic covariance matrix (with probably some ugly sandwiching) instead of scalars.

Hopefully in a few weeks I'll be an expert in M-estimation and will be able to come back and figure this one out !



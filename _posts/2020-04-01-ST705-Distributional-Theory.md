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

Take $U_1, U_2 \sim \chi^2_{p_i}$ independent random variables. And take $X = U_1 / U_2$.


$$
\begin{align}
F_X & = P(X \leq x) \\
	& = P( U_1 / U_2 \leq x) \\
	& = P(U_1 \leq U_2 x) \\
	& = \int_{0}^{\infty} \int_{0}^{x u_2} f_{U_1, U_2} (u_1, u_2) du_1 du_2 \\ \\
f_X & = \int_{0}^{\infty} u_2 f_{U_1 , U_2}(x u_2, u_2) du_2 \\
	& = \int_{0}^{\infty} u_2 f_{U_1}(x u_2) f_{U_2}(u_2) du_2 \\
	& = \int_{0}^{\infty} u_2 \Big( \frac{ 1 }{ 2^{p_1 /2} \Gamma(p_1/2)} (u_2 x)^{p_1/2-1} e^{-x u_2/2} \Big) \Big( \frac{ 1 }{ 2^{p_2 /2} \Gamma(p_2/2)} (u_2)^{p_2/2-1} e^{- u_2/2} \Big) du_2 \\
	& = \frac{ x^{p_1/2-1} }{ \Gamma(p_1/2) 2^{p_1/2} \Gamma(p_2/2) 2^{p_2/2} } \int_{0}^{\infty} u_2^{p_1/2 + p_2/2 - 1} e^{-u_2(x+1)/2} du_2 \\
	& =  \frac{ x^{p_1/2-1} }{ \Gamma(p_1/2) 2^{p_1/2} \Gamma(p_2/2) 2^{p_2/2} } \frac{ \Gamma(p_1 /2 + p_2 /2) }{ (\frac{ z+1 }{ 2 })^{p_1 / 2 + p_2 / 2} } & \text{Gamma kernel} \\
	& = \frac{ \Gamma(\frac{ p_1 + p_2 }{ 2 }) x^{p_1/2-1}}{ \Gamma(\frac{ p_1 }{ 2 }) \Gamma(\frac{ p_2 }{ 2 }) (x+1)^{p_1/2 + p_2/2} }
\end{align}
$$

Then, $F = \frac{ U_1 / p_1 }{ U_2 / p_2 }$.

$$
\begin{align}
F_F(x) & = F_X(p_1 / p_2 x) \\
f_F & = \frac{ p_1 }{ p_2 } f_X(\frac{ p_1 }{ p_2 } x) \\
	& = \frac{ p_1}{ p_2 } \frac{ \Gamma(\frac{ p_1 + p_2 }{ 2 }) (\frac{ p_1 }{ p_2 } x)^{p_1/2-1}}{ \Gamma(\frac{ p_1 }{ 2 }) \Gamma(\frac{ p_2 }{ 2 }) (\frac{ p_1 }{ p_2 } x+1)^{p_1/2 + p_2/2} } \\
	& = \frac{ \Gamma(\frac{ p_1 + p_2 }{ 2 }) (\frac{ p_1 }{ p_2 })^{p_1/2} x^{p_1/2 -1} }{ \Gamma(\frac{ p_1 }{ 2 })\Gamma(\frac{ p_2 }{ 2 }) \Big( \frac{ p_1 }{ p_2 } x+1 \Big)^{\frac{ p_1 +p_2}{ 2 }} }
\end{align}
$$


# 5.10
**Find the density of the noncentral Student's t-distribution. Also find its mean and variance.**

Take $X \sim N(\mu, 1)$ and $Y \sim \chi^2_k$. Since they are independent, the joint distribution is the product of the marginals.


$$
f_{X,Y} = \frac{ 1 }{ \Gamma(k/2) 2^{\frac{ k+1 }{ 2 }} \sqrt{ \pi }} y^{k/2-1} e^{-\frac{ y +(x-\mu)^2 }{ 2 }}
$$

Then take $U = \frac{ X }{\sqrt{ Y/k }  } \sim T_k(1/2 \mu)$ and $V = \sqrt{ Y / k }$. Then $Y = kV^2$ and $X = UV$

$$
J = det\begin{bmatrix}
	\frac{ \partial  X }{\partial U } & \frac{ \partial  X  }{\partial V} \\
	\frac{ \partial  Y }{\partial U } & \frac{ \partial  Y}{\partial V}
\end{bmatrix} = det\begin{bmatrix}
	V & U\\
	0 & 2 kV
\end{bmatrix} = 2kV^2 
$$


$$
f_{U,V} = f_{x,y} 2KV^2
$$


$$
\begin{align}
f_U & = \int_{0}^{\infty} 2 kV^2\frac{ 1 }{ \Gamma(k/2) 2^{\frac{ k+1 }{ 2 }} \sqrt{ \pi }} (kV^2)^{k/2-1} e^{-\frac{ kV^2 +(UV-\mu)^2 }{ 2 }} dv \\
	& = \frac{ 2 k^{k/2} }{ \Gamma(k/2) 2^{\frac{ k+1 }{ 2 }} \sqrt{ \pi }} \int_{0}^{\infty}  (V)^{k} e^{-\frac{ kV^2 +(UV-\mu)^2 }{ 2 }} dv \\
\end{align}
$$


For the mean and variance variance recall that $Y \sim \chi^2_\nu = gamma(\frac{ \nu }{ 2 }, 2)$ and $X \sim N(\mu, 1)$ and $Y \perp X$. Then,

$$
\begin{align}
E(T) & = E(\frac{ X }{ \sqrt{ Y/\nu } }) \\
	&  = E(X) \sqrt{ \nu } E(Y^{-1/2}) \\
	& = \mu \sqrt{ \nu } \frac{ \Gamma(\frac{ \nu - 1 }{ 2 }) }{ \Gamma(\frac{ \nu }{ 2 }) \sqrt{ 2 }} \\ \\
E(T^2) & = E(\frac{ X^2 }{ Y / \nu }) \\
	& = E(X^2) \nu E(Y^{-1}) \\
	& = (\mu^1 + 1) \nu \frac{ Gamma(\frac{ \nu - 2 }{ 2 }) }{ \Gamma(\nu / 2) 2 } \\
	& = \frac{ (\mu^2 + 1) \nu }{ \nu - 2 } \\ \\
Var(T) & = \frac{ (\mu^2 + 1) \nu }{ \nu - 2 } - \Big( \mu \sqrt{ \nu } \frac{ \Gamma(\frac{ \nu - 1 }{ 2 }) }{ \Gamma(\frac{ \nu }{ 2 }) \sqrt{ 2 }} \Big)^2
\end{align}
$$


# 5.11
**Let $U \sim \chi^2_k (\phi)$; find its mean and variance. Confirm with Lemmas 4.1 and Result 4.6 (use $\sigma^2  =1$, $\gamma_3 = 0$, and $\gamma_4 = 3$).**

$$
M_U(t) = (1-2t)^{-k/2} e^{\frac{ 2 \phi t }{ 1 - 2 t }}
$$

$$
\begin{align}
E(U) & = \frac{ d }{ dt } M_U(t) |_{t=0} \\
	& = (1-2 t)^{-\frac{k}{2}-2} e^{\frac{2 t \phi }{1-2 t}} (-2 k t+k+2 \phi )|_{t=0} \\
	& = k + 2 \phi \\ \\
E(U^2) & = \frac{ d^2 }{ dt^2 } M_U(t) |_{t=0} \\
	& = (1-2 t)^{-\frac{k}{2}-4} e^{\frac{2 t \phi }{1-2 t}} \left(-4 (k+2) (2 t-1) \phi +k (k+2) (1-2 t)^2+4 \phi ^2\right) |_{t=0} \\
	& = k^2 + 4 \phi (2 + \phi) + k (2 + 4 \phi) \\ \\
Var(U) & = E(U^2) - E(U)^2 \\
	& = k^2 + 4 \phi (2 + \phi) + k (2 + 4 \phi) - \Big( k + 2 \phi \Big)^2 \\
	& = 2k + 8 \phi
\end{align}
$$

 Looking at Lemma 4.1 and result 5.9, we can take $A = I_n$ and $Z = N(\mu, I_p)$. Then our expected value is
 
 $$
 E(Z^T A Z) = \mu^T I_n \mu + tr(I_n I_n) = \mu^T \mu + n = 2 \phi + n.
 $$


This is the mean of a $\chi^2_n(\frac{ 1 }{ 2 }\mu^T \mu)$ distributed variable.
 

Looking at result 4.6 and result 5.9, we can take $P = I$ and $\mu + e \sim N(\mu, I_n)$. Then our variance is 

$$
4 \mu^T \mu + n(3 - 1) = 2 n + 4 \mu^T \mu = 2 n +4\cdot 2 \phi = 2 n + 8 \phi
$$

This is the variance of a $\chi^2_n(\frac{ 1 }{ 2 }\mu^T \mu)$ distributed variable.


# 5.12
**Let $X \sim N_p( \mu, V)$ with $V$ nonsingular, and let $U = X^T A X$ for $A$ symmetric.**


## a
**Show that the mgf of $U$ is $m_U(t) = \| I - 2tAV \|^{-1/2} exp\\{-\frac{ 1 }{ 2 }[\mu^T V^{-1} \mu - \mu^T(V - 2t VAV)^{-1} \mu]\\}$**

Take $V = L L^T$, then $Y = L^{-1} X \sim N_p(L^{-1} \mu, I_p)$.

$$
\begin{align}
E(e^{t (L^{-1} X)^T L^T A L L^{-1} X}) & = E(e^{y Y^T L^T A L Y}) \\
	& = \int e^{y Y^T L^T A L Y} (2 \pi)^{-p/2}e^{-1/2 (Y - L^{-1} \mu)^T(Y - L^{-1} \mu)} dy \\
\end{align}
$$

We can focus on the exponential part.

$$
\begin{align}
\exp[\frac{ 1 }{ 2 } (2 t Y^T L^T A L Y \\
+ 2 \mu^T (L^T)^{-1}Y - Y^T Y - \mu^T V^{-1} \mu)] & = \exp[\frac{ 1 }{ 2 }(-Y^T \underbrace{I-2tL^TAL}_{W}Y + 2 \mu^T (L^T)^{-1}Y - \mu^T V^{-1} \mu)] \\
	& = \exp[\frac{ -\mu^T V^{-1} \mu }{ 2 }] \exp[\frac{ 1 }{ 2 } (-W^T W + 2 \underbrace{\mu^T (LT)^{-1}(I-2tL^T A L)^{-1/2}}_{M^T} W] \\
	& = \exp[\frac{ -\mu^T V^{-1} \mu }{ 2 }] \exp[\frac{ 1 }{ 2 } (-W^T W + 2 \underbrace{\mu^T (LT)^{-1}(I-2tL^T A L)^{-1/2}}_{M^T} W \pm ||M||^2] \\
	& = \exp[\frac{ -\mu^T V^{-1} \mu }{ 2 }] \exp[-\frac{ 1 }{ 2 }(W-M)^T(W-M)] \exp[\frac{ 1 }{ 2 } \mu^T L^{-1} (I-2tL^TAL)^{-1}L^T \mu] \\ \\
\exp[\frac{ 1 }{ 2 } \mu^T L^{-1} (I-2tL^TAL)^{-1}L^T \mu] & = \exp[\frac{ 1 }{ 2 } \mu^T (L (I-2tL^TAL)L^T)^{-1} \mu] \\
	& = \exp[\frac{ 1 }{ 2 } \mu^T(V-2tVAV)^{-1} \mu] \\
W - M & = I- 2tL^T AL- (I-2tL^T A L)^{-1/2} L^{-1} \mu \\
	& = (I-2tL^T A L)^{-1/2}(Y - \underbrace{(I-2tL^T A L)^{-1} L^{-1} \mu}_{\widetilde \mu}) \\
(W-M)^T(W-M) & = (Y - \widetilde \mu)^T (I-2tL^T A L)^{-1} (Y -\widetilde \mu)
\end{align}
$$

Then,

$$
E(e^{t U}) = e^{\frac{ -\mu^T V^{-1} \mu }{ 2 }}  e^{\frac{ 1 }{ 2 } \mu^T(V-2tVAV)^{-1} \mu} \int (2 \pi)^{-p/2} e^{-1/2(y - \widetilde \mu)^T(I-2tL^T A L)(y - \widetilde \mu)}dy.
$$

This integral is the kernel of $N_n(\widetilde \mu,(I-2tL^T A L)^{-1})$. Thus, our MGF is,

$$
\begin{align}
M_U(t) & = e^{\frac{ -\mu^T V^{-1} \mu }{ 2 }}  e^{\frac{ 1 }{ 2 } \mu^T(V-2tVAV)^{-1} \mu} |I - 2tL^TAL|^{-1/2} \\
	& = e^{\frac{ -\mu^T V^{-1} \mu }{ 2 }}  e^{\frac{ 1 }{ 2 } \mu^T(V-2tVAV)^{-1} \mu} (|L^T| |(L^T)^{-1} - 2tAL|)^{-1/2} \\
	& = e^{\frac{ -\mu^T V^{-1} \mu }{ 2 }}  e^{\frac{ 1 }{ 2 } \mu^T(V-2tVAV)^{-1} \mu} (|(L^T)^{-1} - 2tAL||L^T| )^{-1/2} \\
	& = e^{\frac{ -\mu^T V^{-1} \mu }{ 2 }}  e^{\frac{ 1 }{ 2 } \mu^T(V-2tVAV)^{-1} \mu} |I - 2tAV| ^{-1/2} \\
	& = | I - 2tAV |^{-1/2} e^{-\frac{ 1 }{ 2 }[\mu^T V^{-1} \mu - \mu^T(V - 2t VAV)^{-1} \mu]}
\end{align}
$$

## b
**Show that if $A \mu = 0$, then $m_U(t) = \|I-2tAV \|^{-1/2}$.**

We want to show that

$$
e^{-\frac{ 1 }{ 2 }[\mu^T V^{-1} \mu - \mu^T(V - 2t VAV)^{-1} \mu]} = 1
$$


or, equivalently,

$$
\mu^T V^{-1} \mu - \mu^T(V - 2t VAV)^{-1} \mu = 0.
$$


We will show that $\mu^T(V - 2t VAV)^{-1} \mu = \mu^T V^{-1} \mu$.

$$
\begin{align}
\mu^T(V - 2t VAV)^{-1} \mu & = \mu^T((I - 2t VA)V)^{-1} \mu \\
	& = \mu^T V^{-1} (I - 2t VA)^{-1} \mu \\
	& = \mu^T V^{-1} (V^{-1} - 2tA)^{-1} V^{-1}\mu.
\end{align}
$$

From here we will use the Sherman-Morrison-Woodbury Identity.

$$
(Q + W E R)^{-1} = Q^{-1} -  Q^{-1} W(E^{-1}+R Q^{-1} W)^{-1} R Q^{-1}
$$

Take $V^{-1} = Q$, $W = -2t I$, $E = I$, and $R = A$. Then,

$$
\begin{align}
\mu^T(V - 2t VAV)^{-1} \mu & = \mu^T V^{-1} \Big( V  -V 2tI(I^{-1} +  AV 2t I)^{-1} AV \Big) V^{-1}\mu \\
	& = \mu^T V^{-1} \Big( V V^{-1} \mu -V 2tI(I^{-1} +  AV 2t I)^{-1} AV V^{-1}\mu \Big)\\ 
	& = \mu^T V^{-1} \Big( \mu +V 2tI(I^{-1} -  AV 2t I)^{-1} A I \mu \Big)\\ 
	& = \mu^T V^{-1} \Big( \mu +V 2tI(I^{-1} -  AV 2t I)^{-1} (A \mu) \Big)\\ 
	& = \mu^T V^{-1} \Big( \mu +V 2tI(I^{-1} -  AV 2t I)^{-1} (0) \Big)\\ 
	& = \mu^T V^{-1} \mu.
\end{align}
$$


Thus,

$$
m_U(t) = |I-2tAV |^{-1/2}.
$$

# 5.14
**Using the result of Exercise 5.12, show that**

## a
$$Var(X^T A X) = 2 tr(AV)^2 + 4 \mu^T AVA \mu$$

We will need a few derivative properties from the matrix cookbook.

$$
\begin{align}
\frac{ \partial  X^{-1} }{\partial t} & = -X^{-1} \frac{ \partial  X }{\partial t} X^{-1} & (40) \\
\frac{ \partial  \det(Y) }{\partial t} & = \det(Y) Tr\Big[ Y^{-1}  \frac{ \partial  Y }{\partial t}\Big] & (46)
\end{align}
$$

Also define $x(t) = \mu^T V^{-1} \mu - \mu^T(V-2tVAV)^{-1} \mu$. Notice that $x(0) = 0$.

Then,

$$
\begin{align}
E(U) & = \frac{ \partial  M_U(t) }{\partial t} |_{t=0} \\
	& = \frac{ \partial   }{\partial t} | I - 2tAV |^{-1/2} e^{-\frac{ 1 }{ 2 }[\mu^T V^{-1} \mu - \mu^T(V - 2t VAV)^{-1} \mu]} |_{t=0} \\ \\
\frac{ \partial   }{\partial t} | I - 2tAV |^{-1/2} & = -\frac{ 1 }{ 2 } |I-2tAV|^{-3/2} \frac{ \partial  |I-2tAV| }{\partial t}\\
	& = -\frac{ 1 }{ 2 } |I-2tAV|^{-1/2} Tr \Big( (I-2tAV)^{-1} \frac{ \partial  I-2tAV }{\partial t} \Big) \\
	& = -\frac{ 1 }{ 2 } |I-2tAV|^{-1/2} Tr \Big( (I-2tAV)^{-1} (-2AV) \Big) \\
	& = |I-2tAV|^{-1/2} Tr \Big( (I-2tAV)^{-1} AV \Big) \\ \\
\frac{ \partial  }{\partial t} e^{-\frac{ 1 }{ 2 }x} & = e^{-\frac{ 1 }{ 2 }x} \frac{ -1 }{ 2 }(\mu^T \cdot - (V-2tVAV)^{-1} (-2VAV)(V-2tVAV)^{-1}\mu) \\
	& = e^{-\frac{ 1 }{ 2 }x} (\mu^T (V-2tVAV)^{-1} (VAV)(V-2tVAV)^{-1}\mu) \\ \\
E(U) & = |I-2tAV|^{-1/2} Tr \Big( (I-2tAV)^{-1} AV \Big) e^{-\frac{ 1 }{ 2 } x} \\
	& + | I - 2tAV |^{-1/2} e^{-\frac{ 1 }{ 2 }x} (-\mu^T (V-2tVAV)^{-1} (VAV)(V-2tVAV)^{-1}\mu) |_{t=0} \\
	& = Tr(AV) + \mu^T A \mu \\ \\
E(U^2)& = \frac{ \partial^2  M_U(t) }{\partial^2 t} |_{t=0} \\
	& = |I-2tAV|^{-1/2} Tr \Big( (I-2tAV)^{-1} AV \Big)^2 e^{- x} \\
	& + |I-2tAV|^{-1/2} Tr \Big( 2 AV (I-2tAV)^{-1} AV (I-2tAV)^{-1} \Big) e^{-\frac{ 1 }{ 2 } x} \\
	& + |I-2tAV|^{-1/2} Tr \Big( (I-2tAV)^{-1} AV \Big) e^{-\frac{ 1 }{ 2 } x} (\mu^T (V-2tVAV)^{-1} (VAV)(V-2tVAV)^{-1}\mu) \\
	& + |I-2tAV|^{-1/2} Tr \Big( (I-2tAV)^{-1} AV \Big) e^{-x} (\mu^T (V-2tVAV)^{-1} (VAV)(V-2tVAV)^{-1}\mu) \\
	& + |I-2tAV|^{-1/2} e^{-x} (\mu^T (V-2tVAV)^{-1} (VAV)(V-2tVAV)^{-1}\mu)^2 \\
	& + |I-2tAV|^{-1/2} e^{-\frac{ 1 }{ 2 }x} \Big(\mu^T (V-2tVAV)^{-1} (VAV)(V-2tVAV)^{-1}(-2 VAV)(V-2tVAV)^{-1}\mu + -\mu^T (V-2tVAV)^{-1} (VAV)(V-2tVAV)^{-1}(-2 VAV)(V-2tVAV)^{-1}\mu \Big) |_{t=0} \\
	& = Tr(AV)^2 + Tr(2AVAV) + Tr(AV)(\mu^T A \mu) - Tr(AV) \mu^T A \mu+ (\mu^T A \mu)^2 + 4 \mu^T AVA \mu \\
	& = Tr(AV)^2 + 2 Tr(AV) \mu^T A \mu + (\mu^T A \mu)^2 + 4 \mu^T AVA \mu \\ \\
Var(U) & = E(U^2) - E(U)^2 \\
	& = Tr(AV)^2 + Tr(2AVAV) + 2 Tr(AV) \mu^T A \mu + (\mu^T A \mu)^2 + 4 \mu^T AVA \mu - (Tr(AV) - \mu^T A \mu)^2 \\
	& = Tr(AV)^2 + 2 Tr(AV) \mu^T A \mu + (\mu^T A \mu)^2 + 4 \mu^T AVA \mu - Tr(AV)^2 + 2 Tr(AV) (\mu^T A \mu) - (\mu^T A \mu)^2 \\
	& = Tr(AV)^2 - Tr(AV)^2 \\
	& + - 2 Tr(AV) \mu^T A \mu + 2 Tr(AV) (\mu^T A \mu) \\
	& + (\mu^T A \mu)^2 - (\mu^T A \mu)^2 \\
	& + 4 \mu^T AVA \mu  \\
	& = Tr(AV)^2 - Tr(AV)^2 + Tr(2AVAV) + 4 \mu^T AVA \mu \\
	& = 2Tr(AV)^2 + \mu^T AVA \mu.
\end{align}
$$






## b
**(Easier) If $X \sim N_p(0, V)$, then $Var(X^TAX)=2 tr(AV)^2$.**

From (a), if $Var(X^T A X) = 2 tr(AV)^2 + 4 \mu^T AVA \mu$ and $\mu = 0$, then,

$$
Var(X^T A X) = 2 tr(AV)^2 + 4 \mu^T AVA \mu = Var(X^T A X) = 2 tr(AV)^2+ 4 0^T AVA 0 = 2 tr(AV)^2.
$$


# 5.16
**Prove a converse to Result 5.16, assuming $V$ to be non-singular.**

Since they are independent, we know that 

$$
\begin{align}
BVQ_1 & = 0 \\
BVQ_1 \Lambda_1 Q^T & = 0 \Lambda_1 Q^T \\
BVA & = 0.
\end{align}
$$


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

**Show that the conditional distribution of $X_1$ given $X_2 = x_2$ is multivariate normal with mean vector $\mu_1 + V_{12}V_{22}^{-1} (x_2 - \mu_2)$ and covariance matrix $V_{11} - V_{12}V_{22}^{-1}V_{21}$. Hint: Use the partitioned inverse result from Exercise A.72.**

We want to find 

$$
f(X_1 | X_2 = x_2) = \frac{ f_{X_1, X_2} }{ f_{X_2} }.
$$

We know that $X_1$ and $X_2$ are independent based on the definition of a multivariate normal distribution.

$$
f(X_1 | X_2 = x_2) = \frac{ (2\pi)^{-p/2} |V|^{-1/2} e^{-1/2 (x-\mu)^T V^{-1}(x-\mu)} }{ (2\pi)^{-p_2/2} |V_{22}|^{-1/2} e^{-1/2 (x_2-\mu_2)^T V^{-1}(x_2-\mu_2)} }.
$$

We can rewrite $\|V\|^{-1/2} = \|V_{22}\|^{-1/2} \|V_{11} - V_{12} V_{22}^{-1}V_{21}\|^{-1/2}$. Thus the constant term out front simplifies to

$$
(2 \pi)^{-p_1/2} |V_{11} - V_{12} V_{22}^{-1}V_{21}|^{-1/2}.
$$


Take 

$$
\begin{align}
V & = 
\begin{bmatrix}
	V_{11} & V_{12} \\
	V_{21} & V_{22}
\end{bmatrix} \\
	& = \begin{bmatrix}
	A & B \\
	C & D
\end{bmatrix} \\ \\

V^{-1} & = \begin{bmatrix}
	A^{-1} + A^{-1} B E^{-1} C A^{-1} & -F^{-1} B D^{-1} \\
	-D^{-1} C F^{-1} & -D^{-1}+D^{-1} C F^{-1} B D^{-1}
\end{bmatrix}.
\end{align}
$$

Where $E = D - CA^{-1} B$ and $F = A - BD^{-1}C$. Then our numerator exponent looks like

$$
\begin{align}
-1/2 (x-\mu)^T V^{-1}(x-\mu) & = -1/2 \begin{bmatrix}x_1 - \mu_1 & x_2 - \mu_2 \end{bmatrix}V^{-1}(x-\mu) \begin{bmatrix} x_1 - \mu_1 \\ x_2 - \mu_2\end{bmatrix} \\
	& = \frac{ -1 }{ 2 }\Big[ (x_1 - \mu_1)^T (A^{-1} + A^{-1} B E^{-1} C A^{-1}) (x_1 - \mu_1) + (x_1 - \mu_1)^T (-D C ^{-1})(X_2 - \mu_2) + (x_2 - \mu_2)^T(-F^{-1}C D^{-1})(x_1 - \mu_1)+(x_2-\mu_2)^T(-D^{-1}+D^{-1} C F^{-1} B D^{-1})(x_2-\mu_2) \Big] \\
	& = \frac{ -1 }{ 2 }\Big[ (x_1 - \mu_1)^T (A^{-1} + A^{-1} B E^{-1} C A^{-1}) (x_1 - \mu_1) + 2(x_1 - \mu_1)^T (-D C ^{-1})(X_2 - \mu_2) + (x_2-\mu_2)^T(D^{-1} C F^{-1} B D^{-1})(x_2-\mu_2)-(x_2-\mu_2)^T D^{-1}(x_2-\mu_2) \Big] \\
	& = \frac{ -1 }{ 2 }\Big[ (x_1 - \mu_1 + B D^{-1} (x_2 - \mu_2))^T F^{-1}(x_1 - \mu_1 + B D^{-1} (x_2 - \mu_2))-(x_2-\mu_2)^T D^{-1}(x_2-\mu_2) \Big].
\end{align}
$$

The last simplification comes from simplifying the variance terms and from the fact that, for symmetric $M$,

$$
x^T M x - 2 x^T M y + y^T M y = (y-x)^T M (y-x).
$$


Then the exponential term in the bottom of our conditional distribution will cancel and we will be left with

$$
f(X_1 | X_2 = x_2) = (2 \pi)^{-p_1/2} |V_{11} - V_{12} V_{22}^{-1}V_{21}|^{-1/2} e^{\frac{ -1 }{ 2 }\Big[ (x_1 - \mu_1 + V_{12} V_{22}^{-1} (x_2 - \mu_2))^T (V_{11} - V_{12} V_{22}^{-1}V_{21})^{-1}(x_1 - \mu_1 + V_{12} V_{22}^{-1} (x_2 - \mu_2)) \Big]}.
$$

Thus, $X_1 \| X_2 = x_2 \sim N(\mu_1 + V_{12} V_{22}^{-1} (x_2 - \mu_2), V_{11} - V_{12} V_{22}^{-1}V_{21})$.


# 5.25
**Show that $R^2$ given by (5.12) is also equal to the right-hand side of (5.11).**

Take $X$ to be our $n \times p$ design matrix, including an intercept column. Also note that the column vector $1_n$ has the projection matrix

$$
P_{1_n} = \frac{ 1 }{ n } \begin{bmatrix}
	1 & \dots &  1\\
	\vdots & \ddots & \vdots \\
	1 & \dots & 1
\end{bmatrix}.
$$

Also notice that $P_{1_n} y \in \text{ column }( 1_n ) \subseteq \text{ column }( X )$. 

Thus, $\mu P_X  P_{1\_n}y = P_{1_n} y$. Further,

$$
\begin{align}
y^T (P_X - P_{1_n}) y & = y^T (P_X y - P_{1_n} y) \\
	&= y^T(P_X y - P_X P_{1_n} y) \\
	& = (P_X y)^T (y - P_{1_n}y) \\
	& = (\widehat y)^T (y - P_{1_n}y) \\
	& = \sum_{i=1}^{n} \widehat y_{i} (y_i - \overline{ y }) \\
	& = \sum_{i=1}^{n} \widehat y_{i} (y_i - \overline{ y }) + \underbrace{\sum_{i=1}^{n} \overline{ y_{i} } (y_i - \overline{ y })}_{=0} \\
	& = \sum_{i=1}^{n} (\widehat y_i - \overline{ y })(y_i  - \overline{ y }).
\end{align}
$$

Notice that

$$
(P_X - P_{1_n} )y = P_X y - P_{1_n}y = \widehat y - \overline{ y } 1_n.
$$

So,

$$
\begin{align}
\sum_{i=1}^n (\widehat y_i - \overline{ y })^2 & = ||(P_X - P_{1_n}) y ||^2 \\
	& = y^T(P_X - P_{1_n})^T(P_X - P_{1_n}) y \\
	& = y^T P_X y - y^T P_{1_n} P_X y - y^T P_X P_{1_n} y + y^T P_{1_n} y \\
	& = y^T (P_X - P_{1_n}) y \\
	& = \sum_{i=1}^{n} (\widehat y_i - \overline{ y })(y_i  - \overline{ y }).
\end{align}
$$


Thus,

$$
R^t = \frac{ \Big( \sum_{i=1}^n  (\widehat y_i - \overline{ y })(y_i  - \overline{ y }) \Big)^2 }{  \sum_{i=1}^n  (\widehat y_i - \overline{ y })^2 \sum_{i=1}^n (y_i  - \overline{ y })^2 } = \frac{\sum_{i=1}^n  (\widehat y_i - \overline{ y })(y_i  - \overline{ y }) }{  \sum_{i=1}^n (y_i  - \overline{ y })^2 } = \frac{ y^T (P_X -P_{1_n} )y }{ y^T (I_n - P_{1_n})y }
$$


# 5.27
**Prove Corollary 5.4.**

By Corollary 5.3, take $Y_1 = X^T B X$ and $Y_2 = X^T A X$. Then,

$$
(X^T B) V (X^T A)^T = X^T B V A^T X = X^T B V A X = X^T 0 X = 0.
$$
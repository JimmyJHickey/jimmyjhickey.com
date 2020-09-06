---
layout: post
comments: false
title: Example Problems on Asymptotic Variance
description: ST793 Homework 3 on Asymptotic Variance
tags: ST793 Likelihoods Statistics
category: ST793
---

* Do not remove this line (it will not be displayed)
{:toc}

2.34 , 2.35, 2.42, 2.44, 2.47  

# 2.34
**Continuation of problem 2.2 p107.**

## a
**Find an estimate of the asymptotic covariance of $\widehat \mu, \widehat \sigma$. Here it helps to know that the Fisher information matrix has elements $I(\mu, \sigma)\_{11} =1 / \sigma^2, \ I(\mu, \sigma)\_{12} = -0.423 / \sigma^2, \ I(\mu, \sigma)\_{22} = 1.824/\sigma^2$.**

Recall that our MLEs are $\widehat \mu = 4395.147$ and $\widehat \sigma = 1882.499$. Then we can find our asymptotic covariance.

$$
\begin{align*}
\text{AsyCov}(\widehat \mu, \widehat \sigma^2) & = \frac{ 1 }{n  }  I^{-1}(Y, \mu, \sigma^2) \\
  & \approx \frac{1}{35  }  \widehat \sigma^2
  \begin{bmatrix}
  1 & -0.423 \\
  -0.423 & 1.824
  \end{bmatrix}^{-1} \\
  & = \frac{  1}{ 35 } 1882.499^2 
      \begin{bmatrix}
       112264 & 26035 \\
       26035 & 61548.4 \\
      \end{bmatrix} \\
  & = 1882.499^2 
  \begin{bmatrix}
  0.031679 & 0.00734662 \\
  0.00734662 & 0.0173679
  \end{bmatrix} \\
  & = \begin{bmatrix}
    112264 & 26035 \\
    26035 & 61548.4
  \end{bmatrix}
\end{align*}
$$

## b
**Estimate the median of the distribution of the largest flow rate in 100 years.**

$$
\widehat Q = \widehat \sigma [-\log(-\log(0.993))] + \widehat \mu.
$$

See c.



## c.
**Find an estimate of the variance of $\widehat Q$**

Notice that

$$
\begin{bmatrix}
\widehat \mu \\
\widehat \sigma
\end{bmatrix} \sim
N_2 \Big( 
\begin{bmatrix}
\mu \\
\sigma
\end{bmatrix},
\sigma^2
\begin{bmatrix}
  0.031679 & 0.00734662 \\
  0.00734662 & 0.0173679
\end{bmatrix}
\Big).
$$

Thus, 

$$
\begin{align*}
\widehat Q & = 
\begin{bmatrix}
1 & -\log(-\log(0.993))
\end{bmatrix} 
\begin{bmatrix}
\widehat \mu \\
\widehat \sigma
\end{bmatrix} \\
& \sim N \Big(\widehat\mu - \widehat \sigma (-\log(-\log(0.993))) , \\
& 
\begin{bmatrix}
1 & -\log(-\log(0.993))
\end{bmatrix}
\widehat \sigma^2
\begin{bmatrix}
  0.031679 & 0.00734662 \\
  0.00734662 & 0.0173679
\end{bmatrix}
\begin{bmatrix}
1 & -\log(-\log(0.993))
\end{bmatrix} ^T
\Big) \\
& = N\Big( 4395.147 - 1882.499 (-\log(-\log(0.993))) , \\
& \widehat \sigma^2 \left(
\begin{array}{cc}
 1 & -\log (-\log (0.993)) \\
\end{array}
\right).\left(
\begin{array}{cc}
 0.031679 & 0.00734662 \\
 0.00734662 & 0.0173679 \\
\end{array}
\right).\left(
\begin{array}{cc}
 1 & -\log (-\log (0.993)) \\
\end{array}
\right)^T \Big) \\
& = N(13729.2, 1883617)
\end{align*}
$$

Since this is a normal distribution, the median is the mean.

# 2.35
**Derive the Fisher information matrix $I(\theta)$ for the reparameterized ZIP model**

$$
\begin{align}
P(Y = 0)& = \pi \\
P(Y = y)& = \Big( \frac{ 1 - \pi }{ 1 - e^{-\lambda} } \Big) \frac{ \lambda^y e^{-\lambda} }{ y! } & y = 1, 2, \dots
\end{align}
$$


**The (2,2) element of $I(\theta)$ is**

$$
(1-\pi) \Big( \frac{ 1 }{ \lambda(1- e^{-\lambda}) } - \frac{ e^{-\lambda} }{ (1-e^{-\lambda})^2 } \Big)
$$


$$
\begin{align}
\log (f(y;\lambda, \pi)) & = \log(\pi) \mathbb I(Y = 0) + \Big[ \log(1 - \pi) - \log(e^{\lambda} - 1 ) + y \log(\lambda) - \log(y !) \Big] \mathbb I(Y>0) \\ \\
\frac{ \partial  \log (f(y;\lambda, \pi)) }{\partial \lambda} & = \Big( \frac{ -1 }{ 1-e^{-\lambda} } + \frac{ y }{ \lambda }\Big) \mathbb I(Y > 0)\\
\frac{ \partial^2  \log (f(y;\lambda, \pi)) }{\partial \lambda^2} & = \Big( \frac{ e^{-\lambda} }{ (1-e^{-\lambda} )^2} - \frac{ y }{ \lambda^2 }\Big) \mathbb I(Y > 0)\\
\frac{ \partial  \log (f(y;\lambda, \pi)) }{\partial \pi} & = \frac{ 1 }{ \pi } \mathbb I(Y = 0) - \frac{ 1 }{ 
(1-\pi)^2 } \mathbb I(Y > 0)\\
\frac{ \partial^2 \log (f(y;\lambda, \pi)) }{\partial \pi^2} & =  \frac{ -1 }{ \pi^2 } \mathbb I(Y = 0) - \frac{ 1 }{ 1-\pi } \mathbb I(Y > 0)\\
\frac{ \partial^2 \log (f(y;\lambda, \pi)) }{\partial \lambda \pi} & = 0
\end{align}
$$

Notice that 

$$
\begin{align}
\mathbb E(Y) & = 0 + \mathbb E(Y | Y > 0) \\
    & = \frac{ 1-\pi }{ 1-e^{-\lambda} } \sum_{y=1}^\infty \frac{ y \lambda^y e^{-\lambda} }{ y! } \\
    & = \frac{ 1-\pi }{ 1-e^{-\lambda} } \sum_{y=0}^\infty \frac{ y \lambda^y e^{-\lambda} }{ y! } \\
    & = \frac{ 1-\pi }{ 1-e^{-\lambda} } \lambda & \text{Poisson expectation}
\end{align}
$$

Recall $\mathbb E(\mathbb I(Y = 0)) = \pi$ and $\mathbb E(\mathbb I(Y > 0))=1 -P(Y = 0) = 1- \pi$.

$$
\begin{align}
- \mathbb E \Big(\frac{ \partial^2  \log (f(y;\lambda, \pi)) }{\partial \lambda^2}\Big) & =  -\frac{ (1-\pi) e^{-\lambda} }{ (1-e^{-\lambda} )^2} + \frac{ 1 }{ \lambda^2 } \frac{ (1-\pi) \lambda }{ 1-e^{-\lambda} }\\
    & = (1 -\pi) \Big( \frac{ 1 }{ \lambda(1 - e^{-\lambda}) } - \frac{ e^{-\lambda} }{ (1-e^{-\lambda})^2 } \Big)\\
- \mathbb E \Big(\frac{ \partial^2  \log (f(y;\lambda, \pi)) }{\partial \pi^2}\Big) & = \frac{ \pi }{ \pi^2 } + \frac{ 1 - \pi }{ (1-\pi)^2 } \\
    & = \frac{ 1 }{ \pi(1-\pi) }
\end{align}
$$

So, 

$$
I = \begin{bmatrix}
\frac{ 1 }{ \pi(1-\pi) } & 0 \\
0 & (1 -\pi) \Big( \frac{ 1 }{ \lambda(1 - e^{-\lambda}) } - \frac{ e^{-\lambda} }{ (1-e^{-\lambda})^2 } \Big)
\end{bmatrix}
$$


# 2.42
**Use simulation to verify that the inverse information matrix Example 2.21 (p. 78) is correct when $\mu = 1$ and $\sigma = 1$. One approach is to generate samples of size $n=100$ (or larger) form a $\text{normal}(1,1)$ distribution and exponentiate to get lognormal data. Then form the log likelihood and find the estimates $\mu, \sigma^2, \lambda$. Repeat for 1000 replications giving a data matrix of size 1000 by 3 estimates. Compute the sample covariance matrix of these and compare it to the inverse of the given information matrix.**

See code https://github.com/JimmyJHickey/grad-scripts/blob/master/st793-advanced-inference/hw3/hw3.R.



# 2.44
**Continuing the last problem, show that the Fisher information matrix for the $\beta$ part of the generalized linear model is given by**

$$
\overline{ I }(\beta) = \frac{ 1 }{ n } \sum_{i=1}^n \frac{ D_i D_i^T }{ \text{Var}(  Y_i ) }
$$

**Here you can use either of two methods: a) take the expectation of the negative of the derivative of $S(\beta, \phi)$, and noting that all the ugly derivatives drop out because $E(Y_i - \mu_i) = 0$. or b) the individual summed components of $\overline{ I }(\beta)$ can also be found using the cross-product definition of information in (2.39 p. 67).**


Recall that $\theta_i = b'^{-1}\Big(g^{-1}(x_i^T \beta) \Big)$. Then, 

$$
\begin{align}
\log(f(y_i; \theta_i, \phi)) & = \frac{ y_i \theta_i - b(\theta_i)}{ a_i(\phi) } + c(y_i, \phi) \\
    & = \frac{ y_i  b'^{-1}\Big(g^{-1}(x_i^T \beta) \Big) - b\Big( b'^{-1}\Big(g^{-1}(x_i^T \beta) \Big)\Big)}{ a_i(\phi) } + c(y_i, \phi) \\ \\
\frac{ \partial  }{\partial \beta^T} \log(f(y_i; \theta_i, \phi)) & = \frac{ y_i b''^{-1}\Big(g^{-1}(x_i^T \beta) \Big)g^{-1}(x_i^T \beta) x_i}{a_i(\phi)} \\
    & - \frac{b'\Big( b'^{-1}(g^{-1}(x_i^T \beta)) \Big) b''^{-1}(g^{-1}(x_i^T \beta))g'^{-1}(x_i^T \beta)x_i}{ a_i(\phi) } \\
    & = \frac{ y_i b''^{-1}\Big(g^{-1}(x_i^T \beta) \Big)g^{-1}(x_i^T \beta) x_i}{a_i(\phi)}- \frac{b''^{-1}(g^{-1}(x_i^T \beta))g'^{-1}(x_i^T \beta)x_i}{ a_i(\phi) } \\ \\
\frac{ \partial \ell }{\partial \beta^T} & = \sum_{i=1}^n \frac{ 1 }{ a_i(\phi) } \Big( \frac{ y_i }{ b''(\mu_i) } \frac{ \partial \mu_i }{\partial \beta^T} - \frac{ \mu_i }{ b''(\mu_i) } \frac{ \partial \mu_i }{\partial \beta^T}\Big) \\
    & = \sum_{i=1}^n \Big[ \frac{ \partial \mu_i }{\partial \beta^T} \Big( \frac{ y_i - \mu_i }{ a_i(\phi)b''(\mu_i) } \Big) \Big] \\ \\
\frac{ \partial S }{\partial \beta} & = \sum_{i=1}^n \Big[ \frac{ \partial^2 \mu_i}{\partial \beta \partial \beta^T} \Big( \frac{ y_i - \mu_i }{ a_i(\phi)b''(\mu_i) } \Big) \\
    & - \frac{ \partial \mu_i }{\partial \beta^T} \Bigg( \frac{ a_i(\phi) b''(\mu_i) \frac{ \partial \mu_i }{\partial \beta} - (y_i - \mu_i) \frac{ \partial b''(\mu_i) }{\partial \mu_i} \frac{ \partial \mu_i }{\partial \beta} a_i(\phi)}{ \Big( a_i(\phi) b''(\mu_i) \Big)^2 } \Bigg)\Big] \\
- \mathbb E(\frac{ \partial S }{\partial \beta}) & = \sum_{i=1}^n 0 + \frac{ \partial \mu_i }{\partial \beta} \frac{ a_i(\phi) b''(\mu_i) \frac{ \partial \mu_i }{\partial \beta} }{ a_i(\phi) b''(\mu_i)^2 } \\
    & = \sum_{i=1}^n \frac{ D_i D_i^T }{ Var(Y_i)  } \\ \\
\overline{ I } & = \frac{ 1 }{ n }\sum_{i=1}^n \frac{ D_i D_i^T }{ Var(Y_i)  }
\end{align}
$$


# 2.47
**A mixture of three component densities has the form**

$$
f(y; \theta, p) = p_1 f_1(y; \theta) + p_2 f_2(y; \theta) + p_3 f_3(y; \theta)
$$

**where $p_1 + p_2 + p_3 = 1$. We observe an iid sample $Y_1, \dots , Y_n$ from $f(y; \theta, p)$.**

## a
**Show how to define multinomial$(1; p_1, p_2, p_3)$ vectors $(Z_{i1}, Z_{i2}, Z_{i3})$ to get a representation for the $Y_i$ from $f(y; \theta, p)$ based on independent random variables $X_{i1}, X_{i2}, X_{i3}$ from the individual components.**

We can redefine our random variable as

$$
Y_i = Z_{1i} X_{1i} + Z_{2i} X_{2i} + Z_{3i} X_{i3}.
$$

Where $X_i \sim f_i(x; \theta)$ and $\begin{bmatrix} Z_1 & Z_2 & Z_3\end{bmatrix}^T \sim \text{Multinomial}(1, p_1, p_2, p_3)$. Then we can rewrite our mixture distribution as

$$
f(y; \theta) = (p_1 f_1(y; \theta))^{Z_1} + (p_2 f_2(y; \theta))^{Z_2} + (p_3 f_3(y; \theta))^{Z_3}.
$$

## b
**Give the complete data log likelihood and the function $Q$ to be maximized at the M step.**

Our complete log likelihood will be

$$
\begin{align}
\log(L_C(\theta | Y, Z)) &  \sum_{i=1}^n \Big[ z_{1i} \log(f_1(y_i;\theta)) + z_{2i} \log(f_2(y_i;\theta)) + z_{3i} \log(f_3(y_i;\theta)) \\
    & + z_{1i} \log(p_1) + z_{1i} \log(p_2) + z_{1i} \log(p_3) \Big].
\end{align}
$$

Finally,

$$
\begin{align}
Q(\theta, \theta^{(\nu), Y }) & = \mathbb E_{\theta^{(\nu)}}(\log(L_C(\theta | Y, Z)) \\
    & =  \sum_{i=1}^n \Big[ w_{1i}^{(\nu)} \log(f_1(y_i;\theta)) + w_{2i}^{(\nu)} \log(f_2(y_i;\theta)) + w_{3i}^{(\nu)} \log(f_3(y_i;\theta)) \\
    & + w_{1i}^{(\nu)} \log(p_1) + w_{2i}^{(\nu)} \log(p_2) + w_{3i}^{(\nu)} \log(p_3) \Big] \\ \\
w_{ji}^{(\nu)} & = \frac{ p_{j}^{(\nu)} f_j(Y_i; \theta) }{ \sum_{k=1}^3 p_{k}^{(\nu)} f_k(Y_i; \theta) }.
\end{align}
$$

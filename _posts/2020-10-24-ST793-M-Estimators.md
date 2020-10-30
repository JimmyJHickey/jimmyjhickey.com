---
layout: post
comments: false
title: Example Problems on M-Estimators
description: ST793 Homework 9 on M-Estimators
tags: ST793 Statistics M-Estimators
category: ST793
---

* Do not remove this line (it will not be displayed)
{:toc}


# 7.7
**The generalized method of moments (GMM) is an important estimation method found mainly in the econometrics literature and closely related to M-estimation. Suppose that we have iid random variables $Y_1, \dots , Y_n$ and a $p$ dimensional unknown parameter $\theta$. The key idea is that there are a set of $q \geq p$ possible estimating equations**

$$
\frac{ 1 }{ n } \sum_{i=1}^{n} \psi_j(Y_i; \theta) = 0. \ j = 1, \dots , q
$$

**motivated by the fact that $E_{\psi_j}(Y_1; \theta_0) = 0$ , $j = 1, \dots , q$, where $\theta_0$ is the true value. These motivating zero expectaions come from the theory in the subject area being studied. But notice that if $q > p$, then we have too many equations. The GMM approach is to minimize the object function**

$$
T = \Big[ \frac{ 1 }{n  }\sum_{i=1}^{n} \psi(Y_{i};\theta) \Big]^T W \Big[ \frac{ 1 }{n  }\sum_{i=1}^{n} \psi(Y_{i};\theta) \Big].
$$

**To find $\widehat \theta$ we just take the partial derivative of $T$ with respect to $\theta$ and set it equal to 0:**

$$
S(Y; \theta) = 2 w_1 \Big[ \frac{ 1 }{n  }\sum_{i=1}^{n} \psi_1(Y_{i};\theta) \Big] \Big[ \frac{ 1 }{n  }\sum_{i=1}^{n} \psi_1'(Y_{i};\theta) \Big] + 2 w_2 \Big[ \frac{ 1 }{n  }\sum_{i=1}^{n} \psi_2(Y_{i};\theta) \Big]\Big[ \frac{ 1 }{n  }\sum_{i=1}^{n} \psi_2'(Y_{i};\theta) \Big] = 0.
$$

## a
**Prove that $S(Y; \theta_0)$ converges to 0 in probability as $\lim_{n\rightarrow \infty}$ making any moment assumptions that you need. (This suggest to you that the solution of the equation $S(Y; \theta)=0$ above is consistent.)**

Let's start by looking at the $\psi$ terms. By WLLN

$$
\frac{ 1 }{ n } \sum_{i=1}^{n} \psi_j (Y_i; \theta_0) \stackrel{ \text{p,d}}{\rightarrow} E( \psi_j(Y_1; \theta_0)) = 0.
$$

We can also apply WLLN for the $\psi'$ terms.

$$
\frac{ 1 }{ n } \sum_{i=1}^{n} \psi'_j (Y_i; \theta_0) \stackrel{ \text{p,d}}{\rightarrow} E( \psi_j(Y_1; \theta_0)) =A_{jj}
$$

Assuming that these $A_{jj}$ terms exist and are finite, we can use the continuous mapping theorem or Slutsky's (since convergence in probability and distribution to a constant are the same) to say

$$
S(Y; \theta_0) \stackrel{ \text{p}}{\rightarrow} 2w_1 \cdot 0 \cdot A_{11} + 2w_2 \cdot 0 \cdot A_{22} = 0.
$$

## b
**To get asymptotic normality for $\widehat \theta$, a direct approach is to expand $S(Y; \widehat \theta)$ around $\theta_0$ and solve for $\widehat \theta - \theta_0$.**

$$
\widehat \theta - \theta_0 = \Big[ - \frac{ \partial S(Y; \theta_0) }{\partial \theta^T} \Big]^{-1} S(Y; \theta_0) + \Big[ - \frac{ \partial S(Y; \theta_0) }{\partial \theta^T} \Big]^{-1} R_n
$$


**Then one ignores the remainder term and uses Slutsky's Theorem along with asymptotic normality of $S(Y; \theta_0)$. But how to get the asymptotic normality of $S(Y; \theta_0)$? Find $h(Y_i;\theta_0)$ such that**

$$
S(Y; \theta_0) = \frac{ 1 }{ n } \sum_{i=1}^{n} h(Y_i;\theta_0) + R_n
$$

**No proofs required.**



## c
**The equation $S(Y; \theta)= 0$ is not in the form for using M-estimation results (because the product of sums is not a simple sum). Show how to get it in M-estimation form by adding two new parameters, $\theta_2$ and $\theta_3$, and two new equations so that the result is a system of three equations with three $\psi$ functions; call them $\psi\_1^\*, \psi\_2^\*, $ and $\psi\_3^\*$ because $\psi\_1^\*$ is actually a function of the original $\psi\_1$ and $\psi\_2$.**



# 7.9
**Let $Y_1, \dots , Y_n$ be iid from some continuous distribution with nonzero density at the population mean, $f(\mu_0)>0$. For defining a "positive" standard deviation similar to the positive mean deviation from the median, one needs to estimate the proportion of the population that lies above the mean, $1-p_0 = 1 - F(\mu_0)$, using $1 - F_n(\overline Y)$ where $F_n$ is the empirical distribution function. Letting $\psi(Y_i; \mu, p)^T = (Y_i - \mu, I(Y_i \leq \mu) - p)$, find $A(\theta_0)$, $B(\theta_0)$, and $V(\theta_0)$. Note that we have to use the nonsmooth definition of $A(\theta_0)$:**

$$
A(\theta_0) - \frac{ \partial  }{\partial \theta} \{ E_F(\psi(Y_i; \mu, p)) \}\rvert_{\mu = \mu_0, p = p_0}.
$$

**The off-diagonal element of $B$ turns out to be $b_{12} = \int_{-\infty}^{\mu_0} y f(y) dy - p_0 \mu_0$. In your calculations, just let this be called $b_{12}$.**

We can start by finding $A(\theta_0)$.

$$
\begin{align}
A(\theta_0) & = \frac{ -\partial  }{\partial \theta} \Big( E \begin{bmatrix}
Y_i - \mu \\
I(Y_i \leq \mu) - p
\end{bmatrix}\Big) \rvert_{\mu =\mu_0, p = p_0} \\
    & = \frac{ -\partial  }{\partial \theta} \Big( \begin{bmatrix}
        \mu_0 - \mu \\
        P(Y_i \leq \mu) - p
        \end{bmatrix}\Big) \rvert_{\mu =\mu_0, p = p_0} \\
    & = \frac{ -\partial  }{\partial \theta} \Big( \begin{bmatrix}
        \mu_0 - \mu \\
       F(\mu)- p
        \end{bmatrix}\Big) \rvert_{\mu =\mu_0, p = p_0} \\
    & = \begin{bmatrix}
    1 & 0 \\
    -f(\mu_0) & 1
    \end{bmatrix}
\end{align}
$$

Now we can find $B(\theta_0)$. 

$$
\begin{align}
B(\theta_0) & = E(\psi(Y_1; \theta_0) \psi(Y_1; \theta_0)^T) \\
    & = E \begin{bmatrix}
        (Y_i - \mu_0)^2 & (Y_i - \mu_0) (I(Y_i \leq \mu_0) - p_0) \\
        (Y_i - \mu_0) (I(Y_i \leq \mu_0) - p_0) & (I(Y_i \leq \mu_0) - p_0)^2
    \end{bmatrix} \\
    & = \begin{bmatrix}
        \sigma_0^2 & E\Big[ (Y_i - \mu_0) (I(Y_i \leq \mu_0) - p_0) \Big] \\
        E\Big[ (Y_i - \mu_0) (I(Y_i \leq \mu_0) - p_0) \Big]   & E \Big[ I(Y_i \leq \mu_0)^2 - 2 p_0 I(Y_i \leq \mu_0) + p_0^2 \Big]
\end{bmatrix} \\ \\
 E\Big[ (Y_i - \mu_0) (I(Y_i \leq \mu_0) - p_0) \Big] & = E(Y_i I(Y_i \leq \mu_0)) - E( \mu_9 I(Y_i \leq \mu_0)) - p_0 E(Y_1) + \mu_0 p_0 \\
    & = \int_{-\infty}^{\mu_0} y f(y) dy - p_0 \mu_0 \\
    & = b_{12} ✅ \\ 
E \Big[ I(Y_i \leq \mu_0)^2 - 2 p_0 I(Y_i \leq \mu_0) + p_0^2 \Big] & = F(\mu_0) - 2 p_0 F(\mu_0) + p_0^2 \\
    & = p_0 - 2 p_0^2 + p_0^2 \\
    & = p_0 (1 - p_0) \\ \\
B(\theta_0) & = \begin{bmatrix}
\sigma_0^2 & b_{12} \\
b_{12} & p_0(1-p_0)
\end{bmatrix}
\end{align}
$$


Now we can find $V(\theta_0)$.

$$
\begin{align}
V(\theta_0) & = \begin{bmatrix}
    1 & 0 \\
    -f(\mu_0) & 1
    \end{bmatrix}
    \begin{bmatrix}
\sigma_0^2 & b_{12} \\
b_{12} & p_0(1-p_0)
\end{bmatrix}
    \begin{bmatrix}
    1 & -f(\mu_0)  \\
    0 & 1
    \end{bmatrix} \\
    & = \begin{bmatrix}
    \sigma_0^2 & b_{12} \\
    f(\mu_0) \sigma^2 + b_{12} & f(\mu_0) b_{12} + p_0(1-p_0)
    \end{bmatrix}
    \begin{bmatrix}
    1 & -f(\mu_0)  \\
    0 & 1
    \end{bmatrix} \\
    & = \begin{bmatrix}
    \sigma_0^2 & \sigma_0^2 f(\mu_0) + b_{12} \\
    f(\mu_0) \sigma_0^2 + b_{12} & \sigma_0^2 f(\mu_0) + 2 b_{12} f(\mu_0) + p_0 ( 1- p_0)
    \end{bmatrix}
\end{align}
$$

# 7.11
**Consider the simple no intercept model**

$$
Y_i = \beta x_i + e_i, \ i = 1, \dots, n,
$$

**where the $x_1, \dots x_n$ are fixed constants and $e_1, \dots e_n$ are independent with $E(\psi^\*(e_i)) = 0$ and $E(\psi^\*(e_i)^2) < \infty$ with values possibly depending on $i$, and $\psi^\*$ is a real-valued function (with the subscript "$\*$" to differentiate from our usual $\psi(Y_i, x_i, \beta)$).**

## a
**A classical robust M-estimator $\widehat \beta$ satisfies**

$$
\sum_{i=1}^{n} \psi^*(Y_i - \widehat \beta x_i) x_i = 0.
$$

**Write down the asymptotic variance of $\widehat \beta$ and an estimator of this asymptotic variance. You may assume that the derivative $\psi^\* ' $ of $\psi^\*$ exists everywhere and that $E \| \psi^\* ' (e_i) \|<\theta$ for all $i$.**



## b
**Let's simplify and assume that $e_i, \dots e_n$ are iid. How does the asymptotic variance expression from a) change? Find an improved asymptotic variance estimator in this situation.**


# 8.10
**Suppose we have data $X_1, \dots , X_n$ that are iid. The sign test for $H_0: \text{median} = 0$ is to count the number of $X$'s that are above 0, say $Y$, and compare $Y$ to a binomial($n, p = 1/2$) distribution. Starting with the defining M-estimator equation for the sample median (see Example 7.4.2, p 312, with $p = 1/2$),**


## a
**Derive the generalized score statistic $T_{GS}$ for $H_0: \text{median} = 0$ and note that it is the large sample version of the two-sided sign statistic.**

We know $\psi = 0.5 - I(Y_i \leq \theta)$. Since $\theta$ is a scalar, we know $V(\theta_0) = B(\theta_0) = p(1-p) = \frac{ 1 }{ 4 }$. Thus,

$$
T_{GS} = \frac{ 1 }{ n } \Big[ \sum_{i=1}^{n} \psi(Y_i; 0) \Big] (\frac{ 1 }{ 4 })^{-1})\Big[ \sum_{i=1}^{n} \psi(Y_i; 0) \Big]  = \frac{ 4 }{ n } \Big[ \sum_{i=1}^{n} 0.5 - I(Y_i \leq 0) \Big] ^2
$$



## b
**Using the expression for the asymptotic variance of the sample median, write down the form of a generalized Wald statistic $T_{GW}$, and explain why it is not as attractive to use here as $T_{GS}$.**

From 7.4.2 we know $V(\theta) = \frac{ 1 }{ 4 f(\theta)^2 }$ Thus, our generalized Wald statistics is

$$
T_{GW} = n ( \widehat \theta - 0) \frac{ 1 }{ 4   f(\widehat \theta)^2} (\widehat \theta - 0) = \frac{ n \widehat \theta^2 }{ 4 f(\widehat \theta) }.
$$

This is less attractive than the score statistics because it requires that we know the distribution $f$, which we are not necessarily given.
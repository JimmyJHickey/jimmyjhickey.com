---
layout: post
comments: false
title: Example Problems on Asymptotics
description: ST793 Homework 6 on Hypothesis Testing
tags: ST793 Testing Asymptotics Statistics
category: ST793
---

* Do not remove this line (it will not be displayed)
{:toc}

# 6.2

_1._

$$
\begin{align}
F(y; \sigma) & = \int_{0}^y \frac{ 2y }{ \sigma^2 } \exp(\frac{ -y^2 }{ \sigma^2 }) dy \\
    & = \frac{ 2 }{ \sigma^2 } \int_{0}^y y \exp(\frac{ -y^2 }{ \sigma^2 }) dy \\
    & = \frac{ 2 }{ \sigma^2 } \int_{0}^{\sqrt{ u }} y \exp(\frac{ -u }{ \sigma^2 }) \frac{ 1 }{2y  }du & u = y^2\\
    & = 1 - \exp(\frac{ -y^2 }{ \sigma^2 })
\end{align}
$$

If $\sigma_1 \neq \sigma_2$ and $y=1$,

$$
F(1; \sigma_1) = 1 - e^{-1/\sigma_1^2} \neq 1 - e^{-1/\sigma_2^2} = F(1; \sigma_2) \text{✅}
$$

_2._

Notice that the support of $F(y; \sigma)$ does not depend on $\sigma$. ✅
 
 _3._
 
 Let's find the log likelihood.
 
 $$
 \ell(f(y;\sigma)) = \log(\frac{ 2y }{ \sigma^2 }) - \frac{ y^2 }{ \sigma^2 } = -2 \log(\sigma) - \frac{ y^2 }{ \sigma^2 }
 $$
 
 Now we will take derivatives with respect to $\sigma$. 
 
 $$
 \begin{align}
 \ell ' & = \frac{ -2 }{ \sigma } + \frac{ 2 y^2 }{ \sigma^3 } \\
 \ell '' & = \frac{ 2 }{ \sigma^2 } - \frac{ 6y^2 }{ \sigma^4 } \\
 \ell ''' & = \frac{ -4 }{ \sigma^3 } + \frac{ 24 y^2 }{ \sigma^5 }
 \end{align}
 $$
 
 All of these exist for $y > 0$. ✅
 
 _4._
 
 We will start by defining $g(y)$.
 
 $$
 \begin{align}
 | \frac{ -4 }{ \sigma_0^3 } + \frac{ 24 y^2 }{ \sigma_0^5 } | & = | -4 \sigma_0^{-3} + 24 y^2 \sigma_0^{-5}| \\
    & \leq |-4 \sigma_0^{-3}| + |24 y^2 \sigma_0^{-5}| & \text{Triangle Inequality} \\
    & = 4 \sigma_0^{-3} + 24 y^2 \sigma_0^{-5} & y, \sigma_0 >0 \\
    & = g(y)
 \end{align}
 $$
 
 Then,
 
 $$
 \begin{align}
 \int_{0}^{\infty} g(y) dF(y;\sigma_0) & =  \int_{0}^{\infty} g(y) f(y; \sigma_0) dy \\
    & = (4 \sigma_0^{-3} + 24 y^2 \sigma_0^{-5})(\frac{ 2 y }{ \sigma_0 } \exp(\frac{ -y^2 }{ \sigma_0^2 })) dy \\
    & = \frac{ 28 }{ \sigma^3 } < \infty \text{✅}
 \end{align}
 $$
 
 _5._
 
 First we will check that the expectation of the score function is 0. Integrals can be found in [this Mathematica script](https://github.com/JimmyJHickey/grad-scripts/blob/master/st793-advanced-inference/hw6/hw6.nb).
 
 $$
 \begin{align}
 E( - \frac{ 2 }{ \sigma } + \frac{ 2 y^2 }{\sigma^3  }) & = -\frac{  2}{ \sigma } + \frac{ 2 }{ \sigma^3 } \int_{0}^{\infty} \frac{ 2 y^3 }{ \sigma^2 } \exp(\frac{ -y^2 }{ \sigma^2 }) dy \\
    & = \frac{ -2 }{ \sigma } + \frac{ 2 }{ \sigma^3 } \cdot \sigma^2 \\
    & = 0 \text{✅}
 \end{align}
 $$
 
 Now we will check that the two forms of the information are equivalent.
 
 $$
 \begin{align}
 E\Big[ (\frac{ \partial \ell }{\partial \sigma})^2  \Big] & =   \int_{0}^{\infty} \Big( \frac{ -2 }{ \sigma } + \frac{ 2 y^2 }{ \sigma^3 }  \Big) \frac{ 2y }{ \sigma^2 } \exp(\frac{ -y^2 }{ \sigma^2 }) dy \\
    & = \frac{ 4 }{ \sigma^2 } \\ \\
 E\Big[\frac{ \partial^2 \ell }{\partial \sigma^2}  \Big] & = \int_{0}^{\infty} \Big( \frac{ 2 }{ \sigma^2 } + \frac{ 6 y^2 }{ \sigma^4 }  \Big) \frac{ 2y }{ \sigma^2 } \exp(\frac{ -y^2 }{ \sigma^2 }) dy \\
    & = \frac{ 4 }{ \sigma^2 } \text{✅} 
 \end{align}
 $$
 

 
# 6.3

Recall the definition of the derivative

$$
\frac{ \partial  }{\partial \theta} f(y; \theta) = \lim_{n \rightarrow \infty} \frac{ f(y; \theta + 1/n) - f(y;\theta) }{ 1/n } = \lim_{n\rightarrow \infty} f_n(y; \theta)
$$

We know that $\| \frac{ \partial f(y;\theta) }{\partial \theta} \| = \|  f_n(y; \theta)\| \leq g_1(y)$ for all $\theta$ in a neighborhood around $\theta_0$. Now we can directly apply the dominated convergence theorem.

$$
\begin{align}
\lim_{n\rightarrow \infty} \int f_n(y;\theta) dy & = \int f dy \\
    & \text{or} \\
\frac{ \partial  }{\partial \theta} \int f(y; \theta) dy & = \int \frac{ \partial  }{\partial \theta} f(y;\theta) dy
\end{align}
$$


# 3.1
We will start by finding the MLE.


$$
\begin{align}
S(\theta) & = \frac{ \partial \ell }{\partial \theta} = b(y) - 2c\theta \stackrel{\text{set}}{=} 0  \\
\widehat \theta & = \frac{ b(y) }{ 2c } \\
\frac{ \partial ^2 \ell}{\partial \theta^2} & = -2 c
\end{align}
$$

So we have an MLE for $c > 0$. Now we can find our information.

$$
I_T(\widehat \theta) = - E(\frac{ \partial S(\theta) }{\partial \theta}) = -E(-2c) = 2c
$$

Now we can find our test statistics.

$$
\begin{align}
\text{Wald} \\
T_W &  = \frac{ (\widehat \theta - \widehat \theta_0)^2 }{ I_T(\widehat \theta)^{-1} } \\
    & = \frac{ (b(y) - \theta_0)^2 }{ 1/(2c) } \\
    & = \frac{ b(y)^2 }{ 2c } - 2 b(y) \theta_0 + 2 c \theta_0^2 \\ \\
\text{Score} \\
T_S & = \frac{ S(\theta_0)^2 }{ I_T(\theta_0) } \\
    & = \frac{ (b(y)-2c\theta_0)^2 }{ 2c } \\
    & = \frac{ b(y)^2 }{ 2c } - \frac{ 2b(y)2c\theta_0 }{ 2c } + \frac{ (2c)^2 \theta_0}{ 2c } \\
    & = \frac{ b(y)^2 }{ 2c } - 2 b(y) \theta_0 + 2 c \theta_0^2 \\ \\
\text{Likelihood Ratio} \\
T_{LR} & = -2(\ell(\theta_0) - \ell(\widehat \theta)) \\
    & = -2(a(Y) - b(y) \theta_0 - c (\theta_0)^2 - a(y) - b(y) \widehat \theta + c(\widehat \theta)^2) \\
     & = \frac{ b(y)^2 }{ 2c } - 2 b(y) \theta_0 + 2 c \theta_0^2
\end{align}
$$

# 3.6
We will start by finding the log likelihood.

$$
\begin{align}
L(p_1, p_2 | Y_1, Y_2) & = p_1(1-p_1)^{y_1 - 1} p_2(1-p_2)^{y_2-1} \\
\ell(p_1, p_2 | Y_1, Y_2) & = \log(p_1) + (y_1 - 1) \log(1 - p_1) + \log(p_2) +(y_2 - 1) \log(1-p_2)
\end{align}
$$

Now we will find the score vector.

$$
S(\theta) = \begin{bmatrix}
\frac{ \partial \ell }{\partial p_1} \\ \frac{ \partial \ell }{\partial p_2} \end{bmatrix}
= \begin{bmatrix}
\frac{ 1 }{ p_1 } - \frac{ y_1 - 1 }{ 1 - p_1 } \\
\frac{ 1 }{ p_2 } - \frac{ y_2 - 1 }{ 1 - p_2 }
\end{bmatrix}
= \begin{bmatrix}
\frac{ 1 - p_1 y_1 }{ p_1 (1-p_1) } \\
\frac{ 1 - p_2 y_2 }{ p_2 (1-p_2) }
\end{bmatrix}
$$

We need to find the second derivatives to find the information matrix.

$$
\begin{align}
\frac{ \partial ^2 \ell }{\partial p_i^2} & = \frac{ -1 }{ p_i^2 } - \frac{ y_i-1 }{ (1-p_i)^2 } \\
I_T(p_1, p_2)_{ii} & = -E(\frac{ 1 }{ p_i^2 } + \frac{ y_i-1 }{ (1-p_i)^2 }) \\
    & = \frac{ 1 }{ p_i^2 } + \frac{ 1 }{ p_i(1-p_i) } \\
    & = \frac{ 1 }{ p_i^2(1-p_i) } \\ \\
\frac{ \partial ^2 \ell }{\partial p_i p_j} & = 0 
\end{align}
$$

Thus,

$$
I_T(p_1, p_2) = \begin{bmatrix}
\frac{ 1 }{ p_1^2 (1-p_1) } & 0 \\
0 & \frac{ 1 }{ p_2^2 (1-p_2) }
\end{bmatrix}.
$$

In order to find the score, we will need to find the restricted MLE under $H_0: p_1 = p_2 = p$. 

$$
S(p) = \frac{ 2 }{ p } - \frac{ y_1 + y_2 + 2 }{ (1-p) } \stackrel{\text{set}}{=} 0 \Rightarrow \widehat p = \frac{ 2 }{ Y_1 + Y_2 } = \widetilde p
$$

Now we can find the score statistic.

$$
\begin{align}
T_S & = S(\widetilde p)^T I_T(\widetilde p)^{-1} S(\widetilde p) \\
    & = \begin{bmatrix}
\frac{ 1 - \widetilde p y_1 }{ \widetilde p (1-\widetilde p) } &
\frac{ 1 - \widetilde p y_2 }{ \widetilde p (1-p_2) }
\end{bmatrix} 
\begin{bmatrix}
\widetilde p^2 (1-\widetilde p & 0 \\
0 & \widetilde p^2 (1-\widetilde p)
\end{bmatrix}
\begin{bmatrix}
\frac{ 1 - \widetilde p y_1 }{ \widetilde p (1-\widetilde p) } &
\frac{ 1 - \widetilde p y_2 }{ \widetilde p (1-p_2) }
\end{bmatrix} \\
    & = \frac{ (1 - \widetilde p y_1)^2 + (1 - \widetilde p y_2)^2 }{ 1-\widetilde p } \\
    & = \frac{ 1 }{ 1 - \widetilde p } (2 - 2 \widetilde p y_1 - 2 \widetilde p y_2 + (\widetilde p y_1)^2 + (\widetilde p y_2)^2 ) \\
    & = \frac{ 1 }{ 1 - \widetilde p } (\widetilde p^2(y_1^2 + y_2^2) - 2 \widetilde p(y_1 + y_2) + 2 ) \\
    & = \frac{ 1 }{ 1 - \widetilde p } ((\frac{ 2 }{ y_1 +  y_2})^2(y_1^2 + y_2^2) - 2 (\frac{ 2 }{ y_1 +  y_2})2(y_1 + y_2) + 2 ) \\
    & = \frac{ 1 }{ 1 - \widetilde p } (\frac{ 4 }{ (y_1+y_2)^2 } (y_1^2+y_2^2) -4 + 2   ) \\
    & = \frac{ 1 }{ 1 - \widetilde p } (\frac{ 4 }{ (y_1+y_2)^2 } (y_1^2+y_2^2) -\frac{ 2(y_1+y_2)^2 }{ (y_1+y_2)^2 }  ) \\
    & = \frac{ 1 }{ 1 - \widetilde p } \frac{ 4y_1^2 + y_2^2 - 2y_1^2 - 4y_1 y_2 - 2y_2^2 }{ (y_1+y_2)^2 } \\
    & = \frac{ 1 }{ 1 - \widetilde p } \frac{ 2(y_1-y_2)^2 }{ (y_1+y_2)^2 } \\
    & =  \frac{ \widetilde p^2 }{ 2(1 - \widetilde p) } (Y_1 - Y_2)^2
\end{align} 
$$

# 3.9
$$
\begin{align}
L(\pmb \lambda | \pmb Y) & = \prod_{i=1}^{n} \frac{ e^{-\lambda_i} \lambda_i^{y_i} }{ y_i! } \\ \\
\ell(\pmb \lambda | \pmb Y) & = \sum_{i=1}^{n} - \lambda_i + \sum_{i=1}^{n} y_i \log(\lambda_i) + c \\ \\
S(\pmb \lambda)_i & = \frac{ \partial \ell }{\partial \lambda_i} \\
    & = -1 + \frac{ y_i }{ \lambda_i } \\ \\
\frac{ \partial^2 \ell }{\partial \lambda_i^2 } & = \frac{ -y_i }{ \lambda_i^2 } \\
I_T(\lambda)_{ii} & = -E(\frac{ -y_i }{ \lambda_i^2 }) \\
    & = \frac{ 1 }{ \lambda_i } \\
\frac{ \partial ^2 \ell }{\partial \lambda_i \lambda_j} & = 0 & i \neq j\\
I_T(\lambda) & = 0
\end{align}
$$

Now we need to find the MLE under $H_0$.

$$
\begin{align}
S(\lambda) & = -n + \frac{ \sum_{i=1}^{n} y_i}{ \lambda } \stackrel{\text{set}}{=} 0 \\
\hat \lambda_0 & = \overline{ Y }
\end{align}
$$

Thus,

$$
\begin{align}
T_S & = S( \widehat \lambda_0)^T I_T(\widehat \lambda_0)^{-1} S( \widehat \lambda_0) \\
    & = \begin{bmatrix}
\frac{ Y_1 }{ \overline{ Y } } - 1 & \dots & \frac{ Y_n }{ \overline{ Y } } - 1
\end{bmatrix}
\begin{bmatrix}
\overline{ Y } & 0 \\
0 & \overline{ Y }
\end{bmatrix} 
\begin{bmatrix}
\frac{ Y_1 }{ \overline{ Y } } - 1 \\ \vdots \\ \frac{ Y_n }{ \overline{ Y } } - 1
\end{bmatrix} \\
    & = \sum_{i=1}^{n} \overline{ Y } (\frac{ Y_i }{\overline{ Y } } - 1) (\frac{ Y_i }{ \overline{ Y } }-1) \\
    & = \sum_{i=1}^{n} \frac{ (Y_i - \overline{ Y })^2 }{ \overline{ Y } }
\end{align} 
$$
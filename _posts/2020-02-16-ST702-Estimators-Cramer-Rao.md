---
layout: post
comments: false
title: Example Problems on Estimators
description: ST702 Homework 5 on Estimators
tags: ST702 Cramer-Rao Estimators
category: ST702
---

* Do not remove this line (it will not be displayed)
{:toc}

# 7.45
**Let $X_1, X_2, \dots X_n$ be iid from a distribution with mean $\mu$ and variance $\sigma^2$, and let $S^2$ be the usual unbiased estimator of $\sigma^2$. In Example 7.3.4 we saw that, under normality, the MLE has smaller MSE than $S^2$. In this exercise we will explore variance estimators some more.**

## a
**Show that, for any estimator of the form $aS^2$, where $a$ is some constant,**

$$
MSE(aS^2) = E[aS^2 - \sigma^2]^2 = a^2 Var(S^2) + (a - 1)^2 \sigma^4
$$

$$
	\begin{align}
		MSE(aS^2) & = E[W - \theta]^2 \\
			& = E[aS^2 - \sigma^2]^2 \\
			& = Var(aS^2) - (Bias(aS^2))^2 \\
			& = a^2 Var(S^2) - (E(aS^2) - \sigma^2)^2 \\
			& = a^2 Var(S^2) - (a^2 E(S^2)^2 - 2a E(S^2)\sigma^2 + \sigma^4)\\
			& = a^2 Var(S^2) - (a^2 (\sigma^2)^2 - 2a \sigma^2 \sigma^2 + \sigma^4) & \text{unbiased}\\
			& = a^2 Var(S^2) + (a-1)^2 \sigma^4
	\end{align}
$$

## b
**Show that**

$$
Var(S^2) = \frac{ 1 }{ n } \Big( \kappa - \frac{ n-3 }{ n-1 }  \Big)\sigma^4
$$

**where $\kappa = E[X-\mu]^4 / \sigma^4$ is the _kurtosis_.**


$$
	\begin{align}
		V(S^2) & = V\Big( \frac{ 1 }{ n-1 } \sum (X_i - \overline{ X })^2 \Big) \\
			& = \frac{ 1 }{ (n-1)^2 } \sum V( (X_i - \overline{ X })^2) \\
			& = \frac{ 1 }{ (n-1)^2 } \sum \Big[ E( ((X_i - \overline{ X })^2)^2 ) - E((X_i - \overline{ X })^2)^2 \Big]  \\
			& = \frac{ 1 }{ (n-1)^2 } \sum \Big[ E( (X_i - \overline{ X })^4 ) - E((X_i - \overline{ X })^2)^2 \Big]  \\
			& = \frac{ 1 }{ (n-1)^2 } \sum \kappa \sigma^4 - (\sigma^2)^2 \\
			& = \frac{ 1 }{ (n-1)^2 } ( n \kappa \sigma^4 - n \sigma^4)
	\end{align}
$$

## c
**Show that under normality, the kurtosis is $3$ and establish that, in this case, the estimator of the form $aS^2$ with the minimum MSE is $\frac{ n-1 }{ n+1 }S^2$. (Lemma 3.6.5 may be helpful)**

We can bring the $\sigma^4$ inside the fraction to get

$$
\kappa = E\Big[ \Big( \frac{ X-\mu }{ \sigma } \Big)^4 \Big].
$$

Notice that the inside function now follows a $N(0,1)$ distribution. We can also make use of Lemma 3.6.5 which says

$$
E\Big[ g(x) (x - \mu) \Big] = \sigma^2 E(g'(x)).
$$

Now we can take $g(Z) = Z^3$. Then,

$$
	\begin{align}
		\kappa & = E[Z^4] \\
			& = E[g(Z) (Z - 0)] \\
			& = \sigma^2 E[g'(Z)] \\
			& = \sigma^2 E[3 Z^2] \\
			& = 3 \sigma^2 E[Z^2] \\
			& = 3 \sigma^2 (V(Z) + E(Z)^2) \\
			& = 3 \cdot 1 ( 1 + 0) \\
			& = 3.
	\end{align}
$$

Now we can use our MSE equation from (a) and our variance equation from (b). We are trying to optimize with respect to $a$.

$$
	\begin{align}
		MSE & = a^2 \frac{ 1 }{ n } \Big( \kappa - \frac{ n-3 }{ n-1 }  \Big)\sigma^4 + (a-1)^2 \sigma^4 \\
		\frac{ \partial  MSE }{\partial a} & = 2 a \frac{ 1 }{ n } \Big( \kappa - \frac{ n-3 }{ n-1 }  \Big)\sigma^4 + 2(a-1) \sigma^4 = 0 \\
		a & = \frac{ \sigma^4 }{ \frac{ 1 }{ n } \Big( \kappa - \frac{ n-3 }{ n-1 }  \Big)\sigma^4 + \sigma^4  } \\
			& = \frac{ \sigma^4 }{ \frac{ 1 }{ n } \Big( 3 - \frac{ n-3 }{ n-1 }  \Big)\sigma^4 + \sigma^4  } \\
			& = \frac{ 1 }{ \frac{ 1 }{ n } \Big( 3 - \frac{ n-3 }{ n-1 }  \Big) + 1 } \\
			& = \frac{ n-1 }{ n+1 }
	\end{align}
$$

## d 
**If normality is not assumed, show that $MSE(aS^2)$ is minimized at**

$$
a = \frac{ n-1 }{ n+1 + \frac{ (\kappa - 3) (n-1) }{ n } }
$$

**which is useless as is depends on a parameter.**

From above

$$
	\begin{align}
		a & = \frac{ \sigma^4 }{ \frac{ 1 }{ n } \Big( \kappa - \frac{ n-3 }{ n-1 }  \Big)\sigma^4 + \sigma^4  } \\
			& = \frac{ 1 }{ \frac{ 1 }{ n } \Big( \kappa - \frac{ n-3 }{ n-1 }  \Big) + 1 }\\
			& = \frac{ n-1 }{ n+1 + \frac{ (\kappa - 3) (n-1) }{ n } }
	\end{align}
$$


## e
**Show that**


### i
**for distributions with $\kappa > 3$, the optimal $a$ will satisfy $a < \frac{ n-1 }{ n+1 }$.**

Taking $\kappa > 3$ will make the second term in our denominator positive, which will make the denominator larger than $n+1$. So our overall expression will be less than $\frac{ n-1 }{ n+1 }$.

### ii
**for distributions with $\kappa < 3$, the optimal $a$ will satisfy $\frac{ n-1 }{ n+1 } < a < 1$.**

Similarly, making $\kappa < 3$ will make the second term in our denominator negative, which will make the denominator smaller than $n+1$. So our overall expression will be greater than $\frac{ n-1 }{ n+1 }$.


# 7.48
**Suppose that $X_i, \ i = 1, \dots , n$ are iid $Bernoulli(p)$.**

## a
**Show that the variance of the MLE of $p$ attains the Cramér-Rao Lower Bound.**

The MLE is,

$$
	\begin{align}
		L(p | x) & = \prod f(x_i | p) \\
			& = \prod p^{x_i} (1-p)^{1-x_i}\\
			& = p^{\sum x_i} (1-p)^{1-\sum x_i} \\ \\
		\ell(p|x) & = \sum x_i \log(p) + (n - \sum x_i) \log(1-p) \\ \\
		\frac{ \partial \ell  }{\partial p } & = \sum x_i \frac{ 1 }{ p } + -(n - \sum x_i) \frac{ 1 }{ 1-p } \\
		0 & = \sum x_i \frac{ 1 }{ p } + -(n - \sum x_i) \frac{ 1 }{ 1-p } \\ \\
		\sum x_i \frac{ 1 }{ p } & = (n - \sum x_i) \frac{ 1 }{ 1-p }  \\
		\frac{ 1-p }{ p } & = \frac{ n - \sum x_i }{ \sum x_i } \\
		\widehat p & = \overline{ X }.
	\end{align}
$$

The Cramér-Rao lower bound is,


$$
	\begin{align}
		V_\theta ( W(X)) & \geq \frac{ \Big( \frac{ \partial   }{\partial \theta} E_\theta(W(X)) \Big)^2 }{ -E_\theta \Big( \frac{ \partial^2   }{\partial \theta^2} \log(f(x|\theta)) \Big) } \\
			-E_\theta \Big( \frac{ \partial^2   }{\partial \theta^2} \log(f(x|\theta)) \Big) & = -E_\theta \Big( \frac{ \partial   }{\partial \theta} \sum \frac{ x_i }{ p } - (n - \sum x_i) \frac{ 1 }{ 1-p } \Big) \\
				& =  -E_\theta \Big( - \frac{ \sum x_i }{ p^2 } + \frac{ -(n-\sum x_i) }{ (1-p)^2 } \Big) \\
				& = \frac{ 1 }{ p^2 } \sum E(x_i) +  E\Big( \frac{ n = \sum x_i }{ (1-p)^2 } \Big) \\
				& = \frac{ n }{ p^2 } p + \frac{ n-np }{ (1-p)^2 } \\
				& = \frac{ n }{ p } + \frac{ n(1-p) }{ (1-p)^2 } \\ \\
			CRLB & = \frac{ 1 }{ \frac{ n }{ p } + \frac{ n(1-p) }{ (1-p)^2 } } \\
				& = \frac{ p(1-p) }{ n }.
	\end{align}
$$

Now we can find the variance of our estimator.

$$
	\begin{align}
		V(\widehat p) & = V \Big( \frac{ \sum x_i }{ n } \Big) \\
			& = \frac{ 1 }{ n^2 } \sum V(x_i) \\
			& = \frac{ 1 }{ n^2 } n p (1-p) \\
			& = \frac{ p(1-p) }{ n }\\
			& = CRLB
	\end{align}
$$


## b
**For $n \geq 4$, show that the product $X_1 X_2 X_3 X_4$ is an unbiased estimator of $p^4$. and use this fact to find the best unbiased estimator of $p^4$.**

$$
	\begin{align}
		E\Big[ X_1 X_2 X_3 X_4 \Big] & = E(X_1)E(X_2)E(X_3)E(X_4) & \text{independence} \\
			& = p^4.
	\end{align}
$$


Also $\sum_{i=1}^{n} x_i$ is sufficient for $p$ by the Factorization Theorem.

$$
	\begin{align}
		f(X | p) & = \prod p^{x_i} (1-p)^{1-x_i} \\
			& = p^{\sum x_i} (1-p)^{1-\sum x_i}
	\end{align}
$$

We can use the Rao-Blackwell theorem to find a UMVUE.

$$
	\begin{align}
		\phi(T) & = E\Big( X_1 X_2 X_3 X_4 | \sum_{i=1}^{n} X_i = t \Big) \\
			& = \frac{ P(X_1, X_2, X_3, X_4 = 1 \land \sum_{i=1}^{n} X_i = t) }{ P(\sum_{i=1}^{n} X_i = t) } \\
			& = \frac{ P(X_1, X_2, X_3, X_4 = 1 \land \sum_{i=5}^{n} X_i = t-4) }{ P(\sum_{i=1}^{n} X_i = t) } \\
			& = \frac{ P(X_1, X_2, X_3, X_4 = 1) P(\sum_{i=5}^{n} X_i = t-4) }{ P(\sum_{i=1}^{n} X_i = t) } & \text{independence} \\
			& = \frac{ p^4 \cdot {n-4 \choose t-4} p^{t-4} (1-p)^{n-4-(t-4)} }{ {n \choose t} p^t (1-p)^{n-t} } \\
			& = \frac{ {n-4 \choose t-4} }{ {n \choose t} }
	\end{align}
$$

# 7.49
**Let $X_1, \dots , X_n$ be iid $exponential(\lambda)$.**

## a
**Find an unbiased estimator of $\lambda$ based only on $Y = \min \{X_1, \dots , X_n \}$.**

$$
	\begin{align}
		F_Y & = P(X < X_i) \\
			& = [1 - F(X)]^n \\ \\
		f_y & = n f(x) (1- F(X))^{n-1} \\
			& = n \frac{ 1 }{ \lambda } e^{-\frac{ 1 }{ \lambda } x} \Big( 1 - (1 - e^{\frac{ -1 }{ \lambda } x}) \Big)^{n-1} \\
			& = n \frac{ 1 }{ \lambda } e^{- n \frac{ 1 }{ \lambda } x}.
	\end{align}
$$

So $ Y\sim Exp(\lambda / b)$. So $nY$ is unbiased.

$$
E(nY) = n E(Y) = n \lambda/n = \lambda
$$


## b
**Find a better estimator than the one in part (a). Prove that it is better.**

Since it's an exponential family, $\sum x_i$ is sufficient and complete. Notice that $\overline{ X }$ is a function of $\sum x_i$ and is unbiased.

$$
E(\overline{ X }) = \frac{ 1 }{ n } \sum E(x_i) = \frac{ 1 }{ n } n \lambda = \lambda
$$

By Lehmann-Scheffe, $\overline{ X }$ is UMVUE, so it is better than the estimator in (a).

## c
**The following data are high-stress failure times (in hours) of Kevlar/epoxy spherical vessels used in a sustained pressure environment on the space shuttle:**

$$
50.1, 70.1, 137.0, 166.9, 170.5, 152.8, 80.5, 123.5, 112.6, 148.5, 160.0, 125.4.
$$

**Failure times are often modeled with the exponential distribution. Estimate the mean failure time using the estimators from parts (a) and (b).**

From (a) $\widehat \lambda = 50.1 \cdot 12 = 601.2$. For (b) we can take the average $\widehat \lambda = 124.825$.



# 4
**Consider a random sample $X_1, X_2, \dots X_n$ from the density $f(x\| \theta) = \exp\Big[ -(x-\theta) \Big]$, $\theta < x < \infty$, and 0 elsewhere. Show that the first order statistic $X_{(1)} = \min X_i$ is a complete sufficient statistic for $\theta$, and find the UMVUE of $\theta$.**

$$
	\begin{align}
		f(X | \theta) & = \prod e^{-(x-\theta)} I[\theta < x< \infty] \\
			& = e^{-\sum x_i - n \theta} I[\theta < X_{(1)}] \\
			& = e^{- \sum x_i} e^{n \theta} I[\theta < X_{(1)}]
	\end{align}
$$

By the factorization theorem $X_{(1)}$ is sufficient. Now we can show that it is complete. First, we need its distribution.


$$
	\begin{align}
		f_{X_{(1)}} & = n \cdot f_x ( 1- F_X)^{n-1} \\
			& = n e^{-(x-\theta)} \Big[ 1 - \int_{\theta}^{x} e^{-(t - \theta)} dt \Big]^{n-1} \\
			& = n e^{-(x-\theta)} \Big[ 1 - (1 - e^{-x + \theta}) \Big]^{n-1} \\
			& = n e^{-(x-\theta)} \Big[ e^{-x + \theta} \Big]^{n-1} \\
			& = n e^{n(-x + \theta)}
	\end{align}
$$

Now we can show completeness.

$$
	\begin{align}
		\int_{\theta}^{\infty} g(x) n e^{n(\theta - t)}dx & = n e^{n \theta} \int_{\theta}^{\infty} g(x) e^{- nt}dx
	\end{align}
$$

This is only 0 if $g(x)$ is 0. Now we can look at the expectation of the minimum order statistic.

$$
	\begin{align}
		E(X_{(1)}) & = \int_{\theta}^{\infty} x n e^{(-x + \theta)n} dx \\
			& = \frac{ n (1+n\theta) }{ n^2 } \\
			& = \frac{ 1 }{ n } + \theta
	\end{align}
$$

So $X_{(1)} - \frac{ 1 }{ n }$ in unbiased.

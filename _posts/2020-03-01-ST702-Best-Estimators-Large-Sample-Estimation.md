---
layout: post
comments: false
title: Example Problems on Best Estimators and Large Sample Estimation
description: ST702 Homework 6 on Best Estimators and Large Sample Estimation
tags: ST702 Large-Sample Estimators
category: ST702
---

* Do not remove this line (it will not be displayed)
{:toc}



# 7.55
**For each of the following pdfs, let $X_1, \dots , X_n$ be a sample from that distribution. In each case, find the best estimator of $\theta^r$. (See Guenther 1978 for a complete discussion of this problem.)**


## a
$$
f(x | \theta) = \frac{ 1 }{ \theta } ,\ 0 < x < \theta, \ r < n
$$



## b
$$
f(x | \theta) = e^{-(x-\theta)}, \ x > \theta
$$




## c
$$
f(x | \theta) = \frac{ e^{-x} }{ e^{-\theta} - e^{-b} }, \ \theta < x < b, \ b \text{ known}
$$





# 7.58
**Let $X$ be an observation from the pdf**


$$
f(x|\theta) = \Big( \frac{ \theta }{ 2 } \Big)^{|x|} (1-\theta)^{1-|x|}, \ x = -1, 0, 1, \ 0 \leq \theta \leq 1
$$


## a
**Find the MLE of $\theta$.**




## b
**Define the estimator $T(X)$ by**

$$
T(X) = \begin{cases}
		2 & \text{if } x=1\\
		0 & \text{otherwise.}
	\end{cases}
$$

**Show that $T(X)$ is an unbiased estimator of $\theta$.**



## c
**Find a better estimator of $T(X)$ and prove that it is better.**



# 7.60
**Let $X_1, \dots , X_n$ be iid $gamma(\alpha, \beta)$ with $\alpha$ known. Find the best unbiased estimator of $\frac{ 1 }{ \beta }$.**






# 10.1
**A random sample $X_1, \dots , X_n$ is drawn from a population with pdf**

$$
f(x|\theta) = \frac{ 1 }{ 2 }(1 + \theta x), \ -1 < x< 1, \ -1< \theta < 1.
$$

**Find a consistent estimator of $\theta$ and show that it is consistent.**


First let's find the mean and variance.

$$
E(X) = \int_{-1}^{1} 1/2 x + 1/2 \theta x^2 dx = \frac{ \theta }{ 3 }
$$


$$
E(X^2) = \int_{-1}^{1} 1/2 x^2 + 1/2 \theta x^3 dx = \frac{ 1 }{ 3 }
$$


$$
Var(X) = \frac{ 1 }{ 3 } - \frac{ \theta^2 }{ 3 }
$$


Let's try $\widehat \theta = 3 \overline{ X }$.

$$
E(\widehat \theta) = E(3 \overline{ X }) = 3 / n \sum E(X_i) = 3/n \cdot n \frac{ \theta }{ 3 } = \theta
$$

So $\widehat \theta$ is unbiased. Now we need to find its asymptotic variance.

$$
Var(3 \overline{ X }) = \frac{ 9 }{ n^2 } \sum V(X_i) = \frac{ 3 }{ n^2 } n \Big( \frac{ 1 }{ 3 } - \frac{ \theta^2 }{ 9 } \Big) = \frac{ 3- \theta^2 }{ n }
$$


Since this goes to 0 as $n\rightarrow \infty$, we have a consistent estimator.

# 10.3
**A random sample $X_1 , \dots , X_n$ is drawn from a population that is $n(\theta, \theta)$, where $\theta > 0$.**


## a
**Show that the MLE of $\theta$, $\widehat \theta$, is a root of the quadratic equation $\theta^2 + \theta - W = 0$ where $W = (1/n)\sum_{i=1}^{n}X_i^2$, and determine which root equals the MLE.**

Our distribution looks like

$$
N(\theta, \theta) = \frac{ 1 }{ \sqrt{ 2 \pi \theta } } e^{\frac{ (x-\theta)^2 }{ 2\theta }}.
$$


We can find our log likelihood and MLE.

$$
	\begin{align}
		\ell & = -n \log(\sqrt{ 2 \pi \theta }) + - \sum \frac{ (x_i - \theta)^2 }{ 2 \theta } \\
			& = \frac{ -n }{ 2 } \log( 2 \pi \theta) - \frac{ \sum x_i^2 - 2 \theta \sum x_i + n \theta^2}{ 2 \theta }\\
			& = \frac{ -n }{ 2 } \log(2 \pi \theta^2) - \frac{ \sum x_i^2 }{ 2 \theta } + \sum x_i - \frac{ n \theta }{ 2 } \\ \\
		\frac{ \partial  \ell }{\partial \theta} & = \frac{ -n }{ 2 \theta } + \frac{ \sum x_i^2 }{ 2 \theta^2 } - \frac{ n }{ 2 } \\ \\
		\text{set } =0 \\
		0 & = \frac{ -n }{ 2 \theta } + \frac{ \sum x_i^2 }{ 2 \theta^2 } - \frac{ n }{ 2 } \\
			& = \frac{ -1 }{ \theta } + \frac{ \sum x_i^2 }{ n \theta^2 } - 1
	\end{align}
$$

We can find the roots of our quadratic using the quadratic formula.

$$
\theta = \frac{ -1 \pm \sqrt{ 1^2 - 4(1)(-W) } }{ 2 }= \frac{ -1 \pm \sqrt{ 1+4W } }{ 2 }
$$


Our solution above is the positive root (since $\theta$ is a variance and thus must be greater than 0).

## b
**Find the approximate variance of $\widehat \theta$ using the techniques of Section 10.1.3.**

We can use the asymptotic efficiency of MLEs (theorem 10.1.12). To say that 

$$
\sqrt{ n } ( \tau(\widehat \theta) - \tau(\theta)) \rightarrow N(0, v(\theta))
$$

where $v(\theta)$ is the Cramér-Rao lower bound.

$$
	\begin{align}
		CRLB & = \frac{ 1 }{ I_n } \\ \\
		I_n & = - E\Big[\frac{ \partial ^2 \ell }{\partial \theta^2}\Big] \\
			& = - \frac{ n }{ 2 \theta^2 } + \frac{ 2 }{ \theta^3 } \sum E[X_i^2] \\
			& =  - \frac{ n }{ 2 \theta^2 } + \frac{ 2 }{ \theta^3 } n (\theta^2 + \theta \theta) \\
			& = - \frac{ n }{ 2 \theta^2 } +\frac{ 2n(1+1) }{ \theta } \\ 
			& = \frac{ 8n \theta - n  }{ 2 \theta^2 } \\ \\
		CRLB & = \frac{ 1 }{ \frac{ 8n \theta - n  }{ 2 \theta^2 } } \\
			& = \frac{ 2 \theta^2 }{ 8n \theta - n  }
	\end{align}
$$
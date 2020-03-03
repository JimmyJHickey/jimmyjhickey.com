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

Notice that for all of the PDFs below we can expressed as 

$$
f(x | \theta) = c(\theta) m(x), \ a < x < \theta.
$$

Then we know

$$
\int_{a}^{\theta} c(\theta) m(x) dx = 1 \Rightarrow \frac{ 1 }{ c(\theta) } = \int_{a}^{\theta} m(x) dx = 1.
$$

Also as we have shown before, $X_{(n)}$ is a complete sufficient statistic for $\theta$. So any function of $T(X_{(n)})$ that is unbiased for $h(\theta)$ is the best unbiased estimator. The distribution of the max is

$$
f(X_{(n)}) = n \cdot m(y) \frac{ c(\theta)^n }{ c(y)^{n-1} }, \ a < y < \theta.
$$

Take $h(\theta) = \theta^r$. Then, $h'(\theta) = r \cdot \theta^{r-1}$. Consider

$$
	\begin{align}
		\int_{a}^{\theta} f(x) dx = 1 & \iff \int_{a}^{\theta} m(x) dx = \frac{ 1 }{ c(\theta) } \\
		\int_{a}^{\theta} T(X_{(n)}) g(X_{(n)}) = h(\theta) & \iff \int_{a}^{\theta} \frac{ T(X_{(n)}) \cdot n m(y) }{ c(y)^{n-1} } dy = \frac{ h(\theta) }{ c(\theta)^n }.
	\end{align}
$$

We can use the Fundamental Theorem of Calculus to solve for for $T(X_{(n)})$.

$$
	\begin{align}
		m(\theta) & = \frac{ -c'(\theta) }{ c(\theta)^2 } \\
		\frac{ T(\theta) \cdot n m(\theta) }{ c(\theta)^{n-1} } & = \frac{ c(\theta)^n h'(\theta) - h(\theta) \cdot n c(\theta)^{n-1} c'(\theta) }{ c(\theta)^{2n} } \\ \\
		T(X_{(n)}) & = h(X_{(n)}) + \frac{ h'(X_{(n)}) }{ n \cdot m(X_{(n)}) c(X_{(n)})}
	\end{align}
$$



## a
$$
f(x | \theta) = \frac{ 1 }{ \theta } ,\ 0 < x < \theta, \ r < n
$$

Here we take $m(x) = 1$ and $c(\theta) = 1/\theta$. Then,

$$
T(x_{(n)}) = x_{(n)}^r + \frac{ r \cdot x_{(n)}^{r-1} }{ n \frac{ 1 }{ x_{(n)} } } = \frac{ n + r }{ n } x_{(n)}^r
$$


## b
$$
f(x | \theta) = e^{-(x-\theta)}, \ x > \theta
$$

The difference with this PDF is that our estimator will be the minimum order statistic, so

$$
T(X_{(1)}) = h(X_{(1)}) - \frac{ h'(X_{(1)}) }{ n \cdot m(X_{(1)}) c(X_{(1)})}.
$$

Now we can $m(x) = e^{-x}$ and $c(\theta) = e^\theta$.

$$
T(X_{(1)}) = X_{(1)}^r - \frac{ r X_{(1)}^{r-1} }{ n e^{-X_{(1)}} e^{X_{(1)}}} = X_{(1)}^r - \frac{ r X_{(1)}^{r-1} }{ n }
$$


## c
$$
f(x | \theta) = \frac{ e^{-x} }{ e^{-\theta} - e^{-b} }, \ \theta < x < b, \ b \text{ known}
$$

Here we take $m(x) = e^{-x}$ and $c(\theta) = \frac{ 1 }{ e^{-\theta} - e^{-b} }$. Then,

$$
T(X_{(n)}) = X_{(n)}^r - \frac{ r X_{(n)}^{r-1} }{ ne^{-X_{(n)}} } (e^{-X_{(n)}} - e^{-b}) = X_{(n)}^r - \frac{ r X_{(n)}^{r-1} (1-e^{-(b-X_{(n)})}) }{ n }
$$



# 7.58
**Let $X$ be an observation from the pdf**


$$
f(x|\theta) = \Big( \frac{ \theta }{ 2 } \Big)^{|x|} (1-\theta)^{1-|x|}, \ x = -1, 0, 1, \ 0 \leq \theta \leq 1
$$


## a
**Find the MLE of $\theta$.**

$$
	\begin{align}
		L(\theta | x) & = \prod f(x | \theta) \\
			& = \Big( \frac{ \theta }{ 2 } \Big)^{\sum | x_i |} (1-\theta)^{\sum 1 - |x_i| } \\ \\
		\ell & = \sum |x_i| \log(\theta / 2) + (\sum 1 - | x_i |) \log(1 - \theta) \\ \\
		\frac{ \partial  \ell }{\partial \theta} & = \frac{ \sum | x_i | }{ \theta } - \frac{ n - \sum | x_i | }{ 1 - \theta } \\ \\
		0 & = \frac{ \sum | x_i | }{ \theta } - \frac{ n - \sum | x_i | }{ 1 - \theta } \\
		\widehat \theta & = \frac{ \sum |x_i| }{ n } \\
			& = | x_i | & \text{one observation}
	\end{align}
$$


## b
**Define the estimator $T(X)$ by**

$$
T(X) = \begin{cases}
		2 & \text{if } x=1\\
		0 & \text{otherwise.}
	\end{cases}
$$

**Show that $T(X)$ is an unbiased estimator of $\theta$.**

$$
	\begin{align}
		E(T(X)) & = \sum T(X) f(x | \theta) \\
			& = 0 + 0 + 2 \cdot (\frac{ \theta }{ 2 })^{|1|}(1-\theta)^{1-|1|} \\
			& = \theta
	\end{align}
$$

## c
**Find a better estimator of $T(X)$ and prove that it is better.**

Our new estimator will be

$$
S(X) =
\begin{cases}
	1 & \text{if } x = 1 \\
	0 & \text{otherwise}.
\end{cases}
$$

This is the same for $x = -1, 0$ and better for $x = 1$ because $1$ is in the range of $\theta$ whereas $2$ is not.

# 7.60
**Let $X_1, \dots , X_n$ be iid $gamma(\alpha, \beta)$ with $\alpha$ known. Find the best unbiased estimator of $\frac{ 1 }{ \beta }$.**

Notice that $\sum X_i$ is complete sufficient for $\beta$ because it is an exponential family. Also notice $\sum X_i \sim gamma(n \alpha, \beta)$. Then,

$$
	\begin{align}
		E\Big(\frac{ 1 }{ \sum X_i }\Big) & = \frac{ 1 }{ \beta (n \alpha - 1) } \\
		E\Big((n \alpha - 1)  \frac{ 1 }{ \sum X_i }\Big) & =(n \alpha - 1)  \frac{ 1 }{ \beta (n \alpha - 1)} \\
			& = \frac{ 1 }{ \beta }
	\end{align}
$$

Since this is unbiased and based only on the complete sufficient statistic, it is the unique best unbiased estimator by Lehmann-Scheffe.


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

We can find the roots of our quadratic using the quadratic formula.

$$
\theta = \frac{ -1 \pm \sqrt{ 1^2 - 4(1)(-W) } }{ 2 }= \frac{ -1 \pm \sqrt{ 1+4W } }{ 2 }
$$


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
			& = \frac{ -1 }{ \theta } + \frac{ \sum x_i^2 }{ n \theta^2 } - 1 \\
			& = \frac{ -1 }{ \theta } + \frac{ W }{ \theta^2 } - 1 \\
			& = \theta^2 + \theta - W \\ \\
		\theta & = \frac{ -1 \pm \sqrt{ 1+4W } }{ 2 }.
	\end{align}
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
		CRLB & = \frac{ 1 }{ \frac{ 8n \widehat \theta - n  }{ 2 \widehat \theta^2 } } \\
			& = \frac{ 2 \widehat \theta^2 }{ 8n \widehat \theta - n  }
	\end{align}
$$
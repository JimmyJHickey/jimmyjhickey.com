---
layout: post
comments: false
title: Example Problems on Sufficient and Ancillary Statistics
description: ST702 Homework 2 on Sufficient and Ancillary Statistics
tags: ST702 Sufficient Ancillary Statistics
category: ST702
---

* Do not remove this line (it will not be displayed)
{:toc}

# 6.9 (c  and e)
**For each of the following distributions let $X_1, \dots X_n$ be a random sample. Find a minimal sufficient statistic for $\theta$.**

## c
$$
	\begin{align}
		f(x | \theta) & = \frac{ e^{-(x-\theta)} }{ (1+e^{-(x-\theta)})^2 }, & -\infty < x< \infty, & -\infty < \theta < \infty, & \text{logistic}
	\end{align}
$$


$$
	\begin{align}
		\frac{ f(\mathbf{x} | \theta) }{ f(\mathbf{y} | \theta) } & = \frac{ \prod_{ i=1 }^{ n } \frac{ \exp(-(x_i-\theta)) }{ (1+\exp(-(x_i-\theta)))^2 }}{ \prod_{ i=1 }^{ n } \frac{ \exp(-(y_i-\theta)) }{ (1+\exp(-(y_i-\theta)))^2 } } \\
			& = e^{-\sum_{ i=1 }^{ n } y_i - x_i} \frac{ \prod_{ i=1 }^{ n } (1+\exp(-(y_i-\theta)))^2 }{ \prod_{ i=1 }^{ n } (1+\exp(-(x_i-\theta)))^2 }
	\end{align}
$$


Notice that the left exponential is independent of $\theta$ and the right exponentials are only constant in $\theta$ is the order statistcs of $x$ and $y$ are the same. Thus, the order statistics are the minimal sufficient statistics.


## e
$$
	\begin{align}
		f(x | \theta) & = \frac{ 1 }{ 2 } e^{-|x-\theta}, & -\infty < x< \infty, & -\infty < \theta < \infty, & \text{double exponential}
	\end{align}
$$


$$
\frac{ f(\mathbf{x} | \theta) }{ f(\mathbf{y} | \theta) } = \frac{ 1/2 e^{- \sum_{ i=1 }^{ n } |x_i - \theta |} }{ 1/2 e^{- \sum_{ i=1 }^{ n } |y_i - \theta | }}
$$

This looks like another case where we need matching order statistics, but the absolute values may throw that off. This is constant in $\theta$ if $\sum \| x_i - \theta \| = \sum \| y_i - \theta \|$. We can simplify this as

$$
\sum_{x > \theta} (x_i - \theta) + \sum_{x \leq \theta} (\theta - x_i) + \sum_{x > \theta} (y_i - \theta) + \sum_{x \leq \theta} (\theta - y_i) = 0.
$$


Let's say that there are $n_x$ elements in $\\{ x: x < \theta \\}$ and $n_y$ elements in $\\{ y : y < \theta \\}$. Then, 

$$
	\begin{align}
		0 & = \sum_{x > \theta} (x_i - \theta) + \sum_{x \leq \theta} (\theta - x_i) + \sum_{x > \theta} (y_i - \theta) + \sum_{x \leq \theta} (\theta - y_i) \\
			& = (n_x) \theta + \sum_{i=1}^{n_x}(-x_{(i)}) - (n-n_x) \theta + \sum_{i=n_x+1}^{n} (x_{(i)}) + (n_y) \theta+  \sum_{i=1}^{n_y}(-y_{(i)}) - (n-n_y) \theta + \sum_{i=n_y+1}^{n} (y_{(i)})
	\end{align}
$$

Now we are sure that the order statistics are minimal sufficient as that is the only way that this equality holds.

# 6.12
**A natural ancillary statistic in most problems is the _sample size_. For example, let $N$ be a random variable taking values $1, 2, \dots$ with known probabilities $p_1, p_2, \dots$, where $\sum p_i = 1$. Having observed $N = n$, perform $n$ Bernoulli trials with success probability $\theta$, getting $X$ successes.**



## a
**Prove that the pair $(X, N)$ is minimal sufficient and $N$ is ancillary for $\theta$. (Note the similarity to some of the hierarchical models discussed in section 4.4).**

$$
	\begin{align}
		\frac{ f(\mathbf{x}, n_x | \theta) }{ f(\mathbf{y}, n_y | \theta) } & = \frac{ f(\mathbf{x} | \theta, n_x) P(N = n_x) }{ f( \mathbf{y} | \theta, n_y ) P(N=n_y) } \\
			& = \frac{ {n_x \choose x} \theta^x (1-\theta)^{n_x-\theta} p_{n_x} }{ {n_y \choose y} \theta^y (1-\theta)^{n_y-\theta} p_{n_y} } \\
			& = \frac{ {n_x \choose x}  }{ {n_y \choose y}  } \frac{ p_{n_x} }{ p_{n_{y}} } \theta^{x=y} (1-\theta)^{n_x - x - (n_y - y)}
	\end{align}
$$

This is constant in $\theta$ if $x = y$ and $n_x = n_y$. So, our minimal sufficient statistic is $(X, N)$. Also, $P(N = n_i) = p_i$ is constant in $\theta$, so it is ancillary.


## b
**Prove that the estimator $X/N$ is unbiased for $\theta$ and has variance $\theta (1-\theta) E(1/N)$.**

Here we can apply iterated expectations.

$$
	\begin{align}
		E(X / N) & = E[ E(X / N | N)] \\
			& = E[ 1/N \cdot E(X | N)] \\
			& = E[1/N \cdot N \theta] \\
			& = \theta.
	\end{align}
$$


$$
	\begin{align}
		V(X / N)  &= E[V(X / N | N)] + V[E(X / N | N)] \\
			& = E[ 1/N^2\cdot V(X | N)] + V[\theta] \\
			& = E[ 1/N^2 \cdot (N\theta (1 - \theta))] + 0 \\
			& = \theta (1-\theta) E[1/N]
	\end{align}
$$



# 6.19

**The random variable $X$ takes the values $0, 1, 2$ according to one of the following distributions:**

$$
\begin{array}{l c c c c}
	& P(X = 0) & P(X = 1) & P(X = 2) & \\ \hline
	\text{Distribution 1} & p & 3p & 1-4p & 0 < p < \frac{ 1 }{ 4 } \\
	\text{Distribution 2} & p & p^2 & 1 - p - p^2 & 0 < p < \frac{ 1 }{ 2 }
\end{array}
$$

**In each case determine whether the family of distributions of $X$ is complete.**

For a family of distributions to be complete, it must be that case that $E(g(T)) = 0 \forall \theta \Rightarrow P(g(T) = 0) = 1 \forall \theta$.

Family 1 :

$$
E(g(T)) = p \cdot g(0) + 3p \cdot g(1) + (1-4p) \cdot g(2) = p(g(0) + 3 g(1) - 4 g(2)) + g(2)
$$

In order for this to be $0$, we need $g(2) = 0$ and $g(0) = -3 g(1)$. But $g(0)$ and $g(1)$ are not **required** to be $0$, so this family is not complete.

Family 2 : 

$$
E(g(T)) = p \cdot g(0) + p^2 \cdot g(1) + (1 - p - p^2) \cdot g(2) = p^2 (g(1) - g(2)) + p( g(0) - g(2)) + g(2)
$$

In order for this to be $0$, we need $g(2) = 0$, $g(0) = g(2)$, and $g(1) = g(0)$. Thus, $g(0) = g(1) = g(2) = 0$. Thus, the family is complete.


# 6.20
**For each of the following pdfs let $X_1, \dots X_n$ be iid observations. Find a complete sufficient statistic or show that one does not exist.**


## a
$$
	\begin{align}
		f(x | \theta) & = \frac{ 2x }{ \theta^2 }, & 0 < x < \theta, & & \theta > 0
	\end{align}
$$


We can use the factorization theorem to find a sufficient statistic.


$$
	\begin{align}
		f(\mathbf{x} | \theta) & = \prod (\frac{ 2x }{ \theta^2 }) I(max(x_i) < \theta) \\
			& = \underbrace{\prod (2x)}_{h(x)} \underbrace{1/\theta^{2n} I(x_{n}< \theta)}_{g(T(X) | \theta)}
	\end{align}
$$


Thus, the minimum sufficient statistic is the maximum. We can look at the distribution of the maximum.

$$
f_{x_{(n)}} = n f(x) F(X)^{n-1} = n \frac{ 2x }{ \theta^2 } \int^{x}_{0} \frac{ 2t }{ \theta^2 }dt = 2n \frac{ x^{2n-1} }{ \theta^{2n} }
$$

This has the same indicator function as before. Now we can check if it is complete.

$$
E(g(x)) = \int_{0}^{\theta} g(x) 2n \frac{ x^{2n-1} }{ \theta^{2n} }dx =  \frac{ 2n }{ \theta^{2n} }  \int_{0}^{\theta} g(x) x^{2n-1} dx = 0
$$

This is only $0$ for all $\theta$ if $g(x)=0$ (by repeated integration by parts). Thus, it is complete.
## b
$$
	\begin{align}
		f(x | \theta) & = \frac{ \theta }{ (1+x)^{1+\theta}}, & 0 < x< \infty, & & \theta > 0
	\end{align}
$$

$$
	\begin{align}
		f(\mathbf{x} | \theta) & = \prod = \frac{ \theta }{ (1+x)^{1+\theta}} \\
			& = \theta^n \prod (1+x)^{-(1+\theta)}
	\end{align}
$$


We can exponential and log the inside of the product.


$$
	\begin{align}
		f(x | \theta) & = \theta^n \prod (1+x)^{-(1+\theta)} \\
			& = \theta^n e^{\sum (\log((1+x)^{-(\theta+1}))} \\
			& = \theta^n e^{-(\theta + 1) \sum \log(1+x_i)}
	\end{align}
$$

Since this is an exponential family, $\sum \log(1+x_i)$ is our complete sufficient statistic.


## c
$$
	\begin{align}
		f(x | \theta) & = \frac{ \log(\theta) \theta^x }{ \theta - 1 }, & 0 < x< 1, & & \theta > 1
	\end{align}
$$


$$
	\begin{align}
		f(\mathbf{x} | \theta) & = \prod  \frac{ \log(\theta) \theta^x }{ \theta - 1 } \\
			& = (\log(\theta) / (\theta - 1))^n \prod \theta^x \\
			& = (\log(\theta) / (\theta - 1))^n e^{\sum \log(\theta^{x_i})} \\
			& = (\log(\theta) / (\theta - 1))^n e^{\sum x_i \cdot \log(\theta)} \\
			& = (\log(\theta) / (\theta - 1))^n e^{\log(\theta) \sum x_i } \\
	\end{align}
$$


Since this is an exponential family, we know that $\sum x_i$ is our complete sufficient statistic.

## d
$$
	\begin{align}
		f(x | \theta) & = e^{-(x-\theta)} exp(-e^{-(x-\theta)}) & -\infty < x< \infty, & & -\infty \leq \theta \leq \infty
	\end{align}
$$


$$
	\begin{align}
		\frac{ f( \mathbf{x} | \theta) }{ f(\mathbf{y} | \theta) } & = \frac{ \prod e^{-(x-\theta)} exp(-e^{-(x-\theta)}) }{ \prod e^{-(y-\theta)} exp(-e^{-(y-\theta)}) }
	\end{align}
$$

Unfortunately this does not simplify nicely, and we will need the order statistics to be our sufficient statistic. However, notice that this is a location family with $\theta$ as the location parameter. We previously proved that the range $R = X_{(n)} - X_{(1)}$ is ancillary in a location family. Because we have an ancillary statistic that is a function of our sufficient statistic, we know that this family is not complete.


## e
$$
	\begin{align}
		f(x | \theta) & = {2 \choose x} \theta^x (1-\theta)^{2-x}, & x=0,1,2, & & 0 \leq \theta \leq 1
	\end{align}
$$


$$
	\begin{align}
		f(\mathbf{x} | \theta) & = \prod {2 \choose x_i} \theta^{x_i} (1-\theta)^{2-x_i} \\
			& = \prod {2 \choose x_i}  e^{\sum \log( \theta^x (1-\theta)^{2x} )} \\
			& = \prod {2 \choose x_i} e^{\sum \log( \theta^x) + \log( (1-\theta)^{2x} )} \\
			& = \prod {2 \choose x_i}  e^{\sum x_i \log( \theta) + 2x_i \log( 1-\theta )} \\
			& = \prod {2 \choose x_i} e^{(\log( \theta) + 2 \log( 1-\theta ))\sum x_i } \\
	\end{align}
$$

This is an exponential family, so our complete sufficient statistic is $\sum x_i$. 
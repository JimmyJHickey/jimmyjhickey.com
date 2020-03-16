---
layout: post
comments: false
title: Example Problems on Hypothesis Testing
description: ST702 Homework 7 on Hypothesis Testing
tags: ST702 Hypothesis-Testing
category: ST702
---

* Do not remove this line (it will not be displayed)
{:toc}


# 8.2
**In a given city it is assumed that the number of automobile accidents in a given year follows a Poisson distribution. In past years the average number of accidents per year was 15, and this year it was 10. Is it justified to claim that the accident rate has dropped?**

Since $\lambda$ is also the mean of the Poisson distribution, we want to test

$$
P(X = 10 \| \lambda 15) = \sum_{i=0}^{10} \frac{ e^{-15} 15^i }{ i! }.
$$

We can do this in R.

```
> ppois(10, 15)
[1] 0.1184644
```


# 8.6
**Suppose that we have two independent random samples: $X_1, \dots , X_n \stackrel{ \text{iid}}{\sim} exp(\theta)$ and $Y_1, \dots , Y_m \stackrel{ \text{iid}}{\sim} exp(\mu)$.**




## a
**Find the LRT of $H_0: \theta = \mu \text{ vs. } H_1: \theta \neq \mu$.**

Our LRT looks like


$$
\begin{align}
	\lambda(x,y) & = \frac{ \sup_{\theta} \prod_{i=1}^{n} \frac{ 1 }{ \theta } e^{-x_i/\theta} \prod_{j=1}^{m} \frac{ 1 }{ \theta } e^{-y_j/\theta}}{ \sup_{\theta, \mu} \prod_{i=1}^{n} \frac{ 1 }{ \theta } e^{-x_i/\theta} \prod_{j=1}^{m} \frac{ 1 }{ \mu } e^{-y_j/\mu} } \\
		& = \frac{ \sup_{\theta} \frac{ 1 }{ \theta^n } e^{-\sum_{i=1}^{n} x_i/\theta} \frac{ 1 }{ \theta^m } e^{-\sum_{j=1}^{m} y_j/\theta}}{ \sup_{\theta, \mu} \frac{ 1 }{ \theta^n } e^{-\sum_{i=1}^{n} x_i/\theta} \frac{ 1 }{ \mu^m } e^{-\sum_{j=1}^{m} y_j/\mu} } \\
		& = \frac{ \sup_{\theta} \frac{ 1 }{ \theta^{n+m} } e^{- \frac{ \sum_{i=1}^{n}x_i + \sum_{j=1}^{m}y_i }{ \theta }}}{ \sup_{\theta, \mu} \frac{ 1 }{ \theta^n } e^{-\sum_{i=1}^{n} x_i/\theta} \frac{ 1 }{ \mu^m } e^{-\sum_{j=1}^{m} y_j/\mu} } \\
\end{align}
$$


We can take the derivative of the top and set it equal to zero to find the supremum.

$$
\begin{align}
	\frac{ \partial  top }{\partial \theta} & = e^{\frac{ \sum x_i + \sum y_j }{ \theta }} \theta^{-(m+n+2)} (\sum x_i + \sum y_j - (m+n)\theta)\\
	& = 0 \\
	\Rightarrow \\
	\widehat \theta & = \frac{ \sum x_i + \sum y_j }{ m+n }
\end{align}
$$


We can do the same to the bottom. In Mathematica:

$$
\text{Solve}\left[\frac{\partial }{\partial t}\frac{e^{-\frac{x}{t}} e^{-\frac{y}{\mu }}}{\mu ^m t^n}=0\land \frac{\partial }{\partial \mu }\frac{e^{-\frac{x}{t}} e^{-\frac{y}{\mu }}}{\mu ^m t^n}=0,\{\mu ,t\}\right].
$$

This gives

$$
\widehat \mu = \overline{ y }, \ \widehat \theta = \overline{ x }.
$$


Thus,

$$
\lambda(x,y) = \frac{ (m+n)^{m+n} (\sum_{i=1}^{n} x_i)^n  (\sum_{j=1}^{m} y_j)^m}{ n^n m^m \Big( \sum_{i=1}^{n} x_i + \sum_{j=1}^{m} y_j \Big)^{m+n} }.
$$

## b
**Show that the test in part (a) can be based on the statistic**

$$
T = \frac{ \sum X_i }{ \sum X_i + \sum Y_i }.
$$

$$
\begin{align}
\lambda(x,y) & = \frac{ (m+n)^{m+n} (\sum_{i=1}^{n} x_i)^n  (\sum_{j=1}^{m} y_j)^m}{ n^n m^m \Big( \sum_{i=1}^{n} x_i + \sum_{j=1}^{m} y_j \Big)^{m+n} } \\
	& = \frac{ (m+n)^{m+n}}{ n^n m^m } \Big( \frac{  \sum_{i=1}^{n} x_i }{ \sum_{i=1}^{n} x_i + \sum_{j=1}^{m} y_j  }\Big)^n \Big( \frac{ \sum_{j=1}^{m} y_j }{ \sum_{i=1}^{n} x_i + \sum_{j=1}^{m} y_j  }\Big)^m \\
	& = \frac{ (m+n)^{m+n}}{ n^n m^m } T^n (1-T)^m
\end{align}
$$

## c
**Find the distribution of $T$ when $H_0$ is true.**

If $H_0$ is true then $\theta = \mu$

$$
\begin{align}
T & = \frac{ \sum_{i=1}^{n} x_i }{ \sum_{i=1}^{n} x_i + \sum_{j=1}^{m} y_j }\\
	& \sim \frac{ \sum_{i=1}^{n} gamma(1, \theta) }{ \sum_{i=1}^{n} gamma(1, \theta) + \sum_{j=1}^{m} gamma(1, \theta) } \\
	& = \frac{ gamma(n, \theta) }{ gamma(n, \theta)  + gamma(m, \theta) } \\
	& = \frac{ gamma(n, \theta) }{  gamma(n+m, \theta) } \\
	& = beta(n, m)
\end{align}
$$


# 8.8
**A special case of a normal family is one in which th mean and the variance are related, that $n(\theta, a \theta)$ family. If we are interested in testing this relationship regardless of the value of $\theta$, we are again faced with a nuisance parameter problem.**

## a
**Find the LRT of $H_0: a = 1 \text{ vs. } H_1: a \neq 1$ based on a sample $X_1, \dots , X_n$ from a $n(\theta, a \theta)$ family, where $\theta$ is unknown.**

We will start by finding our MLEs (since we can follow the same process for top and bottom).


$$
\begin{align}
\ell(\theta, a) & = - n \log(\sqrt{ 2 \pi }) - 2 n \log(a \theta) - \frac{ \sum x_i^2 - 2 \theta \sum x_i + n \theta^2 }{ 2 a \theta } \\
\frac{ \partial  \ell }{\partial a} & = \frac{ - n }{ 2a } + \frac{ \sum x_i^2 - 2 \theta \sum x_i + n \theta^2 }{ 2 a^2 \theta } \\
\frac{ \partial  \ell }{\partial \theta} & = \frac{ -n }{ 2\theta } + \frac{ \sum x_i^2 - 2 \theta \sum x_i + n \theta^2 }{ 2 a \theta^2 } + \frac{ \sum x_i - n \theta }{ a \theta }
\end{align}
$$

We can then set these equal to 0 and solve. In Mathematica:

```
Solve[-n/(2 a) + (x2 - 2 \[Theta] x1 + n \[Theta]^2)/(
    2 \[Theta] a^2) == 
   0 && -n/(2 \[Theta]) + (x2 - 2 \[Theta] x1 + 
   n \[Theta]^2)/(
    2 a \[Theta]^2) + (x1 - n \[Theta])/(a \[Theta]) == 
   0, {a, \[Theta]}]
```

Which gives

$$
\widehat \theta = \overline{ x } , \widehat a = \frac{ (\sum x_i)^2+ n \sum (x_i^2) }{ n \sum x_i }.
$$


When $a=1$, 

```
Solve[-n/(2 \[Theta]) + 
	(x2 - 2 \[Theta] x1 + n \[Theta]^2)/(
   2 *1 *\[Theta]^2) + 
   (x1 - n \[Theta])/(1* \[Theta]) == 0, \[Theta]]
```

$$
\widehat \theta_1 = \frac{ -n + \sqrt{ n } \sqrt{ n+ 4 \sum (x_i^2) } }{ 2n }
$$

Thus,

$$
\begin{align}
\lambda(x) & = \frac{ \Big( \frac{ 1 }{ 2 \pi \widehat \theta_1 } \Big)^{n/2} e^{-\frac{ \sum(x_i - \widehat \theta_1)^2 }{ 2 \widehat \theta_1 }} }{ \Big( \frac{ 1 }{ 2 \pi \widehat a \widehat \theta } \Big)^{n/2} e^{-\frac{ \sum(x_i - \widehat \theta)^2}{ 2 \widehat a \widehat \theta }} } \\
	& = \frac{ \Big( \frac{ 1 }{ 2 \pi \frac{ -n + \sqrt{ n } \sqrt{ n+ 4 \sum (x_i^2) } }{ 2n } } \Big)^{n/2} e^{-\frac{ \sum(x_i - \frac{ -n + \sqrt{ n } \sqrt{ n+ 4 \sum (x_i^2) } }{ 2n })^2 }{ 2 \widehat \theta_1 }} }{ \Big( \frac{ 1 }{ 2 \pi \frac{ (\sum x_i)^2+ n \sum (x_i^2) }{ n \sum x_i } \overline{ x } } \Big)^{n/2} e^{-\frac{ \sum(x_i - \overline{ x })^2}{ 2 \frac{ (\sum x_i)^2+ n \sum (x_i^2) }{ n \sum x_i } \overline{ x } }} } 
\end{align}
$$

## b
**A similar question can be asked about a related family, the $n(\theta, a \theta^2)$ family. Thus, if $X_1, \dots , X_N \stackrel{ \text{iid}}{\sim} n(\theta, a \theta^2)$, where $\theta$ is unknown, find the LRT of $H_0: a = 1 \text{ vs. } H_1: a \neq 1$.**

We will follow the same process as above.

$$
\begin{align}
\frac{ \partial  \ell }{\partial a} & = \frac{ - n }{ 2a } + \frac{ \sum x_i^2 - 2 \theta \sum x_i + n \theta^2 }{ 2 a^2 \theta^2 } \\
\frac{ \partial  \ell }{\partial \theta} & = -\frac{-2 \theta  n-2 \text{x1}}{2 a \theta ^2}+\frac{\theta ^2 (-n)-2 \theta  \text{x1}+\text{x2}}{a \theta ^3}+\frac{n}{\theta }
\end{align}
$$


``` 
Solve[-(n/\[Theta]) - (-2 x1 - 2 n \[Theta])/(2 a \[Theta]^2) 
	+ ( x2 - 2 x1 \[Theta] - n \[Theta]^2)/(a \[Theta]^3) 
	== 0 && -n/(2 a) + (x2 - 2 \[Theta] x1 + 
	n \[Theta]^2)/(2 \[Theta]^2 a^2) == 0, {\[Theta], a}]
```

This gives

$$
\widehat \theta = \overline{ x }, \ \widehat  a = \frac{ - \sum(x_i^2) + n (\sum x_i)^2 }{ \sum (x_i^2) }.
$$


With $a=1$

``` 
Solve[-(n/\[Theta]) - (- x1 - n \[Theta])/\[Theta]^2 
	+ ( x2 - 2 x1 \[Theta] - n \[Theta]^2)/\[Theta]^3 
	== 0 , \[Theta]]
```

$$
\widehat \theta_1 = \frac{ - \sum x_i + \sqrt{ (\sum x_i)^2 + 4 n \sum (x_i^2) }}{ 2n }.
$$

$$
\begin{align}
\lambda(x) & = \frac{ \Big( \frac{ 1 }{ 2 \pi \widehat \theta_1^2 } \Big)^{n/2} e^{-\frac{\sum (x_i - \widehat \theta_1)^2 }{ 2 \widehat \theta_1^2 }} }{ \Big( \frac{ 1 }{ 2 \pi \widehat a \widehat \theta^2 } \Big)^{n/2} e^{-\frac{\sum (x_i - \widehat \theta)^2 }{ 2 \widehat a \widehat \theta^2 }} } \\
	& =  \frac{ \Big( \frac{ 1 }{ 2 \pi \widehat (\frac{ - \sum x_i + \sqrt{ (\sum x_i)^2 + 4 n \sum (x_i^2) }}{ 2n })^2 } \Big)^{n/2} e^{-\frac{\sum (x_i - \frac{ - \sum x_i + \sqrt{ (\sum x_i)^2 + 4 n \sum (x_i^2) }}{ 2n })^2 }{ 2 \widehat (\frac{ - \sum x_i + \sqrt{ (\sum x_i)^2 + 4 n \sum (x_i^2) }}{ 2n })^2 }} }{ \Big( \frac{ 1 }{ 2 \pi \frac{ - \sum(x_i^2) + n (\sum x_i)^2 }{ \sum (x_i^2) } (\overline{ x })^2 } \Big)^{n/2} e^{-\frac{\sum (x_i - \overline{ x })^2 }{ 2 \frac{ - \sum(x_i^2) + n (\sum x_i)^2 }{ \sum (x_i^2) } (\overline{ x })^2 }} } \\
\end{align}
$$


# 8.9
**Stefanski (1996) establishes the arithmetic-geometric-harmonic mean inequality (see Example 4.7.8 and Miscellanea 4.9.2) using a proof based on likelihood ratio tests. Suppose that $Y_1, \dots , Y_n$ are independent with pdfs $\lambda_i e^{-\lambda_i y_i}$, and we want to test $H_0: \lambda_1 = \dots = \lambda_n \text{ vs. } H_1 \lambda_i \text{ are not all equal}$.**

## a
**Show that the LRT statistic is given by $(\overline{ Y })^{-n}/(\prod Y_i)^{-1}$ and hence deduce the arithmetic-geometric mean inequality.**

Notice that $Y_i \sim exponential(1 / \lambda_i)$. The MLE of $ \widehat \lambda_i is \frac{ 1 }{ Y_i }$. Under $H_0$, all of these are the same, so we have an iid sample and can say that $\widehat \lambda = \frac{ 1 }{ \overline{ Y } }$. Thus, the LRT statistic is

$$
\begin{align}
\lambda(x) & = \frac{ \prod \frac{ 1 }{ \overline{ y } e^{-\frac{ y_i }{ \overline{ y } }} } }{ \prod \frac{ 1 }{ y_i } e^{-\frac{ y_i }{ y_i }} } \\
	& = \frac{ \Big( \frac{ 1 }{ \overline{ y } } \Big) e^{-\frac{ \sum y_i }{ \overline{ y } }} }{ \prod \Big( \frac{ 1 }{ y_i } \Big) e^{-\sum 1} } \\
	& = \frac{ \Big( \frac{ 1 }{ \overline{ y } } \Big)^n e^{-\frac{ -n \overline{ y }}{ \overline{ y } }} }{ \prod \Big( \frac{ 1 }{ y_i } \Big) e^{-n} } \\
	& = \frac{ \Big( \frac{ 1 }{ \overline{ y } } \Big)^n }{ \prod \frac{ 1 }{ y_i } }.
\end{align}
$$


Recall that the LRT is bounded above by 1.

$$
\begin{align}
1 & \geq \frac{ \Big( \frac{ 1 }{ \overline{ y } } \Big)^n }{ \prod \frac{ 1 }{ y_i } } \\
\Big( \frac{ 1 }{ \overline{ y } } \Big)^n & \leq \prod \frac{ 1 }{ y_i } \\
\overline{ y } & \geq \Big( \prod y_i \Big)^{1/n}
\end{align}
$$


## b
**Make the transformation $X_i = 1/Y_i$, and show that the LRT statistic based on $X_1, \dots , X_n$ is given by $\Big[ n / \sum (1/X_i) \Big]^n / \prod X_i$ and hence deduce the geometric-harmonic mean inequality.**

First we can find the PDF of $X$.

$$
\begin{align}
P(X \leq y) & = P(\frac{ 1 }{ Y } \leq y) \\
	& = P(1/y \leq Y)\\
	& = 1 - P(Y \leq 1/y) \\
F_X & = 1 - e^{-\frac{ \lambda }{ x_i }} \\
f_x & = -\frac{ \lambda }{ x^2 } e^{- \frac{ \lambda }{ x }}
\end{align}
$$


Then we can find the MLEs.

$$
\begin{align}
L(\lambda | x) & = \prod \frac{ \lambda_i }{ x_i^2 } e^{-\frac{ \lambda_i }{  x_i}} \\
\ell (\lambda | x) & = \log(\lambda_i) - 2 \log(x_i) - \frac{ \lambda_i }{ x_i } \\
\frac{ \partial  \ell }{\partial \lambda } & = \frac{ 1 }{ \lambda_i } - \frac{ 1 }{ x_i } \\ \\

\text{under } H_0 \\
0 & = \frac{ n }{ \lambda } - \sum \frac{ 1 }{ x_i } \\
\frac{ 1 }{ x_i } & = \frac{ n }{ \lambda } \\
\widehat  \lambda & = \frac{ n }{ \sum \frac{ 1 }{ x_i } } \\ \\

\text{under } H_1 \\
0 & = \frac{ 1 }{ \lambda_i } - \frac{ 1 }{ x_i } \\
\widehat \lambda_i & = x_i
\end{align}
$$

Then, as above, we can calculate our LRT.

$$
\begin{align}
\lambda(x) & = \frac{ \prod -\frac{ \frac{ n }{ \sum \frac{ 1 }{ x_i } } }{ x_i^2 } e^{- \frac{ \frac{ n }{ \sum \frac{ 1 }{ x_i } } }{ x_i }}}{ \prod -\frac{ x_i }{ x_i^2 } e^{- \frac{ x_i }{ x_i }} } \\
	& = \frac{\Big[ \frac{n}{\sum (1/X_i)} \Big]^n}{\prod X_i}
\end{align}
$$

Again, this is bounded by 1, which gives us

$$
\overline{ x } \geq \Big( \prod x_i \Big)^{1/n}
$$
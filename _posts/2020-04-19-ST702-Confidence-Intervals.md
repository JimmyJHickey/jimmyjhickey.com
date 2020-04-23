---
layout: post
comments: false
title: Example Problems on Confidence Intervals
description: ST702 Homework 10 on Confidence Intervals
tags: ST702 Confidence-Intervals
category: ST702
---

* Do not remove this line (it will not be displayed)
{:toc}

# 9.3
**This independent random variables $X_1, \dots , X_n $ have the common distribution**

$$
P(X_i \leq x) = 
\begin{cases}
0 & \text{if } x \leq 0 \\
(x / \beta)^\alpha & \text{if } 0 < x < \beta \\
1 & \text{if } x \geq \beta.
\end{cases}
$$

## a.
**In Exercise 7.10 the MLEs of $\alpha$ and $\beta$ were found. If $\alpha$ is a known constant, $\alpha_0$ find an upper confidence limit for $\beta$ with confidence coefficient 0.95.**


From homework 3, MLE of $\beta$ is $\widehat \beta = X_{(n)}$. We will this and the fact that $\beta$ is a scale parameter to create our pivot quantity $Q(X) = \frac{ X_{(n)} }{ \beta }$.



$$
1 - 0.95 = 0.05 = P\Big( \frac{ X_{(n)} }{ \beta } \leq c \Big) = (P(X \leq \beta c))^n = \Bigg( \Big( \frac{ c \beta }{ \beta } \Big)^{\alpha_0} \Bigg)^n = c^{n \alpha_0}
$$


Take 

$$
c = 0.05^{\frac{ 1 }{ n \alpha_0 }}.
$$

Now we can construct our confidence interval.


$$
0.95 = P( X_{(n)} / \beta > c) = P(X_{(n)} / c > \beta) = P\Big(\beta < \frac{ X_{(n)} }{ 0.05^{\frac{ 1 }{ n \alpha_0 }} }\Big)
$$


## b.
**Use the data of Exercise 7.10 to construct an interval estimate for $\beta$. Assume that $\alpha$ is known and equal to its MLE.**

The max in this data is $ X_{(n)} = 25 = \widehat \beta$ and from homework 3 we know that $\widehat \alpha = 12.5949$. Thus,

$$
0.95 = P\Big(\beta < \frac{ X_{(n)} }{ 0.05^{\frac{ 1 }{ n \alpha_0 }} }\Big) = P\Big(\beta < \frac{ 25 }{ 0.05^{\frac{ 1 }{ 14\cdot 12.5949 }} }\Big) = P(\beta < 25.4284).
$$


So our confidence interval is $(0, 25.4284)$.



# 9.7
## a.
**Find the $1- \alpha$ confidence set for $a$ that is obtained by inverting the LRT of $H_0: a = a_0  \text{ vs. } H_1: a \neq a_0$ based on as sample $X_1, \dots , X_n $ from a $n(\theta, a\theta)$ family, where $\theta$ is known.**

From question 8.8 on homework 7, we know that the unrestricted MLEs are

$$
\widehat \theta = \overline{ x }, \ \widehat a = \frac{ \sum(x_i - \overline{ x })^2 }{ n \overline{ x } }.
$$

Under $H_0$, the restricted MLE for $\theta$ is 


$$
\widehat \theta_0 = \frac{ -a_0 + \sqrt{ a_0^2 + 4 \frac{ x_i^2 }{ n } } }{ 2 }.
$$

Our LRT is

$$
\begin{align}
\lambda(x) & = \frac{ \Big( \frac{ 1 }{ 2 \pi \widehat \theta_1 } \Big)^{n/2} e^{-\frac{ \sum(x_i - \widehat \theta_1)^2 }{ 2 \widehat \theta_1 }} }{ \Big( \frac{ 1 }{ 2 \pi \widehat a \widehat \theta } \Big)^{n/2} e^{-\frac{ \sum(x_i - \widehat \theta)^2}{ 2 \widehat a \widehat \theta }} } \\
	& = \frac{ \Big( \frac{ 1 }{ 2 \pi \frac{ -n + \sqrt{ n } \sqrt{ n+ 4 \sum (x_i^2) } }{ 2n } } \Big)^{n/2} e^{-\frac{ \sum(x_i - \frac{ -n + \sqrt{ n } \sqrt{ n+ 4 \sum (x_i^2) } }{ 2n })^2 }{ 2 \widehat \theta_1 }} }{ \Big( \frac{ 1 }{ 2 \pi \frac{ (\sum x_i)^2+ n \sum (x_i^2) }{ n \sum x_i } \overline{ x } } \Big)^{n/2} e^{-\frac{ \sum(x_i - \overline{ x })^2}{ 2 \frac{ (\sum x_i)^2+ n \sum (x_i^2) }{ n \sum x_i } \overline{ x } }} } 
\end{align}
$$

We can invert this to get the confidence interval $\lambda(x) \geq c(\alpha)$.



## b.
**A similar question can be asked about the related family, the $n(\theta, a\theta ^2)$ family. If $X_1, \dots , X_n $ are iid $n(\theta, a \theta^2)$, where $\theta$ is unknown, find the $1 - \alpha$ confidence set based on inverting the LRT of $H_0: a = a_0  \text{ vs. } H_1: a \neq a_0$.**

We can again take the LRT from problem 8.8b and invert it.

$$
\begin{align}
\lambda(x) & = \frac{ \Big( \frac{ 1 }{ 2 \pi \widehat \theta_1^2 } \Big)^{n/2} e^{-\frac{\sum (x_i - \widehat \theta_1)^2 }{ 2 \widehat \theta_1^2 }} }{ \Big( \frac{ 1 }{ 2 \pi \widehat a \widehat \theta^2 } \Big)^{n/2} e^{-\frac{\sum (x_i - \widehat \theta)^2 }{ 2 \widehat a \widehat \theta^2 }} } \\
	& =  \frac{ \Big( \frac{ 1 }{ 2 \pi \widehat (\frac{ - \sum x_i + \sqrt{ (\sum x_i)^2 + 4 n \sum (x_i^2) }}{ 2n })^2 } \Big)^{n/2} e^{-\frac{\sum (x_i - \frac{ - \sum x_i + \sqrt{ (\sum x_i)^2 + 4 n \sum (x_i^2) }}{ 2n })^2 }{ 2 \widehat (\frac{ - \sum x_i + \sqrt{ (\sum x_i)^2 + 4 n \sum (x_i^2) }}{ 2n })^2 }} }{ \Big( \frac{ 1 }{ 2 \pi \frac{ - \sum(x_i^2) + n (\sum x_i)^2 }{ \sum (x_i^2) } (\overline{ x })^2 } \Big)^{n/2} e^{-\frac{\sum (x_i - \overline{ x })^2 }{ 2 \frac{ - \sum(x_i^2) + n (\sum x_i)^2 }{ \sum (x_i^2) } (\overline{ x })^2 }} } \\
\end{align}
$$

We can invert this to get the confidence interval $\lambda(x) \geq c(\alpha)$.



# 9.13
**Let $X$ be a single observation from the $beta(\theta, 1)$ pdf.**

## a.
**Let $Y = -(\log(X))^{-1}$. Evaluate the confidence coefficient to the set $[y/2, y]$.**


$$
\begin{align}
F_Y(y) & = P( Y \leq y) \\
	& = P( -\log(X)^{-1} \leq y) \\
	& = P(X \geq e^{-1/y}) \\
	& = 1 - P(X < e^{-1/y}) \\ 
	& = 1 - F_X(e^{-1/y}) \\ \\
f_y(Y) & = e^{-1/y}/y^2 F_X(e^{-1/y}) \\
	& = e^{-1/y}/y^2 \frac{ \Gamma( \theta + 1) }{ \Gamma(\theta) \Gamma(1)} e^{(1/y)^{\theta-1}} \\
	& = \frac{ \theta }{ y^2 } e^{-\theta/y}
\end{align}
$$

Thus,

$$
\begin{align}
P( Y/2 \leq \theta \leq Y) & = P( \frac{ 1 }{ 2 } \leq \frac{ \theta }{ Y } \leq 1) \\
	& = P( \frac{ 1 }{ 2 \theta } \leq \frac{ 1 }{ Y } \leq \frac{ 1 }{ \theta }) \\
	& = P( \theta \leq Y \leq 2 \theta) \\
	& = \int_\theta^{2\theta} \frac{ \theta }{ y^2 } e^{-\theta/y} dy \\
	& = \frac{\sqrt{e}-1}{e} \\
	& = 0.238561.
\end{align}
$$

## b.
**Find a pivotal quantity and use it to set up a confidence interval having the same confidence coefficient as the interval in part (a).**

Notice that

$$
f_X(x) = \frac{ \Gamma(\theta + 1) }{ \Gamma(\theta) \Gamma(1) } x^{\theta - 1} = \theta x^{\theta - 1}.
$$


If we take $Z = X^\theta$ as our pivot,

$$
\begin{align}
F_Z & = P(Z \leq z) \\
	& = P(X^\theta \leq z) \\
	& = P(\theta \log(X) \leq \log(z)) \\
	& = P(X \leq Z^{1/\theta}) \\ 
	& = F_X(Z^{1/\theta}) \\
f_Z  & = \frac{ z^{1/\theta - 1} }{ \theta } \theta (z^{1/\theta})^{\theta-1} \\
	& = 1.
\end{align}
$$


Thus, $Z \sim U(0,1)$. We can then find our interval. Take $b- a = 0.238561$.

$$
b-a = P(a \leq X^\theta \leq b) \rightarrow \{\theta : \frac{ \log(b) }{ \log(x) } \leq \theta \leq   \frac{ \log(a) }{ \log(x) } \}
$$

## c.
**Compare the two confidence intervals.**

We can more easily adjust the second interval since we just have to change the range of $b - a$; however, they both accomplish the same $1-\alpha$ coverage.



# 9.25
**If $X_1, \dots , X_n $ are iid with pdf $f( x \| \mu) = e^{-(x-\mu)}I_{[\mu, \infty)}(x)$, then $Y = \min \{ X_1, \dots , X_n \}$ is sufficient for $\mu$ with pdf**


$$
f_Y(y | \mu) = n e^{-n(y-\mu)} I_{[\mu, \infty)}(y). %]
$$

**In Example 9.2.13 a $1 - \alpha$ confidence interval for $\mu$ was found using the method of Section 9.2.3. Compare that interval to $1-\alpha$ intervals obtained by likelihood and pivotal methods.**


Our test is $H_0: \mu = \mu_0  \text{ vs. } H_1: \mu \neq \mu_0 $.

Let's start with the LRT. We can see about that our function is increasing in $\mu$, so the unrestricted MLE is $\widehat \mu = y$. Also, since $Y$ is sufficient for $\mu$, we can use $f_Y$ in the LRT.

$$
\lambda(y) = \frac{ n e^{-n(y - \mu_0)} I(\mu_0 \leq y < \infty)}{ n e^{-n(y-y)} I(\mu \leq y < \infty) } = e^{-n(y-\mu_0)} I(\mu_0 \leq y < \infty) =
\begin{cases}
0 & y < \mu_0 \\
e^{-n(y-\mu_0)} & y \geq \mu_0
\end{cases}
$$

So we reject $H_0$ is $\lambda_Y < c(\alpha)$.

$$
\begin{align}
\alpha & = P(\text{reject null given null}) \\
	& = P(Y > \mu_0 - \frac{ \log(c(\alpha)) }{ n } | \mu = \mu_0) \\
	& = \int_{\mu_0 -  \frac{ \log(c(\alpha)) }{ n }}^\infty f_Y dy \\
	& = c(\alpha)
\end{align}
$$

Thus, take $c(\alpha) = \alpha$. Then the $1 - \alpha$ confidence interval is

$$
\mu \leq y \leq \mu - \frac{ \log(\alpha) }{ n } \rightarrow y + \frac{ \log(\alpha) }{ n } \leq \mu \leq y.
$$


Now let's look at the pivotal method. Since this is a location family, let's take $Z = Y - \mu$ to be our pivot. Then $f_Z$ will be our relocated pdf.

$$
f_Z(z) = n e^{-n z} I(0 \leq z < \infty)
$$

Then we can take find our interval $P(a \leq Z \leq b) = 1 - \alpha$. We will split the probability equally. That is,

$$
\alpha_2 = P(0 \leq Z \leq a) = P(b \leq Z \leq \infty).
$$

``` 
Solve[\[Alpha]/2 == Integrate[n E^(-n z), {z, 0, a}], a]
Solve[\[Alpha]/2 == Integrate[n E^(-n z), {z, b, \[Infinity]}], b]
```


We get

$$
a = \frac{ - \log(1 - \alpha/2) }{ n } , \ b = \frac{ -\log(\alpha/2) }{ n }.
$$

Notice that $\alpha \in [0,1]$, so the $\log$'s will be negative, making $a$ and $b$ positive. We can invert this to find the interval.

$$
Y + \frac{ \log(\alpha/2) }{ n } \leq \mu \leq Y + \frac{ \log(1 - \alpha/2) }{ n }
$$


Since these two intervals have the same $1-\alpha$ coverage, we can compare the lengths.

LRT:

$$
y - y - \frac{ 1 }{ 2 } \log(\alpha) = - \frac{ 1 }{ 2 } \log(\alpha)
$$


Pivotal:

$$
y + \frac{ 1 }{ n } \log(1 - \alpha/2) - y - \frac{ 1 }{ n } \log(\alpha/2) = \frac{ 1 }{ n } \log(\frac{ 1 - \alpha/2 }{ \alpha/2 })
$$


Since $-\log(\alpha) < \log(\frac{ 1 - \alpha /2 }{ \alpha/2 })$ for $\alpha \in [0,1]$, the LRT interval is shorter for the same coverage.
---
layout: post
comments: false
title: Example Problems on Asymptotics
description: ST793 Homework 4 on Asymptotics
tags: ST793 Likelihoods Statistics
category: ST793
---

* Do not remove this line (it will not be displayed)
{:toc}

5.5, 5.9, 5.11, 5.13, 5.24 

# 5.5
**Consider the simple linear regression setting**

$$
Y_i = \alpha + \beta x_i + e_i,  \ i = 1, \dots ,n,
$$

**where the $x\_i$ are known constants, and $e\_1, \dots , e\_i$ are iid with mean 0 and finite variance $\sigma^2$. After a little algebra, the least squares estimator has the following representation**


$$
\widehat \beta - \beta = \frac{ \sum_{i=1}^n (x_i - \overline{ x }) e_i }{ \sum_{i=1}^n(x_i - \overline{ x })^2 }.
$$

**Using that representation, prove that $\widehat \beta \stackrel{ \text{p}}{\rightarrow} \beta$ as $n \rightarrow \infty$ if $\sum\_{i=1}^n (x\_i - \overline{ x })^2 \rightarrow \infty$.**


We can proceed by Chebychev's inequality.

$$
\begin{align}
\lim_{n \rightarrow \infty} P\Big(|\widehat \beta - \beta| > \epsilon) & = \lim_{n \rightarrow \infty} P(\frac{ | \sum_{i=1}^n (x_i - \overline{ x }) e_i |}{ \sum_{i=1}^n (x_i - \overline{ x })^2} > \epsilon\Big) \\
    & = \lim_{n \rightarrow \infty} P\Big(| \sum_{i=1}^n (x_i - \overline{ x }) e_i | >  \sum_{i=1}^n (x_i - \overline{ x })^2 \epsilon\Big) \\
    & \leq \lim_{n \rightarrow \infty} \frac{ \text{Var} \Big( \Big( \sum_{i=1}^n (x_i - \overline{ x })e_i \Big)^2 \Big) }{ \epsilon^2 \Big( \sum_{i=1}^n (x_i - \overline{ x })^2 \Big)^2 } \\
    & = \lim_{n \rightarrow \infty} \frac{ \sigma^2 \sum_{i=1}^n(x_i - \overline{ x })^2 }{ \epsilon^2 \Big( \sum_{i=1}^n (x_i - \overline{ x })^2 \Big)^2 } \\
    & = \lim_{n \rightarrow \infty} \frac{ \sigma^2 }{ \epsilon^2 \Big( \sum_{i=1}^n (x_i - \overline{ x })^2 \Big) }
\end{align}
$$

We know that the denominator goes to infinity, so the limit goes to 0. Thus, $\widehat \beta \stackrel{ \text{p}}{\rightarrow}\beta$.

# 5.9
**Let $X\_1, \dots , X\_n$ be iid from a distribution with mean $\mu$, variance $\sigma^2$ and finite central moments, $\mu\_3$ and $\mu\_4$. Consider $\widehat \theta = \overline{ X } / s\_n$, a measure of "effect size" used in meta-analysis. Prove that $\widehat \theta \stackrel{ \text{p}}{\rightarrow} \theta = \mu / \sigma$ as $n \rightarrow \infty$.**

By WLLN we know $\overline{ X } \stackrel{ \text{p}}{\rightarrow} \mu$. The book also shows that $s_n^2 \stackrel{ \text{p}}{\rightarrow} \sigma^2$. Thus, by CMT we know $\sqrt{ s_n^2 } = s_n \stackrel{ \text{p}}{\rightarrow} \sigma = \sqrt{ \sigma^2 }$. Thus, since $\overline{ X }$ and $s_n$ converge piecewise and are independent, we can apply the continuous mapping theorem again. Take $g(a,b) = a / b$. Then 

$$
g(\overline{ X }, s_n)  = \frac{ \overline{ X } }{ s_n }\stackrel{ \text{p}}{\rightarrow} \frac{ \mu }{ \sigma } = g(\mu, \sigma).
$$

# 5.11
**In the continuation of Example 5.20 (p. 230) on 231, it follows that under the local alternative $\mu\_i = \mu + d\_i/\sqrt{ n }$, $(k-1) F = \sum\_{i=1}^k n (\overline{ X }\_i - \overline{ \overline{ X }})^2/s\_p^2$ converges in distribution to a noncentral chi-squared distribution with $k-1$ degrees of freedom and noncentrality parameter $\lambda = d^T (I\_k - k^{-1} 1\_k 1\_k^T)d/\sigma^2 = \sum\_{i=1}^k(d\_i - \overline{ d })^2 / \sigma^2$. Now, if the data in a one-way ANOVA setup such as Example 5.20 (p.230) are normally distributed with means $\mu\_1 , \dots \mu\_k$ and common variance $\sigma^2$, then the exact power of the ANOVA $F$ statistic is the probability that a noncentral $F$ distribution with $k-1$ and $k(n-1)$ degrees of freedom and noncentrality parameter $\lambda = \sum\_{i=1}^{k}n(\mu\_i - \overline{ \mu })^2 / \sigma^2$ is larger than a percentile of the central version f that $F$ distribution. In R, that would be `1-pf(qf(.95,k-1,k*(n-1)),k-1,k*(n-1),nc)`, where $\text{nc} = \lambda$ and the level is 0.05. Show that if $\mu\_i = \overline{ \mu } + d\_i / \sqrt{ n }$, then $\sum\_{i=1}^k (d_i - \overline{ d })^2 / \sigma^2 = \sum\_{i=1}^k n(\mu\_i - \overline{ \mu })^2 / \sigma^2$, that is, the asymptotic chi-squared approximation uses the same noncentrality parameter. In R that would be `1-pchisq(qchisq(.95,k-1),2,nc)`. Compare the approximation for $k=3$ and $nc=10$ to the true power for $n=5,10,$ and $20$.**


Notice $d_i = \sqrt{ n } (\mu_i - \overline{ \mu })$ and 

$$
\overline{ d } = \frac{ 1 }{ k } \sum_{i=1}^k = \frac{ 1 }{ k } \sum_{i=1}^{k} \sqrt{ n } (\mu_i - \overline{ \mu }) = 0.
$$

Thus,

$$
\sum_{i=1}^k \frac{ (d_i - \overline{ d })^2 }{ \sigma^2 } = \frac{ (\sqrt{ n } (\mu_i - \overline{ \mu }) - 0)^2 }{ \sigma^2 } = \frac{ n( \mu_i - \overline{ \mu }) }{ \sigma^2 }.
$$

Using the R code provided, we get

$$
\begin{array}{ r c c c }
n & 5 & 10 & 20 \\
\text{Exact} & 0.7015083 & 0.7673536 & 0.7933118 \\
\text{Approximate} & 0.8154214 & 0.8154214 & 0.8154214.
\end{array}
$$

Notice that as $n$ increases our exact calculation gets closer to our approximation.

# 5.13
**Suppose that $\widehat \theta_1$ is $\text{AN}(\theta_0, A_1/n)$ as $n \rightarrow \infty$.**


## a.
**What can we say about the consistency of $\hat \theta_1$? Why?**


By Theorem 5.13, if $A_i / n \rightarrow 0$, then $\widehat \theta_1$ is consistent for $\theta_0$.

## b.
**If $\widehat \theta_1 - \widehat \theta_2 \stackrel{ \text{p}}{\rightarrow} 0$, what can we say about the consistency of $\widehat \theta_2$? Why?**

Assuming $ \widehat \theta_1 \stackrel{ \text{p}}{\rightarrow}\theta_0$,

$$
\begin{align}
\widehat \theta_1 - \widehat \theta_2 & \stackrel{ \text{p}}{\rightarrow} 0 \\
\widehat \theta_2 - \widehat \theta_1 & \stackrel{ \text{p}}{\rightarrow} 0 & \text{CMT} \\
\widehat \theta_2 - \widehat \theta_1 + \widehat \theta_1 & \stackrel{ \text{p}}{\rightarrow} 0 + \theta_0 & \text{CMT} \\
\widehat \theta_2  & \stackrel{ \text{p}}{\rightarrow} \theta_0
\end{align}
$$

## c.
**If $\sqrt{ n }(\widehat \theta_1 - \widehat \theta_2) \stackrel{ \text{p}}{\rightarrow} b $, what can we say about the asymptotic normality of $\widehat \theta_2$? Why?**

Assuming what we showed in (a) or that $A_1$ is constant,

$$
\begin{align}
\sqrt{ n }(\widehat \theta_1 - \widehat \theta_2) & \stackrel{ \text{p}}{\rightarrow} b \\
\frac{ \sqrt{ n } }{ \sqrt{ A_1 }  }(\widehat \theta_2 - \widehat \theta_1) & \stackrel{ \text{p}}{\rightarrow} \frac{ -b }{ \sqrt{ A_1 } } & \text{CMT}\\
\frac{ \sqrt{ n } (\widehat \theta_1 - \theta_0) }{ \sqrt{ A_1 } } + \frac{ \sqrt{ n } }{ \sqrt{ A_1 }  }(\widehat \theta_2 - \widehat \theta_1) & \stackrel{ \text{d}}{\rightarrow} N(0,1) - \frac{ b }{ \sqrt{ A_1 } } & \text{Slutsky} \\
\frac{ \sqrt{ n } (\widehat \theta_2 - \theta_0) }{ \sqrt{ A_1 } }& \stackrel{ \text{d}}{\rightarrow} N\Big(- \frac{ b }{ \sqrt{ A_1 } } ,1\Big) \\
\widehat \theta_2 & \sim AN\Big( \theta_0 - \frac{ b }{ \sqrt{ n } }, \frac{ A_1 }{ n } \Big).
\end{align}
$$

# 5.24 
**When two independent binomials $X_1$ is $Binomial(n_1, p_1)$ and $X_2$ is $Binomial(n_2, p_2)$, are put in the form of a $2 \times 2$ table (see Example 5.31, p. 240), then one often estimates the odds ratio**

$$
\theta = \frac{ \frac{ p_1 }{ 1-p_1 } }{ \frac{ p_2 }{ 1-p_2 } } = \frac{ p_1 ( 1- p_2) }{ p_2 (1 - p_1) }.
$$

**The estimate $\widehat \theta$ is obtained by inserting $\widehat p_1 = X_1 / n_1$ and $\widehat p_2 = X_2 / n_2$ in the above expression. Show that the $\log(\widehat \theta)$ has asymptotic variance**

$$
\frac{ 1 }{ n_1 p_1 (1-p_1) } + \frac{ 1 }{ n_2 p_2(1-p_2) }
$$

We know

$$
\widehat p_1 \sim AN \Big( p_1, \frac{ p_1(1-p_1) }{ n_1 } \Big) \perp \widehat p_2 \sim AN \Big( p_2, \frac{ p_2(1-p_2) }{ n_1 } \Big).
$$

Thus,

$$
\begin{bmatrix}
\widehat p_1 \\
\widehat p_2
\end{bmatrix}
\sim AN \Big( \begin{bmatrix}
p_1 \\
p_2
\end{bmatrix},
\begin{bmatrix}
\frac{ p_1(1-p_1) }{ n_1 } & 0 \\
0 & \frac{ p_2(1-p_2) }{ n_2 }
\end{bmatrix}
\Big).
$$

Take 

\$$
\begin{align}
g(\begin{bmatrix}a & b \end{bmatrix}) & = \log(\frac{ a(1-b) }{ b(1-a) }) \\
g'(\begin{bmatrix} a & b \end{bmatrix}) & = \begin{bmatrix} \frac{ 1 }{ a(1-a) } & \frac{ 1 }{ b(b-1) } \end{bmatrix}.
\end{align}
$$



Then, by the delta method

$$
AVar(g(\begin{bmatrix} \widehat p_1 & \widehat p_2 \end{bmatrix})) = \begin{bmatrix}
\frac{ 1 }{ p_1(1-p_1) } & \frac{ 1 }{ p_2(p_2-1) }
\end{bmatrix}
\begin{bmatrix}
\frac{ p_1(1-p_1) }{ n_1 } & 0 \\
0 & \frac{ p_2(1-p_2) }{ n_2 }
\end{bmatrix}
\begin{bmatrix}
\frac{ 1 }{ p_1(1-p_1) } \\
\frac{ 1 }{ p_2(p_2-1) }
\end{bmatrix}
= \frac{ 1 }{ n_1 p_1 (1-p_1) } + \frac{ 1 }{ n_2 p_2(1-p_2) }
$$
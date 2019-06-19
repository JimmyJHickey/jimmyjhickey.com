---
layout: post
comments: false
title: Example Problems on Continuous Random Variables
description: ST501 Homework 4 Continuous Random Variables
tags: ST501 Random-Variables Continuous Probability Examples Statistics
---

Problems: 2.41, 2.46, 2.55, 4.31, 1, 2, 3, 4, 5, 6


* Do not remove this line (it will not be displayed)
{:toc}


# 2.41
**Find the upper and lower quantiles of the exponential distribution.**

Note that the CDF for the exponential distribution is:

$$
F(X)=
    \begin{cases}
        \begin{align}
            & 0 & x < 0 \\
            & 1-e^{-\lambda x} & x \geq 0
        \end{align}
    \end{cases}
$$

Now, we can find the quantiles by setting this equal to $0.25$ and $0.75$.

$$
    \begin{align}
        0.25 & = 1 - e^{-\lambda x_{0.25}} \\
        0.75 & = e^{-\lambda x_{0.25}} \\
        \ln{0.75} & = -\lambda x_{0.25} \\
        x_{0.25} & = \frac{-\ln{0.75}}{\lambda}
    \end{align}
$$

$$
    \begin{align}
        0.75 & = 1 - e^{-\lambda x_{0.75}} \\
        0.25 & = e^{-\lambda x_{0.75}} \\
        \ln{0.25} & = -\lambda x_{0.75} \\
        x_{0.75} & = \frac{-\ln{0.25}}{\lambda}
    \end{align}
$$

# 2.46
**$T$ is an exponential random variable, and $P(T<1)=0.5$. What is $\lambda$?**

For $P(T<1)$ we can plug in $1$ as $t$ in our CDF.

$$
    \begin{align}
        P(T<1) & = 0.25 \\
        1 - e^{-\lambda (1)} & = 0.25 \\
        e^{-\lambda} & = 0.75 \\
        \lambda & = -ln{0.75} \\
            & = 0.287682
    \end{align}
$$

# 2.55
**$X \sim N(\mu, \sigma^2)$, find the value of $c$ in terms of $\sigma$ such that $P(\mu - c \leq X \leq \mu + c)=0.95$.**

Note that $P(\mu - c \leq X \leq \mu + c) = P(X \leq \mu + c) - P(\mu - c \leq X)$. Now, we can convert them each to z scores.

$$
    \begin{align}
        P(X \leq \mu + c) & = P(\frac{X-\mu}{\sigma} \leq \frac{\mu + c - \mu}{\sigma})\\
            & = P(Z \leq \frac{c}{\sigma}) \\
            \\
       P(X \leq \mu - c) & = P(\frac{X-\mu}{\sigma} \leq \frac{\mu - c - \mu}{\sigma})\\
            & = P(Z \leq \frac{-c}{\sigma})
    \end{align}
$$

This gives $P(Z \leq \frac{c}{\sigma}) - P(Z \leq \frac{-c}{\sigma}) = 0.95$. Recombining these gives $P(\frac{-c}{\sigma} \leq Z \leq \frac{c}{\sigma}) = 0.95$. By using a Z table we get $\frac{-c}{\sigma} = -1.96$ and $\frac{c}{\sigma} = 1.96$. Thus, $c = 1.96 \sigma$.

# 4.31
**Let $X$ be uniformly distributed on the interval $[1,2]$. Find $E(1/X)$. Is $E(1/X) = 1/E(X)$?**

$$
    \begin{align}
        E(1/X) & = \int_{1}^{2} \frac{1}{x} \frac{1}{2-1} dx \\
            & = \int_{1}^{2} \frac{1}{x} dx \\
            & = \ln{x} \big|_{1}^{2} \\ 
            & = \ln{2} - \ln{1} \\
            & = \ln{2}
    \end{align}
$$

Now let's check $1/E(X)$.

$$
    \begin{align}
        1/E(X) & = \frac{1}{\frac{2+1}{2}}\\
            & = \frac{2}{3}\\
            \\
            1/E(X) & \neq E(1/X)
    \end{align}
$$

# 1
**From past data it is known that GRE (Graduate Record Examination) scores follow a normal distribution with mean $500$ and variance $100^2$.**


## a. 
**Define a random variable for this question and state the distribution using the $∼$ notation.**

$$
Y \sim N(500, 100^2)
$$

## b.
**The top $5%$ of applicants  (as measured by GRE scores) will receive scholarships. How high does your GRE score have to be to qualify for a scholarship?**

The top $5%$ of applicants are int he $95^{th}%$ percentile of students. So, we are looking for $P(X<x) = 0.95$. For this we can use R. 

```qnorm(0.95, 500, 100) = 665.4854```

## c.
**People that score below $510$ retake the exam. If a person is selected randomly what is the probability they will retake the exam?**

For this we want $P(X<510)$. Again, we can utilize R.

```pnorm(510, 500, 100) = 0.5398```

# 2
**The percentage of impurities per batch in a chemical product is a random variable that $Beta$ distribution with $\alpha = 3$ and $\beta = 2$. A batch with more than $40%$ impurities cannot be sold.**

## a.
**Find the probability that a randomly selected batch cannot be sold because of excessive impurities.**

This is equivalent to saying

$$
    \begin{align}
        P(Y > 0.40) &= 1 - P(Y \geq 0.40) \\
            & = 1 - \int_0^{0.40} \frac{\Gamma(3+2)}{\Gamma(3)\Gamma(2)} y^{3-1} (1-y)^{2-1} dy\\
            & = 0.8208
    \end{align}
$$

Or, in R

```
1 - pbeta(0.40, 3, 2) = 0.8208
```

## b.
**What is the mean percentage of impurities? the variance?**

$$
    \begin{align}
        E(Y) & = \frac{\alpha}{\alpha + \beta}\\
            & = \frac{3}{3 + 2}\\
            & = \frac{3}{5} \\
            \\
        Var(Y) & = \frac{\alpha \beta}{(\alpha + \beta)^2(\alpha + \beta + 1)}\\
            & = \frac{3 \cdot 2}{(3+2)^2(3+2+1)} \\
            & = \frac{1}{25}
    \end{align}
$$

# 3
**A manufacturing plant uses a specific bulk product. The amount used (in tons) in one day has a gamma distribution with $\alpha = 3/2$ and $\lambda = 1/3$.**

## a.
**Find the probability that the plant will use more than $4$ tons on a given day.**


$$
    \begin{align}
        P(X>4) & = 1 - P(X<4) \\
            & = 1 - \int_{0}^{4} \frac{(1/3)^{3/2}}{\Gamma(3/2)} y^{3/2-1} e^{-1/3 y} dy \\
            & = 0.44592
    \end{align}
$$

Or, using R,

```
1 - pgamma(4, 3/2, 1/3) = 0.44592
```
## b.
**How much of the bulk product should be stocked so that the plant’s chance of running out of the product is only $0.05$.**

To have only a $0.05$ chance of running out is equivalent to being in the $0.95$ quantile. We can use R to calculate this:

```
qgamma(0.95, shape = 3/2, rate = 1/3) = 11.72209
```

# 4
**Name the distribution of the random variable described and specify the parameters. A parachutist lands at a random point on a line between point $A$ (call this $0$) and point $B$ (call this $\theta$). Let $Y$ be the distance the parachutist lands from point $A$.**

Since the parachutist can land anywhere with equal probability, this would be described as a uniform distribution with parameters $A$ and $B$ or their corresponding locations $0$ and $\theta$.

$$
Y \sim Unif(0, \theta)
$$

# 5
**Name the distribution of the random variable described and specify the parameters. The time until failure of a computer part tends to be very high early on, but becomes less likely as time goes on. The mean of the failure time is $200$ days (rate=$1/200$). Let $Y$ be the time until failure of the computer part.**

Generally, when looking at rate problems we are dealing with an exponential distribution. This is again confirmed by the higher failures early on and then the failure rate tapering off, much like the PDF of the distribution itself.

$$
Y \sim Exp(1/200)
$$

# 6
**Let $Y \sim Beta(\alpha, \beta)$. Derive $E(Y)$ and $Var(Y)$.**

$$
    \begin{align}
        E(Y) & = \int_{0}^{1} y \cdot \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)\Gamma(\beta)} y^{\alpha - 1} (1-y)^{\beta - 1} dy\\
            & = \int_{0}^{1} \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)\Gamma(\beta)} y^{(\alpha + 1) - 1} (1-y)^{\beta - 1} dy & \text{Multiply in $y$}\\
            & = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)} \int_{0}^{1} \frac{1}{\Gamma(\beta)} y^{(\alpha + 1) - 1} (1-y)^{\beta - 1} dy  & \text{Pull out contants with $\alpha$} \\
            & = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)} \frac{\Gamma(\alpha + 1)}{\Gamma(\alpha + 1 + \beta)}\int_{0}^{1} \frac{\Gamma(\alpha + 1 + \beta)}{\Gamma(\alpha + 1)\Gamma(\beta)} y^{(\alpha + 1) - 1} (1-y)^{\beta - 1} dy & \text{Multiply in new constants}\\
            & = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)} \frac{\Gamma(\alpha + 1)}{\Gamma(\alpha + 1 + \beta)} & \text{The integral is a gamma PDF}\\
            & = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)} \frac{\Gamma(\alpha)}{\Gamma(\alpha + \beta)} \frac{\alpha}{\alpha + \beta} & \text{Pull out terms from gamma function} \\
            & = \frac{\alpha}{\alpha + \beta}
    \end{align}
$$

$$
    \begin{align}
        Var(Y) & = E(Y^2) - E(Y)^2\\
        \\
        E(Y^2) & = \int_{0}^{1} y^2 \cdot \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)\Gamma(\beta)} y^{\alpha - 1} (1-y)^{\beta - 1} dy\\
            & = \int_{0}^{1} \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)\Gamma(\beta)} y^{(\alpha + 2) - 1} (1-y)^{\beta - 1} dy & \text{Multiply in $y^2$} \\
            & = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)} \int_{0}^{1} \frac{1}{\Gamma(\beta)} y^{(\alpha + 2) - 1} (1-y)^{\beta - 1} dy  & \text{Pull out contants with $\alpha$} \\
            & = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)} \frac{\Gamma(\alpha + 2)}{\Gamma(\alpha + 2 + \beta)}\int_{0}^{1} \frac{\Gamma(\alpha + 2 + \beta)}{\Gamma(\alpha + 2)\Gamma(\beta)} y^{(\alpha + 2) - 1} (1-y)^{\beta - 1} dy & \text{Multiply in new constants}\\
            & = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)} \frac{\Gamma(\alpha + 2)}{\Gamma(\alpha + 2 + \beta)} & \text{The integral is a gamma PDF}\\
            & = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)} \frac{\Gamma(\alpha)}{\Gamma(\alpha + \beta)} \frac{(\alpha + 1) (\alpha)}{(\alpha + \beta + 1) (\alpha + \beta)} & \text{Pull out terms from gamma function} \\
            & = \frac{(\alpha + 1) (\alpha)}{(\alpha + \beta + 1) (\alpha + \beta)}\\
            \\
        Var(Y) & = E(Y^2) - E(Y)^2\\
            & = \frac{(\alpha + 1) (\alpha)}{(\alpha + \beta + 1) (\alpha + \beta)} - (\frac{\alpha}{\alpha + \beta})^2 \\
            & = \frac{\alpha \beta}{(\alpha + \beta)^2(\alpha + \beta + 1)}
    \end{align}
$$
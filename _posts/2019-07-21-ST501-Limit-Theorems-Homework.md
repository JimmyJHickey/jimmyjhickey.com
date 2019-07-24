---
layout: post
comments: false
title: Example Problems on Limit Theorems
description: ST501 Homework 7 on Limit Theorems
tags: ST501 Random-Variables Limit Theorems Distribution Probability Examples Statistics
---

Problems: 5.2, 5.5, 5.6, 5.19, 5.28, Extra Problem 1


* Do not remove this line (it will not be displayed)
{:toc}

# 5.2
**Let $X_i$ be as in Problem 1 but with $E(X_i) = \mu_i$ and $n^{-1}\sum_{i=1}^{n}\mu_i \rightarrow \mu$. Show that $\bar X \rightarrow \mu$ in probability.**

Since these distributions have different means, we cannot apply the Law of Large Numbers. Thus, we will start this the definition of convergence in probability.

$$
	\begin{align}
		\lim_{n\rightarrow \infty} P\Big[ | \bar{X_n} - \mu | \geq \epsilon \Big] & = \lim_{n\rightarrow \infty} P\Big[(\bar{X_n} - \mu)^2 \geq \epsilon^2 \Big] \\
		& \leq \lim_{n\rightarrow \infty} \frac{E\Big[ (\bar{X_n} - \mu )^2 \Big]}{\epsilon^2} & \text{Markov's Inequality}
	\end{align}
$$

Let's look at the numerator,

$$
	\begin{align}
		E\Big[ (\bar{X_n} - \mu )^2 \Big] & = E\Big[ (\bar{X_n} - \mu + E(\bar{X_n}) - \bar{X_n})^2 \Big] & = \text{Adding } (E(\bar{X_n}) - E(\bar{X_n}))\\
			& = E\Big[ \Big( (\bar{X_n} - E(\bar{X_n}))  + (E(\bar{X_n})- \mu ) \Big)^2  \Big] \\
			& = E\Big[ (\bar{X_n} - E(\bar{X_n}))^2  + 2(\bar{X_n} - E(\bar{X_n}))(E(\bar{X_n})- \mu ) +  (E(\bar{X_n})- \mu )^2  \Big] \\
			& = E\Big[ (\bar{X_n} - E(\bar{X_n}))^2  \Big]+ E\Big[2(\bar{X_n} - E(\bar{X_n}))(E(\bar{X_n})- \mu ) \Big]+  E\Big[(E(\bar{X_n})- \mu )^2  \Big] & E \text{ is a linear operator} \\
			& = Var(\bar{X_n}) + 0 + (E(X_n) - \mu)^2 & \text{simplifying Expected values} \\
			& = Var(\frac{1}{n} \sum_{i=1}^{n}X_i) + (\frac{1}{n}\sum_{i=1}^{n} \mu_i - \mu)^2 \\
			& = \frac{1}{n^2} \sum_{i=1}^{n}\sigma_{i} + (\frac{1}{n}\sum_{i=1}^{n} \mu_i - \mu)^2
	\end{align}
$$

Now we can back to the original inequality and take the limit.

$$
	\begin{align}
		\lim_{n\rightarrow \infty} \frac{E\Big[ (\bar{X_n} - \mu )^2 \Big]}{\epsilon^2} & = \frac{\frac{1}{n^2} \sum_{i=1}^{n}\sigma_{i} + (\frac{1}{n}\sum_{i=1}^{n} \mu_i - \mu)^2}{\epsilon^2} \\
		& = \frac{0 + (\mu - \mu)}{\epsilon^2} & \text{Using limits from the problem} \\
		& = 0
	\end{align}
$$

Thus, by definition, $\bar X \xrightarrow{p} \mu$.

# 5.5
**Using moment-generating functions, show that as $n\rightarrow \infty, \ p \rightarrow 0$, and $np\rightarrow \lambda$, the binomial distribution with parameters $n$ and $p$ tends to the Poisson distribution.**

To show convergence in distribution with MGFs, we can use the definition: $Y_n \xrightarrow{d} Y$ if $\lim_{n\rightarrow \infty} M_{Y_n}(y) = M_Y(y)$.

$$
	\begin{align}
		M_{Y_n}(y) & = (p e^t + (1-p)^n \\
			& = (p e^t + 1 - p)^n \\
			& = (1 + p(e^t - 1))^n \\
			& = (1 + \frac{n}{n} p(e^t - 1))^n \\
			& = (1 + \frac{np}{n}(e^t - 1))^n
	\end{align}
$$

Now we can take the limits.

$$
	\begin{align}
		\lim_{np\rightarrow \lambda} M_{Y_n}(y) & = (1+\frac{\lambda}{n}(e^t - 1))^n  \\
			& = \lim_{n\rightarrow \infty} (1+\frac{\lambda}{n}(e^t - 1))^n \\
			& = e^{\lambda(e^t - 1)}
	\end{align}
$$

Notice that this is the MGF of a Poisson distribution. Thus, $Bin(n,p) \xrightarrow{d} Poi(\lambda)$ with $n\rightarrow \infty, \ p \rightarrow 0$, and $np\rightarrow \lambda$.

# 5.6
**Using moment-generating functions, show that as $\alpha \rightarrow \infty$ the gamma distribution with parameters $\alpha$ and $\lambda$, properly standardized, tends to the standard normal distributions**

We will need to recall some properties of the Gamma distribution.

$$
	\begin{align}
		X_i\sim Gamma(\alpha_i, \lambda) & \rightarrow \frac{1}{n} \sum_{i=1}^{n}X_i \sim Gamma(\sum_{i=1}^{n} \alpha_i, \lambda)\\
		Y\sim Gamma(\alpha, \lambda) & \rightarrow cY\sim Gamma(\alpha, c \lambda)
	\end{align}
$$

Take $Y \sim Gamma(\alpha, \lambda)$. With this, we can write $X_i \sim Gamma(\alpha,\frac{\lambda}{n})$ so that $Y_n=\frac{1}{n} \sum_{i=1}^{n} X_i$. Standardizing this gives

$$W = \frac{Y - E(Y)}{\sqrt{Var(Y)}}.$$

Next we can examine the MGF of $W$.

$$
	\begin{align}
		M_W(t) & = E\Bigg[ \exp(\frac{Y - \frac{\alpha}{\lambda}}{\sqrt{\frac{\alpha}{\lambda^2}}}t) \Bigg]\\
			& = e^{-\sqrt{\alpha}t}\cdot E\Bigg[ e^{\frac{\lambda y}{\sqrt{\alpha}}t} \Bigg] \\
	\end{align}
$$

Notice that the expectation value follows the form of a gamma MGF with parameter $\frac{\lambda}{\alpha}t$. We can substitute in the MGF.

$$M_W(t) = e^{-\sqrt{\alpha}t}\cdot \Big( 1 - \frac{t}{\sqrt{\alpha}} \Big)^{-\alpha}$$

To simplify this expression, we can take the $\log$.

$$\log(M_W(t)) = -\sqrt{\alpha} t - \alpha \log(1-\frac{t}{\sqrt{\alpha}})$$

From this we can look at the Taylor series expansion to the second term of the logarithm.

$$\log(1-x) = x-\frac{x^2}{2} + \dots$$

$$
	\begin{align}
		\log(M_W(t)) & = -\sqrt{\alpha} t - \alpha \Big( \frac{t}{\sqrt{\alpha}} - \frac{t^2}{2\alpha} \Big) \\
			& = -\sqrt{\alpha} t + \sqrt{\alpha} t + \frac{t^2}{2}
	\end{align}
$$

Now we can go back and exponentiate this to get back to our original MGF.

$$M_W(t) = e^{\frac{t^2}{2}}$$

Notice that this is the MGF of a standard normal distribution. Thus, by MGFS, $W \xrightarrow{d} Z$.

# 5.19

## a.
**Use the Monte Carlo method with $n = 100$ and $n = 1000$ to estimate $\int_0^1 \cos(2\pi x)dx$. Compare the estimates to the exact answer.**

See R Code.

## b.

**Use Monte Carlo to evaluate $\int_0^1 \cos(2\pi x^2)dx$. Can you find the exact answer?**

See R Code.


# 5.28
**Let $f_n$ be a sequence of frequency functions with $f_n(x) = \frac{ 1 }{ 2 }$ if $x = \pm \Big( \frac{ 1 }{2} \Big)^n$ and $f_n(x) = 0$ otherwise. Show that $\lim f_n(x) = 0$ for all $x$ which means that the frequency functions do not converge to a frequency function, but there exists a CDF $F$ such that $\lim F_n(x) = F(x)$.**

Notice that

$$
f_n(x) =
\begin{cases}
\frac{1}{2} & \text{for }  x = \pm \Big( \frac{ 1 }{2} \Big)^n\\
0 & \text{otherwise.}
\end{cases}
$$

This function goes to 0 pointwise as n goes to infinity, $\lim_{n\rightarrow \infty} f_n = 0$. This is not a valid PDF. However, the limit of the CDF does converge to a valid CDF function.

$$
\lim_{n\rightarrow \infty} F_n(x)
	\begin{cases}
		0 & x < 0
		1 & x \geq 0
	\end{cases}
$$

This is an example of why we cannot use PDFs to show convergence as the results do not always match those of the proven CDF.

# Extra Problem 1

**Suppose $X_i$ are independent random variables and that $E(X_i)=\mu, \ Var(X_i) = \sigma^2$.**

## a.
**What is the mean of $(\bar X)^2$?**

$$E((\bar X)^2) = \mu^2$$

## b.
**Prove that $(\bar X)^2$ converges in probability to a constant and give that constant. State any theorems or results you use in your proof.**

Since each $X_i$ is independent and has the same mean and variance, we can apply the Weak Law of Large Numbers to see that

$$\bar{X_n} \xrightarrow{p} \mu.$$

Using the continuity theorem, we get

$$E\Big( (\bar{X_n})^2 \Big) \xrightarrow{p} \mu^2.$$

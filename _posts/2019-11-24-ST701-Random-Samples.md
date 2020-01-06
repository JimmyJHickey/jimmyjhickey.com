---
layout: post
comments: false
title: Example Problems on Properties of a Random Sample
description: ST701 Homework 6 on Properties of a Random Sample
tags: ST701 Distributions Expectations Statistics Random-Sample
category: ST701
---

Problems: 4.54, 5.6, 5.22, 5.24, 5.42, 5.44, 7, 8


* Do not remove this line (it will not be displayed)
{:toc}


# 4.54
**Find the pdf of $\prod_{i=1}^{n} X_i$ where the $X_i$'s are independent uniform(0, 1) random variables. (_Hint_: Try to calculate the cdf, and remember the relationship between uniforms and exponentials.)**

Define $F_Z = P(\prod_{i=1}^{n} X_i < z)$. Then take the negative log of both sides of the inequality since the negative log of a uniform(0, 1) is an exp(1).

$$
F_Z = P(-\log(\prod_{i=1}^{n} X_i) \geq -\log(z)) = P( - \sum \log(X_i) \geq -\log(z)) = 1 - P( - \sum \log(X_i) < -\log(z))
$$

Since the $X_i$'s are iid exp(1), we can take a product of their MGFs to find the distribution.

$$
	\begin{align}
		M(t) & = \prod_{i = 1}^{n} M_{X_i}(t) \\
			& =  \prod_{i = 1}^{n} (\frac{ 1 }{ 1-\beta t })^\alpha \\
			& = \prod_{i = 1}^{n} (\frac{ 1 }{ 1-1 \cdot t })^1 \\
			& = (\frac{ 1 }{ 1- t })^n
	\end{align}
$$

This is the MGF of a $Gamma(\alpha = n, \beta = 1)$.

$$
	\begin{align}
		F_Z & = 1 - P(Z \leq -\log(z)) \\
			& = 1 - \int_{z=0}^{-\log(z)} \frac{ 1 }{ \Gamma(n) } x^n e^{-x/1} dx\\
			& = 1 - \frac{ 1 }{ \Gamma(n) } \\ \\
		f_Z & = -f_z(-\log(z)) \cdot \frac{ d }{ dz }(-\log(z)) \\
			& = -\frac{ -1 }{ z }\frac{ 1 }{ \Gamma(n) } (-\log(z))^{n-1} e^{-(-\log(z))/1} \\
			& = \frac{ 1 }{ z } \frac{ 1 }{ \Gamma(n) } (-\log(z))^{n-1} \cdot z \\
			& = \frac{ 1 }{ \Gamma(n) } (-\log(z))^{n-1} & 0 < z < 1
	\end{align}
$$

# 5.6
**If $X$ has pdf $f_X(x)$ and $Y$, independent of $X$, has pdf $f_Y(y)$, establish formulas, similar to (5.2.3), for the random variable $Z$ in each of the following situations.**



## a.
$$
Z = X - Y
$$


Take $W = X$. Then, $Z = W - Y \Rightarrow Y = Z + W$.

$$
det 
\begin{bmatrix}
	\partial W & \partial Z \\
	1 & 0 \\
	1 & -1
\end{bmatrix}
= -1 - 0
$$

Then,

$$
f_Z(z) = \int^{\infty}_{-\infty} f_X(w)\cdot f_Y(w - z) \cdot | -1 | dw
$$


## b.
$$
Z = XY
$$

Take $W = X$. Then, $Z = WY \Rightarrow Y = Z / W$.

$$
det 
\begin{bmatrix}
	\partial W & \partial Z \\
	1 & 0 \\
	-z/w & 1/w
\end{bmatrix}
= 1/w
$$

Then,

$$
f_Z(z) = \int^{\infty}_{-\infty} f_X(w)\cdot f_Y(z/w) \cdot |1/w | dw
$$


## c.
$$
Z = X/Y
$$

Take $W = X$. Then, $Z = W / Y \Rightarrow Y = W / Z$.

$$
det 
\begin{bmatrix}
	\partial W & \partial Z \\
	1 & 0 \\
	1/z & -w/z^2
\end{bmatrix}
= -w/z^2
$$

Then,

$$
f_Z(z) = \int^{\infty}_{-\infty} f_X(w)\cdot f_Y(w / z) \cdot | -w/z^2 | dw
$$


# 5.22
**Let $X$ and $Y$ be iid n(0, 1) random variables, and define $Z = \min(X,Y)$. Prove that $Z^2 \sim \chi^2_1$.**


Take $U_1 = X$ and $U_2 = Y$; then $Z = U_{(1)}$. Recall,

$$
f_{X_{(j)}}(x) = \frac{ n! }{ (j-1)!(n-j)! } f_X(x)[F_X(x)]^{j-1}[1-F_X(x)]^{n-j}.
$$

$$
	\begin{align}
		f_Z = f_{U_{(1)}} & = \frac{ 2! }{ (1-1)!(2-1)!} f_U(u) [F_U(u)]^{1-1} [1 - F_U(u)]^{2-1} \\
			& = 2 f_U(u) [1-F_U(u)]
	\end{align}
$$

Now take $W = Z^2$.


$$
	\begin{align}
		F_W(w) & = P(Z^2 \leq w) \\
			& = P( -\sqrt{w} \leq Z \leq \sqrt{w})\\
			& = P(Z \leq \sqrt{w}) - P(Z \leq  - \sqrt{w}) \\
			& = F_Z(\sqrt{w}) - F_Z(-\sqrt{w}) \\ \\
		f_{Z^2} & = f_Z(\sqrt{w}) \frac{ 1 }{ 2 \sqrt{w} } - f_Z(-\sqrt{w}) \frac{ -1 }{ 2 \sqrt{w} }
	\end{align}
$$

Notice that the normal PDF is symmetric so we know $F(X) = 1 - F(-X)$ and $f(x) = f(-x)$.

$$
	\begin{align}
		f_{Z^2} & = 2 \cdot f_U(\sqrt{ w }) [1-F_U(\sqrt{ w })] \frac{ 1 }{ 2 \sqrt{ w } } + 2 \cdot f_U(-\sqrt{w }) [1-F_U(-\sqrt{ w })] \frac{ 1 }{ 2 \sqrt{ w } } \\
			& = f_U(\sqrt{ w }) \frac{ 1 }{ \sqrt{ w } } \Big( (1-F_U(\sqrt{ w })) + (1- F_U(- \sqrt{ w })) \Big) \\
			& = f_U(\sqrt{ z }) \frac{ 1 }{ \sqrt{ w } } (1 - F_U(\sqrt{ w } + F_U(\sqrt{ w })) \\
			& = f_U(\sqrt{ w }) \frac{ 1 }{ \sqrt{ w } } \\
			& = \frac{ 1 }{ \sqrt{ w } } \frac{ 1 }{ \sqrt{ 2 \pi } } e^{-(\sqrt{ w })^2/2} \\
			& = \frac{ 1 }{ \sqrt{ 2 \pi w } } e^{-w / 2}
	\end{align}
$$


This is the PDF of a $\chi^2_1$.



# 5.24
**Let $X_1, \dots ,X_n$ be a random sample from a population with pdf**


$$
f_X(x) = 
\begin{cases}
1/\theta & \text{if } 0 < x < \theta \\
0 & \text{otherwise.}
\end{cases}
$$


**Let $X_{(1)}< \dots < X_{(n)}$ be the order statistics. Show that $X_{(1)} / X_{(n)}$ and $X_{(n)}$ are independent random variables.**


Take $U = \frac{ X_{1} }{ X_{(n)} }$ and $V = X_{(n)}$. Then $X_{(1)} = UV$.

$$
J = det 
\begin{bmatrix}
	\partial U & \partial V \\
	V & U \\
	0 & 1
\end{bmatrix}
= V
$$
 
 
 $$
	\begin{align}
		f_{U,V} & = f_{X_{(1)}, X_{(n)}}(UV, V) \cdot | J | \\
			& = |V| \cdot \frac{ n! }{ (1-1)! (n-1-1)! (n-n)! } f_X(UV) f_X(V) [F_X(U)]^{1-1} [F_X(V) - F_X(UV)]^{n-1-1} [1-F_X(V)]^{n-n} \\
			& = V \frac{ n! }{ (n-2)! } f_X(UV) f_X(V)[F_X(V) - F_X(UV)]^{n-2} \\
			& = V (n) (n-1) \frac{ 1 }{ \theta } \frac{ 1 }{ \theta } [\frac{ V-0 }{ \theta } - \frac{ UV - 0 }{ \theta }]^{n-2} \\
			& = \frac{ n (n-1) }{ \theta^2} V \cdot V^{n-2} [\frac{ 1 }{ \theta } - \frac{ U }{ \theta }]^{n-2}
	\end{align}
$$

Since this can be separated into the form $f_{U,V} = g(v) h(u)$, they are independent.

# 5.42
**Similar to Example 5.5.11, let $X_1, X_2, \dots$ be iid and $X_{(n)} = \max_{1 \leq i \leq n} X_i$.**


## a.
**If $X_i \sim beta(1, \beta)$, find a value of $\nu$ so that $n^\nu (1 - X_{(n)})$ converges in distribution.**

$$
	\begin{align}
		P(|X_{(n)} - 1 | \geq \epsilon) & = P(X_{(n)} \geq 1 + \epsilon) + P(X_{(n)} \leq 1 - \epsilon) \\
			& = 0 + P(X_{(n)} \leq 1 - \epsilon) \\ 
			& = P ( X_{i} \leq 1 - \epsilon, i = 1, \dots n) & iid \\
	\end{align}
$$

So we need to find the CDF of $X_i$.

$$
	\begin{align}
		F_{X_i} & = \int_{x=0}^{t} \frac{ \Gamma(\beta + 1) }{ \Gamma(\beta) \Gamma(1) } x^{1-1} (1-x)^{\beta - 1} dx \\
			& = \int_{x=0}^{t} \frac{ \beta \Gamma(\beta ) }{ \Gamma(\beta) } (1-x)^{\beta - 1} dx \\
			& = 1 - (1-t)^\beta
	\end{align}
$$


$$
	\begin{align}
		P(|X_{(n)} - 1 | \geq \epsilon) & = P ( X_{i} \leq 1 - \epsilon, i = 1, \dots n)  \\
			& = (1 - 1 - (1-\epsilon)^\beta )^n \\
			& = (1 - \epsilon^\beta) ^n
	\end{align}
$$


Take $\epsilon = \frac{ t^{1/\beta} }{ n^{1/\beta} }$.

$$
	\begin{align}
		P(|X_{(n)} - 1 | \geq \epsilon) & = P(X_{(n)} - \geq 1 - \frac{ t^{1/\beta} }{ n^{1/\beta} }) \\
			& = P(n^{1/\beta}(1-X_{(n)} \leq t^{1/\beta}) \\
			& \stackrel{d}{\rightarrow} 1 - e^{-t 1/\beta}
	\end{align}
$$

Thus, $\nu = 1 / \beta$.

## b.
**If $X_i \sim exponential(1)$, find a sequence $a_n$ so that $X_{(n)} - a_n$ converges in distribution.**

$$
	\begin{align}
		\lim_{n \rightarrow \infty} F_{X_{(n)} - a_n} & = \lim_{n \rightarrow \infty} P(X_{(n)} - a_n \leq x) \\
			& = \lim_{n \rightarrow \infty} P(X_{(n)} \leq x + a_n) \\
			& = \lim_{n \rightarrow \infty} F_{X{(n)}}(x+a_n) \\ \\
		F_{X_{(n)}} & = F_X(x)^n \\
			& = \lim_{n \rightarrow \infty} (1 - e^{-(x + a_n)})^{n} \\
			& = \lim_{n \rightarrow \infty} (1 - \frac{ n }{ n }e^{-(x + a_n)})^{n} \\
	\end{align}
$$


This converges to $e^{n e^{-(x+a_n)}}$ if $n e^{-(x + an)}$ converges, so choose $a_n$ accordingly, such as $a_n = \log(n)$.

# 5.44
**Let $X_i, i = 1, 2, \dots$ be independent Bernoulli($p$) random variables and let $Y_n = \frac{ 1 }{ n } \sum_{i=1}^n X_i$.**


## a.
**Show that $\sqrt{n} (Y_n - p) \rightarrow n[0, p(1-p)]$ in distribution.**

Since $E(X_i) = p $ and $Var(X_i) = p(p-1) > 0$ and $Y_n = \overline{ X }$, we can use the central limit theorem to say


$$
\sqrt{n} (Y_n - p) \rightarrow n[E(X_i) - p , p(1-p)] = N[0, p(1-p)].
$$


## b.
**Show that for $p \neq 1/2$, the estimate of variance $Y_n(1-Y_n)$ satisfies $\sqrt{n} [Y_n ( 1 - Y_n)-p(1-p) ] \rightarrow n[0, (1-2p)^2 p (1-p)]$ in distribution.**

Here we have $g(z) = z( 1 - z)$ so $g'(z) = 1 - 2z$. Thus,

$$
g'(p) = 1 - 2 (p).
$$

Since $p \neq 1/2$, we can use the first order delta method.

$$
	\begin{align}
		\sqrt{n} [Y_n ( 1 - Y_n)-p(1-p) ] & = \sqrt{ n }(g(Y_n) - g(p)) \\
			& \stackrel{d}{\rightarrow} N(0, \sigma^2 [g'(p)]^2) \\
			& = N(0, (p(1-p)) [1-2p]^2)
	\end{align}
$$



## c.
**Show that for $p = 1/2$, $n [Y_n(1-Y_n)-\frac{ 1 }{ 4 }] \rightarrow \frac{ 1 }{ 4 } \chi^2_1$ in distribution. (If this appears strange, note that $Y_n(1-Y_n) \leq 1/4$, so the left-hand is always negative. An equivalent form is $2n [\frac{ 1 }{ 4 } - Y_n(1-Y_n)] \rightarrow \chi^2_1$.)**

Notice that plugging in $p = 1/2 $ to our derivative above will give 0, so we should instead try the second order delta method. Notice that $g''(x) = 2$. 

$$
	\begin{align}
		n [Y_n(1-Y_n)-\frac{ 1 }{ 4 }]  & = n[g(Yn) - g(p)] \\
			& \stackrel{d}{\rightarrow} \sigma^2 \frac{ g''(\theta) }{ 2 } \chi^{2}_{1} \\
			& = 1/2 ( 1 - 1/2) 2/2 \chi^{2}_{1} \\
			& = \frac{ 1 }{ 4 } \chi^{2}_{1}
	\end{align}
$$

# 7
**Let $X_1, X_2, \dots$ be a sequence of independent random variables with $E(X_i) = \mu$ and $V(X_i) = \sigma_i^2$. Show that if $n^{-2} \sum_{i=1}^n \sigma_i^2 \rightarrow 0 $, then $\bar{X} \rightarrow \mu$ in probability.**

We want to show $P( \| \overline{X } - \mu \| \geq \epsilon) = 0$. We can use Chebyshev's inequality since $E(\overline{ X }) = \mu$.

$$
	\begin{align}
		P( | \overline{X } - \mu | \geq \epsilon) & \leq V(\overline{ X }) / \epsilon^2 \\
			& = \frac{ 1/n^2 V(X_1 + \dots + X_n) }{ \epsilon^2 } \\
			& = \frac{ 1/n^2 \sum \sigma_i^2 }{ \epsilon^2 }
	\end{align}
$$

Since the numerator goes to 0, 

$$
P( | \overline{ X } - \mu | \geq \epsilon ) = 0.
$$

So, $\overline{ X } \stackrel{p}{\rightarrow} \mu$.



# 8
**Let $X_i$ be as in Problem 7 above but with $E(X_i) = \mu_i$ and $n^{-1} \sum_{i=1}^{n} \mu_i \rightarrow \mu$. Show that $\bar{X} \rightarrow \mu$ in probability.**

$$
	\begin{align}
		P( | \overline{X } - \mu | \geq \epsilon) & = P( | \overline{X } + E(\overline{ X })  -E(\overline{ X })- \mu | \geq \epsilon) \\
			& = P(| (\overline{ X } - E(\overline{ X })) + (E(\overline{ X }) - \mu) | \geq \epsilon)
	\end{align}
$$

Take the expression in the absolute value to be $A_n$. Then take

$$
	\begin{align}
		B_n & = \{|\overline{ X } - E(\overline{ X })| \geq \frac{ \epsilon }{ 2 } \} \\
		C_n & = \{| E(\overline{ X }) - \mu | \geq \frac{ \epsilon }{ 2 }\}.
	\end{align}
$$

Notice

$$
	\begin{align}
		P(A_n) & \leq P(B_n \cup C_n) \\
			& \leq P(B_n) + P(C_n) \\ \\
		P(C_n) & = P(| \frac{ 1 }{ n }\sum (\mu_i) - \mu | \geq \frac{ \epsilon }{ 2 }) \\
			& = 0 & \text{by convergence} \\ \\
		P(B_n) & = P(|\overline{ X } - E(\overline{ X })| \geq \frac{ \epsilon }{ 2 }) \\
			& \leq \frac{ V(\overline{ X }) }{ (\epsilon / 2)^2 } & \text{Chebyshev} \\
			& = \frac{ 1/n^2 \sum \sigma_i^2 }{ \epsilon^2 / 2^2 } \\
			& = 0.
	\end{align}
$$



Thus, 


$$
P(A_n) \rightarrow 0 \Rightarrow \overline{ X }_n \stackrel{p}{\rightarrow} \mu.
$$
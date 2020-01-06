---
layout: post
comments: false
title: Example Problems on Common Distributions
description: ST701 Homework 4 Common Distributions
tags: ST701 Distributions Expectations Statistics
category: ST701
---

Problems: 3.4, 3.12, 3.20, 3.25, 3.26 (a), 3.31, 3.38


* Do not remove this line (it will not be displayed)
{:toc}


# 3.4
**A man with $n$ keys wants to open his door and tries the keys at random. Exactly one key will open the door. Find the mean number of trials if**


## (a)
**unsuccessful keys are not eliminated from further selections.**

This follows a geometric distribution with a probability of success of $1/n$. Thus,

$$
E(Y) = \frac{ 1 }{ p } = \frac{ 1 }{ 1/n } = n.
$$


## (b)
**unsuccessful keys are eliminated.**

Notice how the probability of success at each stage.

$$
	\begin{align}
		1) \ p & = \frac{ 1 }{ n }\\
		2) \ p & = \frac{ n-1 }{ n } \cdot \frac{ 1 }{ n-1 } = \frac{ 1 }{ n }\\
		3) \ p & = \frac{ n-2 }{ n-1 }\frac{ n-1 }{ n } \cdot \frac{ 1 }{ n-2 } = \frac{ 1 }{ n }\\
			& \vdots
	\end{align}
$$

Thus, the probability of succeeding on any trial is $\frac{ 1 }{ n }$.

$$
E(Y) = \sum_{y=1}^{n} y \cdot \frac{ 1 }{ n } = \frac{ 1 }{ n } \cdot \frac{ n(n+1) }{ 2 } = \frac{ n+1 }{ 2 }
$$

# 3.12
**Suppose $X$ has a $binomial(n,p)$ distribution and let $Y$ have a $negative\ binomial(r,p)$ distribution. Show that $F_X(r-1) = 1 - F_Y(n-r)$.**

Notice that $F_X(r-1) = P(X \leq r-1)$ is the probability of at most $r-1$ successes in $n$ trials. Also notice that $1-F_Y(n-r) = 1 - P(Y \leq n-r ) = P(Y > n-r)$ is the probability that there are no more than $n-r$ failures before the $r$th success. This is the same as there being $r-1$ sucesses in the first $n$ trials.

# 3.20
**Let the random variable $X$ have the pdf**

$$
f(x) = \frac{ 2 }{ \sqrt{2 \pi} } e^{x^2/2},\ 0 < x < \infty
$$


## (a)
**Find the mean and variance of $X$. (This distribution is sometimes called a _folded normal_.**

$$
	\begin{align}
		E(X) & = \int_0^{\infty} x \cdot \frac{ 2 }{ \sqrt{2 \pi} } e^{x^2/2} \\
			& = \int_0^{\infty} x \cdot \frac{ 2 }{ \sqrt{2 \pi} } e^{-u} \cdot \frac{ 1 }{ x } du \\
			& = \frac{ 2 }{ \sqrt{2 \pi} } \int_0^{\infty} e^{-u} du \\
			& = \frac{ 2 }{ \sqrt{2 \pi} } \\ \\
		E(X^2) & = \int_0^{\infty} x^2 \cdot \frac{ 2 }{ \sqrt{2 \pi} } e^{x^2/2} \\
			& = 1 \\ \\
		Var(X) & = 1 - \Big( \frac{ 2 }{ \sqrt{2 \pi} } \Big)^2 \\
			& = 1 - \frac{ 2 }{ \pi}
	\end{align}
$$


## (b)
**If $X$ has the folded normal distribution, find the trasformation $g(X) = Y$ and values of $\alpha$ and $\beta$ so that $Y \sim gamma(\alpha, \beta)$.**

Take $g(x) = x^2$, $\alpha = 1/2$, and $\beta = 2$.

$$
	\begin{align}
		f_Y(y) & = f_y(g^{-1}(y)) \cdot \Big| \frac{ d }{ dy } g^{-1}(y) \Big| \\
			& = \frac{ 2 }{ \sqrt{2 \pi} } e^{-(\sqrt{y})^2/2} \cdot \Big| \frac{ 1 }{ 2 } \frac{ 1 }{ \sqrt{y} }\Big| \\
			& = \frac{ 1 }{ \sqrt{2 \pi}} \cdot \frac{ 1 }{ \sqrt{y} } \cdot e^{-y/2} \\
			& = \frac{ 1 }{ \Gamma(1/2) 2^{1/2} } y^{1/2 - 1} e^{-y/2} \\
			& = \frac{ 1 }{ \Gamma(\alpha) \cdot \beta^{\alpha}} y^{\alpha - 1} e^{-y/\beta}
	\end{align}
$$


# 3.25
**Suppose the random variable $T$ is the length of life of an object (possible the lifetime of an electrical component or of a subject given a particular treatment). That _hazard function_ $h_T(t)$ associated with the random variable $T$ is defined by**


$$
h_T(t) = \lim_{\delta \rightarrow 0} \frac{ P\Big( t \leq T < t + \delta | T \geq t \Big) }{ \delta }.
$$


**Thus, we can interpret $h_T(t)$ as the rate of change of the probability that the object survives a little past time $t$, givne that the object survives to time $t$. Show that if $T$ is a continuous random variable, then**


$$
h_T(t) = \frac{ f_T(t) }{ 1-F_T(t) } = \frac{ d }{ dt } \log(1 - F_T(t)).
$$


Notice we can use the definition of the derivative.

$$
	\begin{align}
		h_T(t) & = \lim_{\delta \rightarrow 0} \frac{ P\Big( t \leq T < t + \delta | T \geq t \Big) }{ \delta } \\
			& = \lim_{\delta \rightarrow 0} \frac{ P(T \leq t + \delta) - P(T \leq t)}{ (1 - P(T \leq t) \cdot  \delta }\\
			& = \lim_{\delta \rightarrow 0} \frac{F_T(t + \delta) = F_T(t) }{ (1 -F_T(t)) \cdot  \delta }\\
			& = \lim_{\delta \rightarrow 0} \frac{F_T(t + \delta) = F_T(t) }{ \delta } \cdot \frac{ 1 }{ 1-F_T(t) }\\
			& = \frac{ f_T(t) }{ 1-F_T(t) }
	\end{align}
$$

Also,

$$
	\begin{align}
		-\frac{ d }{ dt }(\log(1-F_T(t))) & = - \Big( \frac{ 1 }{ 1-F_T(t) } \Big) \cdot (0 - f_T(t)) \\
			& = \frac{ f_T(t) }{ 1-F_T(t) }.
	\end{align}
$$

# 3.26 (a)
**Verify that the following pdfs have the indicated hazard functions (see exercise 3.25).**

**If $T \sim exponential(\beta)$, then $h_T(t) = \frac{ 1 }{\beta }$**


$$
	\begin{align}
		h_T(t) & = \frac{ f_T(t) }{ 1-F_T(t) } \\
			& = \frac{ 1/\beta \cdot e^{-t/\beta} }{ 1 - \int_{0}^{t} 1/\beta \cdot e^{-x/\beta} dx  }\\
			& - \frac{ 1/\beta \cdot e^{-t/\beta} }{ 1 - 1/\beta(\beta - \beta e^{-t/\beta}) }\\
			& = \frac{ 1 }{ \beta }
	\end{align}
$$


# 3.31
**In this exercise we will prove Theorem 3.4.2.**


## (a)
**Start from the equality**


$$
\int f(x | \theta) = h(x) c(\theta) \exp(\sum^{k}_{i=1} w_i(\theta) t_i(x)) dx = 1,
$$

**differentiate both sides, and then rearrange terms to establish (3.4.4). (The fact that $\frac{ d }{ dx } \log (g(x)) = g'(x)/g(c)$ will be helpful.)**


$$
	\begin{align}
		1 & = \int h(x)\cdot c(\underset{\sim}{\theta}) \cdot \exp \Big(\sum_{i=1}^{k} w_i(\underset{\sim}{\theta}) t_i(x) \Big) dx\\
		\frac{ \partial }{ \partial \theta_j } 1 & = \frac{ \partial }{ \partial \theta_j } \int h(x)\cdot c(\underset{\sim}{\theta}) \cdot \exp \Big(\sum_{i=1}^{k} w_i(\underset{\sim}{\theta}) t_i(x) \Big) dx\\
		0 & = \int h(x)\cdot c'(\underset{\sim}{\theta}) \cdot \exp \Big(\sum_{i=1}^{k} w_i(\underset{\sim}{\theta}) t_i(x) \Big) + h(x)\cdot c(\underset{\sim}{\theta}) \cdot \exp \Big(\sum_{i=1}^{k} w_i(\underset{\sim}{\theta}) t_i(x) \Big) \cdot  \Big( \sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x) \Big)  dx
	\end{align}
$$	

$$
	\begin{align}
		- \int h(x)\cdot c'(\underset{\sim}{\theta}) \cdot \exp \Big(\sum_{i=1}^{k} w_i(\underset{\sim}{\theta}) t_i(x) \Big) dx & =  \int h(x)\cdot c(\underset{\sim}{\theta}) \cdot \exp \Big(\sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x) \Big) \cdot  \Big( \sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x) \Big)  dx \\
		- \frac{ c'(\underset{\sim}{\theta}) }{ c(\underset{\sim}{\theta}) } \int h(x)\cdot c(\underset{\sim}{\theta}) \cdot \exp \Big(\sum_{i=1}^{k} w_i(\underset{\sim}{\theta}) t_i(x) \Big) dx & = E\Big(\sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x) \Big)\\ 
		-\frac{ d }{ d \theta_j } \log(c(\underset{\sim}{\theta})) & = E\Big(\sum_{i=1}^{k} \frac{ d w_i(\underset{\sim}{\theta}) }{ d\theta_j } t_i(x) \Big)
	\end{align}
$$

## (b)
**Differentiate the above equality a second timel then rearrange to establish (3.4.5). (The fact that $\frac{ d^2 }{dx^2  } \log( g(x) ) = (g'' (x) / g(x)) - (g'(x) / g(x))^2$ will be helpful.)**

$$
	\begin{align}
		1 & = \int h(x)\cdot c(\underset{\sim}{\theta}) \cdot \exp \Big(\sum_{i=1}^{k} w_i(\underset{\sim}{\theta}) t_i(x) \Big) dx\\
		\frac{ \partial^2 }{ \partial \theta_j^2 } 1 & = \frac{ \partial^2 }{ \partial \theta_j^2 } \int h(x)\cdot c(\underset{\sim}{\theta}) \cdot \exp \Big(\sum_{i=1}^{k} w_i(\underset{\sim}{\theta}) t_i(x) \Big) dx\\
		0 & = \int h(x)\cdot c''(\underset{\sim}{\theta}) \cdot \exp \Big(\sum_{i=1}^{k} w_i(\underset{\sim}{\theta}) t_i(x) \Big) + h(x)\cdot c'(\underset{\sim}{\theta}) \cdot \exp \Big(\sum_{i=1}^{k} w_i(\underset{\sim}{\theta}) t_i(x) \Big) \cdot \sum_{i=1}^{k} \Big(w_i'(\underset{\sim}{\theta}) t_i(x) \Big) + h(x)\cdot c'(\underset{\sim}{\theta}) \cdot \exp \Big(\sum_{i=1}^{k} w_i(\underset{\sim}{\theta}) t_i(x) \Big) \cdot \sum_{i=1}^{k} \Big(w_i'(\underset{\sim}{\theta}) t_i(x) \Big) + h(x)\cdot c(\underset{\sim}{\theta}) \cdot \exp \Big(\sum_{i=1}^{k} w_i(\underset{\sim}{\theta}) t_i(x) \Big) \cdot \sum_{i=1}^{k} \Big(w_i'(\underset{\sim}{\theta}) t_i(x) \Big)^2 + h(x)\cdot c(\underset{\sim}{\theta}) \cdot \exp \Big(\sum_{i=1}^{k} w_i(\underset{\sim}{\theta}) t_i(x) \Big) \cdot \sum_{i=1}^{k} \Big(w_i''(\underset{\sim}{\theta}) t_i(x) \Big) dx \\
		0 & = \frac{ c''(\underset{\sim}{\theta}) }{ c(\underset{\sim}{\theta}) } \cdot \int h(x)\cdot c(\underset{\sim}{\theta}) \cdot \exp \Big(\sum_{i=1}^{k} w_i(\underset{\sim}{\theta}) t_i(x) \Big) dx + 2\cdot \frac{ c'(\underset{\sim}{\theta}) }{ c(\underset{\sim}{\theta}) } \cdot \int h(x)\cdot c(\underset{\sim}{\theta}) \cdot \exp \Big(\sum_{i=1}^{k} w_i(\underset{\sim}{\theta}) t_i(x) \Big) \cdot \Big( \sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x) \Big) dx + E\Big[ \Big( \sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x) \Big)^2  \Big] + E\Big[ \sum_{i=1}^{k} w_i''(\underset{\sim}{\theta}) t_i(x)  \Big] \\
		0 & = \frac{ c''(\underset{\sim}{\theta}) }{ c(\underset{\sim}{\theta}) } + 2 \cdot \frac{ c'(\underset{\sim}{\theta}) }{ c(\underset{\sim}{\theta}) } \cdot E\Big[ \sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x)  \Big] + E\Big[ \Big( \sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x) \Big)^2  \Big] + E\Big[ \sum_{i=1}^{k} w_i''(\underset{\sim}{\theta}) t_i(x)  \Big] \\
		0 & = \frac{ \partial^2 }{ \partial \theta_j^2 } \cdot \log(c(\underset{\sim}{\theta})) + \Big(\frac{ c'(\underset{\sim}{\theta}) }{ c(\underset{\sim}{\theta}) }\Big)^2 + 2 \cdot \frac{ c'(\underset{\sim}{\theta}) }{ c(\underset{\sim}{\theta}) } \cdot E\Big[ \sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x)  \Big] + E\Big[ \Big( \sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x) \Big)^2  \Big] + E\Big[ \sum_{i=1}^{k} w_i''(\underset{\sim}{\theta}) t_i(x)  \Big]
	\end{align}
$$	


$$
	\begin{align}
		-\frac{ \partial^2 }{ \partial \theta_j^2 } \cdot \log(c(\underset{\sim}{\theta})) - E\Big[ \sum_{i=1}^{k} w_i''(\underset{\sim}{\theta}) t_i(x)  \Big] & = \Big(\frac{ c'(\underset{\sim}{\theta}) }{ c(\underset{\sim}{\theta}) }\Big)^2 + 2 \cdot \frac{ c'(\underset{\sim}{\theta}) }{ c(\underset{\sim}{\theta}) } \cdot E\Big[ \sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x)  \Big] + E\Big[ \Big( \sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x) \Big)^2  \Big] \\
		& = E\Big[ \Big( \sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x) \Big)^2  \Big] + \Big(-E\Big[\sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x)  \Big]\Big)^2 + 2 \cdot - E\Big[\sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x)  \Big] \cdot E\Big[\sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x)  \Big] \\
		& =  E\Big[\Big(  \sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x) \Big)^2  \Big] +  E\Big[ \Big( \sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x) \Big)  \Big]^2 \\
		-\frac{ \partial^2 }{ \partial \theta_j^2 } \cdot \log(c(\underset{\sim}{\theta})) - E\Big[ \sum_{i=1}^{k} w_i''(\underset{\sim}{\theta}) t_i(x)  \Big] & = Var\Big[ \sum_{i=1}^{k} w_i'(\underset{\sim}{\theta}) t_i(x) \Big]
	\end{align}
$$


## (c)
**In addition, use the natural parameter representation of the theorem (see 3.32 part (a)) to verify the mean and variance of general normal distribution.**

Here is the normal PDF.

$$
\frac{1}{\sqrt{2 \pi \sigma}} e^{-\frac{1}{2 \sigma^2}(y-\mu)^2}
$$

We will define the parameters as follows.

$$
	\begin{align}
		\eta_1 & = \frac{ 1 }{ \sigma^2 }\\
		t_1 & = \frac{ -x^2 }{ 2 }\\
		\eta_2 & = \frac{ \mu }{ \sigma^2 }\\
		t_2 & = x \\
		c & = \frac{ \sqrt{\eta_1} }{ \sqrt{2 \pi} } \cdot e^{\frac{ -\eta_2^2 }{ 2\eta_1 }}
	\end{align}
$$


Then,

$$
	\begin{align}
		E(t_2(x)) & = E(X) \\
			& = -\frac{ \partial }{ \partial \eta_2 } \log\Big( \frac{ \sqrt{\eta_1} }{ \sqrt{2 \pi} } \cdot e^{\frac{ -\eta_2^2 }{ 2\eta_1 }} \Big) \\
			& = -\frac{ \partial }{ \partial \eta_2 } \Big[  \log\Big( \frac{ \sqrt{\eta_1} }{ \sqrt{2 \pi} }\Big) + \log \Big(e^{\frac{ -\eta_2^2 }{ 2\eta_1 }} \Big) \Big]\\ 
			& = 0 + -\frac{ \partial }{ \partial \eta_2 } \Big( \frac{ -\eta_2^2 }{ 2\eta_1 }\Big)\\
			& = - \Big( \frac{ -2 \eta_2 }{ 2 \eta_1 } \Big) \\
			& = - \Big( \frac{ -\mu / \sigma^2 }{ 1 / \sigma^2 } \Big) \\
			& = \mu \\
		V(t_2(x)) & = V(x) \\
			& = -\frac{ \partial }{ \partial \eta_2 } \Big( \frac{ -2 \eta_2 }{ 2 \eta_1 } \Big) \\
			& = \frac{ 1 }{ \eta_1 }\\
			& = \frac{ 1 }{ 1/ \sigma^2 } \\
			& = \sigma^2
	\end{align}
$$

# 3.38
**Let $Z$ be a random variable with pdf $f(z)$. Define $Z_\alpha$ to be a number that satisfies this relationship:**

$$
\alpha = P(Z > z_\alpha) = \int^{\infty}_{z_\alpha} f(z) dz.
$$

**Show that if $X$ is a random variable with pdf $(1/ \sigma) f((x - \mu)/ \sigma)$ and $x_\alpha = \sigma z_\alpha + \mu$, then $P(X > x_\alpha = \alpha$. (Thus if a table of $z_\alpha$ values were available, the values of $x_\alpha$ could be easily compute for any member of the location-scale family.)**

$$
P(Z > z_\alpha) = P\Big(\frac{ 1 }{ \sigma } (X - \mu) > \frac{ x_\alpha - \mu }{ \sigma }\Big) = P(X > x_\alpha)
$$
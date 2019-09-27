---
layout: post
comments: false
title: Example Problems on Transformation and Expectations of RVs
description: ST701 Homework 3 on Transformation and Expectations of RVs
tags: ST701 Transformations Expectations Statistics
---

Problems: 2.6, 2.7, 2.9, 2.11, 2.23, 2.24, 2.25, 2.33


* Do not remove this line (it will not be displayed)
{:toc}

# 2.6
**In each of the following find the pdf of $Y$ and show that the pdf integrates to 1.**

## (a)

$$
f_X(x) = \frac{ 1 }{ 2 } e^{-|x|}, \ -\infty < x < \infty; \ Y=|X|^3
$$

We can define our sets and functions

$$
	\begin{array}{l l l l}
		A_0 = \{ 0 \} & & & \\
		A_1 = (-\infty, 0) & g_1(x) = -x^3 & g_1^{-1}(y) = - y^{1/3} & \frac{d}{dy} g_1^{-1}(y) = -\frac{ 1 }{ 3 } y ^{-2/3} \\
		A_2 = ( 0, \infty ) & g_2(x) = x^3 & g_2^{-1}(y) = y^{1/3} & \frac{d}{dy} g_2^{-1}(y) = \frac{ 1 }{ 3 } y ^{-2/3} .
	\end{array}
$$

Then,

$$
	\begin{align}
		f_Y(y) & = \frac{ 1 }{ 2 } e^{- | - y^{1/3} |} \cdot \Big| -\frac{ 1 }{ 3 } y ^{-2/3} \Big| + \frac{ 1 }{ 2 } e^{- |y^{1/3} |} \cdot \Big| \frac{ 1 }{ 3 } y ^{-2/3} \Big| \\
			& = \frac{ 1 }{ 2 } e^{- y^{1/3}} \cdot\frac{ 1 }{ 3 } y ^{-2/3} + \frac{ 1 }{ 2 } e^{- y^{1/3}} \cdot\frac{ 1 }{ 3 } y ^{-2/3} \\
			& = \frac{ 1 }{ 3 }  e^{- y^{1/3}} \cdot y ^{-2/3} & y \in \mathcal{Y}\\
			& = 0 & \text{otherwise.}
	\end{align}
$$

We can then integrate to make sure that we get 1.

$$
	\begin{align}
		\int_{-\infty}^{\infty} f_Y(y) dy & = \int_{-\infty}^{\infty}  \frac{ 1 }{ 3 }  e^{- y^{1/3}} \cdot y ^{-2/3} dy \\
			& = \int_{-\infty}^{\infty} \frac{ 1 }{ 3 } e^{-u} y^{-2/3} \cdot 3 y^{2/3} du & u=y^{1/3}, \ du = \frac{ 1 }{ 3 }y^{-2/3}dy \\
			& = 1
	\end{align}
$$

## (b)

$$
f_X(x) = \frac{ 3 }{ 8 }(x+1)^2, \ -1 < x < 1;  \ Y = 1 - X^2
$$

We can define our sets and functions

$$
	\begin{array}{l l l l}
		A_0 = \{ 0 \} & & & \\
		A_1 = (-1, 0) & g_1(x) = 1-x^2 & g_1^{-1}(y) = (1-y)^{1/2} & \frac{d}{dy} g_1^{-1}(y) = -\frac{ 1 }{ 2 }(1-y)^{-1/2} \\
		A_2 = ( 0, 1 ) & g_2(x) = 1-x^2 & g_2^{-1}(y) = - (1-y)^{1/2} & \frac{d}{dy} g_2^{-1}(y) = \frac{ 1 }{ 2 }(1-y)^{-1/2} .
	\end{array}
$$

Then,

$$
	\begin{align}
		f_Y(y) & = \frac{ 3 }{ 8 }((\sqrt{1-y}) + 1)^2 \cdot \Big|  -\frac{ 1 }{ 2 }(1-y)^{-1/2} \Big|+ \frac{ 3 }{ 8 }((-\sqrt{1-y}) + 1)^2 \cdot \Big|  \frac{ 1 }{ 2 }(1-y)^{-1/2} \Big| \\
			& = \frac{ 3 }{ 8 } \cdot \frac{ 1 }{ 2 }(1-y)^{-1/2} \Big[ \Big( (1-y) + 2 \sqrt{1-y} + 1 \Big) +  \Big( (1-y) - 2 \sqrt{1-y} + 1 \Big)  \Big] \\
			& = \frac{ 3 }{ 16 } (1-y)^{-1/2} (4-2y) & y \in \mathcal{Y}\\
			& = 0 & \text{otherwise.}
	\end{align}
$$

We can then integrate to make sure that we get 1.

$$
	\begin{align}
		\int_{0}^{1} f_Y(y) dy & = \int_{0}^{1} \frac{ 3 }{ 16 } (1-y)^{-1/2} (4-2y) dy \\
			& = \int_{1}^{0}\frac{ 3 }{ 16 }(u)^{-1/2}\cdot 2(1+u)\cdot - du & u=1-y, \ du=-dy \\
			& = -\frac{ 6 }{ 16 } \int_{1}^{0} u^{-1/2} + u^{1/2} du \\
			& = 1
	\end{align}
$$

## (c)

$$
f_X(x) = \frac{ 3 }{ 8 }(x+1)^2, \ -1 < x < 1;  \ Y = 1 - X^2 \text{ if } X \leq 0 \text{ and } Y = 1 - X \text{ if } X > 0
$$

$$
	\begin{array}{l l l l}
		A_0 = \{ 0 \} & & & \\
		A_1 = (-1, 0) & g_1(x) = 1-x^2 & g_1^{-1}(y) = -(1-y)^{1/2} & \frac{d}{dy} g_1^{-1}(y) = \frac{ 1 }{ 2 }(1-y)^{-1/2} \\
		A_2 = ( 0, 1 ) & g_2(x) = 1-x & g_2^{-1}(y) = 1-y & \frac{d}{dy} g_2^{-1}(y) = -1 .
	\end{array}
$$

Thus,

$$
	\begin{align}
		f_Y(y) & = \frac{ 3 }{ 8 }(-\sqrt{1-y} + 1)^2 \cdot \frac{ 1 }{ 2\sqrt{1-y} }+\frac{ 3 }{ 8 }((1-y)+1)^2 |-1| & y \in \mathcal{Y}\\
			& = 0 & \text{otherwise.}
	\end{align}
$$

We can then integrate to make sure that we get 1.

$$
	\begin{align}
		\int_{0}^{1} f_Y(y) dy & = \int_{0}^{1} \frac{ 3 }{ 8 }(-\sqrt{1-y} + 1)^2 \cdot \frac{ 1 }{ 2\sqrt{1-y} }+\frac{ 3 }{ 8 }((1-y)+1)^2 dy \\
			& = \frac{ 3 }{ 8 } \Big[ \int_{0}^{1} \frac{ (1-y)^2 - 2(1-y) + 1 }{ 2 \sqrt{1-y} }dy + \int_{0}^{1} (1-y)^2 + 2(y-1) + 1 \Big]\\
			& = 1
	\end{align}
$$

#  2.7
**Let $X$ have pdf $f_X(x) = \frac{ 2 }{ 9 }(x+1)$ for $-1 \leq x \leq 2$.**

## (a)
**Find the pdf of $Y=X^2$. Note that Theorem 2.1.8 is not directly applicable to this problem.**

We will start by finding the PDF of $Y$. We can use equation 2.1.11 from the book. Notice, because of the square root and the support of $X$, we will split this into two cases, the first being $x\in [-1, 1], \ y \in [0,1)$ and the second $x \in (1, 2],\ y\in (1, 4]$. Let's start with the first case.

$$
	\begin{align}
		f_Y(y) & = \frac{ 1 }{ 2 \sqrt{y} } (f_X(\sqrt{y}) + f_X(-\sqrt{y})) \\
			& = \frac{ 1 }{ 2 \sqrt{y} } \Big( \frac{ 2 }{ 9 }(\sqrt{y} +1) + \frac{ 2 }{ 9 }(-\sqrt{y} +1) \Big)\\
			& = \frac{ 1 }{ 2 \sqrt{y} } (\frac{ 4 }{ 9 })\\
			& = \frac{ 2 }{ 9 \sqrt{y} } & y \in (0,1]
	\end{align}
$$

Now we will look at the second case.

$$
	\begin{align}
		f_Y(y) & = \frac{ 1 }{ 2 \sqrt{y} } (f_X(\sqrt{y}) + f_X(-\sqrt{1})) \\
			& = \frac{ 1 }{ 2 \sqrt{y} } ( \frac{ 2 }{ 9 }(\sqrt{y} +1) + \frac{ 2 }{ 9 }(-1 +1)) \\
			& = \frac{ 1 }{ 2 \sqrt{y} } (\frac{ 2 }{ 9 } \sqrt{y} + \frac{ 2 }{ 9 })\\
			& = \frac{ 1 }{ 9 } + \frac{ 1 }{ 9 \sqrt{y} } & y \in (1, 4]
	\end{align}
$$

Putting these together gives:

$$
f_Y(y) = 
	\begin{cases}
			\begin{align}
				& \frac{ 2 }{ 9 \sqrt{y} } & y \in (0,1] \\
				& \frac{ 1 }{ 9 } + \frac{ 1 }{ 9 \sqrt{y} } & y \in (1, 4] \\
				& 0 & \text{otherwise}
			\end{align}
	\end{cases}
$$

#  2.9
**If the random variable $X$ has pdf**

$$
f(x)=
    \begin{cases}
        \begin{align}
            & \frac{ x-1 }{ 2 } & 1 < x < 3\\
            & 0 & \text{otherwise,}
        \end{align}
    \end{cases}
$$

**find a monotone function $u(x)$ such that the random variable $Y=u(X)$ has a uniform(0,1) distribution.**

Take $Y = F_X(x)$, then by the Probability Integral Transformation, $Y \sim U(0,1)$.

$$ \int_1^x \frac{ z-1 }{ 2} dz = \frac{ 1 }{ 4 }x^2 - \frac{ 1 }{ 2 }x - \frac{ 1 }{ 4 } $$


$$
Y = F_X(x)=
    \begin{cases}
        \begin{align}
            & 0 &  x \leq 1\\
            & \frac{ 1 }{ 4 }x^2 - \frac{ 1 }{ 2 }x - \frac{ 1 }{ 4 } & 1 < x < 3 \\
			& 1 & x \geq 3
        \end{align}
    \end{cases}
$$

#  2.11
**Let $X$ have the standard normal pdf, $f_X(x) = (1/\sqrt{2\pi}) e^{-x^2/2}$.**

## (a)
**Find $E(X^2)$ directly, and then by using the pdf of $Y=X^2$ from Example 2.1.7 and calculate $E(Y)$.**

$$
	\begin{align}
		E(X^2) & = \int_{-\infty}^{\infty} x^2 \cdot f_X(x) dx \\
			& = \int_{-\infty}^{\infty} x^2 \cdot (1/\sqrt{2\pi}) e^{-x^2/2} dx \\
			& u = x & v = -e^{x^2/2}\\
			& du = dx & dv = x e^{x^2/2}dx\\
			& = \frac{ 1 }{ \sqrt{2 \pi} }\Big( x \cdot -e^{x^2/2} |_{-\infty}^{\infty} - \int_{-\infty}^{\infty} -e^{x^2/2} dx  \Big) \\
			& = \frac{ 1 }{ \sqrt{2 \pi} } - (-\sqrt{2 \pi})\\
			& = 1
	\end{align}
$$

We should get the same thing for $E(Y)$. We will start by getting its PDF. We can use example 2.1.7 for this.

$$
	\begin{align}
		f_Y(y) & = \frac{ 1 }{ 2 \sqrt{y} } (f_X(\sqrt{y}) + f_X(-\sqrt{y})) \\
			& = \frac{ 1 }{ 2 \sqrt{y} } \Big( (1/\sqrt{2\pi}) e^{-(\sqrt{y})^2/2} + (1/\sqrt{2\pi}) e^{-(-\sqrt{y})^2/2} \Big) \\
			& = \frac{ 1 }{ \sqrt{2 \pi y} } (e^{-y/2})
	\end{align}
$$

Then,

$$
	\begin{align}
		E(Y) & = \int_{0}^{\infty} y \cdot f_Y(y) dy \\
			& = \int_{0}^{\infty} y \cdot \frac{ 1 }{ \sqrt{2 \pi y} } (e^{-y/2})	dy\\
			& = \frac{ 1 }{ \sqrt{2 \pi} } \int_{-\infty}^{\infty} \sqrt{y} \cdot  (e^{-y/2})	dy\\ \\
			& u = \sqrt{y} & v = -2 e^{-y/2} \\
			& du = \frac{ 1 }{ 2\sqrt{y} } dy & dv = e^{-y/2} dy \\ \\
			& = \frac{ 1 }{ \sqrt{2 \pi} } \cdot \sqrt{y} \cdot -2 e^{-y/2} \Big|_{0}^{\infty} - \int_0^{\infty} \frac{ 1 }{ \sqrt{2 \pi} } \cdot -2 e^{-y/2} \cdot  \frac{ 1 }{ 2\sqrt{y} } dy \\
			& = 0 + \int_0^{\infty} \frac{ 1 }{ \sqrt{2 y \pi} } \cdot e^{-y/2} dy \\
			& = 1.
	\end{align}
$$

## (b)
**Find the pdf of $Y = \| X \|$, and find its mean and variance.**

We will start by finding the pdf of $Y$.

$$
	\begin{align}
		F_Y(y) & = P(Y \leq y) \\
			& = P( | X | \leq y) \\
			& = P(-y \leq X \leq y) \\
			& = F_X(y) - F_X(-y)\\
		f_Y(y) & = \frac{ d }{ dy } F_Y(y) \\
			& = \frac{ d }{ dy } \Big[ F_X(y) - F_X(-y) \Big] \\
			& = f_X(y) (1) - f_X(-y)(-1) \\
			& = (1/\sqrt{2\pi}) e^{-(y)^2/2} - (1/\sqrt{2\pi}) e^{-(-y)^2/2} \\
			& = \frac{ 2 }{ \sqrt{2\pi} } e^{-y^2/2} & y \in [0, \infty) \\
			& = 0 & \text{otherwise} 
	\end{align}
$$

Now we can find the expectation.

$$
	\begin{align}
		E(Y) & = \int_{0}^{\infty} y \cdot f_Y(y) dy \\
			& = \int_{0}^{\infty} y \cdot \frac{ 2 }{ \sqrt{2\pi} } e^{-y^2/2} dy \\
			& = \frac{ 2 }{ \sqrt{2\pi} } \int_{0}^{\infty} y \cdot e^{-y^2/2} dy \\\\
			& u = -y^2 /2 & du = -y dy \\ \\
			& = \sqrt{\frac{ 2 }{ \pi }} \cdot \int y e^u \frac{ -1 }{ y }du\\
			& = -\sqrt{\frac{ 2 }{ \pi }} e^u \Big|  \\
			& = -\sqrt{\frac{ 2 }{ \pi }} e^{-y^2/2} \Big|_{0}^{\infty} \\
			& = -\sqrt{\frac{ 2 }{ \pi }}  (0 - 1)\\
			& = \sqrt{\frac{ 2 }{ \pi }}
	\end{align}
$$

Notice that we need to find $E(Y^2)$ in order to find the variance.

$$
	\begin{align}
		E(Y^2) & = \int_{0}^{\infty} y^2 \cdot f_Y(y) dy \\
			& = \int_{0}^{\infty} y^2 \cdot \frac{ 2 }{ \sqrt{2\pi} } e^{-y^2/2} dy \\ \\
			& u = y & v = -e^{y^2/2}\\
			& du = dy & dv = y e^{y^2/2}dy \\ \\
			& = \frac{ 1 }{ \sqrt{2 \pi} }\Big( y \cdot -e^{y^2/2} |_{-\infty}^{\infty} - \int_{-\infty}^{\infty} -e^{y^2/2} dy  \Big) \\
			& = \sqrt{\frac{ 2 }{ \pi }} ( 0 + \sqrt{\frac{ \pi }{ 2 }}) \\
			& = 1\\
		Var(Y) & = E(Y^2) - E(Y)^2 \\
			& = 1 - \Big( \sqrt{\frac{ 2 }{ \pi }} \Big)^2 \\
			& = 1 - \frac{ 2 }{ \pi }
	\end{align}
$$

#  2.23
**Let $X$ have the pdf**

$$
	\begin{align}
		f(x) & = \frac{ 1 }{2  } (1+x), & -1 < x< 1.
	\end{align}
$$

## (a)
**Find the pdf of $Y = X^2$.**

$$
	\begin{align}
		F_Y(y) & = P(Y \leq y) \\
			& = P(X^2 \leq y)\\
			& = P(-\sqrt{y} \leq X \leq \sqrt{y}) \\
			& = F_X(\sqrt{y}) -  F_X(\sqrt{-y})\\
		f_Y(y) & = \frac{ d }{ dy } (F_X(\sqrt{y}) -  F_X(\sqrt{-y})) \\
			& = f_X(\sqrt{y}) \cdot \frac{ d }{ dy } \sqrt{y} -  f_X(\sqrt{-y})\cdot \frac{ d }{ dy } \sqrt{-y}\\
			& = f_X(\sqrt{y}) \cdot \frac{ 1 }{ 2 \sqrt{y} } -  f_X(\sqrt{-y})\cdot \frac{ - 1 }{ 2 \sqrt{y} }\\
			& = \frac{ 1 }{ 2 \sqrt{y} } \Big( \frac{ 1 }{ 2 } ( 1 + \sqrt{y}) + \frac{ 1 }{ 2 } ( 1 - \sqrt{y}) \Big) \\
			& = \frac{ 1 }{ 2 \sqrt{y} } & 0 < y< 1 \\
			& = 0 & \text{otherwise}
	\end{align}
$$

## (b)
**Find $E(Y)$ and $Var(Y)$.**

$$
	\begin{align}
		E(Y) & = \int_0^1 y \cdot \frac{ 1 }{ 2\sqrt{y} } dy\\
			& = \frac{ 1 }{ 2 } \int_0^1 \sqrt{y} dy \\
			& = \frac{ 1 }{ 2 } (\frac{ 2 }{ 3 } \cdot y^{3/2})\Big|_0^1 \\
			& = \frac{ 1 }{ 3 }\\ \\
		E(Y^2) & = \int_0^1 y^2 \cdot \frac{ 1 }{ 2\sqrt{y} } dy\\
			& = \frac{ 1 }{ 2 } \int_0^1 y^{3/2} dy \\
			& = \frac{ 1 }{ 2 } \frac{ 2 }{ 5 } (y^{5/2}) \Big|_0^1 \\
			& = \frac{ 1 }{ 5 } \\ \\
		Var(Y) & = E(Y^2) - E(Y)^2 \\
			& = \frac{ 1 }{ 5 } - \frac{ 1 }{ 9 } \\
				& = \frac{ 4 }{ 45 }
		\end{align}
$$



#  2.24
**Compute $E(X)$ and $Var(X)$ for each of the following probability distributions.**

## (a)

$$
f_X(x) = ax^{a-1},\ 0 < x< 1,\ a > 0
$$

$$
	\begin{align}
		E(X) & = \int_{0}^{1} x \cdot a x^{a-1} dx \\
			& = \int_{0}^{1} a x^{a} dx\\
			& = \frac{ a }{ a+1 } x^{a+1} \Big|_{0}^{1} \\
			& = \frac{ a }{ a+1 } \\ \\
		E(X^2) & = \int_{0}^{1} x^2 \cdot a x^{a-1} dx \\
			& = \int_{0}^{1} a x^{a+1} dx\\
			& = \frac{ a }{ a+2 } x^{a+2} \Big|_{0}^{1} \\
			& = \frac{ a }{ a+2} \\ \\
		Var(X) & = \frac{ a }{ a+2} - (\frac{ a }{ a+1 })^2
	\end{align}
$$

## (b)

$$
f_X(x) = \frac{ 1 }{ n }, \ x = 1, 2,\dots , n, \ n > 0 \text{ an integer} 
$$

$$
	\begin{align}
		E(X) & = \sum_0^1 \frac{ 1 }{ n }x \\
			& = \frac{ 1 }{ n } \sum_0^1 x \\
			& = \frac{ 1 }{ n } \cdot \frac{ n (n+1) }{ 2 } \\ 
			& = \frac{ n+1 }{ 2 }\\ \\
		E(X^2) & = \sum_0^1 \frac{ 1 }{ n }x^2 \\
			& = \frac{ 1 }{ n } \sum_0^1 x^2 \\
			& = \frac{ 1 }{ n } \cdot \frac{ (2n+1)(n+1)n }{ 6 } \\
			& = \frac{ (2n+1)(n+1) }{ 6 } \\ \\
		Var(X) & = \frac{ (2n+1)(n+1) }{ 6 } - (\frac{ n+1 }{ 2 })^2 \\
			& = \frac{ 1 }{ 12 }(n^2 - 1)
	\end{align}
$$

## (c)

$$
f_X(x) = \frac{ 3 }{ 2 } (x-1)^2, \ 0 < x < 2
$$

$$
	\begin{align}
		E(X) & = \int_0^2 x \cdot \Big( \frac{ 3 }{ 2 }x^2 - 3x + \frac{ 3 }{ 2 } dx \Big) \\
			& = \Big( \frac{ 3 }{ 8 }x^4-x^3+\frac{ 3 }{ 4}x^2 \Big) \Big|_0^2 \\
			& = 1 \\ \\
		E(X^2) & = \int_0^2 x^2 \cdot \Big( \frac{ 3 }{ 2 }x^2 - 3x + \frac{ 3 }{ 2 } dx \Big) \\
			& = \Big( \frac{ 3 }{ 10 }x^5-\frac{ 3 }{ 4 }x^4+\frac{ 1 }{ 2}x^3 \Big) \Big|_0^2 \\
			& = \frac{ 8 }{ 5 } \\ \\
		Var(X) & = \frac{ 8 }{ 5 } - 1^2 \\
			& = \frac{ 3 }{ 5 }
	\end{align}
$$


#  2.25
**Suppose the pdf $f_X(x)$ of a random variable $X$ is an _even function_. ($f_X(x)$ is an _even function_ if $f_X(x) = f_X(-x)$ for every $x$.) Show that**

## (a)
**$X$ and $-X$ are identically distributed.**

To show that two random variables are identically distributed, we need to show that $F_X(x) = F_{-X}(x)$. We will start by taking $Y=-X$ and finding $F_Y(y)$.

$$
	\begin{align}
		F_Y(y) & = P(Y \leq y)\\
			& = P(-X \leq y) \\
			& = P(X > y)\\
			& = 1 - P(X \leq y)\\
			& = 1 - F_X(y)
	\end{align}
$$

Now we will find the PDF of $Y$.

$$
	\begin{align}
		f_Y(y) & = \frac{ d }{ dy }(1 - F_X(-y)) \\
			& = - f_X(-y) \cdot -1 \\
			& = f_X(-y) \\
			& = f_X(y) & \text{since } f_X(x) \text{ is an even function}
	\end{align}
$$


Then,


$$
	\begin{align}
		F_Y(y) & = \int_{-\infty}^{y} f_X(x)dx \\
			& = F_X(x).
	\end{align}
$$

Thus, they are identically distributed.

## (b)
**$M_X(t)$ is symmetric about 0.**

For a function to be symmetric about 0, we must have $M_X(t-0) = M_X(0-t)$.

$$
	\begin{align}
		M_X(t-0) & = E(e^{(t-0)x})\\
			& = E(e^{tx})\\
			& = \int e^{tx} f_X(x) dx \\
		M_X(0-t) & = E(e^{(0-t)x})\\
			& = E(e^{-tx})\\
			& = \int e^{-tx} f_X(x) dx \\
	\end{align}
$$

Since $F_X$ and $F_{-X}$ are identically distributed,

$$
	\begin{align}
		M_X(t-0) & = M_{-X}(t-0)\\
			& = \int e^{(t-0) -x} f_{-X}(x) dx \\
			& = \int e^{-tx} f_{-X}(x) dx \\
			& = \int e^{-tx} f_{X}(x) dx & \text{by identical distribution}\\
			& = M_X(0-t).
	\end{align}
$$

Thus, $M_X(t)$ is symmetric about 0.

#  2.33
**In each of the following cases verify the expression given for the moment generating function, and in each case use the mgf to calculate $E(X)$ and $Var(X)$.**

## (a)

$$
P(X=x) = \frac{ e^{-\lambda} \lambda^x }{ x! },\ M_X(t) = e^{\lambda (e^t - 1)},\ x = 0, 1, \dots;\ \lambda > 0
$$

$$
	\begin{align}
		M_X(t) & = E(e^{tx}) \\
			& = \sum e^{tx} \cdot \frac{ e^{-\lambda} \lambda^x }{ x! }\\
			& = \sum e^{t^x} \cdot \frac{ e^{-\lambda} \lambda^x }{ x! }\\
			& = \frac{ e^{-\lambda} (e^t \cdot \lambda)^x }{ x! }\\
			& = \frac{ e^{-\lambda} }{ e^{-e^{t \lambda}} } \cdot \sum \frac{ e^{-e^{t \lambda}}\cdot (e^t \cdot \lambda)^x }{ x! } \\
			& = \frac{ e^{-\lambda} }{ e^{-e^{t \lambda}} } \cdot 1 \\
			& = e^{\lambda(e^t - 1)} \\ \\
		E(X) & = M^{(1)}_X(0)\\
			& = e^{\lambda(e^t-1)} \cdot (\lambda e^t) \Big|_{t=0} \\
			& = \lambda \\ \\
		E(X^2) & = M^{(2)}_X(0)\\
			& = e^{\lambda (e^t - 1)}(\lambda e^t)(\lambda e^t) + e^{\lambda (e^t-1)}\cdot \lambda e^t \Big|_{t=0} \\
			& = \lambda^2 + \lambda \\ \\
		Var(X) & = \lambda^2 + \lambda  - (\lambda)^2 \\
			& = \lambda
	\end{align}
$$

## (b)

$$
P(X=x) = p(1-p)^x,\ M_X(t) = \frac{ p }{ 1-(1-p)e^t },\ x=0,1,\dots ;\ 0<p<1
$$

$$
	\begin{align}
		M_X(t) & = E(e^{tx}) \\
			& = \sum e^{tx} p (1-p)^x \\
			& = \sum e^{t^x} p (1-p)^x \\
			& = p \sum (e^t(1-p))^x \\
			& = \frac{ p }{ 1 - e^t(1-p) } & \text{by geometric series}
	\end{align}
$$


Notice that our geometric series argument requires


$$
	\begin{align}
		e^t(1-p) & < 1 \\
		e^t & < \frac{ 1 }{ 1-p }\\
		t & < - \log(1-p).
	\end{align}
$$


$$
	\begin{align}
		E(X) & = M_X^{(1)}(0) \\
			& = \frac{ (1-e^t(1-p))\cdot 0 - p(-e^t(1-p)) }{ (1-e^t(1-p))^2 }\Big|_{t=0} \\
			& = \frac{ p(1-p) }{ p^2 }\\
			& = \frac{ 1-p }{ p } \\ \\
		E(X^2) & = M_X^{(2)}(0) \\
			& = p e^t(1-p)\cdot (-2)(1-e^t(1-p))^{-3}(-e^t(1-p))+(1-e^t(1-p))^{-2}\cdot pe^t(1-p) \Big|_{t=0}\\
			& = \frac{ -2(1-p)(p-1) }{ p^2 } + \frac{ p(1-p) }{ p^2 } \\
			& = \frac{ (p-2)(p-1) }{ p^2 } \\ \\
		Var(X) & = \frac{ (p-2)(p-1) }{ p^2 } - (\frac{ 1-p }{ p })^2 \\
			& = \frac{ 1-p }{ p^2 }
	\end{align}
$$

## (c)

$$
f_X(x) = \frac{ e^{-(x-\mu)^2/(2\sigma^2)} }{ \sqrt{2\pi} \sigma },\ M_X(t) = e^{\mu t+ \sigma^2 t^2/2},\ -\infty < x< \infty,\ -\infty < \mu < \infty, \ \sigma > 0
$$

$$
	\begin{align}
		M_X(t) & = E(e^{tx}) \\
			& = \int e^{tx} \cdot \frac{ e^{-(x-\mu)^2/(2\sigma^2)} }{ \sqrt{2\pi} \sigma } dx \\
			& = \int \frac{ 1 }{ \sqrt{2\pi} \sigma} \cdot e^{tx-(x-\mu)^2/(2\sigma^2)}dx \\
			& = \int \frac{ 1 }{ \sqrt{2\pi} \sigma} \cdot e^{(2 \sigma^2 tx-(x-\mu)^2)/(2\sigma^2)} dx
	\end{align}
$$


We can now focus on the numerator of the exponential.

$$
	\begin{align}
		2 \sigma^2 tx-(x-\mu)^2 & = 2 \sigma^2 tx - x^2 - \mu^2 + 2\mu x \\
			& = - ( x^2 - 2x (\sigma^2 t + \mu) + \mu^2 )\\
			& = -(x-(\mu + \sigma^2 t))^2 + (2 \mu \sigma^2 t + (\sigma^2 t )^2)
	\end{align}
$$


Thus,


$$
	\begin{align}
		M_X(t) & = e^{(2 \mu \sigma^2 t + (\sigma^2 t)^2)/2 \sigma^2 } \cdot \int \frac{ 1 }{ \sqrt{2\pi} \sigma} \cdot e^{-(x-(\mu + \sigma^2 t))^2 / 2\sigma^2} dc \\
			& = e^{(2 \mu \sigma^2 t + (\sigma^2 t)^2)/2 \sigma^2 } \cdot 1 \\
			& = e^{\mu t + \frac{ \sigma^2 t^2 }{ 2 }} \\ \\
		E(X) & = M_X^{(1)}(0) \\
			& = e^{\mu t} \sigma^2 t e^{\frac{ \sigma^2 t }{ 2} } + e^{\frac{ \sigma^2 t }{ 2} } \cdot \mu e^{\mu t} \Big|_{t=0}\\
			& = \mu \\ \\
		E(X^2) & = M_X^{(2)}(0)) \\
			& = e^{\mu t} \cdot (\sigma^2 e^{\sigma^2 t^2 /2}+ \sigma^2 t \cdot \sigma^2 t \cdot e^{\sigma^2 t^2 /2}) + \mu (\sigma^2 t + \mu e^t\cdot e^{\sigma^2 t /2}) \Big|_{t=0} \\
			& = \sigma^2 + \mu^2 \\ \\
		Var(X) & = \sigma^2 + \mu^2 - (\mu)^2 \\
			& = \sigma^2
	\end{align}
$$

			
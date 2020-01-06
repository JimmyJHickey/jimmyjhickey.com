---
layout: post
comments: false
title: Example Problems on Multivariate Distributions
description: ST701 Homework 5 on Multivariate Distributions
tags: ST701 Distributions Expectations Statistics
category: ST701
---

Problems: 4.5, 4.10, 4.15, 4, 4.17, 4.24, 4.30, 4.40


* Do not remove this line (it will not be displayed)
{:toc}



# 4.5

## a
**Find $P(X > \sqrt{Y})$ if $X$ and $Y$ are jointly distributed with pdf**

$$
f(x,y) = x + y, \ 0 \leq x \leq 1, \ 0 \leq y \leq 1.
$$

$$
	\begin{align}
		P( X > \sqrt{Y}) & = \int_{y=0}^{1} \int_{x = \sqrt{y}}^{1} f(x,y) dx dy \\
			& = \int_{y=0}^{1} \int_{x = \sqrt{y}}^{1} x + y dx dy \\
			& = \int_{y=0}^{1}  \frac{ 1 }{ 2 }x^2 + yx \Big|^{1}_{\sqrt{y}} dy \\
			& = \int_{y=0}^{1}  \frac{ 1 }{ 2 } + y - \frac{ 1 }{ 2 }y - y^{3/2} dy \\
			& = \frac{ 1 }{ 2 } y + y^2 / 4 - \frac{ 2 }{ 5 } y^{5/2} \Big|^{1}_{0} \\
			& = \frac{ 7 }{ 20 }
	\end{align}
$$


## b
**Find $P(X^2 < Y < X)$ if $X$ and $Y$ are jointly distributed with pdf**

$$
f(x,y) = 2x, \ 0 \leq x \leq 1, \ 0 \leq y \leq 1.
$$


$$
	\begin{align}
		P(X^2 < Y < X ) & = \int_{x=0}^{1} \int_{y=x^2}^{x} 2x dy dx \\
			& = \int_{x=0}^{1} 2xy \Big|^{1}_{x^2} dx \\
			& = \int_{x=0}^{1} 2x^2 - 2x^3 dx \\
			& = \frac{ 2 }{ 3 } x^3 - \frac{  2}{ 4 } x^4 \Big|_0^1 \\
			& = \frac{ 1 }{ 6 }
	\end{align}
$$

# 4.10
**The random pair $(X,Y)$ has the distribution**

$$
\begin{array}{c c | c c c}
	& & & X & \\
	& & 1 & 2 & 3 \\ \hline
	& 2 & \frac{ 1 }{ 12 } & \frac{ 1 }{ 6 } & \frac{ 1 }{ 12 }\\
	Y & 3 & \frac{ 1 }{ 6 } & 0 & \frac{ 1 }{ 6 }\\
	& 4 & 0 & \frac{ 1 }{ 3 } & 0
\end{array}
$$


## a
**Show that $X$ and $Y$ are dependent.**

Notice that $P(X = 2, Y = 3) = 0$, however $P(X=2) P(Y=3) = \frac{ 2 }{ 6 } \frac{ 6 }{ 12 } = \frac{ 1 }{ 3 } \neq 0$. The product of the marginals is not the same probability of the joint, so they are not independent.

## b
**Given a probability table for random variables $U$ and $V$ that have the same marginals as $X$ and $Y$ but are independent.**

$$
\begin{array}{c c | c c c | c}
	& & & X & &\\
	& & 1 & 2 & 3 &\\ \hline
	& 2 & \frac{ 1 }{ 12 } & \frac{ 2 }{ 12 } & \frac{ 1 }{ 12 } & \frac{ 4 }{ 12 }\\
	Y & 3 & \frac{ 1 }{ 12 } & \frac{ 2 }{ 12 } & \frac{ 1 }{ 12 } & \frac{ 4 }{ 12 }\\
	& 4 & \frac{ 1 }{ 12 } & \frac{ 2 }{ 12 } & \frac{ 1 }{ 12 } & \frac{ 4 }{ 12 }\\ \hline
	& & \frac{ 3 }{ 12 } & \frac{ 6 }{ 12 } & \frac{ 3 }{ 12 } & 
\end{array}
$$


# 4.15
**Let $X\sim Poisson(\theta), \ Y\sim Poisson(\lambda)$, independent. It was shown in Theorem 4.3.2 that the distribution of $X+Y$ is $Poisson(\theta + \lambda)$. Show that the distribution of $X \| X+Y$ is binomial with success of probability $\theta / (\theta + \lambda)$. What is the distribution of $Y\| X + Y$?**


$$
	\begin{align}
		f_{X|X+Y} & = \frac{ f(X, X+Y) }{ f(X+Y) } \\
			& = \frac{ \frac{ e^{-\theta} \theta^x }{ x! } \frac{e^{\-\lambda} \lambda^y }{ y! } }{ \frac{ e^{-(\theta+\lambda)} (\theta + \lambda)^{x+y} }{  (x+y)!} }\\
			& = \frac{ (x+y)! }{ x! y! } \frac{ e^{-\theta} \theta^x e^{\-\lambda} \lambda^y }{ e^{-(\theta+\lambda)} (\theta + \lambda)^{x+y} } \\
			& = \frac{ (x+y)! }{ x! y! } \frac{ \theta^x \lambda^y }{ (\theta + \lambda)^{x+y} } \\
			& = {x+y \choose x} \Big( \frac{ \theta }{ \theta + \lambda} \Big)^x \Big( \frac{ \lambda }{ \theta + \lambda } \Big)^y
	\end{align}
$$

Taking $p = \Big( \frac{ \theta }{ \theta + \lambda} \Big)^x$ and $1 - p = \Big( \frac{ \lambda }{ \theta + \lambda } \Big)^y$, we get $X\|X+Y \sim Binomial( p = \frac{ \theta }{ \theta + \lambda })$. Similarly, $Y \| X = Y \sim Binomial( p = \frac{ \lambda }{ \theta + \lambda })$.

# 4
**If $X$ has a binomial distribution with parameters $n$ and $p$, $Y$ has a binomial distribution with parameters $m$ and $p$, and $X$, $Y$ are independent. Show that $X + Y$ has a binomial distribution with parameters $n + m$ and $p$.**

Because the random variables are independent, we can use the product of the MGF to find the MGF of $X+Y$.

$$
	\begin{align}
		M_Z(t) & = M_X(t) M_Y(t) \\
			& = \Big[ p e^t + (1-p) \Big]^n \Big[ p e^t + (1-p) \Big]^m \\
			& = \Big[ p e^t + (1-p) \Big]^{n+m} \\
	\end{align}
$$

Thus, $Z \sim Bin(n+ m, p)$.



# 4.17
**Let $X$ be an $exponential(1)$ random variable and define $Y$ to be the integer part of $X+1$, that is**

$$
Y = i + 1\ \text{if and only if} \ i \leq X < i + 1, \ i = 0, 1, 2, \dots
$$


## a
**Find the distribution of $Y$. What well-known distribution does $Y$ have?**

$$
	\begin{align}
		Y & = \int_{i}^{i+1} e^{-x} dx \\
			& = -e^{-(1+i - i)} \\
			& = -e^{-(i+1) + e^{-i}} \\
			& = e^{-i} - e^{-i} e^{1} \\
			& = e^{-i}(1-e) \\
			& = e^{-1 (i)} (1-e^{-1})
	\end{align}
$$


Notice that $1-e^{-1} = p$. Thus, $Y \sim Geometric(1-e^{-1})$. 

## b
**Find the conditional distribution of $X - 4$ given $Y \geq 5$.**

$$
	\begin{align}
		P(X-4 \leq x | Y \leq 5) & = P(X - 4 \leq x | X \geq 4) \\
			& = \frac{ P(X - 4 \leq x) \land X \geq 4 }{ P(X \geq 4) } \\
			& = \frac{ P(X \leq x+4 \land X \geq 4) }{ P(X \geq 4) } \\
			& = \frac{ P(4 \leq X \leq x-4) }{ P(X \geq 4) } \\
			& = \frac{ \int_{4}^{x+4} e^{-z} dz }{ \int_{4}^{\inf} e^{-x} dx } \\
			& = \frac{ -(e^{-(x+4)} - e^{-4}) }{ - (e^{-\inf} - e^{-4}) } \\
			& = \frac{ e^{-4} - e^{-(x+4)} }{ e^{-4} } \\
			& = 1 - e^{-x}
	\end{align}
$$

This follows an $Exp(1)$ distribution.

# 4.24
**Let $X$ and $Y$ be independent random variables with $X \sim gamma(r, 1)$ and $Y \sim gamma(s,1)$. Show that $Z_1 = X+Y$ and $Z_2 = X/(X+Y)$ are independent, and find the distribution of each ($Z_1$ is gamma and $Z_2$ is beta).**

Notice that $X = Z_1 Z_2$ and $Y = Z_1 - Z_1 Z_2 = Z_1(1-Z_2)$. We can find the determinate of the Jacobian.

$$
det 
\begin{bmatrix}
	Z_2 & Z_1 \\
	1-Z_2 & -Z_1
\end{bmatrix}
= -Z_2 Z_1 (Z_1 - Z_1 Z_2) = -Z_1
$$



$$
	\begin{align}
		f_{Z_1, Z_2} & = f(X, Y) \cdot | J | \\
			& = f_X(Z_1 Z_2) f_Y(Z_1(1-Z_2)) \cdot Z_1 \\
			& = \frac{ 1 }{ \Gamma(R) 1^r } (z_1 z_2)^{r-1} e^{-(z_1 z_2) / 1} \cdot \frac{ 1 }{ \Gamma(s) 1^s } (z_1-z_1 z_2)^{s-1} e^{-(z_1-z_1 z_2)/2}z_1 \\
			& = \frac{ 1 }{ \Gamma(r) } z_1^{r-1} z_2^{r-1} \frac{ 1 }{ \Gamma(s) } z_1^{s-1} (1-z_2)^{s-1} e^{-z_1} z_1 \\
			& = \frac{ 1 }{ \Gamma(r+s) } z_1^{r+s-1} e^{-z_1} \cdot \frac{ \Gamma(r+s)}{\Gamma(r)\Gamma(s)} z_2^{r-1} (1-z_2)^{s-1} 
		\end{align}
$$


Notice that we can separate the $z_1$ and $z_2$ terms, so they are independent. Also, $Z_1 \sim Gamma(r+s,1)$ and $Z_2 \sim Beta(r,s)$

# 4.30
**Suppose the distribution of $Y$, conditional on $X=x$ is $n(x,x^2)$ and that the marginal distribution of $X$ is $uniform(0,1)$.**

## a
**Find $E(Y)$, $Var(Y)$, and $Cov(X,Y)$.**

$$
	\begin{align}
		E(Y) & = E(E(Y|X)) \\
			& = E(E(N(X, X^2))\\
			& = E(X) \\
			& = \frac{ 1 }{ 2 }
	\end{align}
$$


$$
	\begin{align}
		Var(Y) & = Var(E(Y|X)) + E(Var(Y|X)) \\
			& = E(X^2) + Var(X) \\
			& = Var(X) + E(X)^2 + Var(X) \\
			& = \frac{ 1 }{ 12 } + (\frac{ 1 }{ 2 })^2 + \frac{ 1 }{ 12 } \\
			& = \frac{ 5 }{ 12 }
	\end{align}
$$


$$
	\begin{align}
		Cov(X, Y) & = E(XY) - E(X)E(Y) \\
			& = E(E(XY|X)) - \frac{ 1 }{ 2 } \frac{ 1 }{ 2 }\\
			& = E(X E(Y|X) ) - \frac{ 1 }{ 4} \\
			& = E(X \cdot X) - \frac{ 1 }{ 4} \\
			& = Var(X) + E(X)^2 - \frac{ 1 }{ 4 } \\
			& = \frac{ 1 }{ 12 } + \frac{ 1 }{ 4 } - \frac{ 1 }{ 4 } \\
			& = \frac{ 1 }{ 12 }
	\end{align}
$$



## b
**Prove that $Y/X$ and $X$ are independent.**

Take $U = Y/X $ and $V = X$. So, $X = V$ and $Y = UV$. Then,

$$
det 
\begin{bmatrix}
	0 & 1 \\
	V & U
\end{bmatrix}
= -V
$$


$$
	\begin{align}
		f_{U,V} & = f(x, y) \cdot | J | \\
			& = f_{y|x} \cdot f_X \cdot | -v | \\
			& = \frac{ 1 }{ \sqrt{2 \pi x^2 } } e^{-\frac{ (y-x)^2 }{ 2x^2 }} \cdot \frac{ 1 }{ 1-0 } v \\
			& = \frac{ 1 }{ \sqrt{2 \pi v^2} } e^{-\frac{ (uv-v)^2 }{ 2v^2 }} v \\
			& = \frac{ v }{ \sqrt{2 \pi v^2} } e^{\frac{ -u^2 v^2 + 2 uv^2 - v^2 }{ 2 v^2 }} \\
			& = \frac{ v }{ \sqrt{2 \pi v^2} } \cdot e^{\frac{ -u^2+2u + -1 }{ 2 }}
	\end{align}
$$


Notice that the left expression is $f_X$ and the right expression is $f_{Y/X}$. Since we can separate the terms in the joint distribution, they are independent.


# 4.40
**A generalization of the beta distribution is the _Dirichlet_ distribution. In its bivariate version $(X,Y)$ has pdf**

$$
f(x,y) = C x^{a-1} y^{b-1}(1-x-y)^{c-1}, \ 0 < x < 1, \ 0 < y < 1, \ 0 < y < 1 - x < 1,
$$

**where $a>0$, $b>0$, and $c > 0$ are constants.**


## a
**Show that $C = \frac{ \Gamma(a + b + c) }{ \Gamma(a) \Gamma(b) \Gamma(c) }$.**

Take $z = \frac{ y }{ 1-x }$ and $dz = \frac{ 1 }{ 1-x } dy$.


$$
	\begin{align}
		1 & = \int_{x=0}^{1} \int_{y=0}^{1-x} C x^{a-1} y^{b-1} (1-x-y)^{c-1} dy dx \\
		1/C & = \int_{x=0}^{1} \int_{y=0}^{1-x} x^{a-1} y^{b-1} (1-x-y)^{c-1} dy dx \\
			& = \int_{x=0}^{1} \int_{z=0}^{1} x^{a-1} (z(1-x)^{b-1} (1-x-(z (1-x)))^{c-1} (1-x)dz dx \\
			& =  \int_{x=0}^{1} x^{a-1} (x-1)^{c+b-2} (x-1) dx \int_{z=0}^{1}  (z)^{b-1} (1-z)^{c-1} dz \\
			& = \frac{ \Gamma(a) \Gamma(c+b) }{ \Gamma(a+b+c) } \int_{x=0}^{1} \frac{ \Gamma(a+c) }{ \Gamma(a) \Gamma(c) } x^{a-1} (x-1)^{c+b-2} (x-1) dx \cdot \frac{ \Gamma(b) \Gamma(c) }{ \Gamma(b+c) }\int_{z=0}^{1} \frac{ \Gamma(b+c)  }{ \Gamma(b) \Gamma(c)} (z)^{b-1} (1-z)^{c-1} dz \\ \\
		C & = \frac{ \Gamma(a + b + c) }{ \Gamma(a) \Gamma(b) \Gamma(c) }
	\end{align}
$$


## b
**Show that, marginally, both $X$ and $Y$ are beta.**

We will use $z = \frac{ x }{ 1-y }$ and $dz = \frac{ 1 }{1-y  } dx$.

$$
	\begin{align}
		f_Y & = \int_{x=0}^{1-y} \frac{ \Gamma(a+b+c) }{ \Gamma(a) \Gamma(b) \Gamma(c) } x^{a-1} y^{b-1} (1-x-y)^{c-1} dx \\
			& = \frac{ \Gamma(a+b+c) }{ \Gamma(a) \Gamma(b) \Gamma(c) } y^{b-1} \int_{z=0}^{1} (z(1-y))^{a-1} (1-z(1-y)-y)^{c-1} (1-y) dz \\
			& = \frac{ \Gamma(a+b+c) }{ \Gamma(a) \Gamma(b) \Gamma(c) } y^{b-1} (1-y)^{a-1} (1-y)^{c-1} (1-y) \int_{z=0}^{1} (z))^{a-1} (1-z)^{c-1} dz \\
			& = \frac{ \Gamma(a+b+c) }{ \Gamma(a) \Gamma(b) \Gamma(c) } y^{b-1} (1-y)^{a+c-1} \cdot \frac{ \Gamma(a) \Gamma(c) }{ \Gamma(a+c) } \int_{z=0}^{1} \frac{ \Gamma(a+c) }{ \Gamma(a)\Gamma(c) } (z)^{a-1} (1-z)^{c-1} dz \\
			& = \frac{ \Gamma(a+b+c) }{ \Gamma(a+c) \Gamma(b) } y^{b-1} (1-y)^{a+c-1}
	\end{align}
$$


Thus $Y \sim Beta(b, a+c)$. The same process gives $X \sim Beta(a, b+c)$.


## c
**Find the conditional distribution of $Y\| X = x$, and show that $Y/(1-x)$ is $beta(b,c)$.**


$$
	\begin{align}
		f_{Y|X } & = \frac{ \frac{ \Gamma(a+b+c) }{ \Gamma(a) \Gamma(b) \Gamma(c) } x^{a-1} y^{b-1} (1-x-y)^{c-1} }{ \frac{ \Gamma(a+b+c) }{ \Gamma(a+c) \Gamma(b) } x^{a-1} (1-x)^{b+c-1} } \\
			& = \frac{ \Gamma(b+c) }{ \Gamma(b) \Gamma(c) } y^{b-1} \frac{ (1-x-y)^{c-1} }{ (1-x)^{b+c-1} }
	\end{align}
$$


Take $U = Y/(1-X)$ and $V = X$. Then, $X=V$ and $Y=U(1-V)$.

$$
det 
\begin{bmatrix}
	1-V & -U \\
	0 & 1
\end{bmatrix}
= -(1-V)
$$


$$
	\begin{align}
		f_{U,V} & = f(X,Y) |J| \\
			& = f(V, U(1-V)) (1-V) \\
			& = \frac{ \Gamma(a+b+c) }{ \Gamma(a)\Gamma(b)\Gamma(c) } v^{a-1} (u(1-v))^{b-1} (1-v-u(1-v))^{c-1}(1-v) \\
			& = \frac{ \Gamma(a+b+c) }{ \Gamma(a)\Gamma(b)\Gamma(c) } v^{a-1} (1-v)^{b-1}  (1-v)^{c-1} u^{b-1} (1-u)^{c-1} (1-v) \\ \\ 
		f_U & = \frac{ \Gamma(a+b+c) }{ \Gamma(a)\Gamma(b)\Gamma(c) }  u^{b-1} (1-u)^{c-1} \cdot \int_{v=0}^{1} v^{a-1} (1-v)^{b+c-1} dv \\
			& = \frac{ \Gamma(a+b+c) }{ \Gamma(a)\Gamma(b)\Gamma(c) }  u^{b-1} (1-u)^{c-1} \cdot \frac{ \Gamma(b+c) \Gamma(a) }{ \Gamma(a+b+c) } \int_{v=0}^{1} \frac{ \Gamma(a+b+c) }{ \Gamma(a) \Gamma(b+c) }v^{a-1} (1-v)^{b+c-1} dv \\
			& = \frac{ \Gamma(b+c) }{ \Gamma(b) \Gamma(c) }  u^{b-1} (1-u)^{c-1} 
	\end{align}
$$


Thus, $Y / (1-X) \sim Beta(b, c)$

## d
**Show that $E(XY) = \frac{ ab }{ (a+b+c+1)(a+b+c)}$, and find their covariance.**


$$
	\begin{align}
		E(XY) & = \int_{x=0}^{1} \int_{y=0}^{1-x} x y \cdot \frac{ \Gamma(a+b+c) }{ \Gamma(a) \Gamma(b) \Gamma(c) } x^{a-1} y^{b-1} (1-x-y)^{c-1} dy dx \\
			& = \frac{ \Gamma(a+b+c) }{ \Gamma(a) \Gamma(b) \Gamma(c) } \frac{\Gamma(a+1) \Gamma(b+1) \Gamma(c) }{ \Gamma(a + 1 + b + 1 + c) } \int_{x=0}^{1} \int_{y=0}^{1-x} \frac{ \Gamma(a+1 + b + 1+c) }{ \Gamma(a) \Gamma(b) \Gamma(c) }  x^{a+1-1} y^{b+1-1} (1-x-y)^{c-1} dy dx \\
			& = \frac{ a \Gamma(a) b \Gamma(b) \Gamma(c) }{ \Gamma(a) \Gamma(b) \Gamma(c) } \cdot \frac{ \Gamma(a+b+c) }{ (a+b+c+1)(a+b+c) \Gamma(a+b+c) } \\
			& = \frac{ ab }{ (a+b+c+1)(a+b+c) } \\ \\
		Cov(X, Y) & = E(XY) - E(X) E(Y) \\
			& = \frac{ ab }{ (a+b+c+1)(a+b+c) } - \frac{ a }{ a+ b + c  } \frac{ b }{ a + b + c } \\
			& = ab (\frac{ 1 }{(a+b+c+1)(a+b+c)  } - \frac{ 1  }{ (a+ b + c )^2 })
	\end{align}
$$
---
layout: post
comments: false
title: Example Problems on Hypothesis Testing
description: ST705 Homework 12 Hypothesis Testing
tags: ST705 Linear-Algebra Hypothesis-Testing Statistics
category: ST705
---


* Do not remove this line (it will not be displayed)
{:toc}

# 1 (6.15)
**Fill in all of the steps of the Scheffé approach to show that $(\widehat \tau - \tau)^T H^{-1} (\widehat \tau - \tau) / (s \widehat \sigma^2)$ has an $F$ distribution with $s$ and $(N-r)$ degrees of freedom.**

We can substitute in $\widehat \sigma^2$.

$$
\frac{ \frac{ (\widehat \tau - \tau)^T H^{-1} (\widehat \tau - \tau) }{ s }  }{ \frac{ SSE }{ n-r } }
$$

We know that $SSE \sim \chi^2_{n-r}$.

We know that $K^T \widehat b - m \sim N_s(0 , \sigma^2 H)$ and that $(K^T \widehat b - m)^2 (\sigma^2 H)^{-1} (K^T \widehat b - m) \sim \chi^2_s$. Then, by Theorem 6.1, our numerator also follows $\chi^2_s$ and is independent of $SSE$. Thus,

$$
\frac{ \frac{ (\widehat \tau - \tau)^T H^{-1} (\widehat \tau - \tau) }{ s }  }{ \frac{ SSE }{ n-r } } \sim \frac{ \chi^2_s / s }{ \chi^2_{n-r} /(n-r) } = F_{s, n-r}
$$


# 2 (6.18)
**For the one-way ANOVA model with $n_i = n = 5$ and $a=3$, compute th expected length (or squared length) of simultaneous confidence intervals computed using Bonferroni, Scheffe, and Tukey's method for all pairwise difference $\alpha_i - \alpha_k$.**

Take $\alpha = 0.05$.


_Bonferroni_

Our length is

$$
2 t_{15 - 3, \alpha/ (2s) \sqrt{ \widehat \sigma^2 H_{jj} }}.
$$


We can use $R$ to calculate our $t$ value.

``` 
> abs(qt(0.05/6, df = 15-3))
[1] 2.779473
``` 

We can also use $R$ to find $H$

``` 
> X = cbind( rep(1, 15), 
+            c(rep(1,5), rep(0, 10)),
+            c(rep(0,5), rep(1,5), rep(0, 5)),
+            c(rep(0,10), rep(1, 5))
+ )
> X
      [,1] [,2] [,3] [,4]
 [1,]    1    1    0    0
 [2,]    1    1    0    0
 [3,]    1    1    0    0
 [4,]    1    1    0    0
 [5,]    1    1    0    0
 [6,]    1    0    1    0
 [7,]    1    0    1    0
 [8,]    1    0    1    0
 [9,]    1    0    1    0
[10,]    1    0    1    0
[11,]    1    0    0    1
[12,]    1    0    0    1
[13,]    1    0    0    1
[14,]    1    0    0    1
[15,]    1    0    0    1
> # Naomi said I couldn't make this with reps
> Kt = cbind( rep(0,3),
+  c(rep(1,2), rep(0,1)),
+  c(rep(-1,1), rep(0,1), rep(1,1)),
+  c(rep(0,1), rep(-1,2))
+ )
> Kt
     [,1] [,2] [,3] [,4]
[1,]    0    1   -1    0
[2,]    0    1    0   -1
[3,]    0    0    1   -1
> H = Kt %*% ginv( t(X) %*% X ) %*% t(Kt)
> H
     [,1] [,2] [,3]
[1,]  0.4  0.2 -0.2
[2,]  0.2  0.4  0.2
[3,] -0.2  0.2  0.4
```

So our cutoff is

$$
2 t_{15 - 3, \alpha/ (2s) \sqrt{ \widehat \sigma^2 H_{jj} }} = 2 \cdot 2.779473 \cdot \sqrt{ \widehat \sigma^2 0.2 } = 2.486 \widehat  \sigma
$$


_Scheffé:_


$$
2 \cdot c \sqrt{ \widehat \sigma^2 u^T H u } = 2 \sqrt{ s F_{s, n-r, \alpha} \widehat \sigma^2 u^T H u }
$$

We can calculate this in $R$

``` 
> 2 * sqrt(3 * qf(0.05, 3, 15-3, lower.tail = FALSE) )
[1] 6.471749
```

Thus our cutoff is

$$
6.471749 \widehat \sigma \sqrt{ u^T H u }.
$$




_Tukey:_

$$
2 \cdot \frac{ \widehat \sigma }{ \sqrt{ n } } q^*_{a, a(n-1)}
$$


``` 
> 2/sqrt(5) * qtukey(0.05, 3*(5-1), 3)
1.535448
```


Then our cutoff is

$$
1.535448 \widehat \sigma
$$


# 3 (6.19)
**For the one-way ANOVA model with $n_i = n = 5$ and $a = 3$, compute the power when $\alpha_1 = \alpha_2 = 1$ and $\alpha_3 = 0$ when testing the hypothesis of equality in the following ways:**

## a.
**Use the usual $F$-test, writing the hypothesis as $\alpha_1 - \alpha_2 = 0$ and $\alpha_1 - \alpha_3 = 0$.**

Our $F$ statistic looks like

$$
F_{s, N-r} (\phi).
$$

Where $\phi = \frac{ 1 }{ 2 }(K^T b-m)^T(\sigma^2 H)^{-1} (K^T b - m)$


``` 
calc_h = function(Kt, X)
{
 H = Kt %*% ginv( t(X) %*% X ) %*% t(Kt)
 return(H)
}

b = c(0, 1,1,0)


X = cbind( rep(1, 15), 
           c(rep(1,5), rep(0, 10)),
           c(rep(0,5), rep(1,5), rep(0, 5)),
           c(rep(0,10), rep(1, 5))
)

## a
Kt = matrix(c(
 0, 1 , -1 , 0 ,
 0, 1 , 0 , -1
), byrow=T, ncol=4)
m=c(0,0)


H = calc_h(Kt, X)

phi = 1/2 * t( Kt %*% b - m ) %*% solve(H) %*% (Kt %*% b - m)
phi
         [,1]
[1,] 1.666667
```

So we can use this noncentral distribution to find the power

$$
P( F_{2, 12}(\frac{ 5 }{ 3 \sigma^2 }) > c_\alpha = F_{2, 12} | H_1 \text{ is true.})
$$


## b.
**Use the usual $F$-test, writing the hypothesis as $\alpha_1 - \alpha_3 = 0$ and $\alpha_2 - \alpha_3 = 0$.**

Similar to above.

``` 
Kt = matrix(c(
 0, 1 , 0 , -1,
 0, 0 , 1 , -1
), byrow=T, ncol=4)
m=c(0,0)


H = calc_h(Kt, X)

phi = 1/2 * t( Kt %*% b - m ) %*% solve(H) %*% (Kt %*% b - m)
phi
        [,1]
[1,] 1.666667
```

So we can use this noncentral distribution to find the power

$$
P( F_{2, 12}(\frac{ 5 }{ 3 \sigma^2 }) > c_\alpha = F_{2, 12} | H_1 \text{ is true.})
$$


## c.
**Let $\tau_1 = \alpha_1 - \alpha_2$ and $\tau_2 = \alpha_1 - \alpha_3$, and use a Bonferroni correction, rejecting if either component is significant. That is, form $t_j = \widehat \tau_j / se(\widehat \tau_j)$ and reject if $\| t_j \| > t (\alpha /4)$ for $j = 1,2$.**

Our $t$ looks like

$$
t = \frac{ K^T \widehat b}{ \sqrt{ \widehat \sigma^2 (K^T (X^T X)^g K) } }.
$$

With 

$$
K^T = 
\begin{bmatrix}
	0 & 1 & -1 & 0 \\
	0 & 1 & 0 & -1
\end{bmatrix},

K^T (X^T X)^g K =
\begin{bmatrix}
	0.4 & 0.2 \\
	0.2 & 0.4
\end{bmatrix}.
$$

And we would reject if $\| t_j \| > t (\alpha /4) = t_{12, 0.05/4} = 2.56$ and can calculate power under the noncentral $t_{12}$ distribution with noncentrality parameter

$$
\mu = \frac{ K^T b - m }{ \sqrt{ \sigma^2 K^T (X^T X)^g K } }
$$

We can calculate that for each hypothesis.

``` 
> Kt = matrix(c(
+  0, 1 , -1 , 0 ,
+  0, 1 , 0 , -1
+ ), byrow=T, ncol=4)
> 
> 
> mu = (Kt %*% b) / (sqrt( Kt %*% ginv( t(X) %*% X) 
	%*% t(Kt))[1,1])
> mu
         [,1]
[1,] 0.000000
[2,] 1.581139
```



## d.
**Repeat (c) but with $\alpha_1 - \alpha_3$ and $\alpha_2 - \alpha_3$. (Hint: Yes, (a) and (b) should be the same.)**



Our $t$ looks like

$$
t = \frac{ K^T \widehat b}{ \sqrt{ \widehat \sigma^2 (K^T (X^T X)^g K) } }.
$$

With 

$$
K^T = 
\begin{bmatrix}
	0 & 1 & 0 & -1 \\
	0 & 0 & 1 & -1
\end{bmatrix},

K^T (X^T X)^g K =
\begin{bmatrix}
	0.4 & 0.2 \\
	0.2 & 0.4
\end{bmatrix}.
$$

And we would reject if $\| t_j \| > t (\alpha /4) = t_{12, 0.05/4} = 2.56$ and can calculate power under the noncentral $t_{12}$ distribution with noncentrality parameter

$$
\mu = \frac{ K^T b - m }{ \sqrt{ \sigma^2 K^T (X^T X)^g K } } 
$$

We can calculate that for each hypothesis.

``` 
> Kt = matrix(c(
+  0, 1 , 0 , -1,
+  0, 0 , 1 , -1
+ ), byrow=T, ncol=4)
> 
> mu = (Kt %*% b) / (sqrt( Kt %*% ginv( t(X) %*% X) 
	%*% t(Kt))[1,1])
> mu
         [,1]
[1,] 1.581139
[2,] 1.581139
```


# 4 (6.25)
**Four rods, labeled P, Q, R, and S, are nominally 500 mm in length and are to be measured for their actual length. Designate their deviations from 500 mm by $p,q,r,s$ so that the length of rod P is (500+$p$) mm. The rods can only be measured two at a time. The results of the measurements and some analysis are:**

$$
\begin{array}{c c}
\hline 
\text{Rods} & \text{Length(mm)} \\ \hline
\text{P and Q} & 999 \\
\text{P and R} & 1003 \\
\text{P and S} & 1002 \\
\text{Q and R} & 1004 \\
\text{Q and S} & 1003 \\
\text{R and S} & 1001 \\ \hline
\end{array}
$$



$$
\begin{align}
y = \begin{bmatrix}
	-1 \\
	3 \\
	2 \\
	4 \\
	3 \\
	1
\end{bmatrix} , 
Xb & = 
\begin{bmatrix}
	1 & 1 & 0 & 0 \\
	1 & 0 & 1 & 0 \\
	1 & 0 & 0 & 1 \\
	0 & 1 & 1 & 0 \\
	0 & 1 & 0 & 1 \\
	0 & 0 & 1 & 1
\end{bmatrix}
\begin{bmatrix}
	p \\
	q \\
	r \\
	s
\end{bmatrix}, \\

(X^T X)^{-1} & = \frac{ 1 }{ 12 } 
\begin{bmatrix}
	5 & -1 & -1 & -1 \\
	-1 & 5 & -1 & -1 \\
	-1 & -1 & 5 & -1 \\
	-1 & -1 & -1 & 5
\end{bmatrix}, \\

X^T y & = 
\begin{bmatrix}
	4 \\
	6 \\
	8 \\
	6
\end{bmatrix}, 
\widehat b =
\begin{bmatrix}
	0 \\
	1 \\
	2 \\
	1
\end{bmatrix},

y^T y = 40, \overline{ y } =2.
\end{align}
$$

**Let's make the usual linear models distributional assumptions, $y \sim N_6(Xb, \sigma^2 I_6)$.**

## a.
**Give an unbiased estimate of $\sigma^2$ and its degrees of freedom.**

We have $n-r = 6 -4 = 2$.

$$
\begin{align}
\widehat \sigma^2 & = \frac{ SSE }{ n-r } \\
	& = \frac{ y^T (I - P_X) y }{ n-r }
\end{align}
$$


``` 
> get_PX = function(X)
+ {
+  return( X %*% ginv( t(X) %*% X ) %*% t(X) )
+ }
> X = matrix(c(
+  1, 1, 0, 0,
+  1, 0, 1, 0,
+  1, 0, 0, 1,
+  0, 1, 1, 0,
+  0, 1, 0, 1,
+  0, 0, 1, 1
+ ), byrow=T, ncol=4)
> Px = get_PX(X)
> I = diag(6)
> y = c(-1,3,2,4,3,1)
> sigma_hat_sq = t(y) %*% (I- Px) %*% y /(2)
> sigma_hat_sq
     [,1]
[1,]    6
```


$$
\widehat \sigma^2 = 6
$$


## b.
**Test the hypothesis that all four rods are equal in length versus the alternative that they are not equal. First give, $K$, $m$, $K^T \widehat b - m$, and the degrees of freedom of the $F$-statistic, then compute the $F$-statistic (hint: three equals signs).**


$$
K^T = 
\begin{bmatrix}
	1 & -1 & 0 & 0 \\
	0 & 1 & -1 & 0 \\
	0 & 0 & 1 & -1
\end{bmatrix}

m = 
\begin{bmatrix}
	0 \\
	0 \\
	0
\end{bmatrix}
$$


$$
K^T \widehat b - m = 
\begin{bmatrix}
	1 \cdot 0 + -1 \cdot 1 -0 \\
	1 \cdot 1 + -1 \cdot 2 -0 \\
	1 \cdot 2 + -1 \cdot 1 - 0
\end{bmatrix} 
=
\begin{bmatrix}
	0 \\
	-1 \\
	1
\end{bmatrix}
$$

Our degrees of freedom are $s = 3$ and $N-r = 2$.


Then we can test

$$
F = \frac{ (K^T \widehat b - m)^T H^{-1} (K^T \widehat b - m)/3 }{ \widehat \sigma^2}
$$


``` 
> Kt = 
+  matrix(c(
+   1, -1, 0, 0,
+   0, 1, -1, 0,
+   0, 0, 1, -1
+  ), byrow=T, ncol=4)
> bhat = c(0,1,2,1)
> H = calc_h(Kt, X)
> F = ( t( Kt %*% bhat - m) %*% solve(H) %*% 
+        (Kt %*% bhat - m)) / 3 /sigma_hat_sq
> F
          [,1]
[1,] 0.2222222
```


## c.
**Let $\mathcal T = \\{ b: K^T b = m\\}$. Find the vector $c$ so that $\mathcal T = \text{span}\\{c\\}$.**

We want $c$ to be the basis vector for the null space of $K$, so take 

$$
c  = 
\begin{bmatrix}
	1 \\
	1\\
	1\\
	1
\end{bmatrix}.
$$



## d.
**Using $z$ as the parameter, write the restricted model as $y = Xcz + e$, and find $\widehat z$ that minimized $\| \| y-Xcz \| \|^2$. (Hint: If this isn't easy, you're doing it wrong.)**

$$
\begin{align}
\frac{ \partial   }{\partial z} \Big( y^T y - 2 y^T X c z + z^2 c^T X^T X c \Big) & = -2 y^T X c + 2 z c^T X^T X c \\
0 & \stackrel{\text{set}}{=} -2 y^T X c + 2 \widehat z c^T X^T X c \\
\widehat  z & = \frac{ y^T X c }{ c^T X^T X c }
\end{align}
$$


``` 
> c = c(1,1,1,1)
> zhat = (t(y) %*% X %*% c) / (t(c) %*% t(X) %*% X %*% c)
> zhat
     [,1]
[1,]    1
```

$$
\widehat z = 1
$$


## e.
**Taking $\widehat b_H = c \widehat z$, find the complete solution to the restricted normal equations**

$$
\begin{bmatrix}
	X^T X & K \\
	K^T & 0
\end{bmatrix}
\begin{bmatrix}
	b \\
	\theta
\end{bmatrix} =
\begin{bmatrix}
	X^T y \\
	m
\end{bmatrix}.
$$


$$
\begin{align}
K c & = X^T y \\
K^T c \widehat z & = m \\
K^T c & = m \\
0 & = m \\ \\

X^T X c \widehat z + K \hat \theta& = X^T y \\
X^T X c + K \widehat \theta & = X^T y \\
K \widehat \theta & = X^T y - X^T X c \\
K^T K \widehat \theta & = K^T X^T y - K^T X^T X c \\
\widehat \theta & = (K^T K)^{-1} (K^T X^T y - K^T X^T X c)
\end{align}
$$


``` 
> theta_hat= solve(Kt %*% t(Kt)) %*%
+  (Kt %*% t(X) %*% y - 
+    Kt %*% t(X) %*% X %*% c)
> theta_hat
     [,1]
[1,]   -2
[2,]   -2
[3,]    0
```

$$
\widehat \theta = 
\begin{bmatrix}
	-2 \\
	-2 \\
	0
\end{bmatrix}
$$

Notice that this solution is dependent on the choice of $K$. If we take 

$$
K = 
\begin{bmatrix}
	1 & 1 & 1\\
	-1 & 0 & 0\\
	0 & -1 & 0 \\
	0 & 0 & -1
\end{bmatrix}
$$

then we get

``` 
> K = 
+   matrix(c(
+     1, 1, 1,
+     -1, 0, 0,
+     0, -1, 0,
+     0, 0, -1
+   ), byrow=T, ncol=3)
> c = c(1,1,1,1)
> theta_hat= solve(t(K) %*% K) %*%
+  (t(K) %*% t(X) %*% y - 
+    t(K) %*% t(X) %*% X %*% c)
> theta_hat
     [,1]
[1,]    0
[2,]   -2
[3,]    0
```

$$
\widehat \theta = 
\begin{bmatrix}
	0 \\
	-2 \\
	0
\end{bmatrix}
$$

## f.
**Is $\theta = 0$ in the equations in (e)?**


No it is not. Notice that with $\theta = 0$ this reduces to the unrestricted normal equations.


# 5
**Consider the following 150 sorted p-values**


0.0003 0.0005 0.0009 0.0009 0.0012 0.0022 0.0025 0.0033 0.0035 0.0052 0.0238 0.0263 0.0446 0.0470 0.0506 0.0564 0.0585 0.0660 0.0662 0.0685 0.0805 0.0814 0.1084 0.1118 0.1217 0.1247 0.1288 0.1305 0.1447 0.1463 0.1487 0.1541 0.1614 0.1896 0.1931 0.2181 0.2187 0.2218 0.2354 0.2389 0.2485 0.2592 0.2976 0.3012 0.3050 0.3054 0.3122 0.3183 0.3202 0.3233 0.3481 0.3491 0.3506 0.3543 0.3677 0.3738 0.3811 0.3872 0.3940 0.3992 0.4033 0.4185 0.4240 0.4277 0.4361 0.4412 0.4436 0.4890 0.4894 0.4912 0.4954 0.4972 0.5081 0.5193 0.5198 0.5199 0.5232 0.5254 0.5255 0.5290 0.5292 0.5395 0.5397 0.5408 0.5444 0.5629 0.5638 0.5664 0.5767 0.5876 0.5937 0.5960 0.6021 0.6203 0.6378 0.6396 0.6438 0.6513 0.6532 0.6671 0.6857 0.6983 0.7085 0.7122 0.7302 0.7306 0.7426 0.7429 0.7454 0.7486 0.7495 0.7534 0.7613 0.7633 0.7653 0.7681 0.7766 0.7806 0.7821 0.7828 0.7866 0.7867 0.7870 0.7901 0.8039 0.8084 0.8116 0.8140 0.8159 0.8212 0.8229 0.8304 0.8594 0.8698 0.8771 0.8874 0.8886 0.8973 0.9027 0.9043 0.9066 0.9169 0.9208 0.9269 0.9330 0.9452 0.9454 0.9670 0.9781 0.9970


**How many hypotheses would be rejected using without using any multiple test adjustment (set $\alpha$ to whatever you like)?  How many would be rejected using Bonferroni adjustment?**

With $\alpha = 0.05$, we would reject 14 hypotheses. Our adjusted threshold is $\alpha = 0.05/150 = 0.000333$. Thus, we would only reject one hypothesis.


# 6 (8.16)
**For modeling the growth of trees, the following model is often employed: $y_{ij} = \beta_0 + \alpha_i + \beta_1 t +e_{ij}$, $i = 1, \dots , a$; $t = 1, \dots , n$, where $y_{ij}$ measures the girth (circumference) of tree $i$ and time $t$, Here $\beta_0$ represents an average intercept, $\beta_1$ a common slope (growth rate), and $\alpha_i$ a random effect due to the timing of the emergence of the sprout and the initial tagging of the tree. The errors would be modeled as usual as $e_{it}$ iid $N(0, \sigma^2)$, and the random tree effect as $\alpha_i$ iid $N(0, \sigma_a^2)$, both with $e_{it}$ and $\alpha$ independent.**



## a
**For the simple case of $a = 3$ trees and $n = 4$ time points, select appropriate matrices and vectors below, in order to write the model above in the general mixed-model form:**

$$
y = Xb + Z u + e,
$$

**where $Xb$ represents the fixed effects and $u$ the random effects.**


$$
y = 
\begin{bmatrix}
y_{11}	\\
y_{12}	\\
y_{13}	\\
y_{14}	\\
y_{21}	\\
y_{22}	\\
y_{23}	\\
y_{24}	\\
y_{31}	\\
y_{32}	\\
y_{33}	\\
y_{34}	
\end{bmatrix},
e=
\begin{bmatrix}
e_{11}	\\
e_{12}	\\
e_{13}	\\
e_{14}	\\
e_{21}	\\
e_{22}	\\
e_{23}	\\
e_{24}	\\
e_{31}	\\
e_{32}	\\
e_{33}	\\
e_{34}	
\end{bmatrix}

\begin{bmatrix}
	1	&	0	&	0	\\
1	&	0	&	0	\\
1	&	0	&	0	\\
1	&	0	&	0	\\
0	&	1	&	0	\\
0	&	1	&	0	\\
0	&	1	&	0	\\
0	&	1	&	0	\\
0	&	0	&	1	\\
0	&	0	&	1	\\
0	&	0	&	1	\\
0	&	0	&	1	
\end{bmatrix}

\begin{bmatrix}
	1	&	0	&	0	\\
2	&	0	&	0	\\
3	&	0	&	0	\\
4	&	0	&	0	\\
0	&	1	&	0	\\
0	&	2	&	0	\\
0	&	3	&	0	\\
0	&	4	&	0	\\
0	&	0	&	1	\\
0	&	0	&	2	\\
0	&	0	&	3	\\
0	&	0	&	4	
\end{bmatrix}

\begin{bmatrix}
1	&	1	\\
1	&	2	\\
1	&	3	\\
1	&	4	\\
1	&	1	\\
1	&	2	\\
1	&	3	\\
1	&	4	\\
1	&	1	\\
1	&	2	\\
1	&	3	\\
1	&	4	
\end{bmatrix}

\begin{bmatrix}
	1	&	1	&	0	&	0	\\
1	&	2	&	0	&	0	\\
1	&	3	&	0	&	0	\\
1	&	4	&	0	&	0	\\
1	&	0	&	1	&	0	\\
1	&	0	&	2	&	0	\\
1	&	0	&	3	&	0	\\
1	&	0	&	4	&	0	\\
1	&	0	&	0	&	1	\\
1	&	0	&	0	&	2	\\
1	&	0	&	0	&	3	\\
1	&	0	&	0	&	4	\\
\end{bmatrix}

\begin{bmatrix}
	\beta_0 \\
	\beta_1
\end{bmatrix}

\begin{bmatrix}
	1 \\
	2\\
	3\\
	4
\end{bmatrix}

\begin{bmatrix}
	1 \\
	1 \\
	1 \\
	1 
\end{bmatrix}

\begin{bmatrix}
	\alpha_1 \\
	\alpha_2 \\
	\alpha_3
\end{bmatrix}
\begin{bmatrix}
	\mu
\end{bmatrix}
\begin{bmatrix}
	\beta_1
\end{bmatrix}
\begin{bmatrix}
	\beta_1 \\
	\beta_2 \\
	\beta_3 \\
	\beta_4
\end{bmatrix}
\begin{bmatrix}
	\beta_0 \\
	\alpha_1 \\
	\alpha_2 \
	\alpha_3
\end{bmatrix}
$$





$$
\begin{align}
X & = 
\begin{bmatrix}
1	&	1	\\
1	&	2	\\
1	&	3	\\
1	&	4	\\
1	&	1	\\
1	&	2	\\
1	&	3	\\
1	&	4	\\
1	&	1	\\
1	&	2	\\
1	&	3	\\
1	&	4	
\end{bmatrix}
\\
b & =
\begin{bmatrix}
	\beta_0 \\
	\beta_1
\end{bmatrix}
\\
Z &  = 
\begin{bmatrix}
1	&	0	&	0	\\
1	&	0	&	0	\\
1	&	0	&	0	\\
1	&	0	&	0	\\
0	&	1	&	0	\\
0	&	1	&	0	\\
0	&	1	&	0	\\
0	&	1	&	0	\\
0	&	0	&	1	\\
0	&	0	&	1	\\
0	&	0	&	1	\\
0	&	0	&	1	
\end{bmatrix}
\\
u & =
\begin{bmatrix}
	\alpha_1 \\
	\alpha_2 \\
	\alpha_3
\end{bmatrix}
\end{align}
$$


## b.
**Give the distribution of your random effect vector $u$.**

$$
u \sim N_3(0, \sigma_a^2 I_3)
$$




## c.
**We know that $(I-P_X)X b = 0$. Show that $(P_Z - P_1)Xb = 0$ in this problem.**

``` 
> X =  matrix(c(
+  1, 1,
+  1, 2,
+  1, 3,
+  1, 4,
+  1, 1,
+  1, 2,
+  1, 3,
+  1, 4, 
+  1, 1,
+  1, 2,
+  1, 3,
+  1, 4
+ ), byrow=T, ncol=2)
> 
> Px = get_PX(X)
> 
> I12 = diag(12)
> 
> (I12 - Px) %*% X
               [,1]          [,2]
 [1,] -2.858824e-15 -3.774758e-15
 [2,] -1.887379e-15 -3.635980e-15
 [3,] -8.604228e-16 -2.997602e-15
 [4,] -6.106227e-16 -5.107026e-15
 [5,] -2.858824e-15 -3.774758e-15
 [6,] -1.887379e-15 -3.858025e-15
 [7,] -8.604228e-16 -3.441691e-15
 [8,] -7.216450e-16 -5.551115e-15
 [9,] -2.942091e-15 -3.774758e-15
[10,] -1.859624e-15 -3.747003e-15
[11,] -8.881784e-16 -3.108624e-15
[12,] -7.771561e-16 -5.773160e-15
> 
> 
> Z =  matrix(c(
+  1, 0, 0,
+  1, 0, 0,
+  1, 0, 0,
+  1, 0, 0,
+  0, 1, 0,
+  0, 1, 0,
+  0, 1, 0,
+  0, 1, 0, 
+  0, 0, 1,
+  0, 0, 1,
+  0, 0, 1,
+  0, 0, 1
+ ), byrow=T, ncol=3)
> 
> Pz = get_PX(Z)
> 
> one_vec = rep(1,12)
> 
> P1 = get_PX(one_vec)
> 
> (Pz - P1) %*% X
              [,1]         [,2]
 [1,] 8.326673e-17 1.665335e-16
 [2,] 8.326673e-17 1.665335e-16
 [3,] 8.326673e-17 1.665335e-16
 [4,] 8.326673e-17 1.665335e-16
 [5,] 1.387779e-16 2.775558e-16
 [6,] 1.387779e-16 2.775558e-16
 [7,] 1.387779e-16 2.775558e-16
 [8,] 1.387779e-16 2.775558e-16
 [9,] 1.110223e-16 2.220446e-16
[10,] 1.110223e-16 2.220446e-16
[11,] 1.110223e-16 2.220446e-16
[12,] 1.110223e-16 2.220446e-16
```



## d.
**Find the following**

``` 
> sum(diag(I12 - Px))
[1] 10
> sum(diag(Pz - P1))
[1] 2
> sum(diag( t(Z) %*% (I12 - Px) %*% Z ))
[1] 8
> sum(diag(t(Z) %*% (Pz - P1) %*% Z))
[1] 8
```

$$
\begin{align}
\text{tr}( I - P_X ) & = 10\\
\text{tr}( P_Z - P_1 ) & = 2 \\
\text{tr}( Z^T(I - P_X )Z )& = 8 \\
\text{tr}( Z^T(P_Z - P_1)Z ) & = 8 
\end{align}
$$
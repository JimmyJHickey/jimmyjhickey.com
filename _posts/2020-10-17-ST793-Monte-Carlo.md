---
layout: post
comments: false
title: Example Problems on Monte Carlo Simulation and M-Estimators
description: ST793 Homework 8 on Monte Carlo Simulation and M-Estimators
tags: ST793 Testing Asymptotics Monte Carlo Statistics M-Estimators
category: ST793
---

* Do not remove this line (it will not be displayed)
{:toc}

# 9.1
**In the context of Example 9.1 (p. 365) the MSE could be estimated by $\widehat{\text{MSE}}= N^{-1} \sum_{i=1}^N (\widehat{\theta}_i - \theta_0)^2$.**

## a.
**What is the standard deviation of $\widehat{\text{MSE}}$?**

Let's start by finding the variance. We will take $B$ to be the bias.

$$
\begin{align}
\text{Var}( \widehat {MSE}) & =  \text{Var}(  \frac{ 1 }{ N }\sum_{i=1}^{n} (\widehat \theta_i - \theta_0)^2 ) \\
     & = \frac{ 1 }{ N } \Big( E(( \widehat \theta_i - \theta_0)^4 ) - (E[(\widehat \theta_i - \theta_0)^2])^2 \Big) \\
    & = \frac{ 1 }{ N } \Big( E(( \widehat \theta_i + E(\widehat \theta_i) - E(\widehat \theta_i) - \theta_0)^4 ) - (\text{Var}( \widehat \theta_i ) - B^2)^2 \Big)
\end{align}
$$

Let's look at the first term. 

$$
\begin{align}
( \widehat \theta_i & + E(\widehat \theta_i) - E(\widehat \theta_i) - \theta_0)^4  = (\widehat \theta_i - E(\widehat \theta_i) + E(\widehat \theta_i) - \theta_0)^2(\widehat \theta_i - E(\widehat \theta_i) + E(\widehat \theta_i) - \theta_0)^2 \\
    & = \Big[ (\widehat \theta_i -  E(\widehat \theta_i))^2 + 2(\widehat \theta_i -  E(\widehat \theta_i))( E(\widehat \theta_i) - \theta_0) + ( E(\widehat \theta_i) - \theta_0)^2 \Big]^2 \\
    & = (\widehat \theta_i -  E(\widehat \theta_i))^4 + 2(\widehat \theta_i -  E(\widehat \theta_i))^3( E(\widehat \theta_i) - \theta_0) + (\widehat \theta_i -  E(\widehat \theta_i))^2( E(\widehat \theta_i) - \theta_0)^2 +2(\widehat \theta_i -  E(\widehat \theta_i))^3( E(\widehat \theta_i) - \theta_0) + 4 (\widehat \theta_i -  E(\widehat \theta_i))^2( E(\widehat \theta_i) - \theta_0)^2 + 2(\widehat \theta_i -  E(\widehat \theta_i))( E(\widehat \theta_i) - \theta_0)^ + (\widehat \theta_i -  E(\widehat \theta_i))^2( E(\widehat \theta_i) - \theta_0)^2 +2 (\widehat \theta_i -  E(\widehat \theta_i))( E(\widehat \theta_i) - \theta_0)^3 + ( E(\widehat \theta_i) - \theta_0)^4 \\
    & = (\widehat \theta_i -  E(\widehat \theta_i))^4 + 4 (\widehat \theta_i -  E(\widehat \theta_i))^3( E(\widehat \theta_i) - \theta_0) + 7 4 (\widehat \theta_i -  E(\widehat \theta_i))^2( E(\widehat \theta_i) - \theta_0)^2 + 4 (\widehat \theta_i -  E(\widehat \theta_i))( E(\widehat \theta_i) - \theta_0)^3 + ( E(\widehat \theta_i) - \theta_0)^4
\end{align}
$$

Taking it's expectation gives

$$
\mu_4 + 4 \mu_3 B + 8 \mu_2 B^2 + 0 + B^4.
$$

Recall that $\mu_2 = \text{Var}(  \widehat \theta_i )$. Now we can simplify our $\text{Var}(  \widehat {MSE} )$.

$$
\begin{align}
\text{Var}(  \widehat {MSE} ) & = \frac{ 1 }{ N } \Big( \mu_4 + 4 \mu_3 B + 8 \mu_2 B^2 + B^4 - \mu_2^2 - 2 \mu_2 B^2 - B^4 \Big)  \\
    & = \frac{ 1 }{ N } \Big( \mu_4 + 4 \mu_3 B + 6 \mu_2 B^2  - \mu_2^2 - 2 \mu_2 B^2  \Big)  \\
\text{Stddev}(  \widehat {MSE} ) & = \sqrt{ \frac{ 1 }{ N } \Big( \mu_4 + 4 \mu_3 B + 6 \mu_2 B^2  - \mu_2^2 - 2 \mu_2 B^2  \Big) }
\end{align}
$$

## b.
**Based on a preliminary run of size $N_0$, how large should $N$ be to have the standard deviation of $\widehat{\text{MSE}} \leq d$?**

We need to find $N$ such that

$$
\begin{align}
\sqrt{ \widehat{\text{Var}(  \widehat{MSE} )} } & \equiv \sqrt{ \frac{ 1 }{ N }(\mu_4 + 4 \mu_3 B + 4 \mu_2 B^2 - \mu_2^2) } < d\\
\Rightarrow \\
N & = \frac{ N_0  (\mu_4 + 4 \mu_3 B + 4 \mu_2 B^2 - \mu_2^2) }{ d^2 }.
\end{align}
$$

For a choice of $d$. We will simulate this for all of the distributions given in the example. We will use $n = 10, 30, 130$, $N0 = 100$ and $R = 1000$ Monte Carlo replicates.

This gives the following estimates:

```
# Normal

> N * z_stddev
         mean       t20    median
10  1.3824645 1.5848857 1.9077966
30  0.4734433 0.5496464 0.7281993
130 0.1063662 0.1244232 0.1661517


# T_5

> N * t_stddev
         mean       t20   median
10  2.5542148 2.0660546 2.383983
30  0.8229739 0.6672062 0.840764
130 0.1801850 0.1476896 0.186333


# Laplace
> N * l_stddev
         mean       t20    median
10  3.1605571 2.3937543 2.6806677
30  0.9582438 0.6581390 0.6930445
130 0.2173462 0.1466053 0.1323092
```

# 9.7
**Related to the SV of the last problem, one might be interested in reported instead the coefficient of variation (CV), which is just the square root of $\widehat{SV}$, $\widehat{CV} = s_V / \overline{ V }$. Thus, use the Delta theorem with the asymptotic variance expression for $\widehat{SV}$, to obtain the asymptotic variance $\widehat{CV}$:**

$$
\frac{ \sigma^2_n }{ \mu^2_n } \Big( \text{Kurt}( V ) - 1 - 4 \frac{ \sigma_n }{ \mu_n }\text{Skew}( V ) + 4 \frac{ \sigma^2_n }{ \mu_n^2 }\Big)
$$

**where $\sigma^2_n = \text{Var}(  V )$ and $\mu_n = E(V)$.**

Here $g(x) = \sqrt{ x }$ so $g'(x)= \frac{ 1 }{ 2 } x^{-1/2}$. Since $\widehat SV$ is asymptotically normal, we can use the delta theorem.

$$
\begin{align}
AsyVar(\widehat{SV}) & =\frac{ \sigma^4 }{ \mu_n^4 } \Big( \text{Kurt}( V ) -1 - 4 \frac{ \sigma_n }{ \mu_n } \text{Skew}( V ) + 4 \frac{ \sigma_n^2 }{ \mu_n^2 }\Big) \\
AsyVar(\widehat {CV}) & = AsyVar( g(\widehat{SV})) \\
    & = AsyVar(\widehat \theta) g'(\theta)^2 \\
    & = \Big( \frac{ 1 }{ 2 } (\frac{ \sigma^2_n }{ \mu_n^2 })^{-1/2}\Big) \frac{ \sigma^4 }{ \mu_n^4 } \Big( \text{Kurt}( V ) -1 - 4 \frac{ \sigma_n }{ \mu_n } \text{Skew}( V ) + 4 \frac{ \sigma_n^2 }{ \mu_n^2 }\Big) \\
    & = \frac{ \sigma^2 }{ \mu_n^2} \Big( \frac{\text{Kurt}( V ) -1}{4} - \frac{ \sigma_n }{ \mu_n } \text{Skew}( V ) + \frac{ \sigma_n^2 }{ \mu_n^2 }\Big) ✅\
\end{align}
$$

# 9.13
**In section 9.5.3 (p. 380), the phrase "mainly random noise" was used to describe the third decimal place of estimated convergence probabilities based on $N = 1000$ Monte Carlo replications. To quantify this phrase, suppose that $Y$ is $\text{binomial}(1000, 0.95)$ and $Y / 1000$ is the estimate of interest. Model the act of rounding from three decimal places to two as adding an independent uniform random variable $U$ on $(-0.005, 0.005)$ to $Y / 1000$. Show that the increase in the standard deviation of $Y/1000 + U$ compared to the standard deviation of $Y / 1000$ is 8.4%.**

The standard deviation of coverage of $Y /1000$ is $\Big(\frac{ 0.05 \cdot 0.95}{ 1000 } \Big)^{1/2} = 0.007$. Thus,

$$
\begin{align}
\text{Var}( Y/1000 + U) & = \text{Var}( Y/1000  ) + \text{Var}(  U ) \\
\text{Stddev}( Y/1000 + U) & = \sqrt{  \text{Var}( Y/1000  ) + \text{Var}(  U )} \\
    & = \sqrt{ \frac{ 0.05 \cdot 0.95}{ 1000 } + \frac{ (0.005- (-0.005))^2 }{ 12 }} \\
    & = 0.00747.
\end{align}
$$


So the percent increase is

$$
\frac{ 0.00747 - 0.00689 }{ 0.00689 } = 0.084. ✅
$$



# 7.2
**Let $Y_1, \dots , Y_n$ be iid from some distribution with finite fourth moment. The coefficients of variange is $\widehat \theta_3 = s_n / \overline{ Y }$.**

## a
**Define a three dimensional $\psi$ so that $\widehat \theta_3$ is defined by summing the third component. Find $A$, $B$, and $V$, where**

$$
V_{33} = \frac{ \sigma^4 }{ \mu^4 } - \frac{ \mu_3 }{ \mu^3 } + \frac{ \mu_4 - \sigma^4 }{ 4 \mu^2 \sigma^2 }.
$$

First we need to find $\psi_3(Y_i, \theta)$

$$
\widehat \theta_3 = s_n / \overline{ Y } \Rightarrow \psi_3(Y_i, \theta) = \theta_2 - \theta_1 \theta_3.
$$

Thus,

$$
\psi_i(Y_i, \theta) = \begin{bmatrix}
Y_i - \theta_1 \\
(Y_i - \theta_1)^2 - \theta_2^2 \\
 \theta_2 - \theta_1 \theta_3
\end{bmatrix}.
$$

Then,

$$
\psi'(Y_i, \theta) = 
\begin{bmatrix}
-1 & 0 & 0 \\
-2 Y_i + 2 \theta_1 & -2\theta_2& 0 \\
-\theta_3 & 1 & -\theta_1
\end{bmatrix}.
$$

Now we can find $A(\theta_0)$.

$$
\begin{align}
A(\theta_0) & = E[-\psi'(Y_1, \theta_0)] \\
    & = - E \begin{bmatrix}
-1 & 0 & 0 \\
-2 Y_i + 2 \theta_{10} & -2 \theta_{20} & 0 \\
-\theta_{30} & 1 & -\theta_{10}
\end{bmatrix} \\
    & = \begin{bmatrix}
    1 & 0 & 0 \\
    0 & 2 \theta_{20} & 0 \\
    \theta_{30} & -1 & \theta_{10}
    \end{bmatrix}
\end{align}
$$

Then,

$$
A^{-1}(\theta_0) = 
\begin{bmatrix}
1 & 0 & 0\\
0 & \frac{ 1 }{ 2 \theta_{20} } & 0 \\
- \frac{ \theta_{30} }{ \theta_{10} } & \frac{ 1 }{ 2 \theta_{10} \theta_{20} }  & \frac{ 1 }{ \theta_{10} }
\end{bmatrix}
=\begin{bmatrix}
1 & 0 & 0 \\
0 & \frac{ 1 }{ 2 \sigma } & 0 \\
- \frac{ \sigma }{ \mu^2 } & \frac{ 1 }{ 2 \mu \sigma } & \frac{ 1 }{ \mu }
\end{bmatrix}.
$$

Now we can work on finding $B$.

$$
\small
\begin{align}
\psi& (Y_1, \theta)  \psi(Y_1 , \theta)^T = \\
& 
\begin{bmatrix}
(Y_1 - \theta_1)^2 & (Y_1 - \theta_1)^3 - \theta_2^2 (Y_1 - \theta_1) & (Y_1 - \theta_1) (\theta_2 - \theta_1 \theta_3) \\
(Y_1 - \theta_1)^3 - \theta_2^2 (Y_1 - \theta_1) & \Big( (Y_1 - \theta_1)^2 - \theta_2^2 \Big)^2 & ((Y_1 - \theta_1)^2 - \theta_2^2 )(\theta_2 - \theta_1 \theta_2) \\
(Y_1 - \theta_1) (\theta_2 - \theta_1 \theta_3)  & ((Y_1 - \theta_1)^2 - \theta_2^2 )(\theta_2 - \theta_1 \theta_2)  & (\theta_2 - \theta_1 \theta_2)^2
\end{bmatrix} \\ \\ 
B(\theta_0) & = E(\psi (Y_1, \theta_0)  \psi(Y_1 , \theta_0)^T) \\
    & = 
\begin{bmatrix}
\sigma^2 &\mu_3 - 0  & 0 \\
\mu_3 - 0 & E[( (Y_1 - \theta_1)^2 - \theta_2^2) ^2] & \small\theta_{20} \theta_{20}^2 - \theta_{10}\theta_{30}\theta_{20} - \theta_{20} \sqrt{ \theta_{20} } + \theta_{20} \theta_{10} \theta_{30} \normalsize\\
 0 & \tiny \theta_{20} \theta_{20}^2 - \theta_{10}\theta_{30}\theta_{20} - \theta_{20} \sqrt{ \theta_{20} } + \theta_{20} \theta_{10} \theta_{30} \normalsize& (\theta_{20} - \theta_{10}\theta_{30})^2\\
\end{bmatrix} \\
& = \begin{bmatrix}
\sigma^2 & \mu_3 & 0 \\
\mu_3 & \mu_4 - \sigma^4 & 0 \\
0 & 0 & 0
\end{bmatrix}
\end{align}
$$


Now we can find $V$.

$$
\begin{align}
V & = A^{-1} B (A^{-1})^{T} \\
    & = 
\begin{bmatrix}
1 & 0 & 0 \\
0 & \frac{ 1 }{ 2 \sigma } & 0 \\
- \frac{ \sigma }{ \mu^2 } & \frac{ 1 }{ 2 \mu \sigma } & \frac{ 1 }{ \mu }
\end{bmatrix}
\begin{bmatrix}
\sigma^2 & \mu_3 & 0 \\
\mu_3 & \mu_4 - \sigma^4 & 0 \\
0 & 0 & 0
\end{bmatrix}
\begin{bmatrix}
1 & 0 & 0 \\
0 & \frac{ 1 }{ 2 \sigma } & 0 \\
- \frac{ \sigma }{ \mu^2 } & \frac{ 1 }{ 2 \mu \sigma } & \frac{ 1 }{ \mu }
\end{bmatrix}^T \\
& = \begin{bmatrix}
\sigma^2 & \mu_3 & 0 \\
\frac{ \mu_3}{ 2 \sigma } & \frac{ \mu_4 - \sigma^4 }{ 2 \sigma } & 0 \\
\frac{ \mu_3 }{ 2 \mu \sigma } - \frac{ \sigma^3 }{ \mu^2 } & \frac{ -\mu_3 \sigma }{ \mu^2 } + \frac{ \mu_4 - \sigma^4 }{ 2 \mu \sigma } &0
\end{bmatrix}
\begin{bmatrix}
1 & 0 & 0 \\
0 & \frac{ 1 }{ 2 \sigma } & 0 \\
- \frac{ \sigma }{ \mu^2 } & \frac{ 1 }{ 2 \mu \sigma } & \frac{ 1 }{ \mu }
\end{bmatrix}^T  \\
& = \begin{bmatrix}
\sigma^2 & \frac{ \mu_3 }{ 2 \sigma } & \frac{ \mu \cdot \mu_3 - 2\sigma^4 }{ 2 \mu^2 \sigma } \\
\frac{ \mu_3 }{ 2 \sigma } & \frac{ \mu_4 - \sigma^4 }{ 4 \sigma^2 } & \frac{ \mu \cdot mu_4- 2 \mu_3 \sigma^2 - \mu \sigma^4}{ 4 \mu^2 \sigma^2 } \\
\frac{ \mu \cdot \mu_3 - 2 \sigma^4 }{ 2 \mu^2\sigma } & \frac{  \mu \cdot \mu_4 - 2 \mu_3 \sigma^2 - \mu \sigma^4 }{ 4 \mu^2 \sigma^2 } & \frac{ -4 \mu \cdot \mu^3 + 4 \sigma^4 + \frac{ \mu^2 (\mu_4  - \sigma^4)}{ \sigma^2 } }{ 4 \mu^4 }
\end{bmatrix}
\end{align}
$$

# 7.5
**Repeat the calculations in Section 7.2.4 (p.305) with $\widehat \theta_3 = \Phi\{(a - \overline{ Y })/s_n \}$ replacing $s_n$ and $\widehat \theta_4 = \Phi^{-1}(p) s_n + \overline{ Y }$ replacing $\log(s_n^2)$. Note that $\widehat \theta_3$ and $\widehat \theta_4$ are the maximum likeligood estimators of $P(Y\_1 \leq a)$ and the $p$th quantile qualtie of $Y\_1$ respectly, under a normal distribution assumption.**

We can find out $\psi(Y_i, \theta)$ function similar to in the last question. 

$$
\begin{align}
\theta_3 = \Phi(\frac{ a- \overline Y }{ s_n }) & \Rightarrow \psi_3 = \theta_3 - \Phi(\frac{ a- \theta_1}{ \sqrt{ \theta_2 } }) \\
\theta_4 = \Phi(p)^{-1} s_n - \overline Y \Rightarrow \psi_4 = \theta_4 - \Phi(p)^{-1} \sqrt{\theta_2} - \theta_1
\end{align}
$$

So,

$$
\psi(Y_i, \theta) = \begin{bmatrix}
Y_i - \theta_1 \\
(Y_1 - \theta_1)^2 - \theta_2 \\
\theta_3 - \Phi(\frac{ a- \theta_1 }{ \sqrt{ \theta_2 } }) \\
\theta_4 - \Phi(p)^{-1} \sqrt{ \theta_2 } + \theta_1 
\end{bmatrix}
$$

Now we can take the derivative.

$$
\psi '(Y_i, \theta) = \begin{bmatrix}
-1 &0 & 0 & 0 \\
-2Y_i + 2 \theta_1 & -1 & 0&  0  \\
\frac{ -1 }{ \sqrt{ \theta_2 } } \phi(\frac{ a- \theta_1 }{ \sqrt{ \theta_2 } }) & -\frac{ a - \theta_1 }{ 2 \theta_2^{3/2} } \phi(\frac{ a- \theta_1 }{ \sqrt{ \theta_2 } }) & 1 & 0  \\
1 & -\Phi(p)^{-1} \frac{ 1 }{ 2 \sqrt{ \theta_2 } } & 0 & 1
\end{bmatrix}
$$

Then,

$$
\begin{align}
A(\theta_0) & = 
\begin{bmatrix}
1 &0 & 0 & 0 \\
0 & 1 & 0&  0  \\
\frac{ 1 }{ \sqrt{ \theta_{20} } } \phi(\frac{ a- \theta_{10} }{ \sqrt{ \theta_{20} } }) & \frac{ a - \theta_{10} }{ 2 \theta_{20}^{3/2} } \phi(\frac{ a- \theta_{10} }{ \sqrt{ \theta_{20} } }) & -1 & 0  \\
-1 & \Phi(p)^{-1} \frac{ 1 }{ 2 \sqrt{ \theta_{20} } } & 0 & -1
\end{bmatrix}\\
A^{-1}(\theta_0) & = 
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
\frac{  1 }{ \sqrt{ \theta_{20} } } \phi(\frac{ a- \theta_{10} }{ \sqrt{ \theta_{20} } }) & \frac{ (a-\theta_{10}) }{ 2 \theta_{20}^3 } \phi(\frac{ a- \theta_{10} }{ \sqrt{ \theta_{20} } }) & -1 & 0 \\
1 & \frac{ 1 }{ 2 \sqrt{ \theta_2 } } \Phi(p)^{-1}& 0 & -1
\end{bmatrix}
\end{align}
$$

Now we can start finding the $B$ matrix. First we need $\psi \psi^T$. Take $\Phi_1 = \Phi(\frac{ a- \theta_1 }{ \sqrt{ \theta_2 } })$ and $\Phi_2 = \Phi(p)^{-1}$

$$
\small
 \psi(Y_i, \theta) \psi(Y_i, \theta)^T = 
\left[
\begin{array}{cccc}
 (Y_1-\text{$\theta_1$})^2 & \text{$\theta_2$} (\text{$\theta_1$}-Y_1)+(Y_1-\text{$\theta_1$})^3 & (\text{$\theta_3$}-\text{$\Phi_1$}) (Y_1-\text{$\theta_1$}) & (Y_1-\text{$\theta_1$}) \left(\text{$\theta_1$}-\sqrt{\text{$\theta_2$}} \text{$\Phi_2$}+\text{$\theta_4$}\right) \\
 \text{$\theta_2$} (\text{$\theta_1$}-Y_1)+(Y_1-\text{$\theta_1$})^3 & \left((Y_1-\text{$\theta_1$})^2-\text{$\theta_2$}\right)^2 & (\text{$\theta_3$}-\text{$\Phi_1$}) \left((Y_1-\text{$\theta_1$})^2-\text{$\theta_2$}\right) & \left((Y_1-\text{$\theta_1$})^2-\text{$\theta_2$}\right) \left(\text{$\theta_1$}-\sqrt{\text{$\theta_2$}} \text{$\Phi_2$}+\text{$\theta_4$}\right) \\
 (\text{$\theta_3$}-\text{$\Phi_1$}) (Y_1-\text{$\theta_1$}) & (\text{$\theta_3$}-\text{$\Phi_1$}) \left((Y_1-\text{$\theta_1$})^2-\text{$\theta_2$}\right) & (\text{$\theta_3$}-\text{$\Phi_1$})^2 & (\text{$\theta_3$}-\text{$\Phi_1$}) \left(\text{$\theta_1$}-\sqrt{\text{$\theta_2$}} \text{$\Phi_2$}+\text{$\theta_4$}\right) \\
 (Y_1-\text{$\theta_1$}) \left(\text{$\theta_1$}-\sqrt{\text{$\theta_2$}} \text{$\Phi_2$}+\text{$\theta_4$}\right) & \left((Y_1-\text{$\theta_1$})^2-\text{$\theta_2$}\right) \left(\text{$\theta_1$}-\sqrt{\text{$\theta_2$}} \text{$\Phi_2$}+\text{$\theta_4$}\right) & (\text{$\theta_3$}-\text{$\Phi_1$}) \left(\text{$\theta_1$}-\sqrt{\text{$\theta_2$}} \text{$\Phi_2$}+\text{$\theta_4$}\right) & \left(\text{$\theta_1$}-\sqrt{\text{$\theta_2$}} \text{$\Phi_2$}+\text{$\theta_4$}\right)^2 \\
\end{array}
\right]
$$

Now we can take the expectation to get $B(\theta_0)$.

$$
B(\theta_{0}) = 
\begin{bmatrix}
\mu_2 & \mu_3 & 0 & 0 \\
\mu_3 & \mu_4 - \sigma^4 & 0 & 0\\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 
\end{bmatrix}
$$

Finally, we can calculate $V$. Take $\phi = \phi(\frac{ a-\theta_{10} }{ \sqrt{ \theta_{20} } }$ and $\Phi_2 = \Phi(p)^{-1}$

$$
\begin{align}
V & = A^{-1} B (A^{-1})^T \\
    & = 
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
\frac{  1 }{ \sqrt{ \theta_{20} } } \phi(\frac{ a- \theta_{10} }{ \sqrt{ \theta_{20} } }) & \frac{ (a-\theta_{10}) }{ 2 \theta_{20}^3 } \phi(\frac{ a- \theta_{10} }{ \sqrt{ \theta_{20} } }) & -1 & 0 \\
1 & \frac{ 1 }{ 2 \sqrt{ \theta_2 } } \Phi(p)^{-1}& 0 & -1
\end{bmatrix}
\begin{bmatrix}
\mu_2 & \mu_3 & 0 & 0 \\
\mu_3 & \mu_4 - \sigma^4 & 0 & 0\\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 
\end{bmatrix}
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
\frac{  1 }{ \sqrt{ \theta_{20} } } \phi(\frac{ a- \theta_{10} }{ \sqrt{ \theta_{20} } }) & \frac{ (a-\theta_{10}) }{ 2 \theta_{20}^3 } \phi(\frac{ a- \theta_{10} }{ \sqrt{ \theta_{20} } }) & -1 & 0 \\
1 & \frac{ 1 }{ 2 \sqrt{ \theta_2 } } \Phi(p)^{-1}& 0 & -1
\end{bmatrix}^T \\
    & = \left[
\begin{array}{cccc}
 \text{$\mu_2$} & \text{$\mu_3$} & 0 & 0 \\
 \text{$\mu_3$} & \text{$\mu_4$}-\sigma ^2 & 0 & 0 \\
 \frac{\phi \cdot  \left(a \text{$\mu_3$}-\mu  \text{$\mu_3$}+2 \text{$\mu_2$} \sigma ^5\right)}{2 \sigma ^6} & \frac{\phi  \cdot  \left(a \left(\text{$\mu_4$}-\sigma ^2\right)+\mu  \left(\sigma ^2-\text{$\mu_4$}\right)+2 \text{$\mu_3$} \sigma ^5\right)}{2 \sigma ^6} & 0 & 0 \\
 \text{$\mu_2$}+\frac{\text{$\mu_3$} \cdot  \text{$\phi_2$}}{2 \sqrt{\sigma ^2}} & \text{$\mu_3$}+\frac{\text{$\phi_2$} \cdot  \left(\text{$\mu_4$}-\sigma ^2\right)}{2 \sqrt{\sigma ^2}} & 0 & 0 \\
\end{array}
\right]\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
\frac{  1 }{ \sqrt{ \theta_{20} } } \phi(\frac{ a- \theta_{10} }{ \sqrt{ \theta_{20} } }) & \frac{ (a-\theta_{10}) }{ 2 \theta_{20}^3 } \phi(\frac{ a- \theta_{10} }{ \sqrt{ \theta_{20} } }) & -1 & 0 \\
1 & \frac{ 1 }{ 2 \sqrt{ \theta_2 } } \Phi(p)^{-1}& 0 & -1
\end{bmatrix}^T \\ 
    & = \small \left[
\begin{array}{cccc}
 \text{$\mu_2$} & \text{$\mu_3$} & \frac{\phi \cdot  \left(a \text{$\mu_3$}-\mu  \text{$\mu_3$}+2 \text{$\mu_2$} \sigma ^5\right)}{2 \sigma ^6} & \text{$\mu_2$}+\frac{\text{$\mu_3$} \text{$\phi_2$}}{2 \sqrt{\sigma ^2}} \\
 \text{$\mu_3$} & \text{$\mu_4$}-\sigma ^2 & \frac{\phi \cdot \left(a \left(\text{$\mu_4$}-\sigma ^2\right)+\mu  \left(\sigma ^2-\text{$\mu_4$}\right)+2 \text{$\mu_3$} \sigma ^5\right)}{2 \sigma ^6} & \text{$\mu_3$}+\frac{\text{$\phi_2$}\cdot \left(\text{$\mu_4$}-\sigma ^2\right)}{2 \sqrt{\sigma ^2}} \\
 \frac{\phi \cdot \left(a \text{$\mu_3$}-\mu  \text{$\mu_3$}+2 \text{$\mu_2$} \sigma ^5\right)}{2 \sigma ^6} & \frac{\phi \cdot \left(a \left(\text{$\mu_4$}-\sigma ^2\right)+\mu  \left(\sigma ^2-\text{$\mu_4$}\right)+2 \text{$\mu_3$} \sigma ^5\right)}{2 \sigma ^6} & \frac{\phi ^2 \left(4 \text{$\mu_3$} \sigma ^5 (a-\mu )+\text{$\mu_4$} (a-\mu )^2-\sigma ^2 (a-\mu )^2+4 \text{$\mu_2$} \sigma ^{10}\right)}{4 \sigma ^{12}} & \frac{\phi \cdot \left(\text{$\mu_4$} \text{$\phi_2$} (a-\mu )+\sigma ^2 \text{$\phi_2$}\cdot (\mu -a)+2 a \text{$\mu_3$} \sqrt{\sigma ^2}-2 \mu  \text{$\mu_3$} \sqrt{\sigma ^2}+4 \text{$\mu_2$} \sqrt{\sigma ^2} \sigma ^5+2 \text{$\mu_3$} \sigma ^5 \text{$\phi_2$}\right)}{4 \sigma ^6 \sqrt{\sigma ^2}} \\
 \text{$\mu_2$}+\frac{\text{$\mu_3$} \text{$\phi_2$}}{2 \sqrt{\sigma ^2}} & \text{$\mu_3$}+\frac{\text{$\phi_2$} \cdot\left(\text{$\mu_4$}-\sigma ^2\right)}{2 \sqrt{\sigma ^2}} & \frac{\phi \cdot (a-\mu ) \left(2 \text{$\mu_3$} \sqrt{\sigma ^2}+\text{$\phi_2$} \left(\text{$\mu_4$}-\sigma ^2\right)\right)+2 \sigma ^5 \phi \cdot  \left(2 \text{$\mu_2$} \sqrt{\sigma ^2}+\text{$\mu_3$} \text{$\phi_2$}\right)}{4 \sigma ^6 \sqrt{\sigma ^2}} & \text{$\mu_2$}+\frac{\text{$\mu_3$} \text{$\phi_2$}}{\sqrt{\sigma ^2}}+\frac{1}{4} \text{$\phi_2$}^2\cdot  \left(\frac{\text{$\mu_4$}}{\sigma ^2}-1\right) \\
\end{array}
\right]
\end{align}
$$
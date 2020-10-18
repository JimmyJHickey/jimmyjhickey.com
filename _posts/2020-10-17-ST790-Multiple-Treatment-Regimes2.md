---
layout: post
comments: false
title: Example Problems on Multiple Treatment Regimes
description: ST790 Homework 3 on Multiple Treatment Regimes
tags: ST790 Treatment Regimes Statistics
category: ST790-Dynamic-Treatment-Regimes
---

* Do not remove this line (it will not be displayed)
{:toc}

Analytical Problems

# 1

## a
We can proceed as we did in slide 351 of lecture 6.

$$
\begin{align}
E(Y^*(a_1, a_2) | \overline{ X }_2^* = \overline{ x }_2) & = E(Y | \overline{ X }_2 = \overline{ x}_2, A_1 = a_1) & \text{SUTVA} \\
    & = E(Y | \overline{ X}_2 = \overline{ x }_2, A_1 = a_1, A_2 = a_2) & \text{SRA} \\
    & = Q_2(\overline{ X }_2, \overline{ a }_2)
\end{align}
$$

Recall that $a_2 = \{0,1 \}$. Thus,

$$
\begin{align}
d_2^{opt}  = \arg \max_{a_2 \in \psi_2(h_2)} Q_2(\overline{ X }_2, \overline{ a }_2) & = 
\begin{cases}
a_2 = 1 & \text{if } \beta_{27}^0 + \beta_{28}^0 x_2 + \beta_{29}^0 a_1 > 0 \\
a_2 = 0 & \text{otherwise}
\end{cases} \\
& = I(\beta_{27}^0 + \beta_{28}^0 x_2 + \beta_{29}^0 a_1 > 0)
\end{align}
$$


## b
We can now plug this into equation 6.5 to get the maximum expected outcome.

$$
\begin{align}
V_2(h_2) & = \max_{a_2 \in \psi_2(h_2)} E(Y^*(a_1, a_2) | \overline{ X }^*_2(a_1) = \overline{ x }_2) \\
    & = Q_2(d_2^{opt}) \\
    & = \beta_{21}^0 + \beta_{22}^0 x_1 + \beta_{23}^0 a_1 +\beta_{24}^0 x_1 a_1 + \beta_{25}^{0} x_2 + \beta_{26}^0 x_2^2 + I(\beta_{27}^0 + \beta_{28}^0 x_2 + \beta_{29}^0 a_1 > 0)(\beta_{27}^0 + \beta_{28}^0 x_2 + \beta_{29}^0 a_1)
\end{align}
$$



## c
With our value function from step 2, we can proceed to find $Q_1$ is in slide 372 of chapter 6.

$$
\begin{align}
Q_1(h_1, a_1) & = Q_1(x_1, a_1) \\
    & = E(V_2(x_1, X_2, a_1) | X_1 = x_1, A_1 = a_1) \\
    & = E\Big[ \beta_{21}^0 + \beta_{22}^0 x_1 + \beta_{23}^0 a_1 +\beta_{24}^0 x_1 a_1 + \beta_{25}^{0} x_2 + \beta_{26}^0 x_2^2 \\
    & + I(\beta_{27}^0 + \beta_{28}^0 x_2 + \beta_{29}^0 a_1 > 0)(\beta_{27}^0 + \beta_{28}^0 x_2 + \beta_{29}^0 a_1) |X_1 = x_1, A_1 = a_1\Big] \\
    & = \beta_{21}^0 + \beta_{22}^0 x_1 + \beta_{23}^0 a_1 +\beta_{24}^0 x_1 a_1 \\
    & + \beta_{25}^0 E\Big[X_2 |X_1 = x_1, A_1 = a_1\Big] \\
    & + \beta_{26}^0 E\Big[  X_2^2 |X_1 = x_1, A_1 = a_1\Big] \\
    & + \beta_{27}^0 E\Big[ I(\beta_{27}^0 + \beta_{28}^0 X_2  + \beta_{29}^0 a_1 > 0) |X_1 = x_1, A_1 = a_1\Big] \\
    & + \beta_{29}^0 a_1 E\Big[ I(\beta_{27}^0 + \beta_{28}^0 X_2 + \beta_{29}^0 a_1 > 0) |X_1 = x_1, A_1 = a_1\Big] \\
    & + \beta_{28}^0  E\Big[ I(\beta_{27}^0 + \beta_{28}^0 X_2 + \beta_{29}^0 a_1 > 0)X_2|X_1 = x_1, A_1 = a_1\Big]\\
\end{align}
$$
    
Now we can take the expectations! Take $I_1 =I(\beta_{27}^0 + \beta_{28}^0 x_2 + \beta_{29}^0 a_1 > 0) $
    
$$
\begin{align}
E\Big[X_2 |X-1 = x_1, A_1 = a_1\Big] & = \mu_1(x_1, a_1; \psi_1^0)\\
    & = \psi_{11}^0 + \psi_{12}^0 x_1 + \psi_{13}^0 a_1 + \psi_{14}^0 x_1 a_1 \\ \\
E\Big[  X_2^2 |X_1 = x_1, A_1 = a_1\Big] & = E(X_2 | X_1, A_1)^2 + \text{Var}(  X_2 | X_1, A_1 ) \\
    & = (\psi_{11}^0 + \psi_{12}^0 x_1 + \psi_{13}^0 a_1 + \psi_{14}^0 x_1 a_1)^2 + (\sigma_1^0)^2 \\ \\
 E\Big[ I_1 |X_1 = x_1, A_1 = a_1\Big]    & =  P(I_1) \\
    & = P\Big[\beta_{27}^0 + \beta_{28}^0 X_2 + \beta_{29}^0 a_1 > 0 |X_1 = x_1, A_1 = a_1\Big] \\
    & = \int_{\frac{ -(\beta_{27}^0 + \beta_{29}^0 a_1) }{ \beta_{28}^0 }}^{\infty} \frac{ \phi(x_2) - \mu_1 }{ \sigma^0_1 }  dx_2  \\ \\
 E\Big[ I_1 X_2 |X_1 = x_1, A_1 = a_1\Big]  & = E( E(I_1 X_2  | I_1) | X_1, A_1) \\
    & = E(I_1 E(X_2 | I_1) | X_1, A_1) \\
    & = 1 \cdot E(X_2 | I_1 = 1) P(I_1 = 1) + 0 \cdot E(X_2 | I_1 = 0 ) P(I_1 = 0) \\
    & = E(X_2 | I_1 = 1) P(I_1 = 1) \\
    & = \int_{\frac{ -(\beta_{27}^0 + \beta_{29}^0 a_1) }{ \beta_{28}^0 }}^{\infty} x_2 \cdot \frac{ \phi(x_2) - \mu_1 }{ \sigma^0_1 }  dx_2 
    \times \int_{\frac{ -(\beta_{27}^0 + \beta_{29}^0 a_1) }{ \beta_{28}^0 }}^{\infty} \frac{ \phi(x_2) - \mu_1 }{ \sigma^0_1 }  dx_2
\end{align}
$$

## d
### i



### ii



## e


## f
### i



### ii


### iii


### iv


## g

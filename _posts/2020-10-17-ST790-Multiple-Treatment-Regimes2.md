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
    
Now we can take the expectations! Take
    
$$
\begin{align}
E\Big[X_2 |X-1 = x_1, A_1 = a_1\Big] & = \mu_1(x_1, a_1; \psi_1^0)\\
    & = \psi_{11}^0 + \psi_{12}^0 x_1 + \psi_{13}^0 a_1 + \psi_{14}^0 x_1 a_1 \\ \\
E\Big[  X_2^2 |X_1 = x_1, A_1 = a_1\Big] & = E(X_2 | X_1, A_1)^2 + \text{Var}(  X_2 | X_1, A_1 ) \\
    & = (\psi_{11}^0 + \psi_{12}^0 x_1 + \psi_{13}^0 a_1 + \psi_{14}^0 x_1 a_1)^2 + (\sigma_1^0)^2
\end{align}
$$


Notice that $\beta\_{27}^0 + \beta\_{28}^0 x\_2 + \beta\_{29}^0 a\_1  \sim N(\beta\_{27}^0 + \beta\_{28}^0 \mu\_1(x\_1, a\_1 ; \psi^0\_1) + \beta\_{29}^0 a\_1 \| X\_1 = x\_1, A\_1 = a\_1$. To simplify notation, we will define


$$
\Omega = \frac{ (\beta_{27}^0 + \beta_{28}^0 x_2 + \beta_{29}^0 a_1) - (\beta_{27}^0 + \beta_{28}^0 \mu_1 + \beta_{29}^0 a_1)  }{ \sqrt{ (\beta_{28} \sigma_1^0)^2 } } , \zeta = - \frac{ \beta_{27}^0 + \beta_{28}^0 \mu_1 + \beta_{29}^0 a_1  }{ \sqrt{ (\beta_{28} \sigma_1^0)^2 } }.
$$

Now we can say

$$
\begin{align}
E\Big[ I(\Omega > \zeta) & (\beta_{27}^0 + \beta_{28}^0 \mu_1 + \beta_{29}^0 a_1 + H \sqrt{ (\beta_{28} \sigma_1^0)^2 } | X_1= x_1, A_1 = a_1 \Big] \\ 
    & = (\beta_{27}^0 + \beta_{28}^0 \mu_1 + \beta_{29}^0 a_1) E\Big[ I(\Omega > \zeta)  | X_1= x_1, A_1 = a_1 \Big] \\ 
    & + \sqrt{ (\beta_{28} \sigma_1^0)^2 } E\Big[ I(\Omega > \zeta)  H  | X_1= x_1, A_1 = a_1 \Big].
\end{align}
$$

Where $\Omega \|X_1, A_1 \sim N(0, 1)$. Now we can find these expectations.

$$
\begin{align}
E(I(\Omega > \zeta & |  X_1 , A_1))  = 1 - \Phi(\zeta) \\
    & = \Phi(-\zeta) \\ \\
E( I(\Omega > \zeta)  \cdot H & | X_1, A_1) = \int_{\zeta}^\infty x \frac{ 1 }{ \sqrt{ 2\pi } } e^{-\frac{ 1 }{2  } x^2} dx \\
    & = \int \frac{ 1 }{ \sqrt{ 2 \pi } } e^{-\frac{ 1 }{2  } u} 2 du \\
    & = \frac{ 1 }{ \sqrt{ 2 \pi} } e^{-\frac{ 1 }{ 2 } \zeta^2} \\
    & = \phi(\zeta)
\end{align}
$$

Bringing it all back together, we get the following expression for $Q_1$.

$$
\begin{align}
Q_1(h_1, a_1) & = \beta_{21}^0 + \beta_{22}^0 x_1 + \beta_[23]^0 a_1 + \beta_{24}^0 x_1 a_1 \\
    & + \beta_{25}^0 \cdot \mu_1 \\
    & + \beta_{26}^0 \cdot (\mu_1^2 + (\sigma_1^0)^2) \\
    & + (\beta_{27^0} + \beta_{28}^0 \mu_1 + \beta_{29} a_1) \Phi\Big( \frac{ \beta_{27}^0 + \beta_{28}^0 \mu_1 + \beta_{29}^0 a_1  }{ \sqrt{ (\beta_{28} \sigma_1^0)^2 } } \Big) \\
    & +\sqrt{ (\beta_{28} \sigma_1^0)^2 } \cdot  \phi \Big( \frac{ \beta_{27}^0 + \beta_{28}^0 \mu_1 + \beta_{29}^0 a_1  }{ \sqrt{ (\beta_{28} \sigma_1^0)^2 } } \Big)
\end{align}
$$

## d
### i
We can plug in number to our decision rule to get

$$
d_2^{opt}= \begin{cases}
I( -1 + 0.75 x_2 + 0.5 \cdot 1) = I(x_2 > \frac{ 2 }{ 3 }) & \text{if }a_1 = 1 \\
I( -1 + 0.75 x_2 + 0.5 \cdot 0) = I(x_2 > \frac{ 4 }{ 3 }) & \text{if } a_1 = 0 .
\end{cases}
$$


### ii
We can match terms between the $Q$ function given in the hint and the $Q$ function that we got in part (c). Thank goodness for Mathematica simplification!

$$
\begin{align}
\beta_{11}^0 & = \beta_{21}^0 + \beta_{25}^0 \psi_{11}^0 + \beta_{26}^0 (\sigma_1^0)^2 + \beta_{26}^0 (\psi_{11}^0)^2\\
    & + (\beta_{27}^0 + \beta_{28^0}) \Phi(\frac{ \beta_{27}^0 + \beta_{28}^0 \psi_{11}^0 }{ \beta_{28}^0 \sigma_1^0}) + \beta_{28}^0 \sigma_1^0 \phi(\frac{ \beta_{27}^0 + \beta_{28}^0 \psi_{11}^0 }{ \beta_{28}^0 \sigma_1^0}) \\
    & = 6.5 -0.25 \Phi( \frac{ -1 }{ 3 \sqrt{ 2 } }) + \frac{ 3  }{2 \sqrt{ 2 } } \phi(\frac{ 1 }{ 3 \sqrt{ 2 } } )\\ \\
\beta_{12}^0 & = \beta_{22}^0 + \beta_{25}^0 \psi_{12}^0 + \beta_{26}^0 2 \psi_{11}^0 \psi_{12}^0 + \beta_{26}^0 (\psi_{12}^0)^2 \\
    & - (\beta_{27}^0 + \beta_{28}^0 \psi_{11}^0) \Phi(\frac{ \beta_{27}^0 + \beta_{28}^0  \psi_{11}^0}{ \beta_{28^0} \sigma^0_1 }) + (\beta_{27}^0 + \beta_{28}^0 (\psi_{11}^0 + \psi_{12}^0)) \Phi(\frac{ \beta_{27}^0 + \beta_{28}^0  (\psi_{11}^0+\psi_{12}^0)}{ \beta_{28^0} \sigma^0_1 }) \\
    & - \beta_{28}^0 \sigma_1^0 \phi(-\frac{ \beta_{27}^0 + \beta_{28}^0  \psi_{11}^0}{ \beta_{28^0} \sigma^0_1 }) + \beta_{28}^0 \sigma^0_1 \psi(-\frac{ \beta_{27}^0 + \beta_{28}^0  (\psi_{11}^0+\psi_{12}^0)}{ \beta_{28^0} \sigma^0_1 }) \\
    & = \frac{ 3 }{ 2 } + \frac{ 1 }{ 4 } \Phi(- \frac{ 1 }{ 3 \sqrt{ 2 } }) + \frac{ 1 }{ 8 } \Phi(\frac{ 1}{ 6 \sqrt{ 2 } }) - \frac{ 3 }{ 2 \sqrt{ 2 } } \phi(\frac{ 1 }{ 3 \sqrt{ 2 } }) + \frac{ 3 }{ 2 \sqrt{ 2 } } \phi(\frac{ 1 }{ 6 \sqrt{ 2 } })   \\ \\
\beta_{13}^0 & = \beta_{23}^0 + \beta_{25}^0 \psi_{13}^0 + \beta_{26}^0 2 \psi_{11}^0 \psi_{13}^0 + \beta_{26}^0 (\psi_{13}^0)^2 \\
    & - (\beta_{27}^0 + \beta_{28}^0 \psi_{11}^0) \Phi(\frac{ \beta_{27}^0 + \beta_{28}^0  \psi_{11}^0}{ \beta_{28^0} \sigma^0_1 }) \\
    & + (\beta_{27}^0 + \beta_{28}^0  (\psi_{11}^0 + \psi_{13}^0) + \beta_{29}^0) \Phi(\frac{ \beta_{27}^0 + \beta_{28}^0  (\psi_{11}^0 + \psi_{13}^0) + \beta_{29}^0}{ \beta_{28^0} \sigma^0_1 }) \\
    & - \beta_{28}^0 \sigma_1^0 \phi(\frac{ \beta_{27}^0 + \beta_{28}^0  \psi_{11}^0}{ \beta_{28^0} \sigma^0_1 }) \\
    & + \beta_{28}^0 \sigma_1^0 \phi(\frac{ \beta_{27}^0 + \beta_{28}^0  (\psi_{11}^0 + \psi_{13}^0) + \beta_{29}^0}{ \beta_{28^0} \sigma^0_1 }) \\
    & = -1.2125 + 0.25 \Phi(- \frac{ 1 }{ 3 \sqrt{ 2 } }) - \frac{ 5 }{ 16 } \Phi(\frac{ 5 }{ 12 \sqrt{ 2 } }) - \frac{ 3 }{ 2 \sqrt{ 2 } } (\phi(\frac{ 1 }{ 3 \sqrt{ 2 } }) - \phi(\frac{ 5 }{ 12 \sqrt{ 2 } })) \\ \\
\beta_{14}^0 & = \beta_{24}^0 + \beta_{25}^0 \psi_{14}^0 + \beta_{26}^0 ( (\psi_{14}^0)^2 + 2 \psi_{11}^0 \psi_{14}^0 + 2 \psi_{12}^0\psi_{13}^0 + 2 \psi_{12}^0 \psi_{14}^0 + 2 \psi_{13}^0 \psi_{14}^0) \\
    & + (\beta_{27}^0 + \beta_{28}^0  \psi_{11}^0) \Phi(\frac{ \beta_{27}^0 + \beta_{28}^0  \psi_{11}^0}{ \beta_{28^0} \sigma^0_1 }) \\
    & + (\beta_{27}^0 + \beta_{28}^0  (\psi_{11}^0 + \psi_{12}^0 + \psi_{13}^0 + \psi_{14}^0) + \beta_{29}^0) \Phi(\frac{ (\beta_{27}^0 + \beta_{28}^0  (\psi_{11}^0 + \psi_{12}^0 + \psi_{13}^0 + \psi_{14}^0) + \beta_{29}^0)}{ \beta_{28^0} \sigma^0_1 }) \\
    & - (\beta_{27}^0 + \beta_{28}^0  (\psi_{11}^0 + + \psi_{13}^0) + \beta_{29}^0) \Phi(\frac{ (\beta_{27}^0 + \beta_{28}^0  (\psi_{11}^0 + \psi_{13}^0) + \beta_{29}^0)}{ \beta_{28^0} \sigma^0_1 }) \\
    & - (\beta_{27}^0 + \beta_{28}^0  (\psi_{11}^0 + \psi_{12}^0) ) \Phi(\frac{ (\beta_{27}^0 + \beta_{28}^0  (\psi_{11}^0 + \psi_{12}^0 ) )}{ \beta_{28^0} \sigma^0_1 }) \\
    & + \beta_{28}^0 \sigma_1^0 \phi(\frac{ \beta_{27}^0 + \beta_{28}^0  \psi_{11}^0}{ \beta_{28^0} \sigma^0_1 }) \\
    & + \beta_{28}^0 \sigma_1^0 \phi(\frac{ (\beta_{27}^0 + \beta_{28}^0  (\psi_{11}^0 + \psi_{12}^0 + \psi_{13}^0 + \psi_{14}^0) + \beta_{29}^0)}{ \beta_{28^0} \sigma^0_1 }) \\
    & - \beta_{28}^0 \sigma_1^0\phi(\frac{ (\beta_{27}^0 + \beta_{28}^0  (\psi_{11}^0 + \psi_{13}^0) + \beta_{29}^0)}{ \beta_{28^0} \sigma^0_1 }) \\
    & - \beta_{28}^0 \sigma_1^0 \phi(\frac{ (\beta_{27}^0 + \beta_{28}^0  (\psi_{11}^0 + \psi_{12}^0 ) )}{ \beta_{28^0} \sigma^0_1 }) \\
    & = 0.3125 - \frac{ 1 }{ 4 } \Phi(-\frac{ 1 }{ 3 \sqrt{ 2 } }) + \frac{ 1 }{ 4 } \Phi(\frac{ 1 }{ 3 \sqrt{ 2 } }) + \frac{ 5 }{ 16 } \Phi(- \frac{ 5 }{ 12 \sqrt{ 2 } }) - \frac{ 1 }{ 8 } \Phi(\frac{ 1 }{ 6 \sqrt{ 2 } }) + \frac{ 3 }{ 2 \sqrt{ 2 } } \Big( \phi(\frac{ 1 }{ 3 \sqrt{ 2 } }) + \phi(\frac{ -1 }{ 3 \sqrt{ 2 } }) - \phi(- \frac{ 5 }{ 12 \sqrt{ 2 } }) - \phi(\frac{ 1 }{ 6 \sqrt{ 2 } }) \Big)
 \end{align}
$$


## e
$$
\begin{align}
Q_1(x_1, a_1)&  = 6.8098 + 1.6787 x_1 - 1.2372 a_1 + 0.4085 x_1 a_1 \\
d_1^{opt} & = I(- 1.2372 + 0.4085 x_1>0) \\
    & = I(x_1>3.02815) \\
    & = 0 & \text{since } x = \{0 , 1\} \\
V_1(h_1) & = 6.8098 + 1.6787 x_1 + (- 1.2372  + 0.4085 x_1) I(x_1>3.02815) \\
    & = 6.8098 + 1.6787 x_1 \\
V(d^{opt}) & = E(6.8098 + 1.6787 x_1) \\
    & = 6.8098 + 1.6787 \cdot 0.5 \\
    & = 7.64915
\end{align}
$$

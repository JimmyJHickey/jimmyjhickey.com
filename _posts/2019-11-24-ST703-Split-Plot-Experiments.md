---
layout: post
comments: false
title: Example Problems on Split Plot Experiments
description: ST703 Homework 10 on Split Plot Experiments
tags: ST703 SAS Split-Plot-Experiments Examples Statistics
---

Problems: 1, 2, 3, 4

* Do not remove this line (it will not be displayed)
{:toc}

# 1
**An experiment evaluates the taste of three brands of ice cream under different storage conditions. The experiment calls for 12 coolers to be randomized to the 3 brands (4 coolers per brand). Within each cooler, there is room for three half-gallon cartons of ice cream, all from the same brand. One carton was sampled at random at the end of one day, then at the end of one week and then one month. Each carton was evaluated for flavor by a panel of tasters. These panel scores can be found in "icecream.dat" (or also "storage.dat") on the course webpage.**


## a.
**This is a split-plot experiment. What are the whole plot units?**


## b.
**What is/are the whole plot factor(s)?**



## c.
**What is/are the sub plot factor(s)?**



## d.
**Test for an interaction between storage time and brand. (Use $\alpha = 0.05$.)**




## e.
**Test for main effects of storage time. Carry out pairwise comparisons among the three storage time tastes, using a Bonferroni correction to control the exptwise error rate at .05.**



## f.
**Test for main effects of brand. Report the standard error on any pairwise difference among brands.**



## g.
**Suppose you had averaged the data over storage time, reducing the total number of observations from 36 down to 12. Would the F-ratio for brand effect in a one-way ANOVA be the same as the F-ratio from part (f)? Try it and see.**





# 2
**Consider an experiment like the one described in 1.), with $a$ levels of a between-plots factor $A$, $n$ plots per level of $A$m for a total of $nA$ plots and $b$ levels of a within-plots factor $B$. Let $Y_{ijk}$ denote the measurement at level $j$ of factor $B$, from the $k^{th}$ whole plot randomized to level $i$ of factor $A$. The model is then**

$$
Y_{ijk} = \mu + \alpha_i + S_{k(i)} + \beta_j + (\alpha \beta)_{ij} + E_{ijk}
$$


**where $S_{k(i)} \stackrel{iid}{\sim} n(0, \sigma^2_s)$ and**

**$E_{ijk} \stackrel{iid}{\sim} n(0, \sigma^2)$, independently of $S_{k(i)}$.**

## a.
**Derive the standard error for a difference across levels of ...**

### i.
**$B$, for a fixed level of $A$, for example, $\bar{Y}_{12+} - \bar{Y}_{11+}$.**




### ii.
**$B$, after averaging ober levels $A$, for example, $\bar{Y}_{+2+} - \bar{Y}_{+1+}$.**




### iii.
**$A$, for a fixed level of $B$, for examples $\bar{Y}_{21+} - \bar{Y}_{11+}$.**




### iv.
**$A$, after averaging over levels of $B$, for example $\bar{Y}_{2++} - \bar{Y}_{1++}$.**



### v.
**$A$, and across levels of $B$, for example $\bar{Y}_{22+} - \bar{Y}_{11+}$.**



## b.
**For each of the above, construct an estimate of the standard error using linear combinations of $MS$ terms and indicate whether or not an approximation for $df$ is required.**






# 3
**An experiment investigates three formulations of a diet for rats. The response is absorption of a certain chemical by the kidneys. The design involves four litters, each with three rats (a total of 12 rats). Within each litter, rats are randomized to diet formulation. Another factor of interest is the method of measuring this absorption. There are three methods up for investigation, with differences that may be subtle compared to diet formulation effects. So, three specimens are sampled from each rat, and these specimens are randomized to the methods. Data are available as "absorb.dat".**


## a.
**Identify the name of the experimental design used here.**



## b.
**Propose a statistical model.**




## c.
**Sketch an ANOVA table, with columns for source, df and EMS.**



## d.
**Test for an interaction between formulation and method. Use $\alpha = 0.05$.**



## e.
**Test ($\alpha = 0.05$) for simple method effects separately at each level of formulation. (It may be helpful to use the slice option for the lsmeans statement.)**



## f.
**Test for the simple effects of formulation using method 3. Carry out all three pairwise comparisons among formulations using this method, identifying any significant differences.**


# 4
**A food scientist studies the effects of three factors on the viscosity of ice cream:**

* $A$: temperature (2 levels)
* $B$: pressure (2 levels)
* $C$: recipe (3 levels).


**The production equipment is such that temperature and pressure must be held constant for the entire day. The experiment is conducted over 8 days, which are randomly assigned to the four treatment combinations of temperature and pressure. Three batches are produced each day, one of each recipe, for a total of 24 batches. Each batch will have a single viscosity measurement taken. Pertinent SAS code and output are given on the next page.**



## a.
**Propose a mixed model for the viscosity measurements with random day effects. Take the effects of all three treatment factors, $A, B, C$ and their first and second order interactions to be fixed. Assume normal distributions for all random effects.**




## b.
**Carry out $F$-tests for the four hypotheses listed below. For each, report the $F$-ratio, the
associated degrees of freedom, a conclusion regarding the hypothesis, and where available
from the output, a $p$-value**


$$
\begin{array}{l}
\text{Hypothesis} \\ \hline
\text{No } 2^{nd} \text{ order interaction between temperature, pressure and recipe} \\
\text{No } 1^{st} \text{ order interaction between temperature and pressure} \\
\text{No main effect of pressure} \\
\text{No main effect of recipe} \\ \hline
\end{array}
$$



## c.
**Estimate the variance component for the random day effect.**




## d.
**Report an estimate and standard error for**


### i.
**the marginal mean of recipe 1**



### ii.
**the difference between recipes 1 and 2**



### iii.
**the marginal mean of temperature 1**



### iv.
**the difference between tempeartures 1 and 2.**




![SAS output](../img/post_img/2019-11-24-ST703-Split-Plot-Experiments/4-SAS-Output.png)
---
layout: post
comments: false
title: Example Problems on Random Effects
description: ST703 Homework 9 on Random Effects
tags: ST703 SAS Random-Effects Examples Statistics
---

Problems: 1, 2, 3, 4

* Do not remove this line (it will not be displayed)
{:toc}

# 1
**Assume that the one-way random-effects model in Box 14.1 is appropriate for the protein content data in Exercise 14.1.**


## a.
**Construct the ANOVA table showing the mean squares and their expected values.**



## b.
**On the basis of the ANOVA table constructed in (a), would it be reasonable to conclude that there is a significant plant-to-plant variation in the protein content of seeds produced by the $F_3$ generation plants?**



## c.
**Estimate the components of variance, and comment on their relative magnitudes.**



## d.
**Calculate an estimate of the coefficient of variation of the protein content measurements, and comment of its value.**




## e.
**Construct a 95% confidence interval for the proportion of the varaince of the measured protein content values that can be ascribed to plant-to-plant varaition. Interpret this interval.**



## f.
**On the basis of the observed data, would it be reasonable to conclude that the average protein content of seeds produced in the $F_3$ genreation is more than 40%?**




# 2
**To see how the effect of diet supplements on the weights of wethers varied with environmental conditions, a study was conducted in four randomly selected locations; each location represented a randomly selected environment. The experimeners randomly assigned 24 crossbred wethers to the four locations in such a way that each location had six wethers. Within each location, the animals were randomized to receive three diets, with two animals on each diet. Teh four-week weight gains in wethers are as follows:**


$$
\begin{array}{c c c c c}
	\hline
	\text{Died} & & \rlap{\text{Location}} & & \\
	& 1 & 2 & 3 & 4 \\ \hline
	1 & 2.10 & 2.02 & 2.16 & 1.98 \\
	& 2.32 & 2.04 & 2.18 & 1.86 \\ \hline
	2 & 2.24 & 2.30 &2.22 & 1.64 \\
	& 2.22 & 2.12 & 2.18 & 1.73  \\ \hline
	3 & 2.27 & 2.14 & 2.26 & 1.83 \\
	& 2.24 & 2.17 & 2.21 & 1.89 \\ \hline
\end{array}
$$


## a.
**Write a suitable ANOVA model for the data. Explain all the terms in your model.**




## b.
**Obtain estimates of the components of the variance due to location, interaction between location and diet, and error. Interpret the results.**



## c.
**Construct the appropriate ANOVA table for the data and perform all ANOVA $F$-tests. Interpret the results.**




## d.
**Construct a 90% confidnce interval for the true mean weight gain of animals fed diet 1 in a randomly selected location.**




## e.
**Construct a set of Bonferonni 90% simultaneous confidence intervals for all possible difference between diet means. Interpret the intervals.**

# 3
**To estimate the average cost of hospital stay, a random sample of four hospitals (factor $A$) was selected from the population of all hospitals in a large region. For each hospital, patient admission records for three randomly selected days (factor $B$) were examined. Two patients were selected at random from all the patients admitted on each day to each hospital. On the basis o the average daily hospital bill (in dollars) for each selected patient, the following ANOVA table was constructed:**


$$
\begin{array}{c c}
\hline
\text{Source} & \text{Mean square} \\ \hline
A \text{ (hospitals)} & 2240.05 \\
B(A) \text{ (days in hospital)} & 312.32 \\
\text{Error (patients)} & 122.02 \\ \hline
\end{array}
$$

**The average of all 24 patient bills was $380.24.**

## a.
**Estimate the components of variability in the daily hospital cost due to difference between hospitals, due to differences between days, and due to differences between patients. Calculate the proportion of total variability in daily costs due to each of these sources. Comment on the results.**



## b.
**Construct a 95% confidence interval for the expected daily cost for a patient admitted to one of the hospitals in the region.**




## c.
**Construct a 95% lower confidence interval for the expected daily cost to a patient admitted to one of the hospitals in the region. Interpret the result.**

# 4
**In an experiment to compare the serum amylase values determined be four laboratories, 160 serum specimens with a known amylase value of 4.2 were used. The specimens were randomized to 16 technicians (four from each lab) in such a way that each technician was assigned ten specimens. The technicians made independent measurements of the amylase values of the specimens assigned to them. On the basis of the results, the following ANOVA table was constructed:**


$$
\begin{array}{c c}
\hline
\text{Source} & \text{Mean square} \\ \hline
A \text{ (labs)} & 9.07 \\
B(A) \text{ (technician)} & 1.63 \\
\text{Error (Specimens)} & 1.02 \\ \hline
\end{array}
$$

**The totals for each lab may be summarized as follows:**

$$
\begin{array}{c c c c c c}
\hline
\text{Lab} & 1 & 2 & 3 & 4 & \text{Total} \\ \hline
\text{Total} & 152 & 144 & 184 & 176 & 656 \\ \hline
\end{array}
$$

## a.
**Write a model for the data on the assumption that the four technicians in each lab constitute a random sample from the population of technicians working in that lab. Explain all the terms in the model.**



## b.
**Perform a pairwise multiple comparison of the mean values for the four labs. Interpret the result.**




## c.
**Let $\sigma^2_{B(A)}$ and $\sigma^2$ denote, respectively, the components of variance due to differences betweem technicians and due to differences between specimens. Compute an estimate of the quantity**


$$
\rho = \frac{ \sigma^2_{B(A)} }{  \sigma^2_{B(A)} + \sigma^2 }.
$$

**What conclusions can be drawn from the estiamted value of $\rho$?**



## d.
**Let $\mu_i$ denote the true mean mean amylase values for lab $i$ ($i = 1, \dots , 4$). Construct a set of 90% simultaneous confidence intervals for the contrasts:$**

$$
	\begin{align}
		\theta_1 & = \mu_1 - \mu_2 \\
		\theta_2 & = \frac{ 1 }{ 2 }(\mu_1 + \mu_2) - \frac{ 1 }{ 2 }(\mu_3 + \mu_4) \\
		\theta_3 & = \mu_3 - \mu_4.
	\end{align}
$$

**Interpret the intervals.**
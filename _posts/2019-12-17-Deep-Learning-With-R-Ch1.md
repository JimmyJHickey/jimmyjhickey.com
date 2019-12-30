---
layout: post
comments: false
title: Notes on Deep Learning with R Chapter 1
description: Chapter 1 - What Is Deep Learning?
tags: Statistics Deep-Learning-With-R Chollet Allaire
---

These are my notes on Chapter 1 of _Deep Learning with R_ by Chollet and Allaire.


* Do not remove this line (it will not be displayed)
{:toc}


# Deep Learning $\subset$ Machine Learning $\subset$ Artificial Intelligence

The book defines Artificial Intelligence (AI) as "the effort to automate intellectual tasks normally performed by humans". AI includes machine learning and deep learning as well as many other applications. From the 1950s to the late 1980s, the approach to AI was to create a sufficiently large rule set that for a computer could followl; this is known as _symbolic AI_. This culminated in [expert systems](https://en.wikipedia.org/wiki/Expert_system). This approach worked well for very well defined problems, but was not applicable to larger, less well defined problems (e.g. image classification and speech recognition). This lead to the next advancement in AI: _machine learning_.

The concept of machine learning was introduced by Alan Turing's seminal paper _Computer Machinery and Intelligence_. It asks the question if a computer could go beyond "whatever we know how to order it to perform". In symbolic AI, humans provide a set of rules and the computer uses this to process data. In machine learning, humans provide data and the computer uses it to create a set of rules. These rules can then be further applied to new data.

To perform machine learning you need three things

1. _Input data points_ - These are what you will give your system to learn from. E.x. Images of houses with different types of roofs.
2. _Examples of expected output_ - This is what your system will try to predict from the data. E.x. What type of roof each input image has in words.
3. _A way to measure whether the algorithm is doing a good job_ - This criteria will be used to iteratively improve the system (this is the learning). As you run the system each time it will try to optimize its output to improve this measure.

Deep learning is a further subset of machine learning. The _deep_ comes from the amount of processing steps the system takes to go from input to output. These steps are often very simple individually, but combined can perform very well. One popular implementation of deep learning is neural networks.

# Deep Learning or Nah?
Deep learning may be powerful, but it is not the only machine learning method. It is important that you choose the right method to solve your particular problem.

## Probabilistic Modeling
The application of statistical principles to data analysis. Some examples include the Naive Bayes algorithms (using principles of Bayesian Statistics) and logistic regression (a simple approach often used to explore a classification task).

## Kernel Methods
We'll start with an example. A support vector machine (SVM) maps your data to a representation in a new high-dimensional space where a line (or plane/hyperplane) can be drawn in between the classes. Once this boundary is found (and often optimized), you can classify new data by simply checking which side of the boundary it is on. This group of classification algorithms are characterized by their use of the _kernel trick_. They classify by computing the distance between the pairs of points (in the new, output space) in your data rather than computing the coordinates of the points themselves. This is done by a _kernel function_ that finds the distance between your data in the original space and in the new space. 

Unfortunately kernel methods do not scale well to large data sets.

## Trees and Gradient Boosting
Decisions trees are a simple classification algorithm built much like a flow chart. Many simple questions are asked about a data point until a decision can be made and it is classified. To build on this, random forests and gradient boosting use many weak or simple models (such as many small decision trees) and ensemble (combine) the results to make an overall stronger prediction.

## Deep Learning
A major benefit to deep learning that is absent in the other methods is that it automated _feature engineering_. It can find hidden relationships in the data that go unfound even by ensembling other methods. This is because other methods are greedy, they try to optimize performance individually; while combining them may improve performance, it has diminishing returns. Deep learning creates relationships layer-by-layer which are updated as the network optimizes.
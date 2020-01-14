---
layout: post
comments: false
title: Notes on Deep Learning with R Chapter 3
description: Chapter 3 - Getting Started with Neural Networks
tags: Statistics Deep-Learning-With-R Chollet Allaire
category: Deep Learning With R
---

These are my notes on Chapter 3 of _Deep Learning with R_ by Chollet and Allaire.


* Do not remove this line (it will not be displayed)
{:toc}

# Anatomy of a Neural Network

## Layers

At its core, a layer is a function that takes in one or more tensors and outputs one or more tensors. It may be stateless, but often a layer will have one or more tensors of weights associated with it. These weights will be updated with the optimizer. Different layers are appropriate with different input tensors: 2-D tensors often use fully connected layers, 3-D tensors often use recurrent layers, and 4-D tensors often use convolutional layers.


## Models
A deep-learning model is a directed acyclic graph of layers. There are many different network topologies which define the _hypothesis space_.

## Loss functions and optimizers
The _loss function_ (_objective function_) represent a measure of success; it is the quantity that will be minimized during training. The _optimizer_ decides how the network will be updated based on the loss function; it often employs some form of stochastic gradient descent.

It is important to choose the best objective function for a given problem. Some examples: 

* Binary Classiciation - Binary Crossentropy
* Multi-Class Classification - Categorical Crossentropy
* Regression - Mean-Squared Error
* Sequence Learning - Connectionist Temporal Classification


# Binary Classification
The book goes through the keras IMDB dataset. The data is split into 50-50 train-test with 50% of each being negative and the other 50% being positive reviews.

Why split your data into training and test sets? Just because a model performs well on the training set does not mean that it will perform well on new data. At worst, your model could merely memorize the mapping between your training samples and their targets; this would seem to give a perfect predictive result, but it would be useless on new data.

With binary classification your input data is vectors and the labels are scalars.

# Multiclass Classification
Commonly we are trying to fit the data into individually, mutually exclusive classes. This is called single-label multiclass classification. If a datum can have more than one label, it would be a mutilabel, multiclass classification problem.

You should have at least as many nodes/dimensions per layer as you have classes you are trying to classify. That is, until the last layer where you perform the final predictions.

The categorical crossentropy loss function measures distance between two probability distributions. For example, the probability difference between the distribution of the output by the network and the true distribution. Minimizing this distance has the effect of training the network to get closer to the true labels. 

# Regression
In a regression problem we are predicting a continuous outcome.

It is important to do feature normalization: subtracting the mean and dividing by the standard deviation for each feature. This can be done in R with the `scale` function. Also notice that you should use the mean and standard deviation of the training set to scale the predictors of both the training and the test set.
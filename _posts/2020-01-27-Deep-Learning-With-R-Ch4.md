---
layout: post
comments: false
title: Notes on Deep Learning with R Chapter 4
description: Chapter 4 - Fundamentals of Machine Learning
tags: Statistics Deep-Learning-With-R Chollet Allaire
category: Deep Learning With R
---

These are my notes on Chapter 4 of _Deep Learning with R_ by Chollet and Allaire.


* Do not remove this line (it will not be displayed)
{:toc}

# Four Branches of Machine Learning

## Supervised Learning
This consists of learning to map input data to known targets given a set of examples. Along with regression and classification, supervised learning also contains sequence generation, syntax tree prediction, object detection, and image segmentation.


## Unsupervised Learning
This branch deals with finding interesting transformations of the input data **without** any help from the targets. It is useful in data visualization, data compression/ denoising, and to understand underlying structure/correlation in the data. It is an important step in understanding your data prior to performing supervised learning on it. Some use cases are dimensionality reduction and clustering.


## Self-supervised Learning
This is supervised learning without given targets. There is no human annotation. The annotations generally come from a heuristic algorithm. One example is autoencoders.


## Reinforcement Learning
An agent receives information about its environment and learns to choose actions that will maximize reward.


# Evaluating Machine Learning Models
We will examine strategies to minimize overfitting and maximize generalization of our models.


## Training, validation, and test sets
You train on the training data, evaluate your model's performance on the validation data, and then do one final test on the test data. We need a validation and a test set because each time we run our model we will be changing some _hyperparameters_ (configuration settings like number of layers and penalty). We change these to optimize performance, but this can lead to overfitting on the validation set (even though we don't train the model itself on it). This is why we still need yet another set of data, the test data, to ultimately assess our model. 

There are a few ways to perform this data splitting.


### Simple hold-out validation
Simply split the data into two pieces. Train on one and test on the other. 

If little data is available, then your validation and test sets may be too small to be representative. If different random shufflings of the data prior to splitting perform very differently, then there probably is not enough data.


### K-fold validation
Split your data into $K$ partitions of equal size. For each partition $i$, train on the other $K-1$ partitions and then evaluate performance on partition $i$. Average the result to get your final performance. You can use another partition for validation.


### Iterated K-fold validation with shuffling
This is useful when you have relatively little data and you need a precise model. It consist of doing K-fold validation as before, but shuffling the data each time before splitting. 


## Things to keep in mind
* _Data representativeness_ - You want your training and test set to be representative of the data at hand. One way to help with this is to shuffle your data before modeling.
*_Temporal data_ - If you are trying to predict future events from past events, do not shuffle your data. You will create a _temporal leak_ essentially training your model on data from the future. 
* _Redundancy in your data_ - If you have the same data twice try not to put them in the test and training sets as you will be testing on the same data you trained on. Training and validation sets should be disjoint.


# Data preprocessing, feature engineering, and feature learning
These are important steps to prepare the input data and targets before feeding them into a neural network.


## Data preprocessing for neural networks
This aims to make raw data more amenable to neural networks. Here are some strategies.


### Vectorization
All inputs and targets in a neural network must be tensors of floats or integers, so your data needs to be transformed into that format. Some translation scheme needs to be created to vectorize non-numerical data such as sound, images, and text.


### Value Normalization
It generally isn't safe to feed data that takes a large array of values into a neural network (unless all the values are in a specified range like 0-1, 100-200, etc). This can create large gradient updates that prevent the network from converging.  To fix this, scale values to be in the 0-1 range and try to scale features to be in roughly the same range. You can achieve this by normalizing each feature independently to have mean 0 and stdev 1. Remember to scale the data in both the training on the test using the *training set's* mean and stdev. In R this can be done with the `scale()` function.


## Handling missing values
One option is to put a 0 for missing values (assuming 0 isn't a meaningful response for that feature). The network will learn that this means missing. (Not sure if this is really a good idea.) Note that if there are no missing values in your train set but there are in your test set, you should artificially generate training samples with missing data. This can be done by copying some training sample and dropping some of the features.


## Feature engineering
_Feature engineering_ process of using your knowledge of the data and the machine learning algorithm to create new transformations of the input data before it goes into the model. Good features allow you to solve a problem using less computation resources and less data. 


# Overfitting and underfitting
Overfitting happens in every machine learning problem, so it is important to learn to deal with it.

The fundamental issue in machine learning is balancing between optimization (adjusting the model to improve performance) and generalization (how the model performs on new data). If you model is _underfit_ there is still progress to be made; the network hasn't modeled all the patterns in the training data. After a certain number of iterations on the training data the generalization stops improving and you start to overfit. 

Overfitting can be combatted by _regularization_. This is modulating the quantity of information that the model is allowed to store. Only allowing it to store a small number of patterns will force it to choose only the most prominent (via the optimization process). This will cut down on finding irrelevant patterns when overfitting.

## Reducing the network's size
This is the simplest way to prevent overfitting. However, if the network is too small performance will drop.  Test an array of different architectures (on your validation set, not your test set) and compare results. Generally you start small and get bigger until you hit diminishing returns on validation loss.

## Adding weight regularization
This forces weights to take small values which makes the distribution of weights more _regular_. It is done by adding to the loss function a cost associated with having large weights. Some examples are:

* _$L1$ regularization_ - The cost added is proportional to the absolute value of the weight coefficients (the $L1$ norm of the weights).
* _$L2$ regularization_ - The cost added is proportional to the $L2$ norm of the weights. This is the same as _weight decay_.

You can also use a combination of these schemes. These penalties are only added at training time.

## Adding dropout
_Dropout_, applied to a layer, consists of randomly dropping out (setting a number to 0) a number of output features of the layer during training. At test time, no units are dropped out; instead the layer's output values are scaled down by a factor equal to the dropout rate, to balance for the fact that more units are active than at training time.

Introducing noise to the output values of a layer can break up happenstance patterns that aren't significant (which the network would memorize if all neurons were present).


# The universal workflow of machine learning

## Defining the problem and assembling a dataset
First you must define your problem. 

* What will your input data be?
* What are you trying to predict?
	* Binary classification, regression , vector regression, etc.
* Is the data available or do we need to collect it?
* Do we need supervised learning? Unsupervised? Reinforcement?

It is hard to know if your input data will provide useful information in predicting your response. 

"Keep in mind that machine learning can only be used to memorize patterns that are present in your training data. You can only recognize what you've seen before. Using machine learning trained on past data to predict the future is making the assumption that the future will behave like tha past.  That often isn't the case."

## Choosing a measure of success
Accuracy? Precision and recall? Customer-retention?

This metric will guide you to the choice of a loss function: what your model will optimize. It should be directly aligned with the higher-level goals of making the model.

For balanced classification problems accuracy and area under the receiver operating characteristic curve (ROC AUC) are common metrics. For class imbalanced problems you can use precision and recall. For ranking or multilabel classification problems you can use mean average precision. You can also make your own custom metric.

## Deciding on an evaluation protocol
Once you have a measure of success, you need to monitor it to measure progress. This can be done with any of the previously described validation schemes.

## Preparing your data
Vectorize, scale, normalize, feature engineering, etc.

## Developing a model that does better than baseline
Note that if you can't beat a random baseline after multiple attempts, the answer to your problem may not be present in your current data set. 

There are three key choices when building your first working model.
* Last layer activation
* Loss function
* Optimization configuration

Here's a table to help

Problem Type | Last-layer activation | Loss function
--- | --- | ---
Binary classification | `sigmoid` | `binary_crossentropy`
||
Multiclass, single label | `softmax` | `categorical_crossentropy`
||
Multiclass multilabel | `sigmoid` | `binary_crossentropy` 
||
Regression to arbitrary values | None | `mse`
||
Regression to 0-1 | `sigmoid` | `mse` or `binary_crossentropy`

## Scaling up: developing a model that overfits
Is your model sufficiently powerful? Beef up your model until it starts overfitting.

1. Add layers
2. Make the layers bigger
3. Train for more epochs

Monitor training and validation loss and other desired metrics. Once your validation performance starts to degrade you have started overfitting and can scale back a bit.

## Regularizing your model and tuning your hyperparameters
Modify your model, train it, evaluate (on validation), repeat. Try the following things
* Add dropout.
* Try different architectures. Add/remove layers.
* Add $L1$ and/or $L2$ regularization.
* Try different hyperparameters (units per layer, learinng rate).
* Engineer new features.

Remember that every time you test against the validation set you get some information leak.
---
layout: post
comments: false
title: Notes on Deep Learning with R Chapter 2
description: Chapter 2 - The Mathematical Building Blocks of Neural Networks
tags: Statistics Deep-Learning-With-R Chollet Allaire
---

These are my notes on Chapter 2 of _Deep Learning with R_ by Chollet and Allaire.


* Do not remove this line (it will not be displayed)
{:toc}

# Intro to Neural Networks

In machine learning, a _category_ in a classification problem is called a _class_. Data points are called _samples_. The class associated with a sample is called a _label_. The network learns how to classify using _train_ samples to predict train classes. The actual classes of the train data is known; we use them with a _loss function_, _optimizer_, and _metrics monitoring_ to train our network. This is called the _compilation step_. The network is then applied to _test_ samples to predict unknown classes. We can check the accuracy (or any metric of our prediction) for our test and train samples. If the train sample has significantly better prediction than the test sample, we have _overfit_ our network. Its construction is too reliant on the train data.

Each layer of a network extracts _representations_ of the data fed into it. Many simple layers are chained together to refine the data and finally make a prediction.

# Data Representation

Most machine learning models use _tensors_ as their data structure. "Tensors are a generalization of vectors and matrices to an arbitrary number of dimensions". A scalar is a 0 dimensional tensor, a vector is 1 dimensional, and a matrix is 2 dimensional. A tensor has three key attributes.

* Number of axes (rank)
* Shape
* Data type

# Tensor Operations

Element-wise operations are applied independently to each element of the tensors. One example is element-wise addition of two tensors (with the same dimensions). This is highly parellelizable.

Some operations combine elements such as a dot product. This can return an output tensor with different dimensions from the input tensors.

Other operations change the order of elements while leaving the total number unchanged. One example is reshaping a tensor.

Neural networks are built of layers of simple tensor operations.

# Gradient-Based Optimization

A neural network runs many times to improve its performance. Each time it runs, it updates the _weights_ of each layer. These are initially set randomly and then adjusted (the _learning_ in "machine learning") using the training data and a feedback signal. This iterative process is called the _training loop_; it has the following steps.

1. Draw a batch of training samples `x` and corresponding targets `y`.
2. Run the network on `x` (a step called the _forward pass_) to obtain predictions `y_pred`.
3. Compute the loss of the network on the batch, a measure of the mismatch between `y_pred` and `y`.
4. Update all weights of the network in a way that slightly reduces the loss on the batch.

Since we are drawing samples randomly in step 1, this is called _minibatch stochastic gradient descent_.

The 4th step is complicated. You cannot change the weights one at a time because that would be very inefficient. Instead, we take the _gradient_ of the loss with respect regard to the coefficients. We take the gradient at the point of our weights and use this to adjust the weights. 

```
updated_weights = weights - step * gradient(loss(weights))
```

Here the loss function is the difference between our predictions and our expected values. Thus, we subtract because we are trying to update the weights to get this difference to be smaller. We are hoping to get the gradient to be 0 (i.e. we found the minimum of the loss function). The `step` is small adjustment factor needed because our gradient only approximates curvature at `weights`, so we do not want to move too far away from it.

One issue that arises using this method of optimization is addressing local minima. To avoid getting stuck at a local minimum, we can implement the idea of _momentum_, which uses previous weight adjustments in adjusting the current weights.

Notice that taking the gradient of a multilayered network would require the chain rule (as each layer is the input to the subsequent layer). This is often implemented using _backpropogation_.
---
layout: post
comments: false
title: Notes on Deep Learning with R Chapter 5
description: Chapter 5 - Deep Learning for Computer Vision
tags: Statistics Deep-Learning-With-R Chollet Allaire
category: Deep Learning With R
---

These are my notes on Chapter 5 of _Deep Learning with R_ by Chollet and Allaire.


* Do not remove this line (it will not be displayed)
{:toc}

# Convolutional Neural Networks

The main difference between a convolutional layer and a densely connected layer is: dense layers learn global patterns whereas convolutional layers learn local patterns.

The patterns that a convolutional neural network learns is translation invariant. That is, if it finds a patter in one section of the picture (ex the bottom left corner) it can find it anywhere. A densely connected network cannot do that.

They can also learn spatial hierarchies of patterns. The first layer can learn a simple pattern such as edges and then the second layer learns patterns from the first layer output patterns and so on. Because of this, we can use convnets are complex and abstract visual problems.


## The Convolutional Operation

Convolutions operate over 3D tensors called feature maps. THere are two spatial axes (height and width) and one depth axis (alpha, RGB, etc). Every dimension in the depth axis is a filter. The convolution operation extracts patches from its input feature map, applies the same transformation to all of the patches, and produces and output feature map.

Convolutions are defined by two parameters:
* _Size of the patches extracted from the inputs_ - usually $3 \times 3$ or $5 \times 5$.
* _Depth of output feature map_ - The number of features computed by the convolution.

A convolution slides this window ($3 \times 3$, etc) over the 3D input feature map at every possible location and extracting the 3D patch of surrounding features (`shape = (window height, window width, input_depth)`). Each of these patches is then transformed into a 1D vector of `shape = output_depth`. This transformation is done via tensor product with the same learned weight matrix, called the convolutional kernel.

All of the 1D output vectors are spatially reassembled into a 3D output map of `shape = height, width, output_depth`. However, in some cases the output height and width may differ from the input. This may be because of border effects or strides.


### Border Effects and Padding
Example: If you have a $5 \times 5$ feature map, there are only 9 tiles which you could center a $3 \times 3$ window around. So, your output feature map will be $3 \times 3$. 

If you want to mitigate this, you can use _padding_. This consists of adding the appropriate number of columns and rows on each side of the input feature map so that you can center the window around every tile. Example: You could add 1 column and 1 row to a $5 \times 5$ feature map to use a $3 \times 3$ window size.


### Convolutional Strides
A stride is the distance between two successive windows. This downsamples your space. It is set to 1 by default and generally not adjusted. 


## The max-pooling operation
The purpose of max pooling is to aggresively downsample feature maps (e.g. half it from $26 \times 26$ to $13 \times 13$). It consists of extracting windows from the input feature maps and outputting the max value of each channel. It's similar to a convolution but instead of using a learned linear transformation (the convolutional kernel), they're transformed via a hardcoded `max` tensor operation.

Max pooling is usually done with a $2 \times 2$ window and a stride of 2. Without max pooling, the convolutional network would not be able to put its local pattens together and the output would be far too big to put into the final dense layer that does the predictions (which would lead to intense overfitting).

# Training a Convnet from Scratch on a Small Dataset

## Data augmentation
Data augmentation takes the approach of generating more training data from existing training samples, by augmenting the samples via a number of random transformations that yield believable looking images. This helps generate more data when you do not have enough to train with.

This may not be enough to completely combat overfitting, so you should add a dropout layer right before the densely connected classifier.

# Using a Pretrained convnet
A pretrained network is a saved network that was previously trained on a large dataset (typically on large scale image classification). If the original dataset was general enough, the pretrained network should contain a general spatial hierarchy for all images. You can do this even when training for different classes.

## Feature Extraction
Feature extraction consists of using the representations learned by a previous network to extract interesting features from new samples. These features are then run through a new classifier, which is trained from scratch. This is done by taking the _convolutional base_, or the convolutional layers, and adding training a new classifier at the end of it.

Notice that the early layers of a convnet deal with generic features (edges, colors, textures, etc) whereas the later layers find more specific features (cate eye, dog ear, etc). So if you classes are much different, then you may only want to take the first few layers.

You can either use a pretrained base by just saving the output data and putting it in a dense neural net or by the dense layers to the network itself. This former is much cheaper and faster while the former allows for data augmentation. Note that if you do the second it is important to freeze the convolutional layers (freezing the weights) that are already trained.

## Fine-tuning
Fine-tuning consists of unfreezing a few of the top layers of a frozen model base used for feature extraction and jointly training both the newly added part of the model and these top layers. It slightly adjusts the abstract representations to make them more specific to the data being used.


# Visualizing What Convnets Learn
Since we are using image data, we can get a better understanding of what our network is doing at each step.

* _Visualizing intermediate convnet outputs (intermediate activations)_ is useful for seeing how successive layers transform their input.
* _Visualizing convnet filters_ is useful for understanding what visual patterns or concept each filter in a convnet is receptive to.
* _Visualizing heatmaps of class activation_ is useful for understanding which parts of an image were identifies as belonging to a given class. 
---
layout: post
comments: false
title: Notes on Deep Learning with R Chapter 6
description: Chapter 6 - Deep Learning for Text and Sequences
tags: Statistics Deep-Learning-With-R Chollet Allaire
category: Deep Learning With R
---

These are my notes on Chapter 6 of _Deep Learning with R_ by Chollet and Allaire.


* Do not remove this line (it will not be displayed)
{:toc}


# Working with text

You can work with text as either a sequence or characters or as a sequence of words. However, in either case deep learning for natural language is still just pattern recognition, the computer does not actually _understand_ the text.

Neural networks cannot take plain text as input, but rather it must be vectorized into a numeric tensor. This can be accomplished in a few ways.

* Segment the text into words and then transform each word into a vector.
* Segment the text into characters and then transform each character into a vector.
* Exact n-grams of words or characters, and transform each n-gram into a vector.

Whichever unit you choose to break the text into is called a _token_. We must then represent these tokens as vectors. This can be done with one-hot encoding and token embedding.

## One-hot encoding 

A unique integer is associated with every word. Then a binary dictionary is made and the value of each word is set to 1 if it is present in the text and 0 otherwise. 

## Word embeddings

Instead of high-dimensional sparse vectors given by one-hot encoding, word embeddings gives low-dimensional floating point vectors. Word embeddings are learned from the data. This can be done in two ways.

* Learn word embeddings jointly with your main task.
	* Start with random word vectors and then learn word vectors in the same way you learn weights in a network.
* Load into your model word embeddings that were precomputed.


### Using an embedding layer

The simplest way to associate a dense vector with a word vector is to start with a random vector. The problem with this is that the resulting embedding space has no structure (e.g. synonyms may be embedded differently). 

The geometric relationships between word vectors should reflect the semantic relationships between these words. You would expect synonyms to be embedded into similar word vectors. Generally, the geometric distance between two word vectors relates to the semantic difference between the associated words. 

Direction of vector will also hold meaning. For example, a "gender" vector could take the word "king" to the word "queen" and a "plural" vector could take that to "queens".

# Understanding recurrent neural networks
Dense networks and convnets have no memory. If you wanted to analyze something like text or a time series, you would have to read the whole sequence into a single data point. This is called feedforward.

In contrast, recurrent neural networks (RNN) process sequences by iterating through the sequence elements, maintaining a state containing information relevant to what it ha seen so far (via a loop). This state is reset when processing each data sequence (e.g. each movie review).

## LSTM
LSTM stands for Long Short-Term Memory. This helps old signals from gradually vanishing during processing (helping to address vanishing gradients). 

# Advanced use of RNNs

## Recurrent dropout
The same drop out pattern should be applied at every step instead of a random drop out mask at every step.

## Stacking recurrent layers
This will help until it starts overfitting, but it will take a long time to train.

## Bidirectional RNN
Note that these are order dependent (e.g. must receive time stamps in order). Bidirectional RNNs exploits the order by processing the data forward and backward and then combining the representations.

# Sequence processing with convnets
We used convnets to extra local features in images. We may also want to do that with sequence data. We can use a 1D convolution.

These are usually cheaper than RNNs and perform competitively. You can combine CNNs and RNNs to parse long sequences.
---
type: concept
title: Deep Learning
aliases: []
tags:
  - concept
  - personal
updated: 2026-08-12
status: developing
---

# Deep learning

Employs artificial [[neural-networks]] with many layers (hence "deep"). Was vastly democratized in 2010 due to the emergence of [[graphic-processing-unit]] (GPUs)

Inspired by the human brain, NN are interconnected layrs of neurons (nodes) each performing a mathematical operation (activation function). The ouput of each nodes serves as input for the following nodes until the final layer.

Each activation function performed at each node are nonlinear, enabling NN to model complex patterns and dependencies.

Each connection between two neurons is assigned a uniqued **weight** : a multiplier that increases or decreases one neuron's contribution to a neuron in the following layer. Each of which are the parameters to be optimized through [[machine-learning]]

The [[backpropagation]] algorithm is the computation of =="**how each individual node contributes to the overal output of the loss function"**== allowing millions, billions of model wieghts to be individually optimized through [[gradient-descent]] algorithms.


> Neural networks are _universal approximators_: it has been theoretically proven that for any function, there exists a neural network arrangement that can reproduce it.



#### Convolutional neural networks (CNNS).
In mathematics, a convolution is an operation where one function modifies (or convolves) the shape of another. In CNNs, the convlutional layers are used to extract imporant features from data by applying weighted "filters".  CNNs are primarily associated with computer vision models and image data.


#### Recurrent Neural Networks (RNNs).
Work on sequential data, whereas conventional feedforward networks map a single input to a single ouptut, RNNs map a sequence of inputs to an output by operating in a recurrent loop in which the output for a given step in the input sequence servers as input to the computation for the following step. In effect, this creates an inernal "memory", called the hidden state, that allows RNNs to understand context and order.


#### Transfomers.
First introduced in 2017, they are largely responsible for the advent of [[wiki/concepts/large-language-models]] and other pillars of generative AI. 
Like RNNs, transformers are ostensibly designed for sequential data, but clever workarounds have enabled most data modalities to be processed by transformers. The unique strength of a transformer model comes from their innovative attention mechanism, which enables the models to selectively focus on the parts of the input data most relevant at a specific moment in a sequence.



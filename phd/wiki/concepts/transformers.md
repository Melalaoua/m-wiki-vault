---
type: concept
title: Transformer Architecture
aliases: []
tags:
  - concept
  - phd
updated: 2026-08-22
status: developing
---
# What is a transformer model ?
It's a type of [[neural-networks]] architecture that excel at processing sequential data, most prominently associated with [[large-language-models]] (LLMs).
Transformer models have also achieved elite performance in other fields of artifical intelligence such as computer vision, speech recognition and time series forecasting.

First described in the paper "Attention is all you need" by Vaswani et al. which is now considered a watershed moment in [[deep-learning]]

Originally introduced as an evolution of the [[recurent-neural-network]] (RNN)-bsaed sequence to sequence models used for machine transltion, transformer-based models have since attained cutting-edge advancements across nearly every [[machine-learning]] discipline.

BERT (Bidirectional Encoder Representations from Transformers), an encoder-only mondel introduced by Google in 2019, was a major landmark in the establishment of transformers and remains the basis of most modern word embedding applications, from modern [[Vector Databases]] to Google Search.

Autoregressive decoder-only LLms, such as GPT-3 (generative pre-trained transformer) model, catalyzed the modern era of genAI

the Ability of transformer models to intricately discern how each part of a data sequence influences and correlates with the others also lends them many multimodal uses.

- [[vision-transformers]] (ViTs) often exceed the performance of [[convolutional-neural-networks]] (CNNs) on image segmentation, object detection, and related tasks. 
- The transformers architecture also powers many diffusion models used for image generation, multimodal text-to-speech (TTs) and vision language models (VLMs).

#### Why are transformer models important ?
The central feature of transformer models is their [[self-attention]] mechanism, from which transformer models derive their impressive ability to detect relationship or dependencies) between each part of an input sequence.

The transformer architecture uses only attention layers and standard feedforward layers.

The benefits of self-attention, and specifically the multi-head attention technique that transformer models employ to compute it, are what enable transformers to exceed the performance of the RNNs and CNNs.

Before transformers, most NLP tasks relied on RNNs which inputs sequential data in a **serialized** manner: one-at-a-time.

Attention mechanism, conversely, can examine an entire sequence simultaneously and make decisisons about how and when to focus on specific time steps of that sequence. **They dramatically improve the ability to understand long-range dependencies.**

Futhermore, attention mechanism allows **parallelization*** : the abitlity to perform many computational steps at once rather than in a serialized manner.

> Transformers take full advantage of the power and speed offered by [[graphic-processing-unit]] which in turn, **unlocked the opportunity to train transformers models on unprecedentedly massive datasets through [[supervised-learning|self-supervised learning]]


#### What is self-attention ?
*Understanding the mathematical concept of attention,  is essential to grasp the success of transformer models.

Attention mechanism are algorithms designed to determine which parts of a data sequence an AI model should "pay attention to".

##### How does self-attention work ?
Broadly speaking, a transformer model attention layers assess and use the specific context of each part of a data sequence in 4 steps : 
1. The model "reads" raw data sequences and convert them into [[embedding-space|vector-embedding]]




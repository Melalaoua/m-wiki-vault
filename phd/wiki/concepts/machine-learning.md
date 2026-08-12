---
type: concept
title: What is machine learning
aliases: []
tags:
  - concept
  - personal
updated: 2026-08-12
status: developing
---

# What is machine learning ?
ML is a computer science, data science and artificial intelligence subset that enables systems to learn and improve from data without additional programming interventions. 

- Aims to identify patterns within data in order to predict & act upon the real world. The deployment of an AI model is therefore called [[inference]]

- Optimizing a model's performance on a dataset of tasks through a process called [model-training], the model can make accurate predictions on the new data it sees in its ultimate use case.

- [[deep-learning]] (subset of ML) is used everywhere and implies the usage of vast organized layers of neurons (function with input/output). It requires very large amounts of data and computational resources, its emergence was promoted & accelerated with [[big-data]] and [[graphic-processing-unit]]  (GPU).

> All machine learning is [[artificial-intelligence]] but not all AI is machine learning.

Instead of using explicit instructions for perf optimization, ML models rely on algori
#### How ML works.
Extracts features of each data point to numerical data and feed it into a mathematical algorithm that will learn to map a given input to the desired output.

- Data is represented  [[vector-embedding]] which is a set of numerical values for  specifics features. 
- [[feature-selection]] is the process of choosing which aspects of data to use in ML.
- [[feature-extraction]] techniques refine data down to only its most relevant, meaningful dimensions. 
- Both are subsets of [[feature-engineering]] which is to preprocess raw data for use in machine learning.


#### Types of Machine Learning.
- [[supervised-learning]] : training technique to predict the correct feature based on an input. Relies on ground truth.
- [[unsupervised-learning]] : discern patterns from ingested data during training, use the pattenrs to predict on new data.
- [[reinforcement-learning]] : train the model to execute the most rewarding data, no ground truth like in SL, just the "good", "bad", "neutral" actions based on procured reward.

> Training a model entails regularly the usage of multiple techniques.


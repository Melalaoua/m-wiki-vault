---
type: concept
title: Bayes Theorem
aliases: []
tags:
  - concept
  - personal
updated: 2026-08-12
status: developing
---
# Bayes theorem

This theorem, also known as Bayes’ Rule, allows us to “invert” conditional probabilities. As a reminder, conditional probabilities represent the probability of an event given some other event has occurred.

![[Pasted image 20260812180714.png]]

Bayes’ Theorem is distinguished by its use of sequential events, where additional information later acquired impacts the initial probability. These probabilities are denoted as the prior probability and the posterior probability. The prior probability is the initial probability of an event before it is contextualized under a certain condition, or the marginal probability. The posterior probability is the probability of an event after observing a piece of data.


A popular example in [statistics and machine learning literature](https://www.stat.cmu.edu/~brian/463-663/week09/Chapter%2003.pdf) (link resides outside ibm.com) to demonstrate this concept is medical testing. For instance, imagine there is an individual, named Jane, who takes a test to determine if she has diabetes. Let’s say that the overall probability having diabetes is 5%; this would be our prior probability. However, if she obtains a positive result from her test, the prior probability is updated to account for this additional information, and it then becomes our posterior probability. This example can be represented with the following equation, using Bayes’ Theorem:

![[Pasted image 20260812180825.png]]

However, since our knowledge of prior probabilities is not likely to exact given other variables, such as diet, age, family history, et cetera, we typically leverage probability distributions from random samples, simplifying the equation to P(Y|X) = P(X|Y)P(Y) / P(X)
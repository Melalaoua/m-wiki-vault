---
type: concept
title: Data Science
aliases: []
tags:
  - concept
  - phd
updated: 2026-08-19
status: developing
---

# What is statistical machine learning ?

Machine learning is built upon statistical techniques and mathematical tools (bayesian methods, linear, algebra, validation strategies). Whenever you're training a model, you're estimating parameters from data. When you test it : is this pattern real, or just random noise? How can we quantify error by using evaluation metrics ? These are statistical questions.

This note unpacks the **statisticall pillars** behind modern [[machine-learning]].


### What is statistics ?

==Science of extracting insight from data==, it provides the mathematical foundation for understanding data behavior, guiding model choices and evaluating outcomes. **It transforms messy, noisy datasets into actionnable intelligence.**

ML is built on top of statistical methods :
- [[supervised-learning]] uses [[logistic-regression]] or classification.
- [[unsupervised-learning]] uses clustering.
- [[reinforcement-learning]] uses tools rooted in statistical inference.

> Statistics enables quantification of uncertainty, generalization from samples and drawing conclusion about broader populations, all essential toward building trustworthy AI systems.

##### Descriptive statistics : basics.
Applying **==exploratory data analysis==** (EDA), before training models, relies on descriptive statistics to summarze key characteristics of the data. 
- **Mean (average)** : arithmetic average of values. Common in measuring centrality in loss functions like mean squared error (MSE).
- **Median** : the middle value when data is sorted. More robust to outliers than the mean.
- **Mode** : The most frequently ocurring value.
- **Standard deviation (SD)** : How spread out the values are from the mean. A low SD implies that data points are clustered near the mean. Higher SD = greater variability.
- **Interquartile range** (IQR) : The range between the 75th and 25th percentiles (Q3 - Q1)  : captures the middle 50% of the data and is useful for detecting outliers.
- **skew** : indicates the asymmetry of a distribution. Positive skew = longer right tail, negative kew = longer left tail.
- **kurtosis** : describes the "tailedness" of the distribution, that is, how likely extreme values are. High kurtosis implies more frequent outliers.

During EDA, stats helps us :
- assess the distribution : are variables gaussian ? Skewed ? Multimodal ?
- Identify outliers and errors : a mismathc between mean and median might signal unusual values.
- Data quality (negative ages or impossible categories?)
- Aid in model selection : a continous target variable suggests regression; a categorical one, classification. Relationships between features (i.e correlation) might also ifnluence whether to use linear, nonparametric, or kernel-basde methods.


Modeling by using machine learning exists because of uncertainty. Real-world data is messy, incomplete and noisy, so we model ==likelihoods instead of certainties.==


### Probabilities

Probabilities is fundamental to everything [[machine-learning]] and [[artificial-intelligence]] is about, it plays a critical role in modeling uncertainties in ML models predictions.

Diving in the world of probabilities and learning the fundamentals will help ensure that you understand the basis of all statistical learning models and how their predictions come to be.

##### Terminologies 
- **random variables** : a numerical representation of an outcome of a random phenomenon. It's a variable whose possible values are numerical outcomes of a random process.

- **Discrete random variable** : a random variable that can take on a finite or countably infinite number of distinct values. For example, the outcome of a coin flip (heads = 1, Tails = 0).

- **Continuous random variable** : A random variable that can take on any value within a given range. (i.e height, temperature, ...)

- **Event** : A set of one or more outcomes from a random process. (rolling an even number on a die : outcomes : 2, 4, 6)

- **Outcome** : A single possible result of a random experiment. (flipping a coin yield either "Heads" or "Tails")

- **Probability P(A)** : A numerical measure of the likelihood that an event A will occur, ranging from 0 (impossible) to 1 (certain).

- **conditional probability P(A|B)** : The probability of event A occurring, __given that event__ B has already occurred. This step is crucial in ML, as we often want to predict an outcome given specific features.

> Probability = **how likely** an event is to happen, from 0 to 1.

> In genAI, probabilistic models plays a role in determining the results and outputs of a model. Often, in the form of an **activation function** in the layers of [[neural-networks]]



### Distributions
*Modelling how data behave*

A probability distribution describes the possible values and likelihoods that a random variable can take within a particular range. 

- **discrete distributions** : variable take on distinct, countable values
- **continuous distribution** : variable take any value within a range.

##### Core concepts
- ==Probability mass function (PMF)== : Tells the exact probability of each possible discrete outcome (0 or 1, heads or tails). i.e in a dice the PMf assigns a probability of 1/6 to each outcomes.
- ==Probability density function (PDF)==: spreads probability density across a range, helping us reason about percentiles, quantiles and probability thresholds. 
- ==Cumulative distribution function (CDF)== gives cumulative probability that a value is less than or equal to a specific threshold. It grows from 0 to 1 as you move along the x-axis. (i.e what proportion of customers spend under USD 50).
- ==Cumulative Mass function (CMF)== is the discrete counterpart to CDF. Cumulative probability that a discrete variable takes on a value less than or equal to a particular point.

> Many [[machine-learning]] algo rely on the assumptions about your data's distribution, both for model selection and interpretation. **Incorrect assumption can lead  to biased estimates, misaligned loss functions and ultimately, poor generalization or invalid conclusions in real-world applications.


##### Bernoulli trials.
Bernoulli distribution models the success/failure in a single trial of a discrete random event : 1 (success) or 0 (failure) i.e if you flip a coins 10 time with 7 heads (success) and 3 tails (failure), the PMF can be graphed as : 
![[Pasted image 20260820193537.png]]

Let's calculate the PMF with :
- X = random variable representing the outcome of a flip of a coin.
- heads is considered success, X = 1 for heads and X = 0 for tails.
- if the coin is fair, p=0.5

PMF =  P(X=x)=p^x  (1-p)^(1-x)    for  x ∈ {0,1}

![[Pasted image 20260820193803.png]]


##### Application to machine learning: discrete distribution.
Bernoulli's PMF forms the probabilistic backbone of many classification models. I.e [[logistic-regression]] doesn't just output a class label, it estimates the probability that a particular input belongs to class 1.

The logistic (sigmoid) function used in logistic regression ensures that predicted values fall within the [0,1] range, making them valid Bernoulli probabilities.


## Bernoulli → Log-Loss → Cross-Entropy

**Bernoulli PMF**: P(Y=y) = p^y (1-p)^(1-y) — one formula, collapses to p when y=1, to (1-p) when y=0.

**Logistic regression**: predicts p = sigmoid(linear combo of X). Treats true label Y as Bernoulli(p).

**Likelihood**: same PMF, but read backward — data (y) is fixed, p varies. Score how plausible the observed labels are under the model's predicted p's. Multiply across all points → L.

**Log-likelihood**: log(L) = Σ [yᵢ·log(pᵢ) + (1-yᵢ)·log(1-pᵢ)]
→ turns product into sum (avoids underflow, easy to differentiate). Log is monotonic, so same optimum.

**Log-loss**: Loss = −log(L). MLE maximizes log(L) ⇔ gradient descent minimizes −log(L). Same optimum, sign flipped for convention.

**Cross-entropy**: H(P,Q) = −Σ P(x)·log(Q(x)) — average surprisal (−log Q(x)) of outcomes, weighted by their true frequency P(x). Binary cross-entropy = cross-entropy with 2 outcomes = exactly the log-loss formula.

**Intuition**: confident + correct predictions → low surprisal → low loss. Uncertain (p≈0.5) or confidently wrong predictions → high surprisal → high loss.


The task's output type determines which distribution you assume for Y, which in turn *derives* the loss function via negative log-likelihood (MLE). Loss functions aren't arbitrary picks — they fall out of this choice.

- **Discrete, 2 outcomes** (binary classification) → Bernoulli(p) → **binary cross-entropy**
- **Discrete, k outcomes** (multi-class classification) → Categorical distribution → **categorical cross-entropy** (softmax loss)
- **Continuous** (regression) → Gaussian(μ, σ²) → **MSE**

Discrete vs continuous matters mechanically too:
- Discrete → PMF → value at a point *is* a real probability (∈[0,1], sums to 1)
- Continuous → PDF → value at a point is a *density*, not a probability (can exceed 1; only integrating over a range gives a probability)

MLE machinery (multiply likelihoods → log → negate) is identical either way — only the plugged-in distribution changes.

**Other discrete cases**: unbounded counts (e.g. cases per village) don't fit Bernoulli (not binary) or Gaussian (not continuous, no negative values) → reach for Poisson instead.
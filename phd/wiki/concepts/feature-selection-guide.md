---
type: concept
title: Feature Selection Pipeline in AI & Genetics
aliases: [Advanced Feature Selection, Genetics Preprocessing]
tags: [concept, phd, genetics, AI, feature-selection]
updated: 2026-08-26
status: active
---

For a full deep-dive [[feature-engineering]]
## The $p \gg n$ Problem & Pipeline Philosophy
In genetics (e.g., GWAS, RNA-seq), the number of features ($p$, millions of SNPs) vastly outnumbers the samples ($n$, thousands of patients). Feeding this directly into an AI model guarantees catastrophic overfitting. You do not need to be a mathematician to solve this; you must act as a tactical operator. 

Because biological traits are highly interactive, but compute power is limited, you must use a chronological funnel: **Filter first (reduce to thousands) $\rightarrow$ Embed/Unsupervised (reduce to hundreds) $\rightarrow$ Wrapper (fine-tune).**

## 1. Filter Methods (The Fast First Pass)
Filters assess features independently against the target variable, ignoring model performance entirely. They are your first line of defense to cheaply strip out noise.

| Input Variable | Output Variable | Best Filter Approach | Genetics Deep Dive Need |
| :--- | :--- | :--- | :--- |
| **Any** | **Any** | Variance Threshold, Missing Value Ratio | **Minimal:** Standard data cleaning. |
| **Numerical** (Gene expression) | **Numerical** (Blood pressure) | Pearson’s correlation | **Low:** Only detects linear relationships. |
| **Numerical** | **Categorical** (Disease vs Control) | ANOVA, Kendall’s rank | **Moderate:** Assumes specific data distributions. |
| **Categorical** (SNP A/T/C/G) | **Categorical** | Chi-squared | **Moderate:** Expects categorical frequency matching. |
| **Mixed** | **Mixed** | Mutual Information (MI) | **Deep:** Rooted in information theory; catches non-linear complexity. |

## 2. Embedded & Unsupervised (The Heavy Lifters)
Once filtered, you can afford slightly more compute-intensive methods. These techniques look at relationships between variables or fold selection directly into model training.

*   **LASSO Regression (L1):** Adds a training penalty that forces weak feature coefficients to exactly zero. Essential for bioinformatics to create strictly sparse models.
*   **Tree-based Importance (Random Forest/XGBoost):** Scores features by how well they decrease "impurity" during training. Excellent for finding non-linear genetic interactions.
*   **Principal Component Analysis (PCA):** Unsupervised dimensionality reduction. The gold standard for correcting population stratification in GWAS.
*   **Autoencoders:** Unsupervised neural networks that learn latent (hidden) biological variables in complex data, like single-cell RNA-seq.

## 3. Wrapper Methods (The Final Polish)
Wrappers are computationally greedy algorithms that train models on various subsets of features to find the absolute optimal combination. 

*   **Forward/Backward Selection:** Iteratively adds or removes one feature at a time until model performance fails to improve.
*   **Recursive Feature Elimination (RFE):** Iteratively drops the weakest features based on importance scores. Best used with Cross-Validation (RFECV) to prevent overfitting.
> **⚠️ Genetics Warning:** Never use exhaustive wrapper methods on raw genome/RNA-seq data. The compute time scales exponentially. Only use these at the very end of your pipeline.


### The Mandatory Step: Filters First

In genetics, because of your millions of features, **Step 1 is almost always a Filter method.** You must do this first because the other methods are too computationally heavy to run on the raw data. The output of your filter step (e.g., reducing 5 million SNPs down to the top 10,000 using Chi-squared) becomes the input for the next phase.

### The Fork in the Road: Choosing Step Two

Once your data is filtered, you reach a fork in the road. You usually pick _one_ of the following paths depending on your final goal, rather than chaining them all together:

- **Path A (Filter $\rightarrow$ Embedded):** You feed your 10,000 filtered SNPs into a LASSO regression model. As LASSO trains, it acts as an embedded selector, pushing the coefficients of weak SNPs to zero. The model finishes training with only the best 50 SNPs active. You are done.
    
- **Path B (Filter $\rightarrow$ Wrapper):** You feed those 10,000 SNPs into a Recursive Feature Elimination (RFE) algorithm. RFE tests hundreds of feature combinations and outputs the absolute best 50 SNPs. You then train a standard model on those 50.
    
- **Path C (Filter $\rightarrow$ Unsupervised):** You feed the 10,000 SNPs into a PCA algorithm. PCA compresses those 10,000 features into 10 new "principal components" that capture the overall biological variance. You train your final model on those 10 components.
**authors**:: Xianming Li, Jing Li 
**date**::   ```2024-01-30 13:46 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI
**sous-groupe**:: #AI/embeddings 
**pertinence**:: 5
**links**:: https://arxiv.org/abs/2309.12871
**modification date**:: ```Tuesday 30th January 2024 13:46:56 ```

```ad-abstract
High-quality text embedding is pivotal in improving semantic textual similarity
(STS) tasks, which are crucial components in Large Language Model (LLM) ap-
plications. However, a common challenge existing text embedding models face is
the problem of vanishing gradients, primarily due to their reliance on the cosine
function in the optimization objective, which has saturation zones. To address this
issue, this paper proposes a novel angle-optimized text embedding model called
AnglE. The core idea of AnglE is to introduce angle optimization in a complex
space. This novel approach effectively mitigates the adverse effects of the satura-
tion zone in the cosine function, which can impede gradient and hinder optimiza-
tion processes. To set up a comprehensive STS evaluation, we experimented on
existing short-text STS datasets and a newly collected long-text STS dataset from
GitHub Issues. Furthermore, we examine domain-specific STS scenarios with
limited labeled data and explore how AnglE works with LLM-annotated data. Ex-
tensive experiments were conducted on various tasks including short-text STS,
long-text STS, and domain-specific STS tasks. The results show that AnglE out-
performs the state-of-the-art (SOTA) STS models that ignore the cosine saturation
zone. These findings demonstrate the ability of AnglE to generate high-quality
text embeddings and the usefulness of angle optimization in STS.
```

## Notes



```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
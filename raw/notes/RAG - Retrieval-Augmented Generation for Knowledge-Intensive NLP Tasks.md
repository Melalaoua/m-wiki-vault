**authors**:: [Patrick Lewis](https://arxiv.org/search/cs?searchtype=author&query=Lewis,+P), [Ethan Perez](https://arxiv.org/search/cs?searchtype=author&query=Perez,+E), [Aleksandra Piktus](https://arxiv.org/search/cs?searchtype=author&query=Piktus,+A), [Fabio Petroni](https://arxiv.org/search/cs?searchtype=author&query=Petroni,+F), [Vladimir Karpukhin](https://arxiv.org/search/cs?searchtype=author&query=Karpukhin,+V), [Naman Goyal](https://arxiv.org/search/cs?searchtype=author&query=Goyal,+N), [Heinrich Küttler](https://arxiv.org/search/cs?searchtype=author&query=K%C3%BCttler,+H), [Mike Lewis](https://arxiv.org/search/cs?searchtype=author&query=Lewis,+M), [Wen-tau Yih](https://arxiv.org/search/cs?searchtype=author&query=Yih,+W), [Tim Rocktäschel](https://arxiv.org/search/cs?searchtype=author&query=Rockt%C3%A4schel,+T), [Sebastian Riedel](https://arxiv.org/search/cs?searchtype=author&query=Riedel,+S), [Douwe Kiela](https://arxiv.org/search/cs?searchtype=author&query=Kiela,+D)
**date**::   ```2024-01-22 09:52 ```
**tags**:: #papiers/stageS2  
**groupe**:: AI - PROMPTING
**sous-groupe**:: #AI/prompting 
**pertinence**:: 9
**links**:: https://arxiv.org/abs/2005.11401
**modification date**:: ```Monday 22nd January 2024 09:52:03 ```

```ad-abstract
Large pre-trained language models have been shown to store factual knowledge in their parameters, and achieve state-of-the-art results when fine-tuned on downstream NLP tasks. However, their ability to access and precisely manipulate knowledge is still limited, and hence on knowledge-intensive tasks, their performance lags behind task-specific architectures. Additionally, providing provenance for their decisions and updating their world knowledge remain open research problems. Pre-trained models with a differentiable access mechanism to explicit non-parametric memory can overcome this issue, but have so far been only investigated for extractive downstream tasks. We explore a general-purpose fine-tuning recipe for retrieval-augmented generation (RAG) -- models which combine pre-trained parametric and non-parametric memory for language generation. We introduce RAG models where the parametric memory is a pre-trained seq2seq model and the non-parametric memory is a dense vector index of Wikipedia, accessed with a pre-trained neural retriever. We compare two RAG formulations, one which conditions on the same retrieved passages across the whole generated sequence, the other can use different passages per token. We fine-tune and evaluate our models on a wide range of knowledge-intensive NLP tasks and set the state-of-the-art on three open domain QA tasks, outperforming parametric seq2seq models and task-specific retrieve-and-extract architectures. For language generation tasks, we find that RAG models generate more specific, diverse and factual language than a state-of-the-art parametric-only seq2seq baseline.
```

## Notes

Voir note [[Retrieval Augmented Generation]]

![[Pasted image 20240122095905.png]]


- Un retriever qui vient chercher dans une base de données en vecteur afin d'épauler le modèle NLP dans sa réponse.


```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
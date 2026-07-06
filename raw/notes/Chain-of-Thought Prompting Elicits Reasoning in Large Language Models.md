**authors**:: [Jason Wei](https://arxiv.org/search/cs?searchtype=author&query=Wei,+J), [Xuezhi Wang](https://arxiv.org/search/cs?searchtype=author&query=Wang,+X), [Dale Schuurmans](https://arxiv.org/search/cs?searchtype=author&query=Schuurmans,+D), [Maarten Bosma](https://arxiv.org/search/cs?searchtype=author&query=Bosma,+M), [Brian Ichter](https://arxiv.org/search/cs?searchtype=author&query=Ichter,+B), [Fei Xia](https://arxiv.org/search/cs?searchtype=author&query=Xia,+F), [Ed Chi](https://arxiv.org/search/cs?searchtype=author&query=Chi,+E), [Quoc Le](https://arxiv.org/search/cs?searchtype=author&query=Le,+Q), [Denny Zhou](https://arxiv.org/search/cs?searchtype=author&query=Zhou,+D)
**date**::   ```2024-01-17 12:01 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI - PROMPTING
**sous-groupe**:: #AI/prompting 
**pertinence**:: 9
**links**:: https://arxiv.org/abs/2201.11903
**modification date**:: ```Wednesday 17th January 2024 12:01:43 ```

```ad-abstract
We explore how generating a chain of thought -- a series of intermediate reasoning steps -- significantly improves the ability of large language models to perform complex reasoning. In particular, we show how such reasoning abilities emerge naturally in sufficiently large language models via a simple method called chain of thought prompting, where a few chain of thought demonstrations are provided as exemplars in prompting. Experiments on three large language models show that chain of thought prompting improves performance on a range of arithmetic, commonsense, and symbolic reasoning tasks. The empirical gains can be striking. For instance, prompting a 540B-parameter language model with just eight chain of thought exemplars achieves state of the art accuracy on the GSM8K benchmark of math word problems, surpassing even finetuned GPT-3 with a verifier.
```

## Notes
![[Pasted image 20240117123509.png]]
*Le CoT semble améliorer grandement les performances des modèles comparé à du prompting standard.*


Le CoT consiste à diviser un problème complexe en plusieurs étapes intermédiaires jusqu'à la réponse finale.

Le CoT permet d'avoir une certaine traçabilité du modèle jusqu'à sa réponse finale. 

Le CoT permet de prompt les modèles sur des questions plus complexes d'arithmétiques, raisonnement, symbolisme, ...

![[Pasted image 20240117124439.png]]





```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
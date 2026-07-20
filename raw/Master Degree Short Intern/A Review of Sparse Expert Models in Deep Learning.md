**authors**:: [William Fedus](https://arxiv.org/search/cs?searchtype=author&query=Fedus,+W), [Jeff Dean](https://arxiv.org/search/cs?searchtype=author&query=Dean,+J), [Barret Zoph](https://arxiv.org/search/cs?searchtype=author&query=Zoph,+B)
**date**::   ```2024-01-17 14:29 ```
**tags**::  #papiers/stageS2 
**groupe**:: AI
**sous-groupe**:: #AI/architecture 
**pertinence**:: 5
**links**:: https://arxiv.org/abs/2209.01667
**modification date**:: ```Wednesday 17th January 2024 14:29:42 ```

```ad-abstract
Sparse expert models are a thirty-year old concept re-emerging as a popular architecture in deep learning. This class of architecture encompasses Mixture-of-Experts, Switch Transformers, Routing Networks, BASE layers, and others, all with the unifying idea that each example is acted on by a subset of the parameters. By doing so, the degree of sparsity decouples the parameter count from the compute per example allowing for extremely large, but efficient models. The resulting models have demonstrated significant improvements across diverse domains such as natural language processing, computer vision, and speech recognition. We review the concept of sparse expert models, provide a basic description of the common algorithms, contextualize the advances in the deep learning era, and conclude by highlighting areas for future work.
```

## Notes
![[Pasted image 20240117143940.png]]

Le SmOE permet de réduire les coûts en inférence des modèles [[Attention is all you need|Transformers]] en divisant le modèle en plusieurs FFN (Feed-Forward Network). Seuls 2 FFN sont sélectionnés pour l'inférence, le résultat des deux est récupéré.

La variantes la plus populaires de SmOE est le MoE (mixture of Experts) où les différents experts ont tous des poids différents.

Durant l'entrainement et l'inference, le routeur redirige les inputs vers les experts spécifiques. Ainsi, chaque example interagit avec un subset du nombre total de paramètres du modèle.

![[Pasted image 20240117150313.png]]





```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
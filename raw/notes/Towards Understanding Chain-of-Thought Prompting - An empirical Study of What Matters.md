**authors**:: [Boshi Wang](https://arxiv.org/search/cs?searchtype=author&query=Wang,+B), [Sewon Min](https://arxiv.org/search/cs?searchtype=author&query=Min,+S), [Xiang Deng](https://arxiv.org/search/cs?searchtype=author&query=Deng,+X), [Jiaming Shen](https://arxiv.org/search/cs?searchtype=author&query=Shen,+J), [You Wu](https://arxiv.org/search/cs?searchtype=author&query=Wu,+Y), [Luke Zettlemoyer](https://arxiv.org/search/cs?searchtype=author&query=Zettlemoyer,+L), [Huan Sun](https://arxiv.org/search/cs?searchtype=author&query=Sun,+H)
**date**::   ```2024-01-23 01:25 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI - PROMPTING
**sous-groupe**:: #AI/prompting 
**pertinence**:: 7
**links**:: https://arxiv.org/abs/2212.10001
**modification date**:: ```Tuesday 23rd January 2024 01:25:16 ```

```ad-abstract
Chain-of-Thought (CoT) prompting can dramatically improve the multi-step reasoning abilities of large language models (LLMs). CoT explicitly encourages the LLM to generate intermediate rationales for solving a problem, by providing a series of reasoning steps in the demonstrations. Despite its success, there is still little understanding of what makes CoT prompting effective and which aspects of the demonstrated reasoning steps contribute to its performance. In this paper, we show that CoT reasoning is possible even with invalid demonstrations - prompting with invalid reasoning steps can achieve over 80-90% of the performance obtained using CoT under various metrics, while still generating coherent lines of reasoning during inference. Further experiments show that other aspects of the rationales, such as being relevant to the query and correctly ordering the reasoning steps, are much more important for effective CoT reasoning. Overall, these findings both deepen our understanding of CoT prompting, and open up new questions regarding LLMs' capability to learn to reason in context.
```

## Notes
Voir [[Self-Consistency]]


Le papier a réaliser du [[Chain-of-Thought Prompting]] mais avec des étapes de raisonnement invalide, ils ont obtenus des résultats bons malgré le faux raisonnement. Ils se sont rendus compte qu'avoir un raisonnement valide ne contribuait que très peu à la performance du modèle.

![[Pasted image 20240123013004.png]]





```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
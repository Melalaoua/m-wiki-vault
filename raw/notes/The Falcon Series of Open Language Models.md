**authors**:: [Ebtesam Almazrouei](https://arxiv.org/search/cs?searchtype=author&query=Almazrouei,+E), [Hamza Alobeidli](https://arxiv.org/search/cs?searchtype=author&query=Alobeidli,+H), [Abdulaziz Alshamsi](https://arxiv.org/search/cs?searchtype=author&query=Alshamsi,+A), [Alessandro Cappelli](https://arxiv.org/search/cs?searchtype=author&query=Cappelli,+A), [Ruxandra Cojocaru](https://arxiv.org/search/cs?searchtype=author&query=Cojocaru,+R), [Mérouane Debbah](https://arxiv.org/search/cs?searchtype=author&query=Debbah,+M), [Étienne Goffinet](https://arxiv.org/search/cs?searchtype=author&query=Goffinet,+%C3%89), [Daniel Hesslow](https://arxiv.org/search/cs?searchtype=author&query=Hesslow,+D), [Julien Launay](https://arxiv.org/search/cs?searchtype=author&query=Launay,+J), [Quentin Malartic](https://arxiv.org/search/cs?searchtype=author&query=Malartic,+Q), [Daniele Mazzotta](https://arxiv.org/search/cs?searchtype=author&query=Mazzotta,+D), [Badreddine Noune](https://arxiv.org/search/cs?searchtype=author&query=Noune,+B), [Baptiste Pannier](https://arxiv.org/search/cs?searchtype=author&query=Pannier,+B), [Guilherme Penedo](https://arxiv.org/search/cs?searchtype=author&query=Penedo,+G)
**date**::   ```2024-01-06 11:42 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI
**sous-groupe**:: #AI/models 
**pertinence**:: 8
**links**:: https://arxiv.org/abs/2311.16867
**modification date**:: ```Saturday 6th January 2024 11:42:07 ```

```ad-abstract
We introduce the Falcon series: 7B, 40B, and 180B parameters causal decoderonly models trained on a diverse high-quality corpora predominantly assembled from web data. The largest model, Falcon-180B, has been trained on over 3.5 trillion tokens of text–the largest openly documented pretraining run. Falcon-180B significantly outperforms models such as PaLM or Chinchilla, and improves upon concurrently developed models such as LLaMA 2 or Inflection-1. It nears the performance of PaLM-2-Large at a reduced pretraining and inference cost, making it, to our knowledge, one of the three best language models in the world along with GPT-4 and PaLM-2-Large. We report detailed evaluations, as well as a deep dive into the methods and custom tooling employed to pretrain Falcon. Notably, we report on our custom distributed training codebase, allowing us to efficiently
pretrain these models on up to 4,096 A100s on cloud AWS infrastructure with limited interconnect. We release a 600B tokens extract of our web dataset, as well as the Falcon-7/40/180B models under a permissive license to foster open-science and accelerate the development of an open ecosystem of large language models.
```

## Notes
- FALCON semble être le modèle privilégié dans le cadre du stage. Toutefois plusieurs questions se posent : 
	1. Le modèle est-il implémentable dans le secteur suivant les coûts techniques (carte graphique ? CPU ?).
	2. Quels paramètres choisir ? 7B, 40B, 180B ?

- ==The ongoing Cambrian explosion==, en tant que biologiste et informaticien, j'adore ce terme qui illustre parfaitement l'année 2023 avec l'apparition d'une multitude de modèle de LLM, avec l'open-source qui a joué un rôle important.

- Le papier parle de "scalabilité" de l'architecture des [[Attention is all you need|Transformers]]

- Partie "State of the art : from language modelling to frontier models" est très utile pour avoir une compréhension du contexte dû à l'explosion des LLMs en 2023

- Falcon se place comme un très bon choix dans le décor actuel des modèles LLMs, point fort : il est open source.

![[Pasted image 20240106130209.png]]

- Dans les limites, la notion de guardrail est employée. Il faut que je creuse le sujet. Cite aussi le [[RLHF]]





## Détails techniques
- Entrainé sur 4086 A100
- 7B, 40B ou 180B paramètres.
![[Pasted image 20240106123908.png]]


```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
**authors**:: Bernardino Romera-Paredes, Mohammadamin Barekatain, 
**date**::   ```2024-01-02 12:14 ```
**tags**:: #papiers/stageS2
**groupe** :: AI
**sous-groupe**:: #AI/LLM, #AI/functionCalling 
**pertinence**:: 5
**links**:: 
**modification date**:: ```Tuesday 2nd January 2024 12:14:24 ```

```ad-abstract
Large Language Models (LLMs) have demonstrated tremendous capabilities in solving complex tasks, from quantitative reasoning to understanding natural language. However, LLMs sometimes suffer from confabulations (or hallucinations) which can result in them making plausible but incorrect statements (Bang et al., 2023; Borji, 2023). This hinders the use of current large models in scientific discovery. Here we introduce FunSearch (short for searching in the 16 function space), an evolutionary procedure based on pairing a pre-trained LLM with a systematic evaluator. We demonstrate the effectiveness of this approach to surpass the best known results in important problems, pushing the boundary of existing LLM-based approaches (Lehman et al., 2022). Applying FunSearch to a central problem in extremal combinatorics — the cap set problem — we discover new constructions of large cap sets going beyond the best known
ones, both in finite dimensional and asymptotic cases. This represents the first discoveries made for established open problems using LLMs. We showcase the generality of FunSearch by applying it to an algorithmic problem, online bin packing, finding new heuristics that improve upon widely used baselines. In contrast to most computer search approaches, FunSearch searches for programs that describe how to solve a problem, rather than what the solution is. Beyond being an effective and scalable strategy, discovered programs tend to be more interpretable than raw solutions, enabling feedback loops between domain experts and FunSearch, and the deployment of such programs in real-world applications.
```



## Notes
- FunSearch se place dans la continuité des LLMs guidés par des méthodes évolutives 

- Specifications de funsearch : prends en entrée le problème sous la forme d'une fonction attribuant un score à des solutions. En plus de la fonction, un programme est fourni pour permettre au modèle d'évoluer.

- Funsearch semble donner des résultats sans fine-tuning. Modèle LLM [Codey](https://cloud.google.com/blog/products/ai-machine-learning/google-cloud-launches-new-ai-models-opens-generative-ai-studio?hl=en) (construit sur famille PALM-2) : fine-tuned sur un large datasets de codes, acessible via une API (impossible pour le stage)

- Interessant : Les programmes générés par le modèle sont évalués sur la base de plusieurs entrées. Les scores de ces différents entrées sont combinés et le score total correspond au resultat d'une fonction d'aggrégation (moyenne). **Les programmes évalués sont envoyés dans une base de données et évalués selon leur temps d'execution et la validité de leur résultat**, ceux qui ne correspondent pas sont supprimés.

- Les programmes retenus dans la base de données sont utilisés pour générer des meilleurs prompts.

- Afin de préserver la diversité et l'hétérogénéité de la base de données, les auteurs ont utilisé la "méthode des îles" (islands model | multiple population | multiple-deme model) : Création de différentes îles (sous-populations) sont créés, évoluant indépendamment.

```ad-quote
==Une sélection positive des meilleurs programmes tout en conservant un indépendance et hétérogénéité des échantillons.==
This is beneficial because single experiments can get stuck in local minima, where the majority of programs in the population are not easily mutated and combined
into stronger programs.
```

- Création de prompt par  [[Best-shot prompting]]

- Trois workers : program database, samplers et evaluators ([[Async IO|asynchrones]])

- Genetic programming (GP) : 

```ad-todo
title: A developper
Within each island, we further cluster programs according to their signature. We define the signature of a program as the tuple containing the program’s scores on each of the inputs (e.g., the cap set size for each input n). Programs with the same signature are clustered together. When sampling a program within an island, we first sample an island’s cluster, and then a program within that cluster (see Extended Data Figure 3). This approach, which aims at preserving diversity [55, 56], is related to Lexicase [57] in that both approaches consider a set of test cases for scoring an individual, and it is related to fitness uniform optimization [58], which also clusters individuals based on their fitness value, however we sample the clusters based on their score instead of uniformly, as detailed next.
```

### Critères techniques

- LLM codey (famille palm2) : 340 milliards de paramètres.
- 150 CPU (serveurs avec 5 CPU chacun tourant 32 evaluateurs)

**authors**:: Antonia Creswell, Murray Shanahan
**date**::   ```2024-01-06 11:19 ```
**tags**:: #papiers/stageS2 r
**groupe**:: AI - PROMPTING
**sous-groupe**:: #AI/prompting 
**pertinence**::5
**links**:: 
**modification date**:: ```Saturday 6th January 2024 11:19:23 ```

```ad-abstract
Although contemporary large languagemodels (LMs) demonstrate impressive question-answering capabilities, their answers are typically the product of a single call to the model. This entails an unwelcome degree of opacity and compromises performance, especially on problems that are inherently multi-step. To address these limitations, we show how LMs can be made to perform faithfulmulti-step reasoning via
a process whose causal structure mirrors the underlying logical structure of the problem. Our approach works by chaining together reasoning steps, where each step results from calls to two fine-tuned LMs, one for selection and one for inference, to produce a valid reasoning trace. Our method carries out a beam search through the space of reasoning traces to improve reasoning quality. We demonstrate the effectiveness of our model on multi-step logical deduction and scientific question-answering, showing
that it outperforms baselines on final answer accuracy, and generates humanly interpretable reasoning traces whose validity can be checked by the user.
```

## Notes
- Ce papier présente une manière de prompting des LM pour permettre de suivre leur raisonnement et tracer le chemin jusqu'à leur réponse finale suivant une question, une tâche.
![[Pasted image 20240106112508.png]]

- La méthode de Faithful Reasoning repose sur deux LM fine-tuned. L'un ayant pour tâche la "sélection", l'autre pour "l'inference".
- Les deux LMs interagissent entre eux à partir d'un contexte donné. Cela ressemble à une méthode primaire d'[[AI Agents]]

- Deux autres LMs se rajoutent à l'architecture (4 au total donc) : le halter (stop le processus de raisonnement), et le value function (évalue la qualité des étapes de raisonnements). 

- Le faithful reasoning est interessant car : il prend entrée un contexte et une question. Dans le cadre du stage, le contexte pourrait être les données de différentes sources (clinvar, pubmed, base de données des patients précédent) + la question (données de séquençage) 


```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
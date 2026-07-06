**authors**:: [Xi Victoria Lin](https://arxiv.org/search/cs?searchtype=author&query=Lin,+X+V), [Richard Socher](https://arxiv.org/search/cs?searchtype=author&query=Socher,+R), [Caiming Xiong](https://arxiv.org/search/cs?searchtype=author&query=Xiong,+C)
**date**::   ```2024-01-19 15:00 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI
**sous-groupe**:: #AI/graphs 
**pertinence**:: 5
**links**:: https://arxiv.org/abs/1808.10568
**modification date**:: ```Friday 19th January 2024 15:00:09 ```

```ad-abstract
Multi-hop reasoning is an effective approach
for query answering (QA) over incomplete
knowledge graphs (KGs). The problem can be
formulated in a reinforcement learning (RL)
setup, where a policy-based agent sequentially
extends its inference path until it reaches a
target. However, in an incomplete KG en-
vironment, the agent receives low-quality re-
wards corrupted by false negatives in the train-
ing data, which harms generalization at test
time. Furthermore, since no golden action se-
quence is used for training, the agent can be
misled by spurious search trajectories that in-
cidentally lead to the correct answer. We pro-
pose two modeling advances to address both
issues: (1) we reduce the impact of false nega-
tive supervision by adopting a pretrained one-
hop embedding model to estimate the reward
of unobserved facts; (2) we counter the sen-
sitivity to spurious paths of on-policy RL by
forcing the agent to explore a diverse set of
paths using randomly generated edge masks.
Our approach significantly improves over ex-
isting path-based KGQA models on several
benchmark datasets and is comparable or bet-
ter than embedding-based models.
```

## Notes
- Pretrained one-hop embedding model afin d'estimer les récompenses pour des faits non-observés dans des [[Knowledge Graph]]
- Développe une méthode pour forcer l'agent à explorer diverse set de chemins dans le [[Knowledge Graph]] avec des masques différents.

```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
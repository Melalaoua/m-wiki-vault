**authors**:: Milad Moradi, Kathrin Blagec, Florian Haberl, Matthias Samwald
**date**::   ```2024-01-15 16:28 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI
**sous-groupe**:: #AI/limits 
**pertinence**:: 5
**links**:: https://arxiv.org/abs/2109.02555
**modification date**:: ```Monday 15th January 2024 16:28:26 ```

```ad-abstract
Deep neural language models have set new
breakthroughs in many tasks of Natural
Language Processing (NLP). Recent work
has shown that deep transformer language
models (pretrained on large amounts of
texts) can achieve high levels of task-
specific few-shot performance comparable
to state-of-the-art models. However, the
ability of these large language models in
few-shot transfer learning has not yet been
explored in the biomedical domain. We
investigated the performance of two
powerful transformer language models, i.e.
GPT-3 and BioBERT, in few-shot settings
on various biomedical NLP tasks. The
experimental results showed that, to a great
extent, both the models underperform a
language model fine-tuned on the full
training data. Although GPT-3 had already
achieved near state-of-the-art results in
few-shot knowledge transfer on open-
domain NLP tasks, it could not perform as
effectively as BioBERT, which is orders of
magnitude smaller than GPT-3. Regarding
that BioBERT was already pretrained on
large biomedical text corpora, our study
suggests that language models may largely
benefit from in-domain pretraining in task-
specific few-shot learning. However, in-
domain pretraining seems not to be
sufficient; novel pretraining and few-shot
learning strategies are required in the
biomedical NLP domain. Codes to run the
experiments are available at
https://github.com/mmoradi-iut/BioGPT-3
```

## Notes
- Task-specific fine-tuning is then used to master task-specific language capabilities such as named entity recognition, coreference resolution, relation extraction, semantic similarity estimation, etc.
- Etude de GPT-3 (175B) dans diverses tâches BioNLP : textual inference, classification, recherche sémantique, estimation, QA, text classification en [[Few-shot Prompting]]
- Résultat apparemment inférieurs à BioBERT

```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
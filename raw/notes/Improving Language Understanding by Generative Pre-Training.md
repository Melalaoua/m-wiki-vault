**authors**:: Alec Radford, Karthik Narasimhan, Tim Salimans, Ilya Sutskever
**date**::   ```2024-01-17 12:46 ```
**tags**:: #papiers/stageS2 
**groupe**::AI
**sous-groupe**:: #AI/training 
**pertinence**:: 5
**links**:: https://s3-us-west-2.amazonaws.com/openai-assets/research-covers/language-unsupervised/language_understanding_paper.pdf
**modification date**:: ```Wednesday 17th January 2024 12:46:21 ```

```ad-abstract
Natural language understanding comprises a wide range of diverse tasks such as textual entailment, question answering, semantic similarity assessment, and document classification. Although large unlabeled text corpora are abundant, labeled data for learning these specific tasks is scarce, making it challenging for discriminatively trained models to perform adequately. We demonstrate that large gains on these tasks can be realized by generative pre-training of a language model
on a diverse corpus of unlabeled text, followed by discriminative fine-tuning on each specific task. In contrast to previous approaches, we make use of task-aware input
transformations during fine-tuning to achieve effective transfer while requiring minimal changes to the model architecture. We demonstrate the effectiveness of
our approach on a wide range of benchmarks for natural language understanding. Our general task-agnostic model outperforms discriminatively trained models that use architectures specifically crafted for each task, significantly improving upon the state of the art in 9 out of the 12 tasks studied. For instance, we achieve absolute improvements of 8.9% on commonsense reasoning (Stories Cloze Test), 5.7% on question answering (RACE), and 1.5% on textual entailment (MultiNLI).
```

## Notes

Pre-training = entrainer un modèle sur une vaste quantité de données non annotées et ensuite le [[Scaling Instruction-Finetuned Language Models||Fine-Tune]] permet aux modèles d'être plus performants que les modèles initialement entrainés pour une/des tâche(s) spécifique(s), sur des donnée spécifiquement sélectionnées dans cette optique.

- Entrainement d'un modèle deep learning avec une [[Attention is all you need|transformers]]


```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
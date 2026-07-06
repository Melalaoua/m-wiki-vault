**authors**:: Renqian Luo 1;, Liai Sun2, Yingce Xia 1;, Tao Qin 1;, Sheng Zhang 3, Hoifung Poon 3 and Tie-Yan Liu1
**date**::   ```2024-01-06 09:47 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI
**sous-groupe**:: #AI/models
**pertinence**::  9
**links**:: 
**modification date**:: ```Saturday 6th January 2024 09:47:50 ```

```ad-abstract
Pre-trained language models have attracted increasing attention in the biomedical domain, inspired by their great success in the general natural language domain. Among the two main branches of pre-trained language models in the general language domain, i.e., BERT (and its variants) and GPT (and its variants), the rst one has been extensively studied in the biomedical domain, such as BioBERT and PubMedBERT. While they have achieved great success on a variety of discriminative downstream biomedical tasks, the lack of generation ability constrains their application scope. In this paper, we propose BioGPT, a domain-specic generative Transformer language model pre-trained on large scale biomedical literature. We evaluate BioGPT on six biomedical NLP tasks and demonstrate that our model outperforms previous models on most tasks. Especially, we get 44:98%, 38:42% and 40:76% F1 score on BC5CDR, KD-DTI and
DDI end-to-end relation extraction tasks respectively, and 78:2% accuracy on PubMedQA, creating a new record. Our case study on text generation further demonstrates the advantage of BioGPT on biomedical literature to generate fluent descriptions for biomedical terms. Code is available at https://github.com/microsoft/BioGPT
```

## Notes
- Papiers important : intégrer un module de recherche bibliographique dans le bot serait très utile, de 1 pour construire une base de données non exhaustive dans laquelle piocher. De 2 pour avoir une base solide sur lequel faire un diagnostique à partir des données de séquençage.

- Piocher dans des bases de données comme Clinvar, AlphaMissense, Pubmed...

- BioGPT est un [[Attention is all you need|Transformers]]

- BioGPT a été confectionné dans la perspective de différentes tâches :
	- ==Relation Extraction== : le modèle extrait, à partir du papier analysé, les entités ainsi que leur relations. Input : texte (article) => triplet (entitie, relation, entitie) en END-to-END
	- ==Question Answering== : BioGPT est capable de répondre à des questions en se basant sur un contexte.
	- ==Document Classification== : Classer les documents en différents labels.

```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
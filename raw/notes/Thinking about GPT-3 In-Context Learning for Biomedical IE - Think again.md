**authors**:: Bernal Jiménez Gutiérrez1, Nikolas McNeal1, Clay Washington1,
You Chen2, Lang Li1, Huan Sun1, Yu Su1
**date**::   ```2024-01-15 16:05 ```
**tags**:: #papiers/stageS2 
**groupe**:: Biology
**sous-groupe**:: #biology/bioinfo   #AI/limits
**pertinence**::  5
**links**:: https://arxiv.org/abs/2203.08410, https://github.com/dki-lab/few-shot-bioIE
**modification date**:: ```Monday 15th January 2024 16:05:43 ```

```ad-abstract
Large pre-trained language models (PLMs)
such as GPT-3 have shown strong in-context
learning capabilities, which are highly appeal-
ing for domains such as biomedicine that fea-
ture high and diverse demands of language
technologies but also high data annotation
costs. In this paper, we present the first sys-
tematic and comprehensive study to compare
the few-shot performance of GPT-3 in-context
learning with fine-tuning smaller (i.e., BERT-
sized) PLMs on two representative biomedical
information extraction (IE) tasks: named en-
tity recognition and relation extraction. We
follow the true few-shot setting (Perez et al.,
2021) to avoid overestimating models’ few-
shot performance by model selection over a
large validation set. We also optimize GPT-3’s
performance with known techniques such as
contextual calibration and dynamic in-context
example retrieval. However, our results show
that GPT-3 still significantly underperforms
compared to simply fine-tuning a smaller PLM.
In addition, GPT-3 in-context learning also
yields smaller gains in accuracy when more
training data becomes available. More in-
depth analyses further reveal issues of in-
context learning that may be detrimental to IE
tasks in general. Given the high cost of ex-
perimenting with GPT-3, we hope our study
provides helpful guidance for biomedical re-
searchers and practitioners towards more prac-
tical solutions such as fine-tuning small PLMs
before better in-context learning is available
for biomedical IE.1
```

## Notes
- Introduction sur la nécessité de trouver des techniques d'extractions des quantités massives de données biomédicales en information structurées. 
- Fine-tune de GPT3 (pas ChatGPT attention) dans l'extraction d'information biomédicale (NER et RE) en [[True Few-Shot Learning with Language Models]]
![[Pasted image 20240115162543.png]]



```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
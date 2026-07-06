**authors**:: Karan Singhal1,4 ✉, Shekoofeh Azizi1,4 ✉, Tao Tu1,4
, S. Sara Mahdavi1
, Jason Wei1
,
Hyung Won Chung1
, Nathan Scales1
, Ajay Tanwani1
, Heather Cole-Lewis1
, Stephen Pfohl1
,
Perry Payne1
, Martin Seneviratne1
, Paul Gamble1
, Chris Kelly1
, Abubakr Babiker1
,
Nathanael Schärli1
, Aakanksha Chowdhery1
, Philip Mansfield1
, Dina Demner-Fushman2
,
Blaise Agüera y Arcas1
, Dale Webster1
, Greg S. Corrado1
, Yossi Matias1
, Katherine Chou1
,
Juraj Gottweis1
, Nenad Tomasev3
, Yun Liu1
, Alvin Rajkomar1
, Joelle Barral1
,
Christopher Semturs1
, Alan Karthikesalingam1,5 ✉ & Vivek Natarajan1,5 ✉
**date**::   ```2024-01-16 15:00 ```
**tags**:: #papiers/stageS2 
**groupe**:: Health
**sous-groupe**:: #AI/datasets #health/AI  
**pertinence**:: 5
**links**:: https://www.nature.com/articles/s41586-023-06291-2
**modification date**:: ```Tuesday 16th January 2024 15:00:27 ```

```ad-abstract
Large language models (LLMs) have demonstrated impressive capabilities, but the bar for clinical applications is high. Attempts to assess the clinical knowledge of models typically rely on automated evaluations based on limited benchmarks. Here, to address these limitations, we present MultiMedQA, a benchmark combining six existing medical question answering datasets spanning professional medicine, research and consumer queries and a new dataset of medical questions searched online, HealthSearchQA. We propose a human evaluation framework for model answers along multiple axes including factuality, comprehension, reasoning, possible harm and bias. In addition, we evaluate Pathways Language Model[1](https://www.nature.com/articles/s41586-023-06291-2#ref-CR1 "Chowdhery, A. et al. PaLM: scaling language modeling with pathways. Preprint at 
https://doi.org/10.48550/arXiv.2204.02311
(2022).") (PaLM, a 540-billion parameter LLM) and its instruction-tuned variant, Flan-PaLM[2](https://www.nature.com/articles/s41586-023-06291-2#ref-CR2 "Chung, H. W. et al. Scaling instruction-finetuned language models. Preprint at 
https://doi.org/10.48550/arXiv.2210.11416
(2022).") on MultiMedQA. Using a combination of prompting strategies, Flan-PaLM achieves state-of-the-art accuracy on every MultiMedQA multiple-choice dataset (MedQA[3](https://www.nature.com/articles/s41586-023-06291-2#ref-CR3 "Jin, D. et al. What disease does this patient have? A large-scale open domain question answering dataset from medical exams. Appl. Sci. 11, 6421 (2021)."), MedMCQA[4](https://www.nature.com/articles/s41586-023-06291-2#ref-CR4 "Pal, A., Umapathi, L. K. & Sankarasubbu, M. MedMCQA: a large-scale multi-subject multi-choice dataset for medical domain question answering. In Conference on Health, Inference, and Learning 248–260 (Proceedings of Machine Learning Research, 2022)."), PubMedQA[5](https://www.nature.com/articles/s41586-023-06291-2#ref-CR5 "Jin, Q., Dhingra, B., Liu, Z., Cohen, W. W. & Lu, X. PubMedQA: a dataset for biomedical research question answering. Preprint at 
https://doi.org/10.48550/arXiv.1909.06146
(2019).") and Measuring Massive Multitask Language Understanding (MMLU) clinical topics[6](https://www.nature.com/articles/s41586-023-06291-2#ref-CR6 "Hendrycks, D. et al. Measuring massive multitask language understanding. Preprint at 
https://doi.org/10.48550/arXiv.2009.03300
(2020).")), including 67.6% accuracy on MedQA (US Medical Licensing Exam-style questions), surpassing the prior state of the art by more than 17%. However, human evaluation reveals key gaps. To resolve this, we introduce instruction prompt tuning, a parameter-efficient approach for aligning LLMs to new domains using a few exemplars. The resulting model, Med-PaLM, performs encouragingly, but remains inferior to clinicians. We show that comprehension, knowledge recall and reasoning improve with model scale and instruction prompt tuning, suggesting the potential utility of LLMs in medicine. Our human evaluations reveal limitations of today’s models, reinforcing the importance of both evaluation frameworks and method development in creating safe, helpful LLMs for clinical applications.
```

## Notes
```ad-quote
Medicine is a humane endeavour in which language enables key interactions for and between clinicians, researchers and patients. Yet, today’s artificial intelligence (AI) models for applications in medicine and healthcare have largely failed to fully utilize language. These models,
although useful, are predominantly single-task systems (for example, for classification, regression or segmentation) lacking expressivity and
interactive capabilities.
```

- L'arrivée des LLM's offre une opportunité d'intégrer plus efficacement les intelligences artificielles en médecine.

- Le papier présente un nouveau dataset, MultiMedQA afin d'évaluer les LLMs pour répondre aux questions médicales : s'etendant sur examen medicale, recherche médicale, questions médicales des consommateurs.

- Ils ont évalué Palm et Flan-PalM sur le MultiMedQA.
![[Pasted image 20240116150836.png]]


```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
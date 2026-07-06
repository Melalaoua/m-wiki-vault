x²**authors**:: [Harsha Nori](https://arxiv.org/search/cs?searchtype=author&query=Nori,+H), [Nicholas King](https://arxiv.org/search/cs?searchtype=author&query=King,+N), [Scott Mayer McKinney](https://arxiv.org/search/cs?searchtype=author&query=McKinney,+S+M), [Dean Carignan](https://arxiv.org/search/cs?searchtype=author&query=Carignan,+D), [Eric Horvitz](https://arxiv.org/search/cs?searchtype=author&query=Horvitz,+E)
**date**::   ```2024-01-16 11:14 ```
**tags**::  #papiers/stageS2 
**groupe**:: Health
**sous-groupe**:: #health/AI 
**pertinence**:: 6
**links**:: https://arxiv.org/abs/2303.13375
**modification date**:: ```Tuesday 16th January 2024 11:14:04 ```

```ad-abstract
Large language models (LLMs) have demonstrated remarkable capabilities in natural language understanding and generation across various domains, including medicine. We present a comprehensive evaluation of GPT-4, a state-of-the-art LLM, on medical competency examinations and benchmark datasets. GPT-4 is a general-purpose model that is not specialized for medical problems through training or engineered to solve clinical tasks. Our analysis covers two sets of official practice materials for the USMLE, a three-step examination program used to assess clinical competency and grant licensure in the United States. We also evaluate performance on the MultiMedQA suite of benchmark datasets. Beyond measuring model performance, experiments were conducted to investigate the influence of test questions containing both text and images on model performance, probe for memorization of content during training, and study probability calibration, which is of critical importance in high-stakes applications like medicine. Our results show that GPT-4, without any specialized prompt crafting, exceeds the passing score on USMLE by over 20 points and outperforms earlier general-purpose models (GPT-3.5) as well as models specifically fine-tuned on medical knowledge (Med-PaLM, a prompt-tuned version of Flan-PaLM 540B). In addition, GPT-4 is significantly better calibrated than GPT-3.5, demonstrating a much-improved ability to predict the likelihood that its answers are correct. We also explore the behavior of the model qualitatively through a case study that shows the ability of GPT-4 to explain medical reasoning, personalize explanations to students, and interactively craft new counterfactual scenarios around a medical case. Implications of the findings are discussed for potential uses of GPT-4 in medical education, assessment, and clinical practice, with appropriate attention to challenges of accuracy and safety.
```

## Notes
- Evaluation de GPT-4 en examination médicale et sur des datasets de benchmarkings medicaux.
- Evaluation sur un programme en trois étapes évaluant la capacité d'examiner cliniquement et obtenir une licence (USMLE).
- Evaluation sur le dataset MultiMedQA.
- Evaluation avec du [[Zero-shot Prompting]] mais aussi quelques [[Few-shot Prompting]]
- Surpasse Med-PaLM (pas le 2).
- Le papiers explore la capacité de GPT4 sur des questions textuelles exclusivement, mais aussi des questions qui repose sur des images (bien que ce ne soit pas GPT4V)


Methods for refining the models
toward a particular domain include fine-tuning with specialized datasets drawn from target applications and general methods for steering the behavior of the models, such as reinforcement learning with human feedback ([[Deep Reinforcement Learning from Human Preferences|RLHF]]), which guides the system toward a better understanding of end-users’ requests


![[Pasted image 20240116114729.png]]

- Calibration de GPT-4 : permet de limiter les hallucinations. 

- En plus de zero-shot, ils ont aussi effectué du [[Chain-of-Thought Prompting]] 

```ad-quote
 GPT-4 and its
successors can make contributions to clinical reasoning and daily workflows of medical practice. Beyond
uses in decision support, memory jogging, and administrative tasks, GPT-4 and its successors may one
day assist investigators with clinical and biomedical research.
```

### Les risques cités dans le papier :
- Inaccurate recommendation about rankings (DDx)
- Sequencing (informtion gathering testing)
- Hallucinations : "ability to interleave inaccurate and ungrounded assertion with accurate generations".
- Risque de biais envers les populations marginalisées

GPT-4 and its successors coulbe leveraged to provide healthcare practitioners with analytics, reminders and decision support, including assistance with the formulation and revision of differential diagnoses from patient history, physical findings and lab results.

```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
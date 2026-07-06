**authors**:: [Daniel McDuff](https://arxiv.org/search/cs?searchtype=author&query=McDuff,+D), [Mike Schaekermann](https://arxiv.org/search/cs?searchtype=author&query=Schaekermann,+M), [Tao Tu](https://arxiv.org/search/cs?searchtype=author&query=Tu,+T), [Anil Palepu](https://arxiv.org/search/cs?searchtype=author&query=Palepu,+A), [Amy Wang](https://arxiv.org/search/cs?searchtype=author&query=Wang,+A), [Jake Garrison](https://arxiv.org/search/cs?searchtype=author&query=Garrison,+J), [Karan Singhal](https://arxiv.org/search/cs?searchtype=author&query=Singhal,+K), [Yash Sharma](https://arxiv.org/search/cs?searchtype=author&query=Sharma,+Y), [Shekoofeh Azizi](https://arxiv.org/search/cs?searchtype=author&query=Azizi,+S), [Kavita Kulkarni](https://arxiv.org/search/cs?searchtype=author&query=Kulkarni,+K), [Le Hou](https://arxiv.org/search/cs?searchtype=author&query=Hou,+L), [Yong Cheng](https://arxiv.org/search/cs?searchtype=author&query=Cheng,+Y), [Yun Liu](https://arxiv.org/search/cs?searchtype=author&query=Liu,+Y), [S Sara Mahdavi](https://arxiv.org/search/cs?searchtype=author&query=Mahdavi,+S+S), [Sushant Prakash](https://arxiv.org/search/cs?searchtype=author&query=Prakash,+S), [Anupam Pathak](https://arxiv.org/search/cs?searchtype=author&query=Pathak,+A), [Christopher Semturs](https://arxiv.org/search/cs?searchtype=author&query=Semturs,+C), [Shwetak Patel](https://arxiv.org/search/cs?searchtype=author&query=Patel,+S), [Dale R Webster](https://arxiv.org/search/cs?searchtype=author&query=Webster,+D+R), [Ewa Dominowska](https://arxiv.org/search/cs?searchtype=author&query=Dominowska,+E), [Juraj Gottweis](https://arxiv.org/search/cs?searchtype=author&query=Gottweis,+J), [Joelle Barral](https://arxiv.org/search/cs?searchtype=author&query=Barral,+J), [Katherine Chou](https://arxiv.org/search/cs?searchtype=author&query=Chou,+K), [Greg S Corrado](https://arxiv.org/search/cs?searchtype=author&query=Corrado,+G+S), [Yossi Matias](https://arxiv.org/search/cs?searchtype=author&query=Matias,+Y), [Jake Sunshine](https://arxiv.org/search/cs?searchtype=author&query=Sunshine,+J), [Alan Karthikesalingam](https://arxiv.org/search/cs?searchtype=author&query=Karthikesalingam,+A), [Vivek Natarajan](https://arxiv.org/search/cs?searchtype=author&query=Natarajan,+V)
**date**::   ```2024-01-16 09:42 ```
**tags**:: #papiers/stageS2 
**groupe**:: Health
**sous-groupe**:: #health/AI #health/diagnosis 
**pertinence**::  8
**links**:: https://arxiv.org/abs/2312.00164
**modification date**:: ```Tuesday 16th January 2024 09:42:59 ```

```ad-abstract
An accurate differential diagnosis (DDx) is a cornerstone of medical care, often reached through an iterative process of interpretation that combines clinical history, physical examination, investigations and procedures.

Interactive interfaces powered by Large Language Models (LLMs) present new opportunities to both assist and automate aspects of this process. In this study, we introduce an LLM optimized for diagnostic reasoning, and evaluate its ability to generate a DDx alone or as an aid to clinicians. 20 clinicians evaluated 302 challenging, real-world medical cases sourced from the New England Journal of Medicine (NEJM) case reports. Each case report was read by two clinicians, who were randomized to one of two assistive conditions: either assistance from search engines and standard medical resources, or LLM assistance in addition to these tools. All clinicians provided a baseline, unassisted DDx prior to using the respective assistive tools. Our LLM for DDx exhibited standalone performance that exceeded that of unassisted clinicians (top-10 accuracy 59.1% vs 33.6%, [p = 0.04]). Comparing the two assisted study arms, the DDx quality score was higher for clinicians assisted by our LLM (top-10 accuracy 51.7%) compared to clinicians without its assistance (36.1%) (McNemar’s Test: 45.7, p < 0.01) and clinicians with search (44.4%) (4.75, p = 0.03). Further, clinicians assisted by our LLM arrived at more comprehensive differential lists than those without its assistance. Our study suggests that our LLM for DDx has potential to improve clinicians diagnostic reasoning and accuracy in challenging cases, meriting further real-world evaluation for its ability to empower physicians and widen patients’ access to specialist-level expertise
```

## Notes
- Accurate Differential diagnosis (DDx) est central en médecine, il est pour l'instant obtenu par la combinaison du passé clinique, l'examination physique, investigations et procédures.
- Le papiers introduit un LLM optimisé pour le  diagnostique.
- Le LLM réalise un DDx soit seul, soit avec l'aide des practiciens.
- Ils ont prit 20 cliniciens pour étudier 302 cas issus de la NEJM (New England Journal of Medicine).

- 2 cliniciens sont prit au hasard chacun réalisant l'un des deux étapes suivantes : 
	1. Assistés par les pratiques de recherches et ressources médicales habituelles.
	2. Assistés par le LLM en plus des outils en (1). 

- Les cliniciens ont tous réalisés une DDx basique avant de réaliser la tâche ci-dessus.
- Le LLM a réalisé une DDx meilleure que celles des cliniciens en (1).

- Un diagnostic précis est un composant critique en médecine. Construire des systèmes AI capable de performer et/ou assister les cliniciens dans le diagnostic est une tâche importante qui pourrait révolutionner la médecine telle qu'on la connait. 
- Le DDx est un processus qui implique des étapes de raisonnement intensive et répétitives, amenant à jauger multiples potentiels diagnostics.
- Des méthodes de deep learning ont déjà été développée auparavant, toutefois les LLMs apportent une nouvelle saveur à l'équation : le **dialogue**. C'est l'un des forces des LLMs et qui est essentiel à la reflexion, la capacité de pouvoir dialoguer avec (ou avec lui-même) pour avancer dans le raisonnement.

- Mise en place d'un LLM dans un contexte iteratif, c'est à dire ils ont développé un interface pour permettre au LLM d'interagir avec le practiciens pour l'assister dans son diagnostic.

 ```ad-quote
 Our key contributions can be summarized as:
• Introducing an LLM for DDx, a model optimized for differential diagnosis, alongside a user interface
allowing clinicians to interact with the model for improving clinical diagnostic reasoning.
• Evaluating the performance of the LLM on challenging diagnostic cases from the NEJM Case Reports.
• Showing that the LLM outperforms the prior state of the art, GPT-4, in both top-1 and top-10 accuracy
on this benchmark under automated evaluation.
• Evaluating the impact of the LLM as an assistive tool for clinicians in differential diagnosis, with
randomized comparison to the usual practice in which clinicians are assisted by Search and their usual
clinical resources.
```

- Le LLM a été évalué en [[Zero-shot Prompting]] : "You are a helpful medical assistant. You will be provided and asked about a complicated clinical case; read it carefully and then provide a diverse and thorough DDx"

![[Pasted image 20240116102648.png]]

- Mise en place d'un interface pour interagir avec le LLM (comme ChatGPT).



### Détails techniques.
- le LLM repose sur PALM-2 (tout comme  Med-Palm-2).
- Fine-tuned avec QA answering (multiple et longue questions), note summarization, medical dialogue génération et electronic health record : MultiMedQA.


```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
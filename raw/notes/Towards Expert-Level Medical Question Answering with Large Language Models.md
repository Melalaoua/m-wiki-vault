**authors**:: [Karan Singhal](https://arxiv.org/search/cs?searchtype=author&query=Singhal,+K), [Tao Tu](https://arxiv.org/search/cs?searchtype=author&query=Tu,+T), [Juraj Gottweis](https://arxiv.org/search/cs?searchtype=author&query=Gottweis,+J), [Rory Sayres](https://arxiv.org/search/cs?searchtype=author&query=Sayres,+R), [Ellery Wulczyn](https://arxiv.org/search/cs?searchtype=author&query=Wulczyn,+E), [Le Hou](https://arxiv.org/search/cs?searchtype=author&query=Hou,+L), [Kevin Clark](https://arxiv.org/search/cs?searchtype=author&query=Clark,+K), [Stephen Pfohl](https://arxiv.org/search/cs?searchtype=author&query=Pfohl,+S), [Heather Cole-Lewis](https://arxiv.org/search/cs?searchtype=author&query=Cole-Lewis,+H), [Darlene Neal](https://arxiv.org/search/cs?searchtype=author&query=Neal,+D), [Mike Schaekermann](https://arxiv.org/search/cs?searchtype=author&query=Schaekermann,+M), [Amy Wang](https://arxiv.org/search/cs?searchtype=author&query=Wang,+A), [Mohamed Amin](https://arxiv.org/search/cs?searchtype=author&query=Amin,+M), [Sami Lachgar](https://arxiv.org/search/cs?searchtype=author&query=Lachgar,+S), [Philip Mansfield](https://arxiv.org/search/cs?searchtype=author&query=Mansfield,+P), [Sushant Prakash](https://arxiv.org/search/cs?searchtype=author&query=Prakash,+S), [Bradley Green](https://arxiv.org/search/cs?searchtype=author&query=Green,+B), [Ewa Dominowska](https://arxiv.org/search/cs?searchtype=author&query=Dominowska,+E), [Blaise Aguera y Arcas](https://arxiv.org/search/cs?searchtype=author&query=Arcas,+B+A+y), [Nenad Tomasev](https://arxiv.org/search/cs?searchtype=author&query=Tomasev,+N), [Yun Liu](https://arxiv.org/search/cs?searchtype=author&query=Liu,+Y), [Renee Wong](https://arxiv.org/search/cs?searchtype=author&query=Wong,+R), [Christopher Semturs](https://arxiv.org/search/cs?searchtype=author&query=Semturs,+C), [S. Sara Mahdavi](https://arxiv.org/search/cs?searchtype=author&query=Mahdavi,+S+S), [Joelle Barral](https://arxiv.org/search/cs?searchtype=author&query=Barral,+J), [Dale Webster](https://arxiv.org/search/cs?searchtype=author&query=Webster,+D), [Greg S. Corrado](https://arxiv.org/search/cs?searchtype=author&query=Corrado,+G+S), [Yossi Matias](https://arxiv.org/search/cs?searchtype=author&query=Matias,+Y), [Shekoofeh Azizi](https://arxiv.org/search/cs?searchtype=author&query=Azizi,+S), [Alan Karthikesalingam](https://arxiv.org/search/cs?searchtype=author&query=Karthikesalingam,+A), [Vivek Natarajan](https://arxiv.org/search/cs?searchtype=author&query=Natarajan,+V)
**date**::   ```2024-01-16 15:14 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI
**sous-groupe**:: #AI/models  
**pertinence**:: 8
**links**:: https://arxiv.org/abs/2305.09617  
**modification date**:: ```Tuesday 16th January 2024 15:14:06 ```

```ad-abstract
Recent artificial intelligence (AI) systems have reached milestones in "grand challenges" ranging from Go to protein-folding. The capability to retrieve medical knowledge, reason over it, and answer medical questions comparably to physicians has long been viewed as one such grand challenge.  
Large language models (LLMs) have catalyzed significant progress in medical question answering; Med-PaLM was the first model to exceed a "passing" score in US Medical Licensing Examination (USMLE) style questions with a score of 67.2% on the MedQA dataset. However, this and other prior work suggested significant room for improvement, especially when models' answers were compared to clinicians' answers. Here we present Med-PaLM 2, which bridges these gaps by leveraging a combination of base LLM improvements (PaLM 2), medical domain finetuning, and prompting strategies including a novel ensemble refinement approach.  
Med-PaLM 2 scored up to 86.5% on the MedQA dataset, improving upon Med-PaLM by over 19% and setting a new state-of-the-art. We also observed performance approaching or exceeding state-of-the-art across MedMCQA, PubMedQA, and MMLU clinical topics datasets.  
We performed detailed human evaluations on long-form questions along multiple axes relevant to clinical applications. In pairwise comparative ranking of 1066 consumer medical questions, physicians preferred Med-PaLM 2 answers to those produced by physicians on eight of nine axes pertaining to clinical utility (p < 0.001). We also observed significant improvements compared to Med-PaLM on every evaluation axis (p < 0.001) on newly introduced datasets of 240 long-form "adversarial" questions to probe LLM limitations.  
While further studies are necessary to validate the efficacy of these models in real-world settings, these results highlight rapid progress towards physician-level performance in medical question answering.
```

## Notes

- Papier de Google introduisant Med-Palm-2, la suite de [[Large Language models encode clinical knowledge]]

Our key contributions are summarized as follows:
• We developed Med-PaLM 2, a new medical LLM trained using a new base model (PaLM 2 [4]) and
targeted medical domain-specific finetuning (Section 3.2).
• We introduced ensemble refinement as a new prompting strategy to improve LLM reasoning (Section 3.3).
• Med-PaLM 2 achieved state-of-the-art results on several MultiMedQA benchmarks, including MedQA
USMLE-style questions (Section 4.1).
• Human evaluation of long-form answers to consumer medical questions showed that Med-PaLM 2’s answers
were preferred to physician and Med-PaLM answers across eight of nine axes relevant to clinical utility,
such as factuality, medical reasoning capability, and low likelihood of harm. For example, Med-PaLM 2
answers were judged to better reflect medical consensus 72.9% of the time compared to physician answers
(Section 4.2 and Figure 1).
• Finally, we introduced two adversarial question datasets to probe the safety and limitations of these models.
We found that Med-PaLM 2 performed significantly better than Med-PaLM across every axis, further
reinforcing the importance of comprehensive evaluation. For instance, answers were rated as having low
risk of harm for 90.6% of Med-PaLM 2 answers, compared to 79.4% for Med-PaLM. (Section 4.2, Figure 5,
and Table A.3).
 
![[Pasted image 20240116154227.png]]


- Introduction d'une nouvelle technique de prompting proche du [[Self-Consistency]], et autre techniques de prompting.

- Evaluation de Med-Palm-2 sur [[Large Language models encode clinical knowledge|MultiMedQA]]. Mais aussi :
	- Pour les réponses multiples : [MedQA](https://arxiv.org/abs/2009.13081), [MedMCQA](https://arxiv.org/abs/2203.14371) [PubMedQA](https://arxiv.org/abs/1909.06146), [[Measuring Massive Multitask Language Understanding]].
	- Pour les questions longues : Deux sets de questions issuent de [[Large Language models encode clinical knowledge|MultimedQA]], [HealthSearchQA](https://trec.nist.gov/pubs/trec26/papers/Overview-QA.pdf), [MedicationQA](https://pubmed.ncbi.nlm.nih.gov/31437878/)
![[Pasted image 20240116163353.png]]

- Finetune du model via  la méthode de [[Scaling Instruction-Finetuned Language Models]].

### Prompting

- Few-Shot prompting  ([[Language Models are Few-Shot Learners|papier]]) : donner quelques exemples au LLM avec les réponses à ces exemples avant d'énoncer le problème auquel on attend une réponse de la part du modèle. Le Few-shot est une base solide pour prompt les LLMs. Ils ont utilisé les mêmes prompts que [[Large Language models encode clinical knowledge]].

 - Chain of Thought ([[Chain-of-Thought Prompting Elicits Reasoning in Large Language Models|papier]]) implique d'augmenter les exemples Few-Shot avec une explication étape-par-étape (step by step) vers la réponse finale. Ceci permet au LLM de lui procéder à une explication étape par étape de son raisonnement. 

- Self-consistency ([[Towards Understanding Chain-of-Thought Prompting - An empirical Study of What Matters|papier]]) est une stratégie qui implique d'augmenter l'efficacité du LLM sur des questions multiples en prenant un échantillon de plusieurs explications et réponses du modèle sur une même question. La réponse finale est celle avec une majorité de vote.

- Ensemble Refinement : Développé par les auteurs du papier et se basant sur le CoT et le Self-consistency. L'ER consiste à conditionner le LLM sur ses propres générations avant de produire la réponse finale, se base sur [[Self-Refine - Iterative Refinement with Self-Feedback|Self-Refine]] .

L'ER est constitué de deux étapes : 
1. CoT prompt avec une question : le modèle produit plusieurs réponses possibles avec des températures différentes. Chaque réponse implique une explication ainsi qu'une réponse. 
2. Le modèle est conditionné sur la prompt originelle, la question, et les réponses de l'étapes 1 concaténés, il va produire une réponse raffinée.
![[Pasted image 20240117121340.png]]



```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
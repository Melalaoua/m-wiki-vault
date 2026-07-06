 tags:: #master/StageS4 




Le stage concerne l'intégration des intelligences artificielles dans le service diagnostique des hôpitaux de Strasbourg. L'idée est d'entrainer un modèle d'intelligence artificielle (probablement un [[LLM Models]]) sur des données de séquençage génétique pour des maladies génétiques rare. La principale étant [[GE20 - Les ciliopathies|Bardet-Biedl]]

La recherche bibliographique du stage  se divise en multiples grands axes à prendre en compte durant la conception du projet :  
1. [[STG02 - Modèle économique]] : le coût d'intégrer un modèle ? Quel matériel ?  
2. [[STG02 - Data & Privacy]] : Le modèle repose sur des données de santé, un réel enjeu législatif est à prendre en compte
3. [[STG02 - Intelligences Artificielles]] : Comment entrainer, développer un modèle ? Sur quels données ? Quel but ?

Un véritable recherche bibliographique doit être établie afin d'étoffer ces 3 grands axes. 
- Faire une recherche sur comment au mieux intégrer une IA en médecine ? Comment faciliter la tâche des practiciens ? Qu'es-ce qui pourrait au mieux alléger ces derniers (taches répétitives, ...)
- Recherche de modèles LLM open source.
- Recherche du coût d'intégration d'un modèle "in-house"

Cette recherche bibliographique est complétée par un [[STG02 - Recherche biliographique|rapport bibliographique]] qui devra être rendu et présenté le 20/03/2024.

### Brainstorming:
- ~~Lire les papiers sur la méthode RAG : faire une liste des avantages et limites (potentiel candidat avec le Self-RAG)
- ~~Lire papier KBQA : faire une liste des avantages et limites. (la technique ne sera probablement pas utilisée tho)
- Recherche limites des LLM
- ~~Recherche sur les knowledge-graph
- ~~lire https://aimodels.substack.com/p/ai-discovers-new-solutions-to-2-famous?r=2ggphj ~~
- ~~lire https://www.nngroup.com/articles/ai-prompt-structure/?ref=refind ~~
- ~~lire https://huggingface.co/blog/2023-in-llms ~~
- ~~Modèles open-source : [Falcon](https://arxiv.org/abs/2311.16867), [Mixtral](https://arxiv.org/abs/2401.04088?utm_source=substack&utm_medium=email) ? Comment faire tourner efficacement les modèles ? Le coût ?~~ 
- ~~Lire papier Med-Palm-2 (Une compréhension de la méthodologie de Google dans la médecine est essentielle).~~
- ~~regarder https://d223302.github.io/AACL2022-Pretrain-Language-Model-Tutorial/~~

- ~~Etudier la "pipeline" de Mr. Muller dans l'étude d'un patient BBS (détecter les tâches répétitives, complexes, simples, ...)~~

- Les AI agents : [1](https://github.com/yoheinakajima/babyagi), [2](https://github.com/Significant-Gravitas/AutoGPT), [3](https://lilianweng.github.io/posts/2023-06-23-agent/), [4](https://lilianweng.github.io/posts/2023-06-23-agent/)

- Embeddings : [1](https://simplicityissota.substack.com/p/what-is-an-embedding-anyways), [2](https://making.dia.com/embedding-everything-for-anything2anything-recommendations-fca7f58f53ff), [3](https://roycoding.com/blog/2022/embeddings.html), [FlagEmbedding], [Voyage AI]

- Lire papiers Zero-shot-CoT, selection-inference, maieutic prompting, [Bex's prompt engineering](https://github.com/brexhq/prompt-engineering), [prompting guide.ai](https://www.promptingguide.ai/fr), [Lil's log](https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/), 

- Lire papiers vulnerabilities : hackAPrompt, [Task contamination](https://browse.arxiv.org/html/2312.16337v1), [Humanize LLM](https://chats-lab.github.io/persuasive_jailbreaker/?utm_source=substack&utm_medium=email), [Lil's Log](https://lilianweng.github.io/posts/2023-10-25-adv-attack-llm/)

- https://github.com/huggingface/peft pour fine-tuning

- ~~Article sur ce qui a été fait par les [LLM en 2023](https://simonwillison.net/2023/Dec/31/ai-in-2023/)~~

- Ecouter [podcast](https://open.spotify.com/episode/2rAXyDfhdzgW6oo6iN0khH?si=sSqqzfdKSaC-tpYzi4MCAA&nd=1&dlsi=26cba6c53a6248e3) 

- ~~Les AI en génétique ?? faire des recherches~~

- Finir de lire [[Retrieval-Augmented Generation for Large Language Models - A Survey]]

-  ~~Lire ACMG (suite)~~

- Lire https://blog.research.google/2020/07/announcing-scann-efficient-vector.html

- https://ann-benchmarks.com/glove-100-angular_10_angular.html

###  [[STG02 - Papiers|Papiers]].
*Trop volumineux donc divisé dans une autre page*.

### 30/01/2024 -  Début de la conception du système.
Le système est divisé en 4 agents qui auront des tâches bien définies. Une hydre à 5 têtes.
- [[STG02 - Planne|Planner]] : Contrôle le flux d'information et distribue les différentes informations aux différents agents. Reste à déterminer si ce serait un LLM. 
- [[STG02 - Evaluation des variants|Agent Génétique]] : Cet agent va in-fine réaliser une classification ACMG d'un variant
- [[STG02 - Evaluation des patients cliniques par phénotypes|Agent Clinique]] : Effectue un diagnostic possible du patient à partir des données cliniques
- [[STG02 - Knowledge-Base sur la partie théorie du gène|Agent Théorique]] : Repose sur une Knowledge-Base afin d'établir un maximum de données sur un gène
- [[STG02 -  Prise de décision à partir de la Génétique, Clinique et Théorique|Décisionnaire]]  : à partir du résultats des 3 agents précédents, effectue un bilan total du patient.

##### Remarques : 
- La quantité d'agents est totalement modulable, on peut rajouter ou en éliminer.
- Les agents impliqués peut être modulable. Par exemple, l'agent théorique peut être appelé que si nécessaire, lorsque la décision est trop complexe/nécessite plus de ressources.
- Les agents peuvent être appelés plusieurs fois. Par exemple, l'agent génétique peut être appelé une première fois pour un set plus petit de variants annoté x. L'agent peut être appelé une seconde fois pour effectué une analyse sur plus de variants Z (x compris dans  Z, Z > x)
### Réunions.

- [[STG02 - Réunion 18 Janvier 2024]]






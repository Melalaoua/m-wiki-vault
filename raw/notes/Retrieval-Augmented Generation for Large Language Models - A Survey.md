**authors**:: [Yunfan Gao](https://arxiv.org/search/cs?searchtype=author&query=Gao,+Y), [Yun Xiong](https://arxiv.org/search/cs?searchtype=author&query=Xiong,+Y), [Xinyu Gao](https://arxiv.org/search/cs?searchtype=author&query=Gao,+X), [Kangxiang Jia](https://arxiv.org/search/cs?searchtype=author&query=Jia,+K), [Jinliu Pan](https://arxiv.org/search/cs?searchtype=author&query=Pan,+J), [Yuxi Bi](https://arxiv.org/search/cs?searchtype=author&query=Bi,+Y), [Yi Dai](https://arxiv.org/search/cs?searchtype=author&query=Dai,+Y), [Jiawei Sun](https://arxiv.org/search/cs?searchtype=author&query=Sun,+J), [Qianyu Guo](https://arxiv.org/search/cs?searchtype=author&query=Guo,+Q), [Meng Wang](https://arxiv.org/search/cs?searchtype=author&query=Wang,+M), [Haofen Wang](https://arxiv.org/search/cs?searchtype=author&query=Wang,+H)
**date**::   ```2024-01-22 10:09 ```
**tags**::  #papiers/stageS2 
**groupe**:: AI - PROMPTING
**sous-groupe**:: #AI/prompting 
**pertinence**:: 10
**links**:: https://arxiv.org/abs/2312.10997
**modification date**:: ```Monday 22nd January 2024 10:09:53 ```

```ad-abstract
Large Language Models (LLMs) demonstrate significant capabilities but face challenges such as hallucination, outdated knowledge, and non-transparent, untraceable reasoning processes. Retrieval-Augmented Generation (RAG) has emerged as a promising solution by incorporating knowledge from external databases. This enhances the accuracy and credibility of the models, particularly for knowledge-intensive tasks, and allows for continuous knowledge updates and integration of domain-specific information. RAG synergistically merges LLMs' intrinsic knowledge with the vast, dynamic repositories of external databases. This comprehensive review paper offers a detailed examination of the progression of RAG paradigms, encompassing the Naive RAG, the Advanced RAG, and the Modular RAG. It meticulously scrutinizes the tripartite foundation of RAG frameworks, which includes the retrieval , the generation and the augmentation techniques. The paper highlights the state-of-the-art technologies embedded in each of these critical components, providing a profound understanding of the advancements in RAG systems. Furthermore, this paper introduces the metrics and benchmarks for assessing RAG models, along with the most up-to-date evaluation framework. In conclusion, the paper delineates prospective avenues for research, including the identification of challenges, the expansion of multi-modalities, and the progression of the RAG infrastructure and its ecosystem.
```

## Notes
==*"[[Retrieval Augmented Generation|RAG]] synergistically
merges LLMs’ intrinsic knowledge with the vast,
dynamic repositories of external databases.*==

L'explosion cambrienne de modèle LLM en 2023 a donné la mise sur le marché de divers modèles de plus en plus performant ([[GPT-4]], [[LLaMA]], [[Gemini]]) et démontrant de véritables prouesses sur des benchmarks comme Super-GLUE, BIG-Bench, [[Measuring Massive Multitask Language Understanding|MMLU]].

Toutefois, des soucis persistent, comme des risques d'hallucinations. Les LLMs démontrent certaines limites dans des tâches spécifiques ou dans des domaines niches. Les modèles sont limités lorsque les prompts impliquent des données en dehors de leur données d'entrainement (ou nécessite des données datant d'aujourd'hui/ après la cut-off date du modèle).

RAG vient contenir ces limitations en équipant le modèle avec des bases de données externes durant le processus de génération.

- Le RAG implique une première étape de récupération (retrieval) où le LLM va venir questionner les bases de données pour avoir des données externes
- Le LLM peut ensuite répondre à la question initiallement posée.

Le RAG vient tacler/limiter le problème d'hallucination des modèles en se basant sur des données,précédemment récupérée dans la phase de retrieval. Les données peuvent être nettoyées, sourcées, vérifiées, bref un réel contrôle sur la base sur laquelle le modèle va générer sa réponse durant la seconde phase du RAG. 

Le RAG a connu une phase d'adoption rapide, et son évolution s'est divisée en 4 branches principales.

![[Pasted image 20240122102729.png]]


Our contributions are as follows:
• We present a thorough and systematic review of the state-of-the-art RAG, delineating its evolution through paradigms including naive RAG, advanced RAG, and modular RAG. This review contextualizes the broader scope of RAG research within the landscape of LLMs.

• We identify and discuss the central technologies integral to the RAG process, specifically focusing on the aspects of “Retrieval”, “Generator” and “Augmentation”, and delve into their synergies, elucidating how these components intricately collaborate to form a cohesive and
effective RAG framework. 

• We construct a thorough evaluation framework for RAG, outlining the evaluation objectives and metrics. Our comparative analysis clarifies the strengths and weaknesses of RAG compared to fine-tuning from various perspectives. Additionally, we anticipate future directions for RAG, emphasizing potential enhancements to tackle current challenges, expansions into multi-modal settings, and the development of its ecosystem.


#### Définition de RAG.
Dans cette partie, le papier parle de l'arrivée de nouvelles approches répondant aux réponses de "what to retrieve", "when to retrieve" et "how to use" dont RAG a su profiter.

- "What to retrieve" : le papier parle de l'évolution de réucpérer simplement la récupération de tokens  à des méthodes plus complexes comme les [[In-Context Retrieval-Augmented Language Models|chunks]] ou les [[Knowledge Graph-Augmented Language Models for Knowledge-Grounded Dialogue Generation|Knowledge Graph]].

Etapes du RAG:
- Le corpus est partitioné en "discrete chunks" où des indices vectoriels sont construits via un modele encodeur.
- RAG identifies et récupère les chunks en se basant sur la similarité vectorielle de la prompt et des chunks.
- Enfin, le modèle synthétise une réponse en étant conditionné sur les données récupérées et la prompt originale.



### RAG FRAMEWORK
Le papiers introduit 3 types de RAG. 

#### NAIVE RAG.
Le RAG naïf est la méthodologie la première méthodologie du RAG et qui a su être prominente peu après l'adoption massive de ChatGPT. Le RAG naïf suit un processus traditionnel qui inclu l'indexage, le retrieval et la génération.

![[Pasted image 20240122132733.png]]

Limites du RAG Naïf : 
- Le retrieval peut parfois être de basse résolution, menant au retrieval de chunks non pertinent à la query, voir problématique causant des hallucinations du modèle.
- La génération du modèle peut comporter des hallucinations car le modèle génère des réponses qui ne se basent pas sur le contexte fournis.
- Le processus d'augmentation peut être problématique par l'ajout de redondance, répétition (plusieurs passages avec la même information).


#### RAG AVANCE
Développé dans le but de combler les lacunes du RAG naïf, le RAG avancé a raffiné son approche d'indexage en utilisant des techniques telle que le "sliding window", fine-grained segmentation, metadata. Voir https://pub.towardsai.net/advanced-rag-techniques-an-illustrated-overview-04d193d8fec6

##### Pre-Retrieval Process : 
Augmenter la qualité des données qui sont indexées incluant 5 stratégies : **enhancing data granularity, optimizing index structures, adding metadata, alignement optimization, mixed retrieval.**
1. <u>Enhancing data granularity :</u> Elevé la consistence, la précision, pertinence. Ceci inclue enlever l'information inutile, enlever les ambiguïtés, confirmer la précision factuelle, maintenir le contexte, update les documents désués.
2. <u>Optimizing Index structures :</u> Ajuster la taille des chunks afin de capturer des contexte pertinents, "querying across multiple index paths", et incorporer l'information depuis la [[A Gentle Introduction to Graph Neural Networks|structure en graphe]] dans le cadre de données en graphe.
3. <u>Adding metadata information :</u> intégrer des informations comme la date, le but, dans les métadonnées des chunks afin de pouvoir les filtrer de manière plus efficace et pertinente ete intégrer des information comme les chapitres, les sous sections.
4. <u>Alignment optimization :</u> Rajouter des "questions hypothétiques" dans les documents afin de réctifier les problèmes d'alignements et les différences entre les documents ([[Structure-Aware Language Model Pretraining Improves Dense Retrieval on Structured Data|papier]])


##### Retrieval.
- Effectuer un ==fine-tune des enbedding models== permet de significativement impacter la pertinence des contenus récupérés par ce dernier. Il faut donc customizer les embeddings models dans des contexte spécifique au domaine. Le papier cite le [|BGE embedding model](https://github.com/FlagOpen/FlagEmbedding) est un modèle open-source qui peut être fine-tuned afin d'optimiser ses retrieval performances.
- "Training data for fine-tuning can be generated using language models like [[GPT-3|GPT-3.5-turbo]] to formulate questions grounded on document chunks, which are then used as fine-tunig pairs."
- ==Dynamic Embedding== s'adapte au contexte dans lequel les mots sont utilisés, à l'inverse de l'embedding static qui utilise un vecteur unique pour chaque mot. Le modèle ada 02 de openAI est un exemple de modèle d'embedding dynamique très sophistiqué.



##### Post-Retreival.
- ==Re-Ranking ==: Rajoute les éléments importants aux extrémités de la prompt (debut/fin).
- ==Prompt Compression== : Compresse les éléments qui ne sont pas pertinents post-retrieval et met en avant les paragraphes importants, réduisant la taille de la context length.


#### Modular RAG.
Diverge aussi du RAG naïf en étant beaucoup plus flexible et versatile.
- Inclusion d'un module de recherche, fine-tune du retriever
Le modular RAG devient de plus en plus la norme parmi les framework RAG, d'après le papier.

![[Pasted image 20240122142539.png]]



### Modules
- ==**Search module**== : en contraste au retrieval qui lui va faire une recherche de similarité, le module de recherche est adapté à des scénarios spécifiques. Le module inclue une génération d'un code par le LLM (recherche SQL, autre..). Les sources de ces données peuvent inclure des search engines, API, données tabulaires, [[Knowledge Graph]].

- **==[[Lift Yourself Up - Retrieval-augmented Text Generation with Self Memory|Memory module]]==** :Ce module puise dans les capacités de mémorisation par les LLM. La technique consiste à identifier les souvenirs les plus similaires à l'input.

- **==Fusion==** : RAG-FUSION améliore les système de recherche traditionnels en comblant leur lacune au travers d'une approche multi-query qui s'étend de l'input de l'utilisateur à de multiples perspectives diversifiées générées par un LLM. Cette approche, non seulement, capture l'information explicite de l'utilisateur, mais elle dévoile aussi des connaissances enfouies et implicites.
	- Le processus de fusion implique le parallel vector search, re-ranking, pair the best outcomes with new queries.

- **==Routing==** : Utilisation de plusieurs ressources qui diffère par domaine, language et format. Le routeur décide quelles actions prendres à partir de la requête de l'utilisateur : summarization, rechercher des bases de données spécifiques, mélanger différents modules en un. Le routeur décide aussi quelles données sont appropriées par rapport à la requête : vector sotres, graph databases, relational database.

- **==Predict==** : Réponds aux probleèmes de redondances et le bruit générés par le retriever. Plutot que de directement récupérer à partir de la source de données, le module utilise un LLM pour générer un contexte. Le content produit par le LLM est plus enclin à être pertinent comparé à ce qui serait obtenur par un retrieval.

- **==Task Adapter==** : Le module adapte RAG à une variété de tâche en downstream. Permet de généraliser pour développer des tâches spécifique au domaine.


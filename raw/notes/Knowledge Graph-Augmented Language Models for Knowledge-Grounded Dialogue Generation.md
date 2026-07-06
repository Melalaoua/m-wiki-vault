**authors**:: [Minki Kang](https://arxiv.org/search/cs?searchtype=author&query=Kang,+M), [Jin Myung Kwak](https://arxiv.org/search/cs?searchtype=author&query=Kwak,+J+M), [Jinheon Baek](https://arxiv.org/search/cs?searchtype=author&query=Baek,+J), [Sung Ju Hwang](https://arxiv.org/search/cs?searchtype=author&query=Hwang,+S+J)
**date**::   ```2024-01-22 10:39 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI 
**sous-groupe**:: #AI/graphs 
**pertinence**:: 
**links**:: https://arxiv.org/abs/2305.18846
**modification date**:: ```Monday 22nd January 2024 10:39:23 ```

```ad-abstract
Language models have achieved impressive performances on dialogue generation tasks. However, when generating responses for a conversation that requires factual knowledge, they are far from perfect, due to an absence of mechanisms to retrieve, encode, and reflect the knowledge in the generated responses. Some knowledge-grounded dialogue generation methods tackle this problem by leveraging facts from Knowledge Graphs (KGs); however, they do not guarantee that the model utilizes a relevant piece of knowledge from the KG. To overcome this limitation, we propose SUbgraph Retrieval-augmented GEneration (SURGE), a framework for generating context-relevant and knowledge-grounded dialogues with the KG. Specifically, our SURGE framework first retrieves the relevant subgraph from the KG, and then enforces consistency across facts by perturbing their word embeddings conditioned by the retrieved subgraph. Then, we utilize contrastive learning to ensure that the generated texts have high similarity to the retrieved subgraphs. We validate our SURGE framework on OpendialKG and KOMODIS datasets, showing that it generates high-quality dialogues that faithfully reflect the knowledge from KG.
```

## Notes
Les PLMs ([[BERT - pre-training of Deep Bidirectional Transformers for Language Understanding|1]], [[Improving Language Understanding by Generative Pre-Training|2]]) sont capables de générer du texte de manière fluente mais vont être limiter dans la factualisation de leur réponse par manque de connaissances explicites.

Afin de limiter ces hallucinations, des méthodes comme le [[RAG - Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks|RAG]] viennent puiser dans des bases de données externes comme Wikipédia pour baser la réponse du modèle sur des faits.

Ce papier ce concentre sur les Knowledge Graph ([[Knowledge Graph|1]], [[Generate Knowledge Prompting|2]], [[Knowledge-Based Question Answer|3]]), les KG représente la manière la plus compacte et efficace de structuration symbolique des données.

![[Pasted image 20240122105113.png]]

Ce papier propose : 
- Un subgraph retriever [[Graph Neural Network (GNN)|GNN]]-based et context-relevant qui va venir extraire les informations pertinentes à partir des KGs afin de générer une réponse pertinente à la conversation actuelle.
- We propose an invariant yet efficient graph encoder and a graph-text contrastive learning objective to ensure that the generated responses faithfully reflect the retrieved knowledge.
- Validation du SURGE Framework, générant des réponses qui sont plus informative et récupérant des informations pertinentes.





```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
tags:: #thelaboratory/AI 

Les LLM à but général peuvent être fine-tuned afin d'achever plusieurs tâches générales comme l'analyse de sentiment, reconnaissance d'entité... Ces tâches généralement ne requiert pas d'ajout d'informations supplémentaires.

Pour des tâches plus complexes et demandant beaucoup de connaissances, il est possible de construire des modèles de langage basé sur un système qui va aller piocher l'information dans des sources externes. Ceci permet plus de consistance factuelle, améliorer la fiabilité des résultats pour générer des réponses, et aider à mitiger le problème des "hallucinations" par les LLMs.

Les chercheurs à Meta on introduit & nommé cette méthode "Retrieval Augmented Generation (RAG)" afin d'adresser ces tâches intensives. 

RAG combine la recherche d'information à la génération de texte. RAG peut être fine-tuned et ses connaissances internes peuvent être modifiées de manière efficace sans avoir besoin de re-entrainer le modèle en entier.

RAG prend en input et renvoie un set de document important/pertinent pour une source donnée (par exemple Wikipédia). Les document sont concaténés en contexte à partir du prompt original et nourri à générateur de texte qui produit l'output final.

Ceci rend RAG adaptatif pour des prompts originales où les faits peuvent evoluer au cours du temps. C'est très utile vu qu'on sait que les LLMs sont statique (ex : chatGPT est entrainé sur des données allant jusqu'à 2021, 2022 et 2023 sont inconnus).

RAG permet au modèles de bypass le retraining, donnant accès aux dernières actualités et donner des outputs fiables, factuels.

Lewis et al (2021) ont proposé la recette suivante de fine-tuning par RAG, elle est généraliste. a modèle seq2seq déjà entrainé est utilisé comme mémoire paramétrique et un index de vecteur dense provenant de Wikipédia est utilisé comme mémoire non-paramétrique (utilisé via un retriever neuronale pré-entrainé). Ci-dessous l'approche générale :
![[Pasted image 20230713174757.png]]
Source : [Lewis et el.(2021)](https://arxiv.org/pdf/2005.11401.pdf)

RAG effectue plusieurs benchmark sur des datasets comme [Natural Questions](https://ai.google.com/research/NaturalQuestions), [Web Questions](https://paperswithcode.com/dataset/webquestions) et CuratedTrec. RAG génère des réponses qui sont plus factuelles, spécifiques et diversifiées.

Ceci montre le potentiel de la technique RAG et une option sérieuse pour améliorer les outputs des LLMs lors de tâches demandant des connaissances approfondies.

Tu peux trouver [un exemple simple de comment utiliser les retrievers et les LLMs pour du QA sur des sources](https://python.langchain.com/docs/use_cases/question_answering/) dans la documentation de [[Langchain]]

> Suiv [[Automatic Reasoning and Tool-use]]
> Prev [[Tree of Thoughts]]
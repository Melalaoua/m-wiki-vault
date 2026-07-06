tags:: #master/StageS4 


Cet agent établit un profil détaillé du gène sur lequel a été découvert le variant. Il établira une [[Knowledge-Based Question Answer|Knowledge Base]] sur laquelle un [[Transformers Neural Networks|LLM]] établira le profil délivré au [[STG02 -  Prise de décision à partir de la Génétique, Clinique et Théorique|décisionnaire]].

### Architecture.
Un LLM reposant dans une architecture [[RAG - Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks|RAG]].

Il prendra en entrée le nom du gène (autres informations ?) depuis le [[STG02 - Planner|plannificateur]] et effectuera une recherche documentaire sur ce dernier afin d'en établir un profil détaillé.

Les résultats seront archivés dans une [[Vector Databases]]


### Résultats attendus.
Profil détaillé sur le gène

```python
{
 "Fonction du gène" : FonctionGene(),
 "Article Scientifique" : Abstract_Article_Scientifique(),
 "OMIM" : resultats_OMIM(),
 "ClinVar" : resultats_ClinVar()
} 
```


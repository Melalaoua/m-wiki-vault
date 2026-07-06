tags:: #master/StageS4 


Ce module va attribuer une pathogénicité aux variants en se reposant principalement sur [[Howard]] et d'autres sources externes. La pathogénicité du variant respectera les critères [[Standards and guidelines for the interpretation of sequence variants|ACMG]]. Il apportera d'autres informations essentielles pour le [[STG02 -  Prise de décision à partir de la Génétique, Clinique et Théorique|décisionnaire]]. 


### Architecture.
Le coeur de l'agent génétique sera un [[Transformers Neural Networks|Large Language Models]], plus précisément le modèle [[Mixtral of Experts|Mixstral 8x7B]]. 

Le prompting se fera possiblement en [[RAG - Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks|RAG]] (encore à déterminer)

Seront prit en entrée les variants du patients (en batch), émis depuis le [[STG02 - Planner|planner]], au format nomenclature [[Les types de variations du génome humain et leurs conséquences.#Recommandation générales.|HGVS]]  ou format VCF ? (à déterminer)

### Résultats attendus.
Pour un variant de gène donné, les résultats attendus donneront une prévision de la pathogénicité de chaque variant, si le variant a un impact sur la structure de la protéine (si gène codant).

```python
{
	"Variant" : Type_de_variation()
	"Position" : Position(exon ?, intron ?, ...),
	"Fréquence Population" : Frequence(),
	"Classification ACMG-like" : Classification_ACMG(),
	"Perte de fonction" : perte_de_fonction_sur_la_proteine()
}
```


tags: #master/StageS4 



Données en entrées :
- patient ADN2001084 (négatif) : 9 variants
- patient ASG2102975 (positif) : 8 variants



### Critiques 
Problème avec howard : 
- Pas d'HGVS pour les variants en upstream et downstream (exemple : chr11 66278059) : 81 variants vides sans HGVS howard.
- Pas d'annotation de fréquence pour certains variants alors qu'ils existent dans des bases de données comme gnomAD, ExAC.


Problèmes avec l'IA :
- Les variants passent deux fois dans l'IA ce n'est pas normal.
- Les résultats sont mal présentés => du au fait que l'IA Est incapable de générer du JSON correct => à corriger.
- Les prompts sont mal construites, répétitions, mot incohérent (pathogenocity pour un diagnostic ?)
- Hallucine sur les fréquence, hallucine sur les critères ACMG, fait des connections biaisées pour OMIM : vu qu'un champ OMIM existe alors il suggère que c'est un variant pathogène.



/// agent clinique émet hypothèse avec une liste de gène, génétique asses pathogénicité, décisionnaire rassemble tout ///

Il faut une consistence dans tes données pour qu'elles soient comparables entre les différents benchmarks. Back to work





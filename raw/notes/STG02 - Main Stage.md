 tags:: #master/StageS2  


[[STG02 - Recherche bibliographique|Schéma systeme]]

Tester chaque version de kindred avec le temps d'exécution, nombre de variants, nombre de token moyen, qualité de résultats, ...

### Brainstorm
- ~~Faire un module pour prendre en entrée un excel de critères HPO, récupérer le HPO pour chaque patient et ressortir une liste.~~
- Faire le VCF des patients howards restant pour faire un benchmark de la première version.
- Evaluer le resultat du modèle
- L'agent clinique doit output la liste de gènes en lien avec la pathologie
- ~~Mettre en place un benchmark pour évaluer la qualité des résultats ?~~
- Faire un test sur plus de patients ?

- Avoir une démarche **ingénieur**. Quelles données en entrées ? Paramètres de howard ? qu'est ce qui rentre dans l'IA ?
	- Faire une description des données, des patients, du nombres de variants, âge, diagnostic de Mr.Muller
	- Faire une description de howard, quels annotations pour chaque variants, etc..
	- Faire une description des prompts du modèle IA
	- Faire une description des résultats, faire un benchmark sur plusieurs données, calculer le temps, la vitesse pour chaque variant, etc..
	- Faire une description de la qualité des résultats.


### Benchmark du systeme.
Une première ébauche du système a été mise en place, elle est  constituée de l'agent génétique, l'agent clinique et du décisionnaire. L'IA utilisée est [[Mixtral of Experts|Mistral 8x7B]].

- [[STG02 - Kindred - Premier Benchmark|Premier benchmark]] 
- [[STG02 - Kindred - Second Benchmark|Second benchmark]]
- [[STG02 - Kindred - Troisième Benchmark|Troisième benchmark]]
- [[STG02 - Kindred - Quatrième Benchmark|Quatrième benchmark]]

---

Je recommence de zero, j'ai obtenu les modèles quantizés à différents niveaux. Je revois mon approche.

### Benchmark de l'Agent Clinique
Suite à un entretien avec François, l'agent clinique sera testé sur les termes HPO de la cohorte de patient de Mr. Muller. François a réalisé un arbre de décision visant à réaliser un diagnostic à partir des termes HPO. L'agent clinique fera la même chose sur les même données, les deux algorithmes seront comparés.

- [[Benchmark Clinique Kindred - cohortes patients BBS-RP]]

### Benchmark de l'Agent Génétique.
L'agent génétique sera testé sur un workshop du NGS-France.
- [[Benchmark Génétique Kindred - Variants NGS-Diag]]

### Brainstorm pour kindred_v2
- Donner tout ACMG en entrée
- Donner moins d'informations en entrée et se contenter de l'essentiel.
- Inclure les HPO inconnus ? (valeur = 1).
- 
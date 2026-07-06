tags: #master/StageS4 



Données en entrées :
- Variant du Workshop NGS Diag


### Anciennes critiques 
Problème avec howard : 
- Pas d'HGVS pour les variants en upstream et downstream (exemple : chr11 66278059) : 81 variants vides sans HGVS howard.
- Pas d'annotation de fréquence pour certains variants alors qu'ils existent dans des bases de données comme gnomAD, ExAC.


Problèmes avec l'IA :
- Les variants passent 2 fois dans l'IA, ce n'est pas normal.
- Les résultats sont mal présentés => du au fait que l'IA Est incapable de générer du JSON correct => à corriger.
- Les prompts sont mal construites, répétitions, mot incohérent (pathogenocity pour un diagnostic ?)
- Hallucine sur les fréquence, hallucine sur les critères ACMG, fait des connections biaisées pour OMIM : vu qu'un champ OMIM existe alors il suggère que c'est un variant pathogène.



/// agent clinique émet hypothèse avec une liste de gène, génétique asses pathogénicité, décisionnaire rassemble tout ///

Il faut une consistence dans tes données pour qu'elles soient comparables entre les différents benchmarks. Back to work



### Plan d'action.

- [x]  Formater l'IA pour qu'elle soit capable de produire des JSON correctes.  
- [ ] De fait, si les JSON sont valides, produire des résultats lisibles et consistants, comparables entre les différents runs.
- [x] Corriger les prompts qui ont des erreurs de typo et de compréhension.
- [x] Intégrer la classification ACMG dans l'IA.
- [ ] Mettre en place un filtre.
- [x] Retirer OMIM des critères.


### Résolution
~~- Pour le format JSON, cet [article](https://medium.com/@dinber19/enhancing-json-output-with-large-language-models-a-comprehensive-guide-f1935aa724fb) suggère d'utiliser [Jsonformer](https://github.com/1rgs/jsonformer)~~
Nous n'allons pas générer de JSON pour le moment, cela complexifie tout trop rapidement.
Les résultats de l'IA sont très satisfaisants après la résolutions des différents problèmes énoncés ci-dessus, la classification ACMG, et une description des champs howard est donnée en entrée, ce qui améliore grandement l'efficacité de l'outil.

Les résultats de GPT4-o sont beaucoup plus cohérents que ceux de Mixtral 8X7B.

On remarque que l'IA est efficace sur des connecteurs logiques mais elle va tomber dans des pièges très subtiles des variants du workshop. Ainsi, plusieurs problèmes ont été identifiés, à corriger pour le [[STG02 - Kindred - Quatrième Benchmark]].

### Critiques :
- Préciser le treshold des outils - savoir à partir de quelle valeur le treshold est dépassé pour un outil et donc que la variant est détecté délétère par ce dernier.
- Le problème des isoformes. Certaines variants dans certaines isoformes vont être délétère tandis qu'ils ne seront pas dans d'autres, c'était l'un des pièges de l'un des variants, l'IA est tombé dedans ==> ==Possiblement le rôle de l'agent biologique dans cette optique là ?== ==Ou alors séparer les variants / isoformes ? Cela découplerait le temps de calcul de manière considérable.==
- Certains critères sont non superposable, l'IA a par exemple attribué les critères PP3 (outil détecte pathogène) et PVS1 (variant null) alors qu'ils ne sont pas superposables, il faut préciser quels critères ne peuvent pas être attribués.
- Pour les variants d'épissage, il faut préciser la taille des sites canoniques => -2 à +2
- Gpt4-o semble connaître les gènes connus pour avoir des variants faux-sens délétère, c'est interessant.
- Il manque au modèle le mode de transmission des gènes : Dominant, récessif, etc... Il faut donc rajouter la base de données OMIM dans howard.
- Pour la fréquence : si il n'y a pas de fréquence détectée par howard, doit-on considérer le variant comme absent ?
- Pour les gènes à empreinte parentale ? 
- Pour les gènes à pénétrance incomplète ?

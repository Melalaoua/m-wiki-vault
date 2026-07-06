tags: #master/StageS4 



Données en entrées :
- Variants du workshop NGS Diag


Pour les anciennes critiques, se réferer à [[STG02 - Kindred - Troisième Benchmark]].

La première étape est d'[[ACMG NGS Diag v2|extraire les subtilités du mode d'emploi d'interprétation des variants produits par le NGS DIAG (2nde version).]]


### Plan d'action

 - [ ] Préciser le treshold des outils - savoir à partir de quelle valeur le treshold est dépassé pour un outil et donc que la variant est détecté délétère par ce dernier.
 - [ ] Le problème des isoformes. Certaines variants dans certaines isoformes vont être délétère tandis qu'ils ne seront pas dans d'autres, c'était l'un des pièges de l'un des variants, l'IA est tombé dedans ==> ==Possiblement le rôle de l'agent biologique dans cette optique là ?== ==Ou alors séparer les variants / isoformes ? Cela découplerait le temps de calcul de manière considérable.==
 - [x] Certains critères sont non superposable, l'IA a par exemple attribué les critères PP3 (outil détecte pathogène) et PVS1 (variant null) alors qu'ils ne sont pas superposables, il faut préciser quels critères ne peuvent pas être attribués.
 - [x] Refaire l'ACMG (utiliser l'acmg NGS Diag v2).
 - [x] Si fréquence variant absent == variant rare 
 - [ ] Résoudre le problème d'annotation de howard.
 - [x] Pour les variants d'épissage, il faut préciser la taille des sites canoniques => -2 à +2
 - [x] Gpt4-o semble connaître les gènes connus pour avoir des variants faux-sens délétère, c'est interessant.
 - [ ] Il manque au modèle le mode de transmission des gènes : Dominant, récessif, etc... Il faut donc rajouter la base de données OMIM (only gène morbides) dans howard.
 - [x] Pour la fréquence : si il n'y a pas de fréquence détectée par howard, doit-on considérer le variant comme absent ?
 - [ ] Pour les gènes à empreinte parentale ? 
 - [ ] Pour les gènes à pénétrance incomplète ?



### Notes
La corrélation avec le phénotype est indispensable pour le critère PS2
Rajouter un tableau de calcul des scores.
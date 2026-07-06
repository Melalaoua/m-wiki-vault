tags:: #master/génétique 
date:: 04/04/2023
Enseignant :: PR. PITON

Introduction.
	On verra dans ce cours l'utilisation du séquençage directe (approche plus rapide) de tout exome/gène.
	Au début : migration sur gel, puis technique sanger et pour terminer : séquençage haut débit (grande révolution).
	Séquençage de 3e généraiton n'est pas encore très utilisé mais va l'être de plus en plus, cela va permettre d'identifier de nouveaux gènes et nouveaux mécanismes impliqués dans les maladies.)


### I. Séquençage du génome.
---
Prendre ADN -> couper en petits bouts -> mettre des adaptateurs différents de chaque côté. On va visualiser cette lame dans laquelle on fera des réactions de séquençage en parallèle.
- C'est la technique la plus rapide.
- Besoin de beaucoup séquencer : coûté cher -> préfer le séquençage ciblé d'un panel de gène ou d'une partie d'un exome.


#### 1. Séquençage ciblé.
Pour un panel de gène ou l'exome entier.

Réalisation : designer des sondes complémentaires des régions que nous voulons séquencer + incubation des sondes avec l'ADN qu'on veut séquencer pour ne récupérer que les fragments d'ADN complémentaires aux sondes, puis les séquencer.


### II. Séquençage d'exome entier.
---
Le séquençage d'exome entier permet surtout d'identifier de nouveaux gènes liés des pathologies. La variation d'un individu à un autre est d'environ 4000 variations, soit 0.1% du génome humain.

##### 1. Maladies monogéniques.
Dans le cas de la maladie monogénique, on va chercher une mutation responsable de la maladie. Il faut trouver la mutation parmi ces 4000 variations. On se repose sur des programmes afin d'annoter ces variants. Ces programmes vont nous donner une quantité d'informations comme :
- la fréquence dans la populations en se reposant sur des bases de données (GnomAD, ... voir [[GE05+GE07 - Génétique de la bioinformatique]])
- Prédire l'impact de la mutation sur le séquence protéique : variant silencieux, codon STOP, faux sens.
-  Via des algorithmes, tenter de prédire si la mutation sera délétère sur la protéine ou non (rester vigilant).
- Prédire le repliement de la protéine.

Il est possible de chercher dans des bases de données de personnes malades/atteintes (ClinVar) pour regarder si le variant a déjà été retrouvé.


###### A. Syndrome de Miller.
- Trouble de la coordination.
- Hypotonie.
- Dysmorphie faciale.
- Anomalies démentes.

Maladie orpheline : 30 familles dans le monde décrites, avec 1 ou 2 enfants dans la famille. On ne peut pas savoir le mode de transmission de cette maladie, ni faire des études de liaisons génétiques (effectif trop faible). On peut toutefois faire des hypothèses sur le mode de transmission.

**Séquençage de haut débit arrive avec le CGH** : permet l'identification de certains gènes de cette maladie.

Les scientifiques ont regardé 3 choses :
	- NS/SS/I = SNP non-synonymes/variants d'épissage/INDEL = regarder les variants qui impactent la séquence protéique.
	- La présence du variant dans les banques de données générales (dbSNP : base de donnée de variant - HapMap/GnomAD).
Le seul gène qui est ressorti de ces analyses : **DHODH.**

Pour vérifier la pathogénicité du variant, et l'implication fonctionnelle du gène, il faut regarder si ce gène est présent chez les autres patients malades et faire des expériences sur des modèles anmiaux : KO sur souris, drosophile, zebrafish.


### III. Séquençage d'exome vs séquençage du génome.
---
En vert : séquençage du génome.
En rouge : séquençage d'exome.

Le séquençage d'exome par défiinition ne comporte pas d'éléments introniques. Des variations dans ces zones là ne seront pas détectés comme par exemple la création d'un site d'épissage alternatif, une expansion intronique, rétention d'introns.

Le séquençage du génome permet de récuperer les 3'/5' UTR, les zones introniques, les régions régulatrices du promoteur mais aussi :
- Voir les éléments transposables.
- La mutation de microRNA, mutation dans des séquences de polyadénylation.

Exemple des variations qu'on peut retrouver grâce au séquençage du génome :
(image)

Des tests fonctionneles peuvent être fait sur le promoteur ou les UTR : 
- Prendre la séquence sauvage et celle du rapporteur en aval -> regarder l'expression du variant.
- Regarder l'expression du gène concerné par une RT-qPCR ou un RNAseq (transcriptome complet).

#### A. RNAseq.
La RNAseq permet de voir les conséquences d'un variant mais aussi d'identifier des variants chez des personnes non détectés par séquençage.
Le RNAseq permet de séquencer tous les isoformes d'un gène, permettant de voir les altérations dans l'expression et dans l'épissage.

La difficulté se trouve dans le choix du tissu prélevé, il faut choisir un tissu où le gène cible est exprimé. Les cellules iPS sont de bons candidats qui seront redifférenciées en un tissu choisi.


### IV. Conclusion : identification de gènes de maladies monogéniques.
---
Image



# Identification des facteurs génétiques dans les maladies monogéniques et multifactorielles.
==
La génétique de maladies multifactorielles, c'est l'identification de plusieurs facteurs impliqués dans une maladie génétique donnée (facteurs environnementaux et génétiques).

Les polymorphismes, dans certains gènes, peuvent prédisposer (ou protéger) à une maladie en interaction avec des facteurs de l'environnement (alimentaire, cigarette, infection, stress). L'accumulation de plusieurs facteurs génétique/environnementaux peut amener au développement de la maladie.

La génétique et l'environnement vont être dissocié dans ce cours, l'idée est d'essayer d'identifier les facteurs de risque, et les classer selon les "risques" de la maladie.

Exemple de maladies multifactorielles : maladies métaboliques (diabète de type 1 et 2), maladies neurologiques (alzheimer, sclérose en plaque), maladies psychiatriques (schizophrénie, bipolarité).

Un spectre de maladies génétiques nous est présenté en diapositive 4 : 
- **Huntington** : si il y a une mutation dans le gène, la maladie a 100% de risque de se développer.
- **PCU** : on aurait pu penser comme une maladie 100% génétique, mais l'environnement semble apporter un effet protecteur.
- **Lèpre** : les personnes exposées ne tombent jamais malade. C'est une maladie environnemental car il faut êtr exposé au pathogène. Mais la génétique  ne permet de résister ou non à la maladie.
- Schizophrénie et maniaco-dépression : Déterminée par des facteurs génétiques et environnementaux.
- Varicelle : pas de prédisposition génétique, c'est une maladie 100% environnementale. 


### I. Mesure de la part environnemental et génétique.
---

#### 1 Agrégation familiale.
On regarde dans une famille vs dans la population générale. Si il y plus de personnes malades dans une famille, on parle alors d'agrégation familiale (facteur de risque génétique).
Le facteur de risque génétique, en %, augmente en fonction de personnes dans la famille touchés.


#### 2. Jumeaux (Concordance/discordance).
- Jumeaux monozygotes : oeuf séparé en deux après fécondation.
- Jumeaux dizygotes : deux ovules.

Seule différence entre les deux : pas exactement le même patrimoine génétique chez les dizygotes. 

On observe des jumeaux en paire concordantes, développant tout deux la maladie, et des paires discordantes soit un jumeau atteint sur les deux.


Pour des jumeaux monozygotes, on mesure le nombre de paires concordantes(65% des cas) et discordantes.
tags:: #master/Omiques , #master/génétique 
date:: 27/02/2023
enseignant:: Dr. Carapito


Le génome humain est divisé en 46 chromosomes (22 paires autosomes et 1 paire chr sexuels). On y retrouve 3Gb (diploid) soit 6 milliards de bases et environ 20000 gènes.
De nos jours, les génomes sont séquencés via les [[Séquençage ADN (attention)|séquenceurs nouvelle génération]].

L'exome, c'est tout les exons d'un génome, la partie codante du génome. Sur les 3gb d'un génome, ces exons représentent à peu près 1.5% de tout le génome.

C'est souvent là que sont localisés les gènes et variants qui codent pour des protéines altérées menant à une pathologie.

Le WES présente ses avantages : rapide, peu coûteux et temps. Mais se focus que sur la partie codante, on ne regarde que 1.5% du génome.


### Application du WES.
---
Sert deux objectifs : séquençage de génome dans un contexte de recherche, ou alors l'identification de mutation pour un diagnostic.
![[Pasted image 20230303091021.png]]
Plus une pathologie est rare, moins de gènes cause la pathologie.
![[Pasted image 20230303091115.png]]

On s'intéresse aux analyses familliales qui permettent d'aborder les variants  monogéniques.
On séquence les membres d'une même famille et on compare les mutations entre individus sain/malade d'une même famille. 

##### Les principales étapes de l'analyse d'exome.
On part du fichier fastQ (1) qui vont être mappé sur le génome de référence (2). Ensuite on identifie les variants (3) (callers : DECON, CANOE). On les annote (4) ensuite et enfin on les visualise par techniques analytiques.

###### FastaQ
Un fichier fastaQ présente un identifiant (le spot sur la lame de séquençage), la séquence, en dessous aux valeurs de qualité pour chacune des bases et le signe si brin sens ou antisens.

###### BAM
C'est l'alignement des séquences dans le fastQ sur un génome de référence.

###### VCF
Identification des variants via des callers, donc les séquences qui sont différentes du génome de référence. De plus, dans le cadre de notre exemple,  si l'exome séquencé était hétérozygote : on aurait une présence de T et de C



Sont détectés, en moyenne, 50000 variants par exome. Comment passons-nous de 50 000 à 1 variant responsable de la mutation ?
- On assume d'abord que notre mutation a une pénétrance complète (cf. [[GE01 - Introduction générale à la génétique humaine]])
- Notre mutation est aussi totalement détectable (le variant est présent si le phénotype est présentt).
- On doit aussi connaître le mode d'héritance

#### Examples de stratégies de séquençages de l'exome en fonction du modèle.
![[Pasted image 20230303092311.png]]

#### Filtrage de variants.
D'un génome à l'autre, on trouve en moyenne 3 millions de SNPs par individu. Une première étape de filtration, c'est l'**analyse de l'exome** et non du génome (choix stratégie) qui va faire descendre ce nombre à 50 000 SNPs/individu.
Un second filtre opère en enlevant les variants non-codants -> 7k à 10k SNPs/individus.
Un troisième filtre sur la **fréquence des variants** : si il est supérieur à 1% en comparant sur des bases de données comme 1000 genome, GNomAD, dbSNP, ... on conserve que les variants dont la fréquence est faible.
Enfin, le dernier filtre se refère à la famille, en fonction du modèle d'héritage (voir juste avant)



### Confirmation of the causal role of the mutation.
---
Une fois qu'on réduit notre nombre de variants à quelques uns. C'est là que débute le projet de recherche. Différentes méthodes opèrent. La première serait déjà de valider se variants chez une autre famille et croiser les résultats. Suite à celà, il est possible de faire **un KO sur poisson-zèbre ou souris (rescue)**. 
Enfin, des expériences in vitro/ in vivo pour charactériser la protéine mutante.

La suite du cours concerne pleins de rappels de [[Séquençage ADN (attention)]]

Et enfin des exemples.


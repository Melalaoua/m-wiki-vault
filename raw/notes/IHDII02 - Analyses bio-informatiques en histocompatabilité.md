tags:: #master/Immunologie 
date:: 07/03/2023
enseignant:: Nicodème Paul

### I. Introduction.
---
L’histocompatibilité, c’est le degré de compatibilité tissulaire entre un donneur et un receveur permettant la réussite de la greffe. C’est indispensable, un prérequis nécessaire avant toute transplantation, notamment dans le cas d’une greffe de Cellules souches hématopoïétiques (CSH)
L’histocompatibilité, c’est l’observation de la compatibilité, la similarité entre les gènes du complexe majeurs (système HLA). C’est un domaine qui contient avec ou sans fonction immunologique et il est divisé en 3 classes : Classe I, Classe II et Classe III.

#### A. HLA : Détails des classes.
##### 1. HLA-I.
Dans la classe I, la structure des molécules sont similaires, ce sont des molécules de surface avec une chaîne lourde : alpha divisé en trois domaines α1 α2 α3 et une beta2-microglobuline en association avec la chaine alpha α1 et α2 forme le site de fixation de l’antigène pour présentation peptidique. On retrouve des molécules HLA classe I sur toutes les cellules nuclées de l’organisme.


##### 2. HLA-II.
Constitué d’une chaîne alpha et une chaîne beta, le site de fixation de l’antigène peptidique étant formé par les domaines α1 β1.
Pour les molécules de la classe II, elles se retrouve surtout sur les CPA professionnelles (macrophages, lymphocytes B et dendritiques.
Le HLA de Classe III contient aussi des gènes à fonction immunologique mais n’ont pas vraiment de fonction de présentation d’antigène, en histocompatibilité on se focus surtout sur la classe I et classe II.

Le domaine HLA se trouve sur le chromosome 6 avec une taille de 3 Mb. On s’intéresse aux gènes A, B, C (classe I), DR, DQ et DP (classe II) qui sont, les 6 des gènes très polymorphes.
On compte 200 gènes dans ce domaine dont 40 codant pour des protéines HLA.
![[Pasted image 20230426201705.png]]


##### Base de données IPD-IMGT/HLA.
Base de donnée contenant tous les allèles HLA séquencés : on observe une quantité
dominante de HLA-A, HLA-B et HLA-C. Cependant pour les classe II, on observe une **dominance d’allèle pour HLA-DPB1, HLA- DRB1, HLA DQB1**. Ainsi quand on parle de HLA-DR, DP ou DQ en transplantation on fait allusion nécessairement à la chaine beta.
![[Pasted image 20230426201754.png]]


##### Nomenclature.
![[Pasted image 20230426201815.png]]

Dans la nomenclature internationale, la manière de nommer (dia 7) :
- Le nom du gène.
- Première paire de chiffre qui sert à préciser le groupe déterminé par sérologie (par anticorps).
- Seconde paire de chiffre : distinguer les allèles qui ont des différences au niveau de la séquence protéique.
- Troisième et quatrième paire de chiffre : mettre en relief les différences au niveau de la séquence ADN.
En général, les 4 premiers permettent d’avoir un typage de haute résolution, avoir juste deux chiffres est qualifié de basse résolution. La lettre donne une idée sur l’expression (non exprimé = null...). Quest = questionable, Abr = aberrant, S = secrétée.


### II. Techniques de typage HLA
---
Diapostivie 8.

#### A. Typage sérologique.
Prélèvement des lymphocytes T (HLA-I) ou lymphocyte B (HLA-II). Le typage sérologique ne permet d’avoir que la première paire de chiffres. Les lymphocytes sont déposé dans des microplaques et incubés avec anticorps polyclonaux dirigés contre les différents allèles. On observe des spots aux anticorps donnés (ELISA SPOT).

#### B. PCR.
Grace à la biologie moléculaire, on utilise des méthodes plus précises, notamment la PCR. On distingue notamment :
- La **PCR-SSP** ou sequence specific primer : amorces de différentes allèles et amplification dans des puits distincts, là où c’est amplifié détermine notre allèle. Pas de multiplexage possible.
- **PCR-SSO** : PCR sequence specific oligonucleotype : PCR-SSP mais multiplex possible
- **Sanger** : l’enseignant ne détaille pas.
- **NGS** : on dispose de la séquence des allèles, analyse bioinformatique pour avoir un typage précis. Notre cours va se concentrer sur ça.


### III. De l'échantillon à la séquence.
---
#### A. Rappel sur le séquençage.
Pour séquencer un échantillon, on prélève l’ADN, on prépare des librairies, en général la longueur séquencée est déterminée par la technologie (une centaine de PdB : illumina). L’ADN est fragmenté et sont ajoutées des séquences spécifiques à chaque bout.
La technique illumina fonctionne en pontage, je suggère de se rafraichir la mémoire sur les cours du semestre dernier.
L’objectif de la bioinformatique est de reconstituée les données de séquençage afin de déterminer l’allèle du patient.
En diapositive 10 se trouvent des données brutes de séquençage :
- Première ligne : identifiant.
- Seconde : données de séquençage.
- Troisième : séparateur.
- Quatrième : information de qualité sur chaque base séquencée.


#### B. Formulation du problème : approche quantitative.
Du fait du bruit qu’on génère lors de séquençage, on va classer les allèles identifiés de manière probabiliste. La probabilité d’observer ces reads sous l’hypothèse qu’ils proviennent de la même donnée.
On prend l’allèle avec la meilleure probabilité P (dia 11).


#### C. Démarche algorithmique.
Il faut identifier les allèles identifiés par nos reads. Déterminer un scoring pour chaque allèle reflétant l’adéquation entre les reads observés et la séquences des allèles. Et enfin prendre une décision sur quelle allèle candidat choisir en fonction du scoring.

Il y a quand même quelques points de difficultés. Le domaine HLA est très polymorphe, par conséquent pour un gène donné il y a beaucoup d’allèle qui peuvent être très similaire. De plus, des
allèles de gène différent peuvent se ressembler, par exemple les allèles HLA-B ressemblent
fortement au HLA-C, compliquant le diagnostic. En général la séquence des allèles trouvées dans
la base de données, IPD-IMGT sont incomplètes (seul ce qui intéresse est la poche de présentation).

Exemple de comparaison entre deux allèles en diapositive 14. Sur l’exon 2, alignement obtenu à
partir de IMGT/HLA qui sont identiques. Une petite différence sur l’exon 3 à une base près.

Question : Si vous devez choisir une référence afin d’identifier les allèles, quel est le choix qui
serait le plus adapté pour cette identification ?
- Réponse : L’ensemble des séquences des allèles HLA disponibles dans IMGT/HLA

*Le génome de référence à été établit à partir de 20 personnes, dont 70% provenant d’une même personne donc on peut imaginer que les gènes HLA viennent d’une même personne, l’individu peut être différent, d’un point de vue HLA.*

#### D. Alignement et assemblage.
Dans certains cas, on dispose de la référence pour aligner nos reads (très courant). Dans d’autres cas, on va effectuer un assemblage de novo à partir de nos reads.
A partir de nos reads, ils sont découpés en petit morceaux qui vont être aligné de manière aléatoire sur la référence (diapositive 19). Un dictionnaire est généré à partir d’alignements multiples que l’on appelle index (diapositive 20).

Question : Un read s’aligne de manière unique sur la référence.
- Faux.
Les différents allèles se ressemblent beaucoup, de fait plusieurs alignements sont possibles.

Question : le nombre d’alignement augmente avec la longueur du read.
- Faux.

Question : Quand un read a plusieurs alignements, on garde les meilleurs.
- Vrai.
Comme on sait que les allèles se ressemblent, tout les alignements peuvent être utiles, il faut tous
les garder car on sait que deux allèles se ressemblent beaucoup.

Question : Si le meilleur alignement n’est pas parfait. On le garde quand même.
- Vrai

Représentation visuelle en diapositive 25 d’un alignement HLA-B sur la référence du génome humain, en couleur les différences. Simple démonstration de la différence d’un individu à l’autre.


#### E. Approche naïve.

On met les allèles en colonne, et les reads en ligne, un 1 correspond à un alignement. Les données sont quantifiées par un tableau de 0 et 1.

Question : Sachant qu’il s’agit de données NGS, le nb de lignes > nb colonne.
- Vrai

Question : Si deux lignes sont identiques, je peux en supprimer une ?
- Non
Deux lignes identiques ne signifient pas deux reads identiques.

Question ; que représente la somme des colonnes ?
- Le nombre d’alignements par reads.

Question : que représente la somme des lignes ?
- Le nombre d’alignements par allèle.

Question : Si une colonne est incluse dans une autre. Je peux la supprimer ?
Une colonne représente un allèle, un allèle plus petit peut être compris dans un allèle plus grand.Tout ce qui aligné sur A va aussi s’aligner sur B. Mais A va comporter plus d’alignements que B car A est plus grand que B.
- Non.

Question : Nombre de reads par allèle du Gène G (dia 32). Sachant que l’individu est hétérozygote, son typage pour le gène G est A1/A2 ?
- Faux.

On a dit que deux allèles peuvent être très similaires, par conséquent des reads qui s’aligne sur A1 peuvent aussi s’aligner sur A2, augmentant artificiellement le nombre de reads. De fait il est très facile d’identifier le premier allèle chez un hétérozygote, mais c’est très difficile pour le second allèle, on va chercher très loin.

La balance allélique : un allèle paternel et maternel, dans ce séquençage ces chromosomes peuvent ne pas être séquencés de manière égale. Plus un allèle est long, plus il y aura de reads.


#### F. Algorithme : HLA-HD.
Voir dia 33 pour le schéma détaillé, vous ne comprendrez pas sans ce schéma. (non copié car vous devez zoomer dessus).

On observe comment cet algorithme normalise le nombre de reads. Premièrement, on obtient les reads et on y construit un dictionnaire (les allèles disponibles dans la BDD IMGT/HLA). Aux exons du dictionnaire, l’algorithme rajoute des nucléotides « N » signifiant n’importe quel nucléotide. Un alignement est effectué avec les données NGS, et les données sont normalisées. Un read va soit effectuer un perfect match, alignement parfait. Soit s’aligner en partie sur l’exon puis sur les nucléotides N. Un score est déterminé pour ceux qui s’alignent sur ces nuléotides N.

Une pondération est effectuée qui compatibilise le pourcentage d’allèle sur lequel un read s’aligne. Plus un read va s’aligner sur des allèles, plus il aura un poids faible dans le scoring. Fonctionne très bien.
Pour pouvoir départager deux exons ex-aequo, ils vont rajouter plus d’exons aux reads.


#### G. Algorithme HLA\*LA.
Algorithme exploitant les similitudes entre allèles en construisant un alignement multiple à partir des données IPD-IMGT/HLA à partir duquel est créé un graphe.
Comme ces allèles se ressemblent, il est possible de les regrouper afin de former un graphe donnant une représentation condensée de la base de données.
On aligne notre read sur notre « graph » pour déterminer dans quel chemin, de nos graphes représentant les allèles condensés, il se trouve. Un score est déterminé.
Pour le moment, ces méthodes se basent sur des allèles connus. Que ce passe-til pour des allèles inconnus ?

On utilise un assemblage des novos


#### H. Alignement sans référence (OLC).
En général, quand on séquence un individu, on ne séquence pas une seule cellule mais plusieurs, les données sont redondantes. On exploite cette redondance pour mettre bout à bout nos reads pour constituer nos séquences.
Un graph de chevauchement est généré. Le prof explique comment le graph fonctionne mais je ne pense pas que ce soit pertinent. Diapositive 37

#### I. Algorithme HISAT-genotype.
Algorithme récent qui combine assemblage de novo et graph de référence. On part du génome de référence, ensuite des allèles disponibles dans IMGT/HLA.
Un graph est généré qui va prendre en compte toute les variation allélique dans la population (graph de population) qui va être utilisé pour typer notre individu. 

L’enseignant explique comme le graph fonctionne, j’estime que ce n’est pas pertinent : diapositive 40. Si vous souhaitez l’enregistrement de cette explication, me contacter (medhi.el-alaoua@etu.unistra.fr)

Donne le meilleur résultat actuellement.
Liste des algorithmes en diapositive 43.


#### J. Conclusion.
Le polymorphisme du domaine HLA rend le typage difficile. Un potentiel biais d’amplification doit être pris en compte. La ressemblance proche entre les allèles pose des problèmes de cibles multiples.
Les algorithmes de typage reposent sur l’étendu des connaissances disponibles sur IMGT/HLA. Une amélioration de ces derniers est constatée récemment. Enfin, toute solution trouvée exige une inspection visuelle.
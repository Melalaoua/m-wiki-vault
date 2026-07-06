
tags:: #master/génétique 
date:: 28/02/2023
enseignant:: Dr. Muller

### I. Introduction.
---
*Je suis arrivé en retard, ainsi je commence ce ronéo à quelque diapo de différence, rien d'alarmant sur le fond.*

##### La bioinformatique est partout.
Le bioinformaticien va se placer à l'interface entre deux monde : la biologie et l'informatique. Il connecte, traite les données issus de séquençage haut-débit qu'on retrouvera très souvent sous format **.fasta**, VCF, ... voir même des relations entre les protéines, format 3D (pyMol, ..). Le bioinformaticien doit gérer une diversité de fichiers et une quantité massive d'information.

Des algorithme de prédiction vont être développés pour améliorer la qualité de l'information, afin de pouvoir distinguer le "bruit de fond" de l'information réelle.

Quelques idées des diverses champs de biologie où le bioinformaticien joue un rôle primordial : *génomique, génomique structurale, transcriptomique, interactomique, protéomique, phénomique*.

##### De l'artisanat au haut débit.
La génétique est rythmée par l'apparition de grandes avancées scientifiques (cf dia 8). On distingue l'apparition de premiers algorithmes dès 1970 avec l'algorithme de Needleman & Wunsch. 

L'apparition du séquençage de Sanger en 1977 s'est suivi immédiatement par le développement d'outils informatiques et de bases de données pour assister les données de séquençage et faciliter la tâche des biologistes dans le traitement de données. Des formats sont définis pour que les scientifiques puissent se partager les données.

Chaque apparition de nouvelles techniques s'est suivie par une couche de bioinformatique qui vient faciliter le partage, le traitement des données.

L'algorithme **Smith & Waterman** apparu en 1981 est un algorithme qui vient calculer l'alignement local de manière très précise mais qui nécessite des heures de calcul. A l'inverse du **Blast** qui va être moins précis mais beaucoup plus rapide.


##### L'ère post-génomique.
Explosion du nombre de génomes complets séquencés et disponibles sur les bases de données, on retrouve un suivi sur genomsonline.org. 

La métagénomique c'est le séquençage de tout les organismes vivants, l'écosystème à un endroit physique donné (l'enseignant donne l'exemple de séquencer tout ce qui se trouve sur le siège de la classe).

La métagénomique va récemment se porter sur l'intestin, etc pour procéder à un **remplacement de leur microbiome** pour soigner des pathologies.


Les principaux axes en bioinformatique :
- **Les bases de données** (stocker, organiser et rendre accessible l'information)
- **Développement et intégration de logiciels** (pipelines) allant de l'assemblage de contigs, jusqu'à des outils de prédiction, **clustering**.
- **Bioanalyse** : Le but est d'impliquer des méthodes pour synthétiser les informations multiples et comprendre la condition du patient (prédire la fonction d'un gène, énoncer des hyopthèses généralistes). 

>[!INFO]
Une pipeline c'est une chaîne de traitement : un exemple basique c'est une ligne de montage de voiture, c'est une pipeline : 1. installation du moteur, 2. installation du capot, 3. pose des pneus. Les étapes se font l'un après l'autre comme une tuyauterie.

##### Workflow classique retrouvé en NGS.
Le nerf de la guerre en génomique récemment (RNAseq, etc..). Une fois que le génome est séquencé, il doit être mappé sur un génome de référence, l'enseignant nous montre une multitude d'outils developpés servant tous le même objectif (dia 14). Il faut être critique, le bioinformaticien a une multitude de choix qui lui est présenté.


##### Quelques centres de bioinformatique.

###### Les principales.
Les deux principaux sont EBI (institution europpéenne) et NCBI. Récemment beaucoup de techniques se développent dans le cloud.

###### Initiative Europpéenne
bio.tools est fournie par elixir qui est une infrastructure europpéenne qui vise organiser ces outils et données pour ne pas les perdre.

###### Nucleic Acid research
Un autre exemple : Nucleic acids research qui va sortir des éditions en janvier et juillet qui vont venir lister des bases de données, ou des outils web.

###### OMIM
OMIM va cataloguer des gènes chez l'Homme, maladies génétiques mais aussi les signes cliniques, mode de transmission. BDD utilisée assez souvent par Mr. Muller.



### II. Banques de données essentielles.
---

#### A. Bases de séquences.
Deux types de bases de données qui sont le fondement de beaucoup de choses en bioinfo : **les bases nucléiques et protéiques**.

EMBL, etc.. (on les cite juste après) sont des bdd qui sont censées être incontournables voir obligatoire (on peut vous demander d'intégrer vos séquences de recherche dedans) qui vont servir de **base** pour la recherche. Elles sont donc très contrôlées et vérifiées.

Il est possible de soumettre à ces bases de données directement ou par dépôts de brevets.

Ce sont des bases qui sont exhaustives, mais extrêmement redondantes et peuvent contenir des erreurs.

##### Banques de séquences nucléiques généralistes & spécialisées.
Cette base est issue de l'association de trois banques : **GenBank**, **EMBL**(European Nucleotide Archive) et **DDBJ** (DNA databank of Japan) qui vont quotidiennement échanger les données, une synchronisation stricte permettant une sauvegarde si jamais une de ces 3 bases fait défaut (tsunami Japon, ...)

A faire la distinction avec les banques de séquences nucléiques **spécialisées** :
Ce sont des BDD qui vont avoir un objet particulier : dbSNP concernera les variants, etc (gnomAD, DGV) et ces BDD vont nous donner comme information importante la **fréquence allélique**, nombre d'hétérozygote/homozygote qui va servir en clinique (on cherche des variants rares, en général on veut un variant avec une fréquence inférieure à 1%)

##### Banques de séquénces protéiques généralistes
RefSeq et Uniprot qui sont équivalente.
- **RefSeq :** base qui découle de GenBank 
- **Uniprot :** base qui découle de 2 entités (on oublie la 3e) : **TrEMBL** (99%) et **Swissprot** (1%). Pourquoi trEMBL est beaucoup plus massive ? TrEMBL = translatedEMBL, c'est une traduction automatique des séquences nucléiques trouvées dans EMBL. Les protéines annotées via Swissport sont d'une qualité importante, annotée par des humains mais ce n'est pas pérène dans le temps car le "metier" d'annotateur n'est pas reconnu (donc pas payé). Je suggère de regarder le diapo (dia 39) pour observer le contenu offert par ces BDD.

#### B. Agrégateur.
Toutes les infos provenant des BDD protéique et nucléiques vont se retrouver dans les génome browser afin d'accéder très facilement à l'information : exemple du NCBI, UCSC, EBI.


#### C. Qualité des données.
La qualité des séquences protéique est généralement prédites, il fait être très vigilant sur ça car ce ne reflète pas forcément la réalité.

Une hétérogénéité de la qualité d'annotation : le meilleur étant les annotations manuelles (swissprot). Les annotations automatiques sont réalisées par des outils bioinformatiques de prédiction de domaine, de fonctions.. en général on va utiliser des mots qui trahissent une annotation automatique : **"by silmilarity", "homologous to", "related to", "-like", "putative".**

Exemple de l'importance de l'annotation et pourquoi il faut du recul : 
- Exemple 1 : DUF domain **ce n'est pas un domaine propre** : Domain of Unknown Function. On sait que c'est conservé, mais on ne connait pas le domaine. Mais DUF ne veut rien dire en lui-même.
- Exemple 2 : FAM20C : Family with sequence similarity 20 (20% d'identité), member C. mais ca n'informe rien sur la fonction. 



### III. Variations génétiques.
---
On attaque les variants génétiques. Les technologies séquençage haut-débit, puce à ADN, permettent de découvrir un nombre important de variations d'un individu à l'autre :
- **4-5 millions de variants SNV/indel** d'une personne à une autre : on notera les variants faux-sens, frameshift, non-sens, épissage, deep intronic splice, non frameshifting indel, expansions.
- Les **variants de structures**, on en compte en moyenne **5 à 10 000** variants par personne : 
	- **variations structurales déséquilibrées** : Variation de la quantité d'ADN (gain, perte, éléments mobiles). 
	- **variations structurales équillibrées** : Pas de variation de la quantité d'ADN (translocation, inversion) 

>[!TIP]
>sur la dia 54, on observe des sigles vert à rouge, ils symbolisent notre capacité à gérer les différents types de variations avec la technologie actuelle.


Quand on découvre une variation chez un individu, l'objectif est de savoir en premier lieu à quel type de variant nous avons affaire, la seconde étape, c'est l'annotation du variant (rappel annotation d'un variant OGTE semestre 1), la fréquence dans la base gnomAD. La troisième étape conssite à classer ce variant de 1 à 5. Enfin, on réalise l'interprétation qui est en  réalité un "schéma mental" entre le variant et le phénotype qu'il va induire, si il est causal ou non.
![[Pasted image 20230304155238.png]]

L'enseignant présent en dia 58 plusieurs outils qui vont servir à interpreter nos variants en les rentrant dans des bases de données.

Rappel en dia 61 la fameuse nomenclature HGVS à l'étape d'annotation de notre variant qui se doit d'être respectée.


#### A. Bases de données de variations (pathogènes).
Il existe des bases de données de variations qui recensent des variants pathogènes dont on connait les pathologies associées.

##### ClinVar.
Exemple de **ClinVar** qui est une base de donnée parcipatif où tout le monde peut y déposer ses variants, les laboratoires de Strasbourg en font partie.

Comme tout le monde est libre d'y déposer son variant, il peut y avoir des conflits d'interprétation entre deux variants (X suppose que c'est un classe I, Y suppose que c'est un classe IV sur un variant donné). **La base de données est basée aux états-unis**.


##### HGMD.
Base payante, des personnes dédiées lisent les publications et repertorent les variants.

##### Mastermind Database.
Nouvelle base de donnée qui repose sur l'intelligence artificelle, deep learning pour analyser des publications et repertorier les variants.



### IV. Pathogénicité des faux sens.
---
La protéine possède différente conformations (primaire, secondaire, tertiaire, quaternaire) qui vont apporter des informations.
![[Pasted image 20230304180551.png]]

#### A. Conséquence d'une variation Faux-sens.
Les conséquences d'une variation faux-sens va dépendre de sa localisation sur la protéine. 
- **Toucher un résidu fonctionnel critique** qui peut être impliqué dans la catalyse, liaison avec un ligand, ion métallique, communication, oligomérisation...
- **Toucher un résidu structural critique** : coeur hydrophobe, résidu impliqué dans pont disulfure, structuralement proche d'un résidu fonctionnel.

Tout cela est correlé à la nature de l'acide aminé, ci dessous un rappel des différents résidus et leur propriétés physico-chimique.
![[Pasted image 20230304180848.png]]

Le **score de Grantham** va chercher à montrer l'impact d'un changement entre deux acides aminés donné, allant de **0 à 215**. Plus ce score est haut, plus le changement entre deux AA va être important.


#### B. comparaison de séquences.
La comparaison de séquence ce n'est pas du text-mining. L'enseignant insiste sur faire la différence entre une recherche de simiarité (alignement 2 à 2) et un alignement multiple.
- **La recherche de simlarité** : exemple de blastP. On va comparer notre séquence 2 à 2 à des multiples séquences. 
- L'**alignement multiple de séquence** : alignement entre une séquence et une multitude d'autres séquences. Ce n'est pas un alignement 2 à 2. 

##### apparté sur des grands principes d'alignements multiples.
En comparaison des séquences avec d'autres espèces, de préférence éloignées, si on remarque une mutation faux-sens à la flèche rouge qui est une arginine extrêmement conservée entre les espèces, on comprend que la mutation sera probablement pathogène car il y a une pression de selection forte sur cette position là.
![[Pasted image 20230304181709.png]]
A l'inverse, sur la flèche verte, on remarque que l'évolution a toléré d'autres acides aminés d'une espece à une autre, ainsi une variation faux-sens à cette position ne sera problement pas délétère.

L'alignement multiple permet une validation/correction des séquences protéiques (on verra dans un exemple en fin de cours sur BBS-RP). Mais aussi une organisation en domaines et observer la conservation des résidus au sein de la famille ou au cours de l'évolution.


Cependant, il faut faire attention avec l'alignement multiple pour s'il est suffisament multiple, notamment sur la **profondeur phylogénétique**, faire un alignement multiple avec 30 espèces alors que 28 sont des espèces mammifères, est-ce pertinent ? -Sauf  si la protéine est une protéine de mammifère.

De plus, toujours dans les vigilances à prendre en compte avec l'alignement multiple et pour une séquence donnée, il faut savoir quelles séquences on aligne et si cette séquence concerne une famille de protéines -*exemple du gène MTM1 dans le muscle qui est reliée à 14 autres sosu-famille MTM, d'un point de vue évolutif, il y a eu une duplication au cours du temps. Doit-on prendre en compte ces 14 sous-unités ? L'enseignant répond que tout est utilisable, tout dépend de la question, si on met les protéines actives et inactives la question va changer, grosso modo, il faut savoir ce que l'on manipule.*

#### C. Exemple d'outils.
Des multiples d'outils on va parler de deux principaux : polyphen-2 et Sift 

##### PolyPhen-2.
On rentre la séquence d'une protéine ou un identifiant de protéine avec l'acide aminé initial et l'acide aminé qui remplace le dernier (la mutation sur notre protéine). Le site va réaliser des prédiction basés sur 3 éléments :
- **Feature** : annotation de séquence disponible dans les db (site catalytique, site de fixation, ..)
- **Position Specific Independant Counts **: profil de score basé sur l'alignement multiple.
- **Structure** : structure secondaire, accessibilité, etc...

Le site utilise un classifieur naïf bayésien qui va se reposer sur des données issue de deux sets : HumDiv et HumVar (dia 92)

4 préditions possibles vont émerger de notre requête : **unknown, bénin, possiblement délétère, probablement délétère.**


##### SIFT : Sorting Intolerant From Tolerant.
Même procédure que Polyphen-2 (rentrer la séquence, ...) cependant l'outils repose sur une autre technique qui est quand même basé sur la conservation de la séquence.

Les résultats possible sont : toléré ou affecte la fonction de la protéine + un warning si peu de confiance 

Comparaison de deux outils :
Polyphen-2 présente plus d'informations (structure et séquence) et utilise des alignements multiples, cependant, on ne peut pas soumettre son propre alignement multiple, les résultats sur lequel se base l'agorithme sont figés. La structure 3D n'est pas modélisée.

SIFT est plus basique et repose sur la conservation et il est possible de  soumettre son propre alignement multiple.


Exemple du gène DMLX1 : sur le fond ce n'est pas important, ce qui est important de comprendre c'est que en fonction de l'alignement que l'on va utiliser pour Polyphen2 (qu'ont ne peux pas choisir) ou SIFT, il faut faire attention car le résultat peut varier en fonction de l'alignement utilisé, il faut être critique sur les résultats.



#### D. Les structures 3D de la protéine.
Déterminer une structure 3D était très compliqué à établir avec la cristallographie (beaucoup de temps, protéine trop complexe, etc...) mais c'est récemment en train de changer avec l'avènement de **l'intelligence artificielle (AlphaFold).

##### Les structures secondaires.
<u>Hélice alpha</u> : (dia 113) acides aminés qui tournent avec des connections entre elle sur les résidus (pont-disulfure) mais surtout sur la chaîne principale.

<u>Feuillets beta</u> : (dia 114) deux types de chaînes d'acides aminés : parallèles et antiparallèles entre eux. 

Ces organisations vont stabiliser mais aussi définir différents types de protéines qu'on peut prédire avec des logiciels à partir de la séquence en reconnaissant des patternes en connaissant les propriétés physico-chimique des acides aminés.

Structure tertiare : association de structure secondaires entre-elles au sein de la protéine.

##### Fold ou repliement des protéines.
Il existe tout une hierarchie dans les repliements des structures tertiaires chez les protéines. 
- **Familles de protéines** : déterminé à partir de la séquence par une **relation claire d'un lien évolutif**. Ce sont des protéines regroupées entre elles (DMXL1, DMXL2 par ex) et qui partage en général des homologies de séquences assez élevées, en général plus de 30% (contre exemple: les globines avec 15% d'id).
  
- **Superfamilles** : ce n'est pas juste des protéines qui ont des fonction ou une évolution similaire. Ce sont des protéines qui vont **partager une structure 3D qui se ressemble**. Exemple du domaine Actine + ATPase.
  On peut voir que c'est pas les mêmes protéines mais on va voir une organisation 3D similaire bien qu'une identité de séquence faible.
![[Pasted image 20230305124429.png]]


- **Fold** : Similarité structurale forte, un repliement 3D. On a plus de similarité de séquence ou de convergance évolutive possible, c'est vraiment une organisation 3D que l'on va stocker sur des bases de données (CATH et SCOP) : on va retrouver par exemple des protéines qu'avec des hélices alpha, ou des feuillets beta, les deux, ....![[Pasted image 20230305124806.png]] 


#### E. détermination des structures.
Historiquement on identifiait les structures par cristallographie, ou plus récemment avec la NMR, Cryo-EM. Ces technologies vont permette de déterminer la structure des protéines via la production de carte de densité électronique.

Christian Anfinsen (prix nobel Chimie) a fait la prédiction en 1972 qu'il devait être possible en théorie de prédire la structure 3D à partir de la séquence seule de la protéine. Une initiative (Folding@home) a prit forme il y a une dizaine d'années pour utiliser la puissance de calcul des appareils à la maison de particuliers (console, ordinateur, ...) pour calculer les multitudes de repliements des protéines à partir de la séquence.

##### Critical Assesment of protein Structure Prediction (CASP) experiment
Regroupe des jeux de données qui se sont étoffés avec le temps où on vient tester son programme de prédiction. Typiquement CASP sert de modèle d'entrainement pour des programmes produit par la communauté scientifique en comparant avec des résultats humains, correctes. Depuis 1994, on observe une amélioration des programmes de plus en plus rapide. Mais tout a été renversé par l'arrivée d'AlphaFold.
![[Pasted image 20230305130105.png]]


#### D. AlphaFold : l'intelligence artficielle
On ne va pas approfondir l'intelligence artficielle sur ce cours, mais on distingue le machine learning du deep learning. Le Machine learning est piloté par l'Homme en se reposant sur des données quantitatives et structurées, le deep learning ne se repose pas sur des données structurées, l'apprentissage est continuel et non-supervisé par l'Homme (réseaux de neurones artificels).

Google, via sa fillière Deepmind, a publié un code open source nommé AlphaFold 1 et 2 reposant sur des réseaux neuronaux entrainé pour prédire les propriétés d'une protéine à partir de données de séquences. L'algorithme se base sur la dsitance entre les paires d'acides aminés et les angles entre les liaisons chimiques reliant ces acides aminés.

Grace à AlphaFold il est possible de prédire une protéine de manière relativement précise la structure 3D d'une protéine. Comparaison entre BBS1 prédit par AlphaFold et celle déterminé via des manières classiques (Cryo-EM, etc...)
![[Pasted image 20230305130218.png]]

Le fondateur CASP ainsi que ces organisateurs, suite à l'arrivée de AlphaFold, on déterminé que le problème du repliement des protéines a été résolu. C'est assez rare qu'une question scientifique qui est fermée.

Les limites se trouvent dans les zones non structurées et désordonnées.


#### F. Exemple MAOA - Monoamine oxydase A.
Identifié à Strasbourg (25 ans), Mr. Muller (l'enseignnant) ainsi qu'une autre chercheuse on publié un papier sur le gène en 2013. Le gène a attiré l'attention des médias, car il est associé à un retard mental **lié au chromosome X** provoquant une aggressivité forte, appelé le "gène guerrier" par la presse.

Un faux-sens sur le gène a été identifié dans une famille strasbourgeoise sur le chromosome X (les mères sont donc vectrices) et les hommes touchés.
![[Pasted image 20230305131242.png]]

Mr. Muller ont utilisé plusieurs algorithmes qu'on a vu juste avant pour prédire l'impact de la mutation faux-sens sur le gène.
![[Pasted image 20230305131349.png]]

Pourquoi Mr. Muller a utilisé des algorithmes de prédiction d'épissage ? Car lam utation se trouve au bord de l'exon 8.
![[Pasted image 20230305131442.png]]

Les sites d'épissage ont des sites canoniques, mais l'environnement génique autour va aussi jouer un rôle important. Mr. Muller a prédit la structure 3D de la protéine et a tenté de visualiser l'acide aminé en position 266 (dia 135). La mutation de la cystéine (**qui peuvent faire les ponts disulfures** mais ici ce n'est pas du tout le cas) en phénylalanine qui est un gros AA aromatique.

La mutation provoque une activité de la protéine bien amoindrit. Ce qui prouve la pathogénicité de la mutation. L'enseignant demande ce qui permettrait d'aller plus loin pour prouver que c'est spécifiquement cette mutation qui est pathogène : **Un rescue**


Un troisième exemple est disponible dans les dias, mais il montre la même finalité que l'autre exemple sur l'importance de la structure 3D.


#### G. Conclusion
Pour prédire la qualité d'alignement des variants, on a vu que la qualité de l'alignement est primordiale, tout en restant critique. 

La stratégie à adopter doit être réfléchie en faisant usage de la multitudes d'outils (SIFT, Polyphebn etc...) et ne pas utiliser les mêmes qui vont donner tous un même résultat pour justifier la conclusion sur la mutation, on peut très vite tomber dans un raisonnement circulaire. 

Les algorithme utilisés sont callibrés sur des vairants pertes de fonction et non pas gain de fonction.



### V. Effet sur l'épissage.
---
Tout en assumant que ceux qui lisent le ronéo de génétique ont l'UE cancérologie, je passe cette partie introductive sur l'épissage que nous avons vu dans les premiers cours. Dans le cas contraire, merci de me le signaler je corrigerais cette partie en ajoutant les informations nécessaires.

Les outils qu'on utilise actuellement pour détection de l'épissage sont très bons pour les sites cannoniques d'épissage (donneur/accepteur et branchement). Dès qu'on s'eloigne de quelques nucléotides, on va un peu plus galérer.

Les outils actuels vont reposer sur l'intelligence artificielle, l'apprentissage.

Chaque programme va donner un score qui reflète la force du site d'épissage et tenter de prédire la perte d'une ou dégradation avec une variation. Comparaison avec le site d'épissage Wild Type et le variant pour prédire l'effet délétère ou non.

Les différents algorithme n'ont pas les même variation de seuil : 
- MaxEntScan : si variation de 15% : effet délétère.
- SpliceSiteFinder : 5% 
- NNSPLICE : 10%

Si deux de ses algorithme répond positif à un variant délétère, alors on admet que le variant est délétère. Et comme dit précédemment plus on séeloigne des sites canoniques, moins ces algorithmes sont fiables.

##### Zones d'épissage.
Des zones de mutations des sites d'épissages ont été définis
![[Pasted image 20230305155357.png]]


#### L'arrivée Du Deep Learning pour la prédiction d'épissage.
De nouvelles technologies sont en train de changer la donne avec le deep learning et IA.
- Spidex
- SpliceAI
- S-CAP
- CADD-Splice

L'enseignant présente un agregateur de ses outils développé en France par un interne en Pharmacie dans l'équipe de monsieur Mendel : **SPiP**

Ici un récap des différents outils en diapositive 152.

L'enseignant présente ce qu'ils ont fait avec ces différents outils à partir de bases de données qu'on a vu précédemment (HGMD, ClinVar, GnomAD, ....)

Ils ont testé ces différents outils et vous pouvez trouver ces résultats en diapositive 155 avec la ROC Curve

**SpliceAI et Spip** donnent les meilleurs performances.




### VI. Annotateurs automatiques.
---
Différents outils en diapositive 159 d'annotateurs une fois qu'on a récupéré nos variants et qu'ils faut les annoter




### VII. Conclusion.
---
En conclusion un bioinformaticien et un biologiste possèdent de nombreuses sources d'annotations (bases de données et outils de prédictions) et l'enseignant nous met en garde à nouveau avec la circularité et la fausse redondance, et donc de faire attention à ce qu'on manipule.

Ces outils présentent des limites. Pour les faux sens il faut rester vigilant avec les résultats. Des progrès sont fait sur les anomalies d'épissage, nous on avons pas parlé des variations structurales ou modification post-traductionnelle.



### VIII. Application : Syndrome de Bardet-Biedl.
---
Travail de Mr. Muller durant sa thèse sur le syndrôme Bardet-Biedl et cet exemple sert à nous montrer comment la bioinformatique vient épauler le généticiens dans sa tâche.

Un cours dédié sur les ciliopathies aura lieu. Maladie génétique rare (1/150 000) et 500 patients atteints en France de nos jours. En 2005 seulement 9 gènes étaient connus (maintenant 24). C'est une pathologie **hétérogène**.

Ce n'est pas parce qu'il y a 24 gènes que c'est une maladie monogénique. **Les mutations dans un seul gène vont donner la maladie**. C'est une pathologie hétérogène d'un point de vue génétique car plusieurs gènes peuvent donner la maladie.

La pathologie concerne un défaut du cil (nous n'entrons pas dans les détails car un cours sera dédié à ça) qui va provoquer des défauts du développement (rein). LA maladie est détectable en DPI

Les chercheurs ont utilisé la génomique comparative pour identifier les gènes impliqués dans les cils. Ils ont donc comparé le génome d'organisme cilliés et non cillié et trouvé les gènes qui n'étaient pas commun aux deux types d'organismes : 688 gènes identifiés et la listes étaient enrichie en gènes BBS pour lesquels ont ne connaissait pas encore leur fonction ni leur rattachement aux ciliopathies.

A Strasbourg, des analyses sour deux familles consanguines ont permis la découverte de beaucoup plus de gènes BBS. Nous avons parlé de la consanguinité et le fait que ça augmente les chances d'apparition de maladies génétiques car les individus deviennent homozygote à partir de parents hétérozygotes.

Ils ont cherché les variations homozygotes dans les deux familles pour les patients malades et qui ne sont pas homozygotes normaux chez les patients sain de la même famille. C'est de la **cartographie homozygote** ou Homozygotie
![[Pasted image 20230305161906.png]]

Les gènes homozygotes ont été analysées (BBS10 en premier, puis dans un second papier BBS12 ) par blast et on a trouvé une homologie de séquence faible avec des protéines de la famille des chaperonines de type II et ils ont montré que BBS6 était similaire à BBS10 et BBS12

L'alignement multiple à révélé une différence de longueur entre les gènes de l'homme et ceux du chimpanzés où celles de l'homme étaient plus courtes, une différence de 60 acides aminés. L'enseignant nous dit que ce genre de cas est typiquement dû à une erreure de prédiction du codon initiateur. Pour savoir où était l'erreur et la corriger ils ont fait un tblast avec la protéine du chimpanzé pour l'aligner sur le génome humain et on remarque que la partie N-ter de la protéine du chimpanzé est présente sur le génome humain mais qu'elle n'a pas été prédite et alignée dans l'alignement multiple. 

De fait cette correction à permis d'identifier que le gène BBS10 possède un exon codant en plus (l'exon 1) tandis que BBS12 possède juste un exon codant (exon 2).
![[Pasted image 20230305175450.png]]

Un arbre phylogénétique a été constitué ensuite via l'alignement multiple par rapport aux chaperonines de type II. Les chiffres à chaque noeud sont les valeurs de boostrap qui stipule la confiance de l'architecture de l'arbre à cet endroit (exemple 100 fois sur 100, l'algorithme a prédit ce noeud là). Ceci permet de conforter dans l'idée d'appartenance des gènes aux chaperonines de type II.

Ils ont découvert que les gènes BBS10 et BBS12 sont resterints aux organismes vertébrés à l'inverse des autres gènes BBS. Ils ont découvert aussi que les gènes BBS10 et BBS12 évoluent plus vite (pression de sélection moins forte).

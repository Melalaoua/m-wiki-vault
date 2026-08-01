---
Date : September 12, 2022 1:50 PM
---

up:: [[OGTE]]
tags:: #academia/master, #master/génétique




$\LARGE\textbf{\textsf{Chapitre I.}}\\\Large\textsf{Introduction.}$

---

Voici l’arbre de la vie, connectant les trois grands arc de la vie (archées, bactéries et eucryotes) à un ancêtre commun, LUCA.

Cet arbre a été beaucoup critiqué, notamment sur le point suivant : il ne se base que sur une famille de 40 gènes.

Le domaine de l’évolution est un domaine très conflictuel (religion et compétition, croyances…).

Cet arbre se repose essentiellement sur des notions de temps, d’évolution, d’adaptation et de sélection.

Le choix des organismes modèles dans l’étude génomique est important, le choix est principalement influencé par des intérêts économiques, techniques (facilité d’hébergement, développement embryonnaire,…). 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled.png)

### A propos de l’homologie.

En biologie, l’homologie désigne un caractère propre à plusieurs espèces hérité d’un ancêtre commun. Les structures en question, qu’elles soient d’ordre anatomique, moléculaire ou génétique, partagent donc une histoire évolutive. Cette notion est à différencier de l’analogie qui veut dire l’inverse.

La notion d’homologie se dédouble en deux notions :

- **L’orthologie :** Gènes homologues dans 2 espèces ayant évolué à partir d’un gène ancestral suite à une spéciation.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%201.png)

- **Paralogie** : ****Gènes homologues au sein de la même espèce ayant évolué à partir d’un gène ancestral par duplication au cours de l’évolution de cette espèce.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%202.png)

How can we tell whether two human proteins are paralogs or whether a yeast protein is the ortholog of a human protein ? ******Homology is often detectable by significant similarity in nucleotide or amino acid sequence and almost always in three-dimensional structure.******

### Exemple d’homologie.

Exemple pour la gène de la globine, l’ancêtre commun à l’Homme et la Souris possède le gène de cette globine, mais suite à une duplication, il y a eu un **remaniement génétique**, ce qui a résulté en l’expression de **deux protéines paralogues.** (Toujours dans le même individu).

Mais après spéciation et évolution, des modifications se sont accumulés et la souris et l’Homme expriment deux protéines paralogue elle-même à partir de la protéine auparavant. Et de plus ces protéines paralogues vont être orthologue par rapport à celle de l’autre espèce.

Donc observe cette notion d’orthologie et de paralogie s’intriquer assez facilement. 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%203.png)

### Comment déterminer si il y a de l’homologie ou pas ?

Les séquences des génomes peuvent être alignées entres elles tout comme les séquences des protéines. La comparaison de 2 séquences permet d’établir une évaluation de leur proximité ou de leur éloignement par le calcul. Ainsi on détermine deux facteurs : le **pourcentage d’identité** entre ces 2 séquences, et le **pourcentage de similarité** entre ces 2 séquences.

La notion d’identité est stricte, on regarde les différences entre résidus.

La notion de similarité est assez relative, à déterminer. On peut définir des similarités dans les propriétés physico-chimiques. etc…

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%204.png)

Le seuil de significativité est de plus de 20%

<aside>
⚠️ Attention, une similarité non significative ne veut pas dire que les séquences et donc les gènes, ne sont pas homologues. 2 séquences similaires peuvent l’être (similaire) : par hasard, ou par convergence évolutive.

</aside>

### Statistical analysis of Sequence Alignments can Detect homology (Stryer).

A significant sequence similarity between two molecules implies that they are likely to have the same evolutionary origin and, therefore, similar three dimensional structure, functions, and mechanisms. Both nucleic acid and protein sequences can be compared to detect homology. However, the possibility exists that the observed agreement between any two sequences is solely a product of chance.

Because nucleic acids are composed of fewer building blocks than proteins, the likelihood of random agreement between two DNA or RNA sequences is significantly greater than that for protein sequences. For this reason, detection of homology between protein sequences is typically far more effective.

To illustrate sequence-comparison methods, let us consider a class of proteins called the **globins. Myoglobin is a protein that binds oxygen in muscle, whereas hemoglobin is the oxygen-carrying protein in blood. Both proteins cradle a heme group, an iron-containing organic molecule that binds the oxygen. 

Each human hemoglobin molecule is composed of four heme-containing polypeptide chains, two identical  $\alpha$ chain, and two identical $\beta$ chain. Here, we shall consider only the alpha chain. 

To examine the similarity between two amino acid sequence of the human alpha chain and that of human myoglobin, we apply a method, referred to as ******************sequence alignment****************** in which the two sequences are systematically aligned with respect to each other to identify regions of significant overlap

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%205.png)

---

**How can we tell where to align the two sequences ?** In the course of evolution, the sequences of two proteins that have an ancestor in common will have diverged in a variety of ways. Insertions and deletions may have occurred at the ends of the proteins or within the functional domains themselves. Individual amino acids may have been mutated to other residues of  varying degrees of similarity. 

To understand how the methods of sequence alignment take these potential sequence variation into account, let us first consider the simplest approach, where we slide one sequence past the other, one amino acid at a time, and count the number of matched residues, or sequence identities.

For $\alpha$-hemoglobin and myoglobin, the best alignment reveals 23 sequence identity, spread throughout the central parts of the sequences. 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%206.png)

******************However******************, careful examination of all the possible alignments and their scores suggest that important information regarding the relationship between myoglobin and hemoglobin $\alpha$ has been lost with this method. In particular, we see that another alignment, featuring 22 identities, is nearly as good. This alignment is shifted 6 residues relative to the preceeding alignments and yields identities that are concentrated toward the amino-terminal end of the sequences.

By introducing a gap into on of the sequences, the identities found in both alignements will be represented.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%207.png)

Insertion of gaps allows the alignment method to compensate for the insertion or deletions of nucleotides that may have taken place in the gene for one molecule but not the other in the course of evolution.

The use of gaps substantially increases the complexity of sequence alignement because a vast number of possible gaps, varying in both position and length, must be considered throughout each sequence. 

Moreover, the introduction of an excessive number of gaps can yield an artificially high number of identities. Nevertheless, methods have been developed for the insertion of gaps in the automatic alignement of sequences. These methods use scoring systems to compare different alignments, including penalties for gaps to prevent the insertion of an unreasonable number of them.

$\LARGE\textbf{\textsf{Chapitre II}}\\\Large\textsf{Le génome humain.}$

---

## A. Projet de séquencage.

### Homo sapiens.

Un génome nucléaire est constitué de 22 paires chromosomes homologues et 1 paire chromosomes sexuels + du génome mitochondrial (molécule circulaire). 

Nous possédons un génôme diploïde, avec une copie haploïde du génome paternel, et une copie haploïde du génome maternel.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%208.png)

La fresque du génome humain jusqu’à 2003. Le projet international pour séquence le génome humain a un coût de 3 millards $. Le séquençage debuta en 1999 et impliqua 20 centres (6 pays).

### **Stratégie de séquençage hierarchisé.**

Le projet international s’est réposé sur cette stratégie qui consistait, à partir de molécules d’ADN, de fragmenter ces dernières (clonées et marquées pour mappage), puis de générer des BAC séquencables qui seront de nouveaux fragmentés en clones plus petits, au hasard (shotgun).

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%209.png)

### Les différentes versions du génome humain.

2000 : draft 90% de la cible.

2003 : séquence complete (draft final) avec à peu près 99% de la cible initiale.

2022 : première version de la séquence complète du génome humain publiée (sans compter chromosome Y).

*GRC = Genome Reference Consortium.*

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2010.png)

## C. Architecture globale du génome.

### Composition générale du génome.

The human genome contains a large amount of DNA that does not encode proteins. A great challenge in modern biochemistry and genetics is to elucidate the roles of this noncoding DNA. Much of this DNA is present because of the existence of **********************mobile genetic elements**********************. These elements, related to retroviruses, have inserted themselves throughout the genome over time. Most of these elements have accumulated mutations and are no longer functional. 

Le génome nucléaire comporte une écrasante majorité de séquences non conservées :

- ******Elements répétés à 45%.******
- Heterochromatine constitutive à 6.5%
- Autres séquences à 44%.

La partie très conservée  :

- **Séquences codantes à 1.1%**
- **Séquences non codantes à 4%.**

Pour le génome mitochondriale, c’est l’inverse, la séquence codante représente 2/3 du génome. 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2011.png)

### Génome mitochondrial.

Le génome mitochondrial est compact, il fut connu bien avant le génome nucléaire. Il contient précisément **37 gènes**, dont **13 codants pour les protéines impliquées dans la respiration oxydatives**… Et de 24 gènes non codants (tRNA, rRNA).

Le code génétique du génome mitochondrial est aussi différent du nucléaire. 60 codons pour les AA, et 4 codons STOP.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2012.png)

Le génome mitochondrial est extrêmement optimisé, son but principal étant de coder pour des protéines impliquées dans la génération d’énergie. Et pour cause, son origine endosymbiotique lui permet d’éliminer une partie de ses gènes et d’exporter les autres dans le génome nucléaire.  

On va retrouver un millier de copie du génome mitochondrial au sein d’une même cellule. C’est la notion **d’hétéroplasmie : présence de copies différentes du génome mitochondrial au sein de la même cellule.**

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2013.png)

Le génome mitochondrial est d’origine exclusivement maternel.

La notion d’hétéroplasmie va jouer un rôle déterminant dans les maladies génétiques, un défection au niveau d’un gène va pas forcément empacter toute les copies du génome mitochondrial dans une cellule, avec l’hétéroplasmie, certaines mitochondries peuvent être encore opérationnelle, et donc assurer la survie de la cellule.

### Comparaison des génomes mitochondriaux.

Petite subtilité allant d’une espèce à l’autre.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2014.png)

### Génome nucléaire.

Le génome humain, nucléaire, a une taille de 3 . $10^9$ paires de bases avec 0.2 Gb en hétérochromatine constitutive + 2.9 Gb en euchromatine

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2015.png)

### Gène.

Le gène est un segment d’ADN génomique utilisé comme matrice pour synthétiser un ARN simple brin (transcription). Ce terme de gène est utilisé pour les gènes codants et non-codants. Pour les deux cas on va générer un ARN. Certains codants pour des protéines, d’autres non.

20 000 gènes codants environs et pus de 40 000 gènes non-codants. Ce qui porte le nombre total de gènes total à **60 000 (codant + non-codant).**

Schéma résumant la transcription  + épissage. ⏩

**La queue polyA est rajouté après transcription (pas codant dans le gène).**

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2016.png)

### Quelques exemples de structures de gènes codants.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2017.png)

Maladies rare : prévalence 1/2000 dans la population.

## D. Description des principaux éléments constituants du génome.

### Deux organisations pour les gènes.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2018.png)

Le premier groupe étant la version **non regroupée des gènes**. Le territoire génique du gène est indépendant et bien définit. Les gènes ont tous des fonctions bien différentes, pas d’observation d’homologie entre les gènes. Le sens de transcription d’un gène non regroupé est variable.

Mais leur transcription est bien plus complexe qu’on peut le croire. Certains gènes se chevauchent, etc…

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2019.png)

L’autre méthode d’organisation des gènes étant **l’organisation en cluster**. C’est organisation est particulière car on va y observer des duplications en tandems sur le même chromosome. Et les gènes en cluster ont tous le même sens de transcription. 

Pour finir, les gènes en cluster présentes des similarités plus haute que la normale.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2020.png)

Exemple d’organisation remarquables.

La famille des gènes d’histone (plus de 60 gènes). Il existe 3 cluster principaux dans cette famille.

- 2 sur le chromosome 6.
- 1 sur le chromosome 1.
- Plusieurs pseudogènes.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2021.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2022.png)

La famille des gènes des récepteurs olfactifs. Un répertoire définissant notre capacité à détecter des odeurs différentes. Il existe plus de 900 gènes, avec 25 grand clusters.

### Gènes non codants.

Les tRNA, responsables d’apporte rles AA lors de la traduction, environ 500 gènes codants et 300 pseudogènes, et plusieurs clusters répartis un peu partour sur le génome. Et les rRNA, partie composante du ribosome, centre actif de la traduction. Le gène 5S présent en plusieurs copies dans de petits clusters (le plus grand constitué de 16 gènes sur chromosome 1). Les gènes 28S, 5.8S, 18S répétés 30-40 fois.

Les gènes des tRNA sont dupliqués énormément afin de conserver une production importante. Au vu du nombre de protéines qui sont produites dans la cellule, on a toujours besoin de eux.

## D-1 Pseudogène.

Les pseudogènes sont en général des **copies défectueuses d’un gène fonctionnel** avec lequel le pseudogène partage une homologie de séquence significative.

Concernant 10% des gènes codants, ils représentent toutefois un nombre plus important pour des gènes activent transcrits.

Un certain nombre de pseudogènes sont exprimés dans le génome (beaucoup de questions se posent, ils sont censés être défectueux).

Plus de 14000 pseudogènes sont décrit pour 3 catégories principales :

- Les pseudogènes processé (72%, 10000 copies).
- Les pseudogènes non processé (23%, 3500 copies).
- Les pseudogènes unitaire (1.4%, 200 copies).
- Les pseudogènes polymorphiques (0.1%, 20 copies).

### Les pseudogènes non processé.

***Mécanisme d’apparition lié à une duplication d’une partie du génome.*** 

Le pseudogène conserve la même structure intron/exon, ainsi que la région de régulation. Mais de nouvelles variations inactivantes vont apparaître dû au relâchement de mécanismes de régulations de la transcription.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2023.png)

### Pseudogène processé.

***Mécanisme lié à la retrotransposition d’un mRNA*** 

Il y a perte de la structure intron/exon et de la région de régulation. Il peut se réintégrer partout dans le génome. Peut accumuler des variations inactivantes.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2024.png)

### Pseudogène unitaire.

Un pseudogène unitaire est un gène non fonctionnel constitué de variations inactivantes. On va en général retrouver ces même gènes dans d’autres organismes, mais sous forme active.

Ainsi on suppose que les pseudogènes unitaire sont des gènes en fin de vie. Subissant une pression de sélection moins forte car pas vraiment utile.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2025.png)

### Pseudogène polymorphique.

Locus dans notre génome avec des variations inactivante par rapport au génome de référence (pression de sélection diminuée, accumulation des variations).

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2026.png)

### Pseudogènes fonctionnels ou pas ?

15% des pseudogènes sont transcrits. Ci-dessous quelques exemples de mécanismes. 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2027.png)

## D-B. Elements répétés.

### A. Les éléments répétés en tandem.

En tandem = l’un après l’autre.

Les éléments répétés en tandem représentent une fraction relativement faible du génome (6.5%). Ils sont constitués des ADN Satellites, microsatellites et minisatellites.

Chaque élément est constitué d’unités plus petites hautement répétées.

Les **microsatellites** vont être disposés en moyenne tous les 30kb sur le génome humain, ils sont polymorphiques (variable d’un individu à l’autre) et cette particularité va notamment servir dans l’établissemnt de cartes génétiques / empreintes génétiques pour la police / médecine légale.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2028.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2029.png)

### B. Les éléments répétés dispersés.

Les éléments interpersed sont plus actifs et représentent une plus grosse partie du génome (40-45%). On retrouve dedans les rétrotransposons (LINE, SINE, Rétrovirus, Autonomes, non autonomes). Ce sont des éléments dérivés des transposons, mobiles capables de migrer d’une région du génome à une autre.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2030.png)

### Les rétrotransposons.

Mécanisme du **copié/collé** : passage par une étape de transcription, puis transcription inverse, puis intégration.

**Line ou Long Interpersed Nuclear Elements.**

Divisés en 3 sous-familles (Line-1, Line-2, Line-3), seule la première est encore active. 

Il en existe 1 000 000 de copies dont 1% sont complètes. Et seulement 100 éléments sont encore actifs (les Line-1), capables de se déplacer en gros.

Les LINE sont **autonomes.**

**Sine ou Short interpersed Nuclear Elements.**

Répartis eux aussi en 3 sous-familles.

Les principales familles étant **Alu**, spécifique aux primates et l’élément le plus abondant du génome. Et la famille **MIR**; présente chez les mammifères.

Les SINE ne sont **pas autonomes. Utilisant la machinerie d’une LINE environneante.**

**LTR transposons ou rétrovirus.**

Les LTR ou Long Terminal Repeat contiennent la machinerie utile à la transcription.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2031.png)

ORF 1 : protéine de fixation à l’ARN.

ORF 2 : endonucléase, transcriptase inverse.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2032.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2033.png)

### Les Transposons.

Mécanisme de **Coupé/collé.** Se déplacant que via une transposase qui va venir exciser l’élément et le réinsérer à une autre localisation du génome. IL en existe de nombreuses sous-familles, ayant tous une durée de vie limitée dans un génome. 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2034.png)

### Comparaison de nos 2 génomes.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2035.png)

Attention ⚠️ Gène ARN : plus de 40000 (pas 6000)

$\LARGE\textbf{\textsf{Chapitre III.}}\\\Large\textsf{Comparaison aux autres génomes.}$

---

On remarque que pour un bon nombre d’espèce, la partie codante est bien plus importante que pour nous les Humains.

La capacité codante d’une espèce n’est pas proportionnelle à la taille du génome en paires de bases ni au nombre de chromosomes.

Pour les bactéries, on remarque une **relation linéaire entre la taille du génome et le nombre de gènes.**

Tandis que chez les eucaryotes, c’est l’inverse.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2036.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2037.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2038.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2039.png)

$\LARGE\textbf{\textsf{Chapitre IV.}}\\\Large\textsf{Les types de variations du génome humain et leurs conséquences.}$

---

![bubble-chat.png](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/bubble-chat.png)

$\Large\texttt{Commentaires}$

---

*Plan du cours.*

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2040.png)

La convergence évolutive est une forme d’analogie.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2041.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2042.png)

### Ordres de grandeurs.

---

Taille des gènes :

- **54 000 pb en moyenne.**
- Plus petit : une centaine de pdb.
- Plus grand : 2.5 mb la **dystrophine**

Taille des protéines :

- Plus petite : 10 AA.
- Plus grande : 34 350 AA (titin).

Taille des introns : 

Plus petit : 30pb.

Plus grand : 1 mb.

Taille des exons : 

Moyenne de 10 introns par gène 

Taille moyenne de 280pb.

Plus petit : 1 intron dans un gène (pas d’exons) et le plus petit connu en dessous de 10 pb.

Plus grand : 363 introns (titin) et le plus grand connu fait 18 kb.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2043.png)

<aside>
⚠️ Les gènes de Line 1 ne sont ré-exprimable qu’à un très court moment de l’embryogénèse, toutes les zones sont déméthylées et il y a donc une re-expression massive.

</aside>

Eléments considérés comme inactifs ou “fossiles” du génome humain.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2044.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2045.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20220912%20Architecture%20du%20génome%20humain/Architecture%20du%20génome%20humain%20cecf6deac3b14678b9e62a267a5547c4/Untitled%2046.png)

---

$\Large\texttt{Fin de page}$

***Xénologie :*** deux espèces qui ne sont pas reliée entre elles (à priori) et qui effectuent un transfert horizontal. La bactérie d’un tel envoie du matériel génétique à une autre.

**La paralogie :** gènes homologues mais au sein d’une même espèce (suite à un évênement de duplication). Dans la plus part la paralogie va aboutir à une nouvelle fonction pour l’un des deux nouveaux gènes.
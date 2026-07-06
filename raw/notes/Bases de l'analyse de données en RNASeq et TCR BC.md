---
Date : October 4, 2022 10:09 AM
---

up:: [[ImmunoHD]]
tags:: #academia/master, #master/ImmunologieHD



## Analyse de données RNASeq.

*Les types de données analysées sont des données de séquençage.* 

**************RNAseq.**************

Le RNAseq, c’est le séquençage d’un ensemble des ARN ou du transcriptome des cellules par l’utilisation de technologies de séquençage à haut débit dans le but d’identifier les gènes et de quantifier leur expression. En général le RNAseq est effectué sur des cellules d’un même tissu, car le transcriptome de nos cellules va différer d’un tissu à l’autre.

L’expression ou le nombre de copies d’un gène présente une quantification de l’activité du gène. Cette quantification ne reflète pas la complexité fonctionnelle de l’activité, mais permet néanmoins de comprendre la fonction des gènes.

**Utilisation.**

Le RNAseq peut être utilisé pour :

- *Déterminer l’expression différentielle du transcriptome entre tissu cancéreux ou normal.*
- *Etudier l’impact du manque d’un gène suppresseur de tumeur sur l’expression du transcriptome dans une lignée cellulaire donnée.*
- *Caractériser l’expression différentielle du transcriptome suite à l’introduction d’une mutation dans un gène donné.*
- *Quels sont les gènes qui sont sur-exprimés au cours du développement du cerveau ?*
- *Quels sont les gènes qui s’expriment dans la peau, mais pas dans les muscles ?*
- *Quel est l’impact du stress oxydatif sur l’épissage ?*
- *Rechercher de nouveaux miRNAs dans les cellules souches embryonnaires humaines.*

### Réplicats techniques.

En général, quand une personne est étudiée par RNA-seq, c’est pour s’intéresser à l’expresison d’un gène dans une condition par rapport à une autre condition. Si on veut comparer, on ne veut pas juste une seule valeur. Il faut des réplicats. Deux types de réplicats: 

**Les réplicats techniques.**

Le matériel biologique vient d’un seul individu, on mesure la variabilité technique.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCRBCR/Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCR%20BC%202adb1079b86440b6af0116c2e8620b71/Untitled.png)

- Une ou plusieurs extractions du même matériel biologique initial.
- **Séquençage multiple** - quantification de la variation technique.

**Les Réplicats biologiques.**

Si on veut être un peu plus crédible, on sait qu’il y a une variabilité individuelle, il faut aussi une variabilité biologique : on extrait le matériel biologique de plusieurs individus du même groupe, et on quantifie l’expression dans chaque individu. 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCRBCR/Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCR%20BC%202adb1079b86440b6af0116c2e8620b71/Untitled%201.png)

En général, en RNAseq, **le nombre de réplicats biologiques minimum exigé est de 3.**

### Séquençage.

Plusieurs étapes qui mènent au séquençage. En général on part de deux groupe controle-traités, le matériel biologique est extrait, seul l’ARN est gardé, on effectue une réverse transcriptase pour avoir l’ADNc, on utilise une technologie de séquençage, et par imagerie, on va identifier les séquences de chaque fragments.

On ne séquence qu’une seule partie du fragments (single end read) ou les deux extrémités (paired-end reads).

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCRBCR/Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCR%20BC%202adb1079b86440b6af0116c2e8620b71/Untitled%202.png)

### Données.

On obtient un fichier 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCRBCR/Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCR%20BC%202adb1079b86440b6af0116c2e8620b71/Untitled%203.png)

Ligne 1 : identifiant de la séquence qui commence par @ dans lequel on retrouve l’index qui va nous permettre par la suite d’identifier qui est à qui.

Ligne 2 : la séquence nucléotidique.

Ligne 3 : +

Ligne 4 : Score de qualité ou score Phred : Q = -10 x log(P)

- P = probabilité que la base appelée soit inccorecte.
- Un score de 10 signifie que la probabilité que la base appelée soit bonne est 1/10, elle est 1/100 pour un score de 20 et 1/1000 pour un score de 30.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCRBCR/Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCR%20BC%202adb1079b86440b6af0116c2e8620b71/Untitled%204.png)

Nos lectures proviennent de cDNA, eux même provenant de mRNA mature et épissés. Ainsi nos reads vont probablement se retrouver à cheval entre les introns d’un gène.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCRBCR/Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCR%20BC%202adb1079b86440b6af0116c2e8620b71/Untitled%205.png)

### Identification et reconstitution.

Deux références de génomes : Transcriptome de référence ou génome de référence.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCRBCR/Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCR%20BC%202adb1079b86440b6af0116c2e8620b71/Untitled%206.png)

### Alignement.

Assemblage de novo : on utilise pas le genome de reference et peut être utile pour trouver de nouveau transcrits.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCRBCR/Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCR%20BC%202adb1079b86440b6af0116c2e8620b71/Untitled%207.png)

### Quantification.

L’alignement peut être partiel

Différentes stratégie de quantification : 

- Union : la plus flexible, si on prend le 3e cas dans le tabelau, c’est toujours le gène A
- Intersection strict : toute la partie du read n’est pas dedans donc ce n’est plus le gène A.

En fonction des stratégie utilisée, les reads ne vont pas être comptabilisé ou non.

Plus ce gène est exprimé pour il y aura de reads en provenance de ces gènes là

On écarte les ambuiguités.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCRBCR/Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCR%20BC%202adb1079b86440b6af0116c2e8620b71/Untitled%208.png)

Différentes manières de quantifier (la définition d’un gène varie). Si on considère un gène comme un segment génomique avec Exons et introns et les transcrit sont des exons. On peut quantifier en analysant que les sections exons du génome. Une expression par exon permet de savoir quel exons sont exclus (gène isoformes).

Ce qu’on obtient est un tableau avec des lignes qui sont des gènes et des colonnes. On compte le nb de reads par gène. Comme on a des réplicats (colonne), utiliser l’ensemble des réplicats pour effectuer un test statistique.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCRBCR/Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCR%20BC%202adb1079b86440b6af0116c2e8620b71/Untitled%209.png)

### Question.

**Question 1.**

Le nombre de reads du gène B est deux fois plus élevé que le nombre de reads du gène A. Donc B est plus exprimé que A.

⇒ Les deux réponses sont bonnes (vrai et faux).

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCRBCR/Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCR%20BC%202adb1079b86440b6af0116c2e8620b71/Untitled%2010.png)

Le gène B peut en effet être plus exprimé que le gène A. ⏬

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCRBCR/Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCR%20BC%202adb1079b86440b6af0116c2e8620b71/Untitled%2011.png)

Mais il y a un autre scénario qui peut faire que c’est faux, si le gène B est plus long, il y aura plus de reads.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCRBCR/Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCR%20BC%202adb1079b86440b6af0116c2e8620b71/Untitled%2012.png)

**Question 2.**

Le gène A a plus de reads dans l’échantillon 3 par rapport à l’échantillon 2. Il est donc plus exprimé dans l’échantillon 3.

⇒ Faux et Vrai

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCRBCR/Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCR%20BC%202adb1079b86440b6af0116c2e8620b71/Untitled%2013.png)

Il y a deux possibilités, le gène A peut effectivement être plus exprimé dans l’échantillon 3 par rapport à l’échantillon 2 ou peut-être la profondeur de séquençage est plus grande pour l’échantillon 3 par rapport à l’échantillon 2. 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCRBCR/Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCR%20BC%202adb1079b86440b6af0116c2e8620b71/Untitled%2014.png)

### Normalisation.

- La profondeur de séquençage diffère d’un échantillon à un autre.
- Les gènes n’ont pas tous la même longueur.
- Deux échantillons peuvent ne pas avoir la même composition en gène.
- Les gènes n’ont pas tous la même composition GC. Cela peut induire un biais dans la composition en gène d’un échantillon.
- La couverture pour un gène en terme de nombre de reads qui lui est assigné n’est pas nécessairement uniforme.

Voilà les remarques qu’il faut prendre en compte dans l’analyse de nos résultats. 

Dans la littérature, il y a deux quantités qu’on observe : 

- Comptage par million ou ********CPM.********
    
    $$
    CPM_i = \dfrac{c_i}{\Sigma_{j=i}^N c_j}*10^6
    $$
    
    ci est l’expression du gène gi pour i = 1, 2, … N. Cette méthode ajuste pour la profondeur de séquençage.
    
    L’idée est de remarquer quand on regarde l’expression d’un gène donné et qu’on souhaite la quantifier (le nombre de reads pour ce gène), On multiplie par 1 millions pour avoir une valeur entre 0 et 1 million.
    

- **RPKM** : Reads Per kilobase per million of mapped reads.
    
    $$
    RPKM_i=\dfrac{c_i}{\dfrac{L_i}{1000}\dfrac{\Sigma_{j=1}^Nc_j}{10^6}}
    $$
    
    Li est la longueur du gène gi et ci son expression. Cette méthode prend en compte la profondeur de séquençage et la taille des gènes.
    

Voilà ce que ça représente quand ce n’est pas normalisé (à gauche).

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCRBCR/Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCR%20BC%202adb1079b86440b6af0116c2e8620b71/Untitled%2015.png)

### Clustering.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCRBCR/Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCR%20BC%202adb1079b86440b6af0116c2e8620b71/Untitled%2016.png)

### Analyse en composantes principales.

### MDS.

Objet en dimension quelqconque, on le projette de manière à maintenanir les

### analyse différentielle.

L’idée est l suivante : on considère que le matériel biologique est comme une soupe dans lequel on prend des fragments. On essaie de quantifier une distribution à ce que l’on observe. On a besoin d’une distribution afin de pouvoir dire uq’un gène est différentiellement exprimé entre les deux conditions. Test statistique obligatoire (ou interval de confiance).

Ensuite je quantifie la valeur normalisée du nombre de reads. 

### Récaputilatif.

Quatre étape dans la RNA-seq 

- Does données de séquences à une quantification d’expression.
- Normalisation et description.
- Analyse différentielle
- Analyse fonctionelle.

### Caractérisation du répertoire TCR.

Le répertoire immunitaire peut être intéressant dans le cadre physiopathologique. 

### Rosati

Quand on s’intéresse au repertoire immunitaire plus particulièrement TCR. Qu’est ce qu’on va séquencer ? 

On va en général séquencer CDR$\beta$ qui contient une partie du V-D-J. C’est la région en contact directe avec l’antigène et qui présente le plus de varaibilité.

On va aussi séquencer l’alpha.

UMI = unique molecular indetifier. On lit chaque fragemnt seul.

clonotype : partie extraite de la région du CDR3 qui va permettre d’ientifier chaque 

![bubble-chat.png](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCRBCR/Bases%20de%20l'analyse%20de%20données%20en%20RNASeq%20et%20TCR%20BC%202adb1079b86440b6af0116c2e8620b71/bubble-chat.png)

$\Large\texttt{Commentaires}$

---

---

$\Large\texttt{Fin de page}$
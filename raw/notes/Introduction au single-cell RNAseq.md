---
Date : October 4, 2022 3:50 PM
---

tags:: #academia/master, #master/ImmunologieHD, #master/Bioinformatique 


## A. Le séquençage d’ARN en cellule unique, c’est quoi et quelles sont les applications ?

### Single cell versus bulk RNA seq.

Tissu du sang, tissu intestinal, … On retrouve dans tout nos tissus un nombre variable de groupes cellulaires, ces tissus sont hétérogènes. 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled.png)

Le Bulk RNAseq, c’est extraire les ARN de toute les cellules, les mélanger et quantifier les ARN (transcrit), on obtient une moyenne des transcrits. Mais comme il y a différents types cellulaires, on obtient une moyenne de transcriptome tout type confondu

Le **single-cell RNAseq** permet d’obtenir le transcriptome de chaque cellule individuellement. On pourra ainsi étudier quels sont les gènes spécifique à chacune de ces cellules … et bien plus encore.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%201.png)

### Evolution des techniques de single cell RNA-seq.

Le single-celle RNA a été développé en 2009, c’est très récent. Au fur et à mesure des années, la technique s’est perfectionnée, permettant de transcrire plus de cellule individuellement plus rapidement. Certaines techniques que l’on va voir font appel à la microfluidique, au multiplexage, séparation physique des cellules, .. en bref, de nombreuses techniques qui permettent de séquencer de plus en plus de cellules en même temps tout en séparant les transcriptome.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%202.png)

### Applications du scRNA-seq.

Le nombre de publications utilisant le scRNA-seq a été exponentiel d’années en années. La technique permet de couvrir un domaine d’application très large.

A quoi ca sert ? Au sein d’une population hétérogène de caractériser des nouveaux types cellulaires, des populations complexes individuellement, de faire ressortir des types cellulaires rares, analyser un réseaux d’interaction.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%203.png)

## B. Différentes techniques : de la préparation des cellules au séquençage des librairies.

### Préparation de suspension cellulaires.

**Biopsies.**

Biopsies humaines, animales, souris, cellules en culture via différente techniques, généralement dissociation mécanique et enzymatique (collagénase, protéase, trypsine, papaïne, libérase…). 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%204.png)

Dissociateur avec tube falcon, on met notre biopsie, une palme va tourner et écraer la biopsie, les cellules vont se dissocier les unes des autres via l’activité enzymatique des composé cités juste avant.

**Liquides biologiques (sang, moelle).**

On peut partir de liquide biologique comme sang ou moelle osseuse, les globules rouges vont être chiant, on va donc les viser avec des tampons spéciaux ou des gradients de densité.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%205.png)

**Le plus simple : partir d’une culture cellulaire.**

On détache les cellules de la surface de la boîte de pétri via l’action de la trypsine.

---

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%206.png)

Une fois que la biopsie est séparée, il est probable qu’on retrouve encore des morceaux de tissus pas bien séparés : une étape de filtration s’en suit (tamis cellulaires). On peut de nouveau lyser les globules rouges avec une solution, mais ce qui est très important, c’est l’étape d’après, on veut **que des cellules vivantes**, on retire les cellules mortes par tri cellulaire en cytométrie.

⇒ Etape finale ; on vérifie la qualité des cellules (on les compte) et on passe à la partie transcriptomique en scRNA-seq (entre 500 et 10 000 c par échantillons).

### Critères de qualité.

Critères de qualité : on veut des cell isolées, vivantes, exempt de débris, hautement viables, bien isolées

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%207.png)

En fonction des étapes de nettoyage, on voit que la qualité des librairies finales est de mieux en mieux en fct de es étapes de nettoyage.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%208.png)

**Autre méthode possible de préparation des cellules :**

Des fois c’est difficile d’avoir des cellules vivantes à partir de biopsie (comme cerveau à cause d’une protéine particulière). Au lieu d’isoler la cellule entière, on peut isoler leur noyau, dans ce cas là on analyse plus les RNA cytoplasmique mais les nucléaires.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%209.png)

Les tissus difficiles à dissocier, fragiles, congelés, …mais on perd l’information des RNA cytoplasmiques. Tendance à une dégradation des mRNA.

### Préparation des librairies de séquençage.

4 methodes principales qui existent :

- Une basée sur des valves.
- Droplets.
- Nanowells
- Multiplexage.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2010.png)

### Technologie Chromium Droplets.

La technologie des droplets est une des plus utilisée, le principe repose sur un système de ADN barcodés et de micro-fluidique.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2011.png)

- Encapsulation d’une cellule et d’une bille barcodée dans une gouttelette d’huile.
- Jusqu’à 8 échantillons traités en parallèle.
- Séquençage des extrémités 3’ ou 5’ mRNA.

Les cellules sont, par micro-fluidique, séparées les unes des autres dans des gouttelettes lipidique dans laquelle on retrouve aussi une bille de saccharose.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2012.png)

La puce qu’on va utiliser pour faire la manip. On met nos sus dans la ligne 1, nos blles dans la 2. Avec de la microfluidique un flux va se former et des émulsions seront crée avec 1 échantillon différent (jusqu’à 8).

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2013.png)

On lyse les cellules à l’intérieur des gouttelettes, il faut savoir que sur les billes de saccharose on retrouve à la surface des ADN ayant une séquence commune identifiant la bille de saccharose (R1) et une séquence UMI qui identifie chaque ARN associé à la bille RNA.

Les ARN s’accroche à la séquence ADN via leur queues polyA (présence d’une séquence polydT sur les ADN barcodés).

On effectue une reverse transcription et PCR des ADNc puis séquençage.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2014.png)

### Technologie avec microfluidique et valves.

Technologie qui fait aussi appel à la microfluidique, avec des microvalves et contrôle de pression. Repose aussi sur le barcoding. Des valves qui s’ouvrent et qui se ferment. On séquence l’ARN entier mais l’inconvénient un plus faible débit.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2015.png)

### Technologie Nanowell.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2016.png)

### Multiplexage ou combinatorial indexing.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2017.png)

On se fiche d’avoir une seule cellule / puit. On prend notre suspension et on les mets dans des plaques 96 puits avec un nombre variable de cell / puit. On ajoute à nouveau des barcodes (séquence spécifiques). Une fois que les cellules sont barcodées, on prélève et on remélange, et on redistribue de manière aléatoire puis on rebarcode une seconde fois, on répète pour avoir des combinaisons de plus en plus importantes.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2018.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2019.png)

## C. L’analyse et l’interprétation des résultats.

### Pre-processing.

La première étape est celle de pré-processing. On va demultiplexer nos résultats : on va compter toute les séquences, les aligner sur le génome et les quantifier. Dans la cellule 1 par exemple, on a détecté 3 transcrit via leur UMI qui correspondent au gen 1, etc etc

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2020.png)

### Quality control.

On a des étapes de contrôle qualité, il faut nettoyer les données. 

- On va vérifier le nombre de gène par barcode, on élimine les cellules où on va détecter un trop grand nombre de gènes élevées et à l’inverse on élimine aussi les cellules avec très peu de gènes (surement des globules rouges).
- On va aussi faire un filtre sur les gènes mitochondriaux : quand une cellule est en train de mourir, elle va avoir tendance à relarguer l’ARN mitochondriaux. Si on en détecte trop : c’est que la cellule est en train de mourir : on l’élimine de l’analyse.
- Dans le cas des droplets, on a pour objectif d’avoir une seule cellule par gouttelette, c’est globalement le cas, mais parfois on retrouve dans ces gouttelettes du matériel génétique de cellules précédemment lysées, on va aussi cibler ces ARN là durant l’analyse pour les nettoyer

### Normalization et intégration.

effet batch ; couches de couleurs, en corrigeant ces derniers on obtient qqc de plus homogène.

### Pour faire les analyse bioinformatique.

Plusieurs outils comme Seurat (R), scanpy (python), outils qui regroupent 30 catégories fonctionnelles.

On analyse les résultats :

- Au niveau cellulaire : type cellulaire, proportion, évolution cellulaire, …
- Au niveau génique : gène exprimés, dérégulés, voie de signalisation impactées…

### Interprétation cellulaire.

On fait du clustering, on visualise les données en deux dimensions. Chaque point est une cellule, plus les cellules vont avoir un transcriptome qui se ressemble, plus elles seront clusterisées. 3 méthodes populaires : PCA, t-SNe et UMAP. 

On a visualisé nos données en 2D. Certaines cellules se ressemblent mais on ne sait pas à quoi elles correspondent. On va annoter ces clusters et identifier des gènes marqueurs qui les caractérisent.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2021.png)

### Exemple.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2022.png)

### Intérpretation au niveau génique.

**Expression différentielle :** Quels sont les genes différentiellement exprimés entre 2 conditions parmi la population de T-cell. Cf le premier cours avec les patients atteints de COVID.

**Gene set analysis :** A quoi servent les x gens trouvés différentiellement exprimés ? Classification selon les processus biologiques à l’aide de databases (Gene ontology, KEGG…).

**Gene regulatory network :** Identification des genes régulateurs impliqués dans le processus biologique. Analyse de l’expression ligand-récepteur.

## D. Exemple : analyse d’un échantillon de peau.

On analyse la peau d’un patient, on détecte les chiffres suivants dans la biopsie.

### Préparation des cellules et séquençage des librairies.

Biopsie faite (4mm de peau) 2000 euro par échantillon. On analyse cellule de la peau et on sequence 7k cellules, 11 transcript par cellules et environ 1300 genes par cellules. 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2023.png)

### Analyse et interprétation des résultats.

On effectue ensuite un contrôle qualité sur nos librairies scRNA-seq, plus c’est bleu, moins il y a de gènes exprimés, pourquoi ? L’analyse des gènes exprimés permet de voir que ces cellules en bleu (dans le plot) expriment beaucoup d’himunoglobuline, ce sont en réalité des globules rouges.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2024.png)

On filtre ces globules rouges (on les enlève de l’analyse), même processus pour l’ADN mitochondrial, on élimine les doublets, les cellules mortes, ceux avec peu d’UMI.

### Résultat du contrôle qualité.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2025.png)

On procède ensuite à une identification des cellules basé sur des librairies (CellMarker, Human protein Atlas, literature) ou par inspection manuelle.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2026.png)

Si on filtre par différents gènes, on peut ici par exemple mettre en évidence les fibroblastes.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2027.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2028.png)

## E. Nouvelles technologies basées sur le single-cell.

### **ATAC-seq au niveau épigénétique.**

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2029.png)

### **Au niveau protéique : CITE-SEQ.**

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2030.png)

On met en évidence des protéines de surface, épitopes, des complexes. On utilise des anticorps barcodés, ils vont reconnaître un épitope de surface.

On peut aussi au niveau des BCR/TCR : on peut grace à des anticorps marqués par des barcode, avoir la séquence

### **Spatial RNA sequencing (spRNA since 2019).**

Analyse de l’expression des gènes sur une coupe de tissu.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2031.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2032.png)

## F. **Applications à la recherche médicale.**

### Atlas project → Human cell atlas.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2033.png)

15 organes majeur et on fait transcriptome single cell pour voir similarité et différence entre les organes. A permis de developper un site pour savoir quel cellule exprime un gene, sa quantité d’expression et si il est impliqué dans une maladie.

**Human lung atlas.**

Atlas du poumon humain de fait, on découvert 56 types cellulaire different, on pu mapper grace a des coupes histologique de poumons.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2034.png)

**Human Bone Marrow Atlas.**

comment on passe d’une cellule souche a différencier, création d’un site internet pour savoir dans quel type cellulaire exprimé.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2035.png)

![bubble-chat.png](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/bubble-chat.png)

$\Large\texttt{Commentaires}$

---

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2036.png)

<aside>
⚠️ Le premier Bulk RNAseq a été fait en 2006.

</aside>

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2037.png)

**Elimination de l’ADN mitochondrial**

Celles dont l’ADN mitochondrial représente plus de 10% sont éliminés (mort cellulaire).

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2038.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2039.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20Introduction%20au%20single-cell%20RNAseq/Introduction%20au%20single-cell%20RNAseq%202e294072a1904d2798075ef85d9fdfbe/Untitled%2040.png)

---

$\Large\texttt{Fin de page}$
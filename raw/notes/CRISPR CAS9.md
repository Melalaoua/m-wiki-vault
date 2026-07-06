---
Date : October 14, 2022 9:37 PM
---

up:: [[TBMC]]
tags:: #academia/master, #master/Techniques



### Standard maintenance of INBRED COLONY - Based on repeated brother-sister mating.

Chez l’humain, il y a un grand nombre de différences pour les génomes. Il est difficile pour CRISPR d’avoir une coupure aussi diversifiée. On connait cependant le génome de la souris au nucléotide près et ces dernières ne sont pas aussi diversifiée que nous, leurs séquences sont identiques (comme des jumeaux humains).

Le dernier siècle était remplit de découvertes importantes en mutagénèses que l’on va discuter ici. 

On a vu dans le cours précédent sur la transgénèse 3 approches méthodologiques pour manipuler le génome (notamment chez la souris) : 

1. Transgénèse par injection d’ADN dans le proncucléaire.
2. Transgénèse par recombinaison homologue dans les ES de souris.
3. Edition du génome dans des oeufs fertilisés via l’aide de nucléases.
    
    ZFN, TALE, CRISPR/CAS9
    

### Nuclease genome editing by microinjection in fertilized eggs.

En général, pour effectuer de la mutagénèse, un plasmide est utilisée (contenant le gène recombinant) qui sera transcrit sous forme protéique. 

Mais chez la souris, cette mutagénèse n’est pas populaire, l’injection d’ARN dans l’ovocyte sous forme cas9 est très populaire.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221014%20Crisp-Cas9/CRISPR%20CAS9%20edf005ecdda3426daef33f1c91a86714/Untitled.png)

## Les nucléases.

Sommaire :

### Comment les nucléases fonctionnent ?

### ZFN.

### Tale nuclease.

### Crispr/cas9.

---

### How do we use nucleases ?

Les nucléases vont générer des coupures doubles brins à des endroits précis (préalablement choisis) et ces coupures vont faire intervenir des mécanismes de réparation de l’ADN. Il est possible de détourner ces mécanismes de réparation en injectant de l’ADN donneur que la cellule va utiliser pour réparer la séquence, sans donneur elle réparera l’ADN de manière approximative, générant des mutations.

La NHEJ ou ********************Non-homologous end joining******************** va réparer l’ADN sans brin matrice, résultant en une délétion de la séquence ciblée.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221014%20Crisp-Cas9/CRISPR%20CAS9%20edf005ecdda3426daef33f1c91a86714/Untitled%201.png)

Cependant, l’injection de…

- **ADN db donneur.**
- **ADN sb (avec mutation : mutagénèse).**
- **ssDNA délivré par vecteur viral (AAV).**

…Ces ADN insérés vont servir de matrice pour la HR (**homology recombination**)ou la HDR (**Homology-directed repair**) lors de la réparation de l’ADN, résultant en une transgénèse.

### How to generate rodent models faster ?

La nucléase est introduite dans l’ovocyte fertilisé (avec ou sans ADN donneur) par injection ou électroporation. L’ovocyte est ensuite réimplanté dans une femelle pseudo-gestante, donnant naissance à des **************************************souris mosaïques.**************************************

Les souris mosaïques sont des fondateur qui seront croisés (car ils contiennent plusieurs mutations). Lorsqu’un fondateur est croisé, il faut prévoir comment cribler les portées pour trouver la modification cherchée. ****************************************************************************

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221014%20Crisp-Cas9/CRISPR%20CAS9%20edf005ecdda3426daef33f1c91a86714/Untitled%202.png)

### Detection of NHEJ and HDR in founders.

Pour cribler les fondateurs, différentes techniques sont possibles :

- PCR standard.
- Séquençage de Sanger du produit de PCR.
- Sub-cloning of PCR products followed by Sanger sequencing.
- qPCR or ddPCR.
- Gene analyzer.

### How to fix genomic modification ?

Les fondateurs sont croisés avec d’autres souris, donnant des hétérozygotes F1.

Là aussi, les mutations seront recherchées dans des biopsies (oreilles/queues) et par 

- PCR
- Sanger.
- T7 endonuclease.
- qPCR, droplet digital PCR.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221014%20Crisp-Cas9/CRISPR%20CAS9%20edf005ecdda3426daef33f1c91a86714/Untitled%203.png)

Dans les F1 :

1. Une allèle est WT.
2. L’autre est “CRISPRisé”

### Skip sur les ZFN et Tale : ces techniques ne sont plus utilisées.

### Depuis 2013 : A true Evolution.

Arrivée de CRISPR en 2013, une réelle révolution. (7103 publications en 2021).

**How do CRISPR-Cas systems achieve sequence-specific double-strand breaks in DNA ?**

Cleavage of target DNA by the CRISPR-cas system of the bacterium Streptococcus pyogenes requires only a single protein, the nuclease Cas9, and an engineered, single stranded ****************************************************single guide RNA, or sgRNA****************************************************. At it’s 5’ end, the sgRNA contains approximately 20 nucleotides that can be customized to complement the desired target site, followed by multiple stem-loop structures at it’s 3” end, which are required for binding the nuclease.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221014%20Crisp-Cas9/CRISPR%20CAS9%20edf005ecdda3426daef33f1c91a86714/Untitled%204.png)

Cas9 is a large, 158kDa protein which contains two lobes : a REC lobe, which binds to the duplex formed between sgRNA and the target strand of DNA, and a NUC lobe, which contains the two nuclease domains that are responsible for cleavage of the two strands of the target DNA.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221014%20Crisp-Cas9/CRISPR%20CAS9%20edf005ecdda3426daef33f1c91a86714/Untitled%205.png)

Cas9 also contains a region that recognizes short (usually three or four nucleotide) sequence of DNA known as the ******************protospacer-adjacent motif (PAM)******************. if the target DNA sequence complementary to the sgRNA is adjacent to a PAM, the cas9 complex cleaves both target strands using the two nuclease domains fo the NUC lobe.

<aside>
⚠️ As the specificity of this nuclease is driven by a complementary sequence of RNA, the CRISPR-Cas system can be engineered to cleave virtually any DNA sequence, provided it is adjecent to a PAM, without the need for designing new protein recogniation domains such as this is required for ZFNs or TALENs.

</aside>

CRIPSR est l’acronyme de Clustered Regularly Interspaced Short Palindromic Repeats. C’est un locus qui existe chez la bactérie, composé de séquences répétées palindromiques régulièrement interspaced par des séquences variables. Le locus est transcrit en ARN puis coupé pour donner le CRISPR RNA. 

A côté de ce locus, il y a le CRISPR associated genes (cas). Ce sont des processus impliqués dans des défenses contre des virus ou un ARN exogène.

### Systèmes.

Il y a trois systèmes CRISPR : le plus utilisé est le **système de type II**. Il s’agit du système le plus simple parce qu’il y a une seule protéine produite par les gènes Cas (cas9) qui va s’associer à deux petits ARN (CRISPR ARN). La partie variable des répétitions va cibler cette protéine sur l’ADN cible.

S’il y a une reconnaissance spécifique entre l’ARN et l’ADN cible et qu’il y a un site PAM (séquence NGG pour la nuclease Cas9), l’enzyme va s’arrêter et réaliser une coupure double brin.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221014%20Crisp-Cas9/CRISPR%20CAS9%20edf005ecdda3426daef33f1c91a86714/Untitled%206.png)

### Quels sont les bénéfices à utiliser CRISPR/CAS9 ?

- Simple, nécessite que la nucléase Cas9 et un gRNA (ou un dual Cr et TracRNA)
- Nécessite des séquences NGG.
- Rapide et peu couteux.
- Peut s’utiliser sur n’importe quel génome.
- Utilisable dans des organismes ou des cellules.

### Application de CRISPR/CAS9.

Le système est très simple. Si on exprime la nucléase avec un ARN guide (on prend la séquence que l’on souhaite manipuler), on peut cibler n’importe quel gène, il y a donc des centaines d’applications. On peut utiliser CRISPR/CAS9 pour :

- L’édition du génome (Knock-out, Knock-In).
- Visualisation d’un locus donné dans une cellule vivante.
- Protéomique d’un locus particulier.
- Régulation transcriptionnelle (induire ou réprimer l’expression d’un gène donné).
- Modulation épigénétique (introduire les modifications).
- Crible à l’échelle du génome.

La cas9 est une nucléases capable de provoquer une mutation double brin sur l’ADN, lorsqu’elle coupe l’ADN double brin, deux mécanismes de réparation de l’ADN interviennent (vu plus haut) :

- Relier les deux extrémités d’ADN : peut changer le cadre de lecture et donc introduire un codon stop prématuré et générer un KO.
- Recombinaison homologue : si on introduit cas9 et l’ARN guide, on peut utiliser ce pathway de réparation de l’ADN pour faire des KI donc introduire les séquences que l’on veut à l’endroit où l’on veut par homologie.

### The use of Dead Cas9 ( dCas9).

Les applications reposent sur les sites catalytiques de la Cas9. La dCas9 est un mutant avec un site catalytique inactif. Elle va s’associer à l’ADN à l’endroit cible comme elle doit le faire, mais elle ne coupera pas. Elle sera cependant associée à l’ADN cible.

L’avantage de la dCas9 est qu’elle peut être fusionnée à une protéine fluorescente pour cibler n’importe quelle location génomique du moment qu’on exprime le gRNA. **Il est ainsi possible de cibler les télomères ou l’hétérochromatine**.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221014%20Crisp-Cas9/CRISPR%20CAS9%20edf005ecdda3426daef33f1c91a86714/Untitled%207.png)

### Off-target.

La Cas9 est capable d’avoir des effets ********************off-target********************. La cas9 parvient à trouver sa cible via son ARNguide, si il y a un appariement entre l’ADN cible et le gRNA, elle coupera à cette endroit, mais parfois elle peut s’apparier à un autre endroit du génome et générer des mismatch, dans ce cas là elle coupera aussi, même si le gRNA est pas parfaitement apparié à l’ADN.

- Cas9 tolerate mismatches between gRNA and target DNA at different positions in a sequence dependant manner, sensitive to the number, position and distribution of mismatches.
- Cas9-mediated cleavage is unaffected by DNA methylation.
- dosage of CAS9 and sgRNA can be titrated to minimize off-target.

<aside>
⚠️ Les Off-target sont problématiques in vitro mais pas tant que ça in vivo.

</aside>

### Knock-out par Crispr/cas9.

Un des exemple d’application de Crispr/cas9, 

- Génération d’indels : la nucléase coupe à un endroit spécifique, sans insertion d’ADN ⇒ NHEJ, mais il n’est pas possible de contrôler la taille de la coupure.
    
    ⇒ Méthode moyennement utilisée, genotyping pas de bonne qualité.
    

- Délétion d’exon : usage de 2 CRISPR/CAS9 différent
    
    ⇒ Genotyping facile, la délétion exon entraîne l’inactivation et donc un knock out sûr et certain. 
    

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221014%20Crisp-Cas9/CRISPR%20CAS9%20edf005ecdda3426daef33f1c91a86714/Untitled%208.png)

### Understanding IMPC alleles.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221014%20Crisp-Cas9/CRISPR%20CAS9%20edf005ecdda3426daef33f1c91a86714/Untitled%209.png)

![bubble-chat.png](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221014%20Crisp-Cas9/CRISPR%20CAS9%20edf005ecdda3426daef33f1c91a86714/bubble-chat.png)

$\Large\texttt{Commentaires}$

---

### Genome editing as Classical transgenesis.

On a vu ce schéma dans la [Transgénèse.](https://www.notion.so/Transg-n-se-b2cdf9c462d744269ebe19388ceef0b0) , se référer à ce cours.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221014%20Crisp-Cas9/CRISPR%20CAS9%20edf005ecdda3426daef33f1c91a86714/Untitled%2010.png)

Exemple de dcAS9 : single locus visualization.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221014%20Crisp-Cas9/CRISPR%20CAS9%20edf005ecdda3426daef33f1c91a86714/Untitled%2011.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221014%20Crisp-Cas9/CRISPR%20CAS9%20edf005ecdda3426daef33f1c91a86714/Untitled%2012.png)

---

$\Large\texttt{Fin de page}$
# Analyse du transcriptome.

Date: November 12, 2021 5:29 AM
Semaine: 10
Travaillé ?: Yes
Unité d'enseignement: TIG

Le transcriptome est un aspect de l'expression du génome à un moment t, et/ou dans une condition physiologique donnée.

L'analyse globale du transcriptome permet **d'identifier l'ensemble des gènes qui s'expriment dans un type cellulaire** donné et de **mettre en évidence des aberrations génomiques** dans le cas de cancer (translocations conduisant à l'apparition de protéines chimères). Mais aussi **de mettre en évidence la présence d'ARNm isoformes**, issus de mécanismes de polyadénylation alternative, d'épissage alternatif ou synthétisés à partir de promoteurs alternés.

**Quantification d'un ou plusieurs ARNm.**

- **Nothern blot, puces à adn :** techniques basées sur l'hybridation d'une sonde marquée à l'ARNm cible.
- **RT-qPCR :** PCR quantitative effectuée sur un 'reverse transcript".

**Analyse globale du transcriptome.**

- **RNA-seq :** séquençage à haute débit ou NGS (next generation sequencing) : illumina, 454 pyro....

**Préparation d'une solution ARN totaux.**

1. Broyage des cellules dans un tampon adéquat : extrait brut.
2. Extraction des ARN :
    1. addition de phénol ou trizol.
    2. Agitation.
    3. Centrifugation.

1. Précipitation des ARN : 
    1. Prélever la phase aqueuse.
    2. Précipitation (sel(NaCL, NH4Cl) + Alcool (EtOH, Isopropanol)).
    3. centrifugation.

1. Quantification des ARN : mesure A260 (absorbance).

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled.png)

### Profil des gels d'agarose sur lesquels des ARN sont séparés par électrophorèse.

---

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%201.png)

## I. Nothern blot.

L'objectif du nothern blot est de **détecter la présence d'un ARN** et/ou ses isoformes dans un extrait total d'ARN en se basant sur le principe d'**hybridation d'une sonde marquée à un ARN cible** selon les étapes suivantes :

- Electrophorèse en conditions dénaturantes (gel agarose pour long ARN, PAGE pour petits ARN).
- Fixation des ARN sur la membrane.
- Hybridation avec une sonde marquée spécifique d'un ARN donné.
- Lavages.
- Révélations.

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%202.png)

### Hybridation des acides nucléiques.

---

La cible est l'ARN ou les ARN que l'ont veut détecter, ces derniers sont fixés sur un support solide comme une membrane.

On utilise comme sonde un oligodésoxyribonucléotide de séquence complémentaire et antiparallèle à une région de l'ARN cible qui va s'hybrider à ce dernier et former un hétéroduplexe.

Les conditions d'hybridation : 

- Optimiser la formation du duplexe.
- Limiter le bruit de fond.
- Assurer une spécificité d'hybridation.

### Condition d'hybridation et stringence.

---

La stringence d'hybridation : degré de tolérance des mésappariements de bases dans les hétéroduplexes

- Stringence élevée : seuls les appariements forts subsistent.
- Stringence faible : certains mésappariements peuvent devenir stables en diminuant la température d'hybridation ou en augmentant la concentration en sels monocationiques.

<aside>
📎    - Les Ions Na+ stabilisent les liaisons hydrogènes.
   - Les molécules fortement polaires (urée, formamide) rompent les liaisons hydrogènes et abaissent le Tm.

</aside>

### Taille de la sonde et stringence.

---

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%203.png)

### Analyse comparative de l'expression d'un gène dans différents tissus.

---

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%204.png)

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%205.png)

## II. La PCR en temps réel ou qPCR (PCR quantitative).

La qPCR permet **l'analyse d'expression de gènes** (quantification d'ADN et d'ARN).

On peut y étudier la réponse cellulaire face à différentes substances, détecter et quantifier des agents pathogènes, diagnostiquer... 

 

<aside>
📎 On peut rechercher et détecter les virus de dengue, chikungunya, Coronavirus, cancers...

</aside>

La PCR classique est utlisée pour amplifier in vitro l'ADN. La quantité d'amplicons obtenue est mesurée après plusieurs cycles de PCR. Elle ne permet cependant pas de quantifier l'ADN cible de départ (matrice ADN).

- La PCR en temps réel est basée sur le principe de la PCR classique.
- La quantité d'amplicons produite est mesurée au cours de la réaction en temps réel grâce à l'utilisation dans le milieu réactionnel d'un marqueur fluorescent qui s'intercale dans l'ADN au cours de sa synthèse.
- La quantité de fluorescence mesurée à chaque cycle est proportionnelle à la quantité d'ADN synthétisé.
- La cinétique d'amplification d'ADN est suivie au cours du temps, ce qui permet de quantifier le matériel de départ (l’ADN cible) au niveau de la phase exponentielle de la synthèse.

### Cinétique d'une réaction de PCR.

---

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%206.png)

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%207.png)

### qPCR.

---

Marquage de l'ADN au cours de son amplification : plusieurs méthodes. Le fluorochrome utilisé est le **SYBR Green.**

- En solution ne fluoresce pas.
- S'intègre dans l'ADN au cours de sa synthèse.
- Fluoresce quand il est lié à l'ADN.
- Se dissocie lors de la dénaturation de l'ADN.

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%208.png)

### qPCR : représentation graphique sous forme de courbes sigmoïdes.

---

Ci-dessous voici l'image qui apparaît en temps réel sur l'écran de la machine.

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%209.png)

### qPCR : Quantification de l'ADN cible.

---

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2010.png)

Ce cycle seuil ou ct (cycle treshold) correspond au nombre de cycles de PCR nécessaires pour détecter de la fluorescence au niveau du seuil de détection.

Le Ct est dépendant de la quantité de matrice utilisée dans la réaction.

Equation d'amplification de l'ADN cible, au bout de n cycles de PCR.

$$
X_n = X_0* (1+E)^n
$$

Le nombre de molécules cibles obtenues au bout de n cycles (=Ct) de PCR dépend de :

- X0 : le nombre de molécules cibles au temps Zéro.
- E : efficacité de l'amplification de la matrice.
- Si efficacité : 100% Xn= X0 . 2n.

### qPCR : effet de l'efficacité de réaction.

---

L'efficacité de la PCR doit être vérifiée

AU niveau de la phase exponentielle pour une efficacité de 100% (E=1).

- La quantité d'ADN cible double à chaque cycle.
- La quantité d'amplicons est le reflet de la quantité d'ADN cible introduit dans le milieu réactionnel.

Effet de l'efficacité de la réaction sur le taux d'amplification de l'ADN, exemple au bout de 25 cycles de PCR (X0 = 1).

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2011.png)

### qPCR : détermination de l'efficacité.

---

Préparation d'une gamme d'une dilution d'ADN (e.g ADN plasmidique), et tracer une courbe standard.

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2012.png)

### qPCR : courbe standard.

---

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2013.png)

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2014.png)

L'efficacité dépend de la longueur de l'amplicon (pas plus de 150 bp), de la teneur en GC, structure secondaire dans les amorces, concentration des composants de la PCR (matrice, Mg2+).

Le choix des amorces est très important :

- Spécificité d'hybridation ; vérifier grâce à la courbe de fusion ou sur gel.
- Pas de formation de dimères (vérification avec courbe de fusion).
- Le Tm doit être élevé 58-60°C.
- Le Tm des deux amorces doit être proche <2°C.
- La taille des amorces : 18 à 30 nucléotides.
- La taille des amplicons ; 150 bp.
- %GC : 30-60%.

<aside>
📎 Choisir des amorces et s'hybrident sur des exons différents.

</aside>

### qPCR : courbe de fusion.

---

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2015.png)

### qPCR : contrôle de la spécificité de réaction.

---

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2016.png)

### qPCR : témoins pour la spécificité des amorces.

---

Essai sans matrice (NTC) : détection d'un contaminant présent dans les solutions ou sur le matériel utilisé (cônes à filtre).

Essai NoRT : pas d'ajout de reverse transcriptase dans la préparation du cDNA = détection de l'ADNg contaminant.

<aside>
📎 Choisir des amorces qui s'hybrident sur des exons différents.

</aside>

Courbes de fusion effectuées en parallèle :

- Permet de contrôle s'il y a un seul produit amplifié.

- Mettre en évidence d'éventuels dimères d'amorce.

<aside>
📎 La courbe de fusion permet de mettre en évidence la contamination de l'échantillon par de l'ADNg.

</aside>

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2017.png)

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2018.png)

### qPCR : méthodes de quantification.

---

Deux méthodes de quantification sont possibles : quantification **absolue** et **relative.** La quantification relative ou quantification comparative consiste à **mesurer la variation de la quantité d'une molécule donnée par rapport à une référence**.

Exemple : un traitement augmente l'expression d'un gène 

→ Les résultats de la quantification absolue :

- Avant traitement 10 000 copies du transcrit.
- Après traitement 50 000 copies du transcrit.

La **quantification relative donnera comme information :** une augmentation d'un facteur 5 de l'efficacité d'expression du gène étudié.

### Quantification absolue.

---

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2019.png)

### Quantification relative.

---

**Méthode des $\Delta \Delta$Ct.**

- La variation de l'expression d'un gène cible (avant et après traitement) est comparée à la variation d'expression d'un gène contrôle (avant et après traitement).

- L'efficacité d'amplification de la molécule cible et de la molécule de référence doit être la même soit 100 %

Un standard interne sera un gène dont l'expression ne varie pas (gène de ménage) qui va permettre de **normaliser les résultat, corriger les variations dues à la qualité des échantillons, le rendement d'extraction, les erreurs de pipetage.**

<aside>
📎 Gène de ménage utilisés : GAPDH, ARNr 18S, actine. (GAPDH augmente la qte de cancers, attention).

</aside>

### Equation de l'amplification exponentielle.

---

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2020.png)

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2021.png)

### qPCR : exercice de TD.

---

echantillon A : cell traitées par la drogue.

Rapport positif donc 

### Quantification relative.

---

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2022.png)

### Exemple de résultats obtenus.

---

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2023.png)

### Synthèse de l'ADNc (rappel).

---

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2024.png)

## III. Analyse globale.

Analyse du transcriptome par séquençage à haut-débit **RNA-seq.**

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2025.png)

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2026.png)

Cellule de flux (flow cell) utilisée pour le séquençage.

Des oligonucléotides de séquence complémentaire et antiparallèle à la séquence des étiquettes ligaturées aux extrémités des fragments d'ADNc, sont fixés sur la cellule.

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2027.png)

### Principale étapes de la méthode.

---

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2028.png)

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2029.png)

Séquençage basé sur l'incorporation de dNTPs marqués spécifiquement par un fluorophore donné. Un seul dNTP est ajouté à chaque cycle. 

Analyse séquentielle de la fluorescence.

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2030.png)

![Untitled](Analyse%20du%20transcriptome%203cc1b95d7462442eaa5f556603477df0/Untitled%2031.png)

→ Suite [Maturation des pré-ARN.](https://www.notion.so/Maturation-des-pr-ARN-2feb80264d4447fab52859e6e99c31db)
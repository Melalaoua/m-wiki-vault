---
Date : October 19, 2022 2:05 PM
---

up:: [[OGTE]]
tags:: #academia/master, #master/génétique





## **Préambule.**

**La méthylation : sur la cytosine en position 5. La méthylation des CpG permet la répression de la transcription surtout des séquences répétées (LINE, SINE,…).**

**Dans l’embryon, on perd la méthylation, du coup les séquences répétées peuvent s’exprimer. Dans l’embryon précoce, c’est le cas. Une minorité de séquence LINE sont entières car très souvent les LINE sont tronquées.**

### Différentes niveaux d’organisation de la chromatine.

Dans un noyau en interphase : compaction de l’ADN dépend de différents niveaux d’interactions impliquant les histones.

**Questions :**

- Rôles de ces différents niveaux de compaction.

- Décrire le profil d’organisation de la chromatine sur l’ensemble du génome.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20221019%20Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’ensemble%20du%20génome/Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’%200fb021e586be446fb6de4713989b1591/Untitled.png)

### Dynamique de la structure chromatinienne.

La structure des nucléosomes n’est pas statique, particulièrement aux points d’entrée et de sortie du nucléosome. Au niveau de ces fragments d’ADN, il y a des facteurs de la transcription qui peuvent lier l’ADN. La position d’un nucléosome peut varier sur l’ADN, déterminé par plusieurs facteurs, mais il existe en particulier des complexes protéiques qui permettent de **déplacer** ces derniers, les histones peuvent aussi être **dissociées**, ou **remplacées par des variants d’histones**.

<aside>
⚠️ **Les nucléosomes peuvent subir des modifications post-traductionnels (PTMs).**

</aside>

### **Les complexes de remodelage.**

Complexe de remodelage qui permettent de **déplacer les nucléosomes de la séquence ADN** (activité ATPasique) qui permet de modifier la structure du nucléosome. 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20221019%20Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’ensemble%20du%20génome/Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’%200fb021e586be446fb6de4713989b1591/Untitled%201.png)

⇒ Le complexe se fixe et interagit à la fois avec l’ADN et le nucléosome : **fait glisser la molécule d’ADN sur le nucléosome.**

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20221019%20Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’ensemble%20du%20génome/Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’%200fb021e586be446fb6de4713989b1591/Untitled%202.png)

Il y a aussi des complexes de remodelage qui vont pouvoir enlever une partie (perte d’un dimère H2A-H2B)/ ou supprimer totalement / un nucléosome.

<aside>
⚠️ L’activité des complexes de remodelage de la chromatine est fortement régulée : permet de modifier localement la compaction de la chromatine.

</aside>

### Distribution des nucléosomes : positionnement et taux d’occupation (occupancy).

**Positionnement** (à chaque pb du génome) : localisation des nucléosomes. Fraction des cellules d’une population parmi lesquelles cette position correspond au centre de symétrie d’un nucléosome (probabilité que le dyad d’un nucléosome soit à une position génomique déterminée).

**Taux d’occupation** : fraction des cellules d’une population parmi lesquelles cette position est occupée par un octamère d’histone 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20221019%20Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’ensemble%20du%20génome/Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’%200fb021e586be446fb6de4713989b1591/Untitled%203.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20221019%20Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’ensemble%20du%20génome/Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’%200fb021e586be446fb6de4713989b1591/Untitled%204.png)

### Un profil moyen de distribution des nucléosomes sur le génome dépend du positionnement et du taux d’occupation.

Les méthodes d’analyse de la localisation génomique des nucléosomes sont réalisées en utilisant la chromatine extraite de très nombreuses cellules.

Pour une région génomique donnée, le profil obtenu dépend de deux facteurs :

1. La position exacte de chaque nucléosomes dans chaque cellule = positionnement.
2. Le pourcentage de cellules ayant un nucléosome à chaque position : occupancy.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20221019%20Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’ensemble%20du%20génome/Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’%200fb021e586be446fb6de4713989b1591/Untitled%205.png)

## Méthodes d’analyse de la distribution génomique des nucléosomes.

Toutes méthodes comportent une étape clé de **fragmentation de la chromatine.** De purification de l’ADN, préparation de banques de séquençage haut débit, alignement des reads sur le génome et interprétation. ******************************************************************************Deux méthodes de choix : Mnase et Atac-seq.******************************************************************************

---

### Analyse de la distribution des nucléosomes par MNase-seq (digestion à la MNase couplée au séquençage haut débit).

1. Isoler les noyaux à partir d’une population cellulaire.

2. Traitement des noyaux perméabilisés avec **MNase** (microccal nuclease) et Ca2+ : coupe ADN entre les nucléosomes -digère l’ADN au bord du nucléosome : très bonne résolution.

1. Extraction de l’ADN (fragments protégés par nucléosomes) - sélection de taille des fragments.

1. Séquençage haut débit.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20221019%20Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’ensemble%20du%20génome/Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’%200fb021e586be446fb6de4713989b1591/Untitled%206.png)

Le MNase-seq donne la position des nucléosomes sur le génome et indique, de façon indirecte, les régions accessibles du génome.

⇒ Peut être couplé à une étape d’IP avec des AC anti-histones -pour différencier des complexes protéiques associés à l’ADN : p.ex le PIC) ou anti-variants d’histones ou anti-PTN d’histones.

### Analyse de la distribution des nucléosomes par ATAC-seq (assay for transposase-accessible chromatin).

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20221019%20Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’ensemble%20du%20génome/Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’%200fb021e586be446fb6de4713989b1591/Untitled%207.png)

Cette technique implique l’usage de la transposase (Tn5) qui va apprécier les régions d’ADN “nues”. Le rôle de la transposase est d’apporter l’ADN quelque part, donc elle est utilisée (la transposase est “chargée”)pour déposer des adaptateurs sur toute les régions nues de l’ADN.

L’ADN est ensuite extrait (suppression des histones) et une PCR est réalisée pour amplifier l’ADN qui se trouve entre les adaptateurs, c’est à dire au anciennes position des nucléosomes (vu que les histones sont purifiées). 

Mais la PCR va aussi amplifier l’ADN au niveau des adaptateurs, résultant en des petits fragments.

Une librairie est ensuite réalisée, puis séquençage à haut débit pour déceler les positions des 150 pb.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20221019%20Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’ensemble%20du%20génome/Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’%200fb021e586be446fb6de4713989b1591/Untitled%208.png)

### Analyse de la distribution génomique des nucléosomes.

Le positionnement des nucléosomes varie sur l’ensemble du génome (profil moyen chez S. cerevisiae).

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20221019%20Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’ensemble%20du%20génome/Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’%200fb021e586be446fb6de4713989b1591/Untitled%209.png)

Juste en amont du TSS : région déplété en nucléosome : que l’on nomme **NFR pour nucleosome free region (constitutive)**. A ne pas confondre avec NDR pour nucleosome depleted region qui est elle due à une régulation.

Le nucléosome +1 (qui suit la NFR) est fortement positionné (toujours au même endroit) avec une forte occupation. La NFR est toujours flanquée de deux nucléosomes +1 et -1 bien postionnées.

Mais plus il y a progression dans le gène, moins les nucléosomes sont bien positionnés.

Est observé un enrichissement en un variant d’histones : **H2A.Z** qui a une séquence légèrement différente de H2A, le rendant moins stable.

### Distribution des nucléosomes sur les gènes chez S. cerevisiae.

Profil moyen de distribution des nucléosomes sur les gènes de levure (metagen analysis) : 

- NFR en 5’, flanquée de 2 nucléosomes fortement positionnées (-1 et +1).
- NFR en 3’ correspondant au site de terminaison.
- Enrichissement en histone variant H2A.Z et en histone acétylés autour du TSS (en vert).

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20221019%20Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’ensemble%20du%20génome/Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’%200fb021e586be446fb6de4713989b1591/Untitled%2010.png)

Taux d’occupation, positionnement et composition des nucléosomes + modifications de l’ADN (méthylation) et des histones (histones PTMs) : **EPIGENOME.**

### Mini résumé.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20221019%20Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’ensemble%20du%20génome/Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’%200fb021e586be446fb6de4713989b1591/Untitled%2011.png)

→ **************************************Suite → [Régulation transcriptionnelle.](https://www.notion.so/R-gulation-transcriptionnelle-2b7e60a6b9724e26b367269099ea8234)** 

 

![bubble-chat.png](Pro/Scholar/no01.%20Notes/01%20S1/OGTE/20221019%20Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’ensemble%20du%20génome/Analyse%20de%20la%20distribution%20des%20nucléosomes%20sur%20l’%200fb021e586be446fb6de4713989b1591/bubble-chat.png)

$\Large\texttt{Commentaires}$

---

---

$\Large\texttt{Fin de page}$
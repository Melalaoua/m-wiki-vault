---
Date : August 30, 2022 5:26 PM
---

up:: [[Bioinformatique]]
tags:: #academia/master, #master/Bioinformatique 


[td.pdf](td.pdf)

[molécules.pdf](molcules.pdf)

Recherche de séquences nucléotidiques, reprise sous format FASTA, comparaisons BLAST

$\LARGE\textbf{\textsf{Préambule}}\\\Large\textsf{Introduction à la recherche documentaire}$

---

Facteur H : Indice de popularité réelle (avec des biais), disant que sur les X article, il y en a a X  qui sont au moins cité X fois.

Facteur d’impact des journaux dans lesquels le chercheur publie.

Exofiolative toxine A produite par une bactérie qui provoque l’exfiolation qui peut être source d’une infection.

Ce sont surtout les jeunes enfants qui sont touchés par cette bactérie, certains cas chez les individus à l’immunité abaissée comme les personnes en dialyse reinale, souffrant de defficit immunitaire, ou alcoliques.

ETA peut aussi avoir le nom d’epidermolysine A, c’est une protease spécialisée trouvant sa cible au niveau des desmosomes, coupant spécifiquement la desmobléine 1. 

$\LARGE\textbf{\textsf{Questions}}\\\Large\textsf{Premier paragraphe}$

---

Pour connaître les auteurs, se referrer au debut du fichier.

La séquence est constituée de différents éléments, les éléments de régulation (TATA box, …) ou bien la CDS

La toxine qu’on étudie, lorsque’elle est secrétée, est reconnue via son peptide signal (peptide de sécrétion) par un complexe (varie si bactérie gram - ou +). Reponsable d’apeptigo ?

Deux séquences T1 et T2 (terminateur) après la CDS, ce sont des séquences d’arrêts de la transcription. L’ARN polymérase va dérouler de l’ADN, ces deux séquences sont anindromiques (s’hybrider l’une sur l’autre), bloquant le passage de la transcriptase, terminant la transcription.

Pour le GC% et les sites de coupure :

Nebcutter outil permettant d’analyser les séquences génomiques.

Le GC de E.Coli 64%

Le GC% de L’HOMME c’est comme E.Coli 

GC% DE La tuberculose : 71% un des plus élevé.

Sur Nebccutter : possibilité en bas de sortir des listes d’enzymes qui vont couper 1 fois, 2 fois…. Sortir les listes (1 et 2 sont interessant) et se pencher exclusivement sur des sites comme DraI, qui reconnaissent un site et coupent à l’interieur en blunt end.

### Oligonucléotides.

**Clonage our diagnostique (PCR) :** On choisit des oligonucléotides à l’intérieur du gène : amplification de fragments d’une taille précise, éventuellement pour les distinguer sur gel ou alors approche Taq Man. 

**Clonage pour un plasmide pBR322 :** En amont des cassettes régulatrices et en aval du régulateur. (le terminateur doit toujours être présent, à +150 pb). On rajoute les sites de restriction (5-6 bases).

**Clonage dans un plasmide d’expression :** oligo juste après le peptide signal (inclure l’ATG) et se soucier du site de clonage et rajoute le site de restriction 

**Clonage pour mutagénèse dirigée :** choisir l’endroit de la mutation, pour chaque amorce faire un Tm de 57-60 de chaque côté. Dpn est une démethylase, elle ne coupe qu’un seul brin.

Pour les amorces : le TM doit être compris entre 57° minimum et 60° : 4° pour les GC et 2° pour les AT 

**Oligo 1.**

TAATTTGTTTTGAAATAGAA environ 48° donc +4 nucléotides sur notre séquence et + la séquence EcoRI. En général on rajoute des Nts sur la séquence EcoRI pour avoir une coupe favorable. 

**Oligo 2.**

GTGCAGGATCC - TGTAGTTTGATCATTTATAATAT

On essaie de rapprocher au mieux le Tm des oligonucléotides

Sur le BLASTN : La toxine est présent sur un phage. Des pro-phage qui ont été intégré dans le génome bactérien. Le gène existe chez pas mal d’espèces de Staphylococcus.

BlastN donne des informations sur les gènes parents à partir d’un pourcentage d’identité.

Peptide signal : environ 25 à 40 acides aminés. les séquences avant sont éliminées.

![bubble-chat.png](Pro/Scholar/no01.%20Notes/01%20S1/Bioinfo/20220901%20Recherches%20documentaires%20PubMed%20et%20valeur%20d’une%20recherche/Recherches%20documentaires%20PubMed%20et%20valeur%20d’une%20re%20053a11ba95c6411087a516683e54fe4b/bubble-chat.png)

$\Large\texttt{Commentaires}$

---

***Revoir la définition.***

La desmobléine 1 est présente majoritairement en grande quantité chez les enfants jusqu’à 10 ans ou dans les cas particuliers cités juste avnt.

**ATG = Methionine**

Parfois il y a aussi la présence d’une autre séquence après la peptide signal (toujours en N-ter), résultant en la formation d’un pro-peptide et d’une seconde maturation.

Pour être sécrété, nécessite des acides aminés hydrophobes

terminateur : quand génèse, il y a hybridation → signal de terminaison de la transcription. Permet une stabilité à l’ARNm

---

$\Large\texttt{Fin de page}$
---
Date : September 9, 2022 8:31 AM
---

up:: [[TBMC]]
tags:: #academia/master, #master/Techniques, #master/Bioinformatique 




[Cytométrie en flux 2021.pdf](Cytomtrie_en_flux_2021.pdf)

[https://www.beckman.fr/resources/videos/scientific/fcm-principle](https://www.beckman.fr/resources/videos/scientific/fcm-principle)

## A. Le FCM.

### La fonction d’un FCM (trieur).

Un FCM est capable d’analyse les particules en suspension individuellement par rapport à leurs propriétés de diffusion de la lumière et en fonction de leurs émission de la fluorescence, pouvant aller jusqu’à 25000 evts/sec. Le tri des particules s’effecutant en fonction de ces criètes 

- Un particule peut être une cellule (animale ou végétale, une bactérie, une levure, un chromosome sur une bille, …), tout élément pouvant diffuser suffisamment la lumière et/ou émettre une fluorescence suffisante pour être détectée par le cytomètre.

### Composants du FCM.

| Events | Partie |
| --- | --- |
| Les cellules en suspension s’écoulent goute par goute à travers…. ⏬ | Fluidique. |
| ..Un volume éclaire où ils diffusent de la lumière et émettent une fluorescence qui est collectée, filmée et…. ⏬ | Optique. |
| ..convertis en valeurs numérique stockées sur un ordinateur. | Electronique. |

### Principe.

Les cellules que l’on veut étudier doivent être mises en suspension dans un milieu. Si nécessaire, on peut utiliser un milieu permettant la survie des cellules. Les cellules sont poussées par un système de pompe et envoyées une à une devant -ou plusieurs- faisceau laser qui permet de mesurer ou d’évaluer des paramètres cellulaires.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled.png)

### Schéma de la partie fluidique.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%201.png)

### Quelques exemple de mesure.

**Le paramètre FCS ou forward scatter.**

⇒ Mesure de la taille des cellules.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%202.png)

**Le paramètre SSC ou Side scatter.**

⇒ **Mesure de la granularité.**

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%203.png)

### La focalisation hydrodynamique.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%204.png)

### Analyse.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%205.png)

## B. Les différentes application du FCM.

Le FCM sert :

- Détecter les organites cellulaires, antigènes, récepteurs.
- Détecter les cytokines, enzymes et autres produits cellulaires.
- Mesurer la teneur en ADN, ARN cellulaire.
- Mesurer l’activité cellulaire : prolifération, activation, transduction du signal, apoptose, flux Ca++, pH, enzymes…

### Les sondes à ADN.

La principale clé des sondes à ADN est qu’elles sont stochiométriques (ainsi, le nombre de molécule sondées est équivalent au nombre de molécules). On utilise par exemple le phenatridiniums qui s’intercale entre les bases des acides nucléiques. Ensuite, il y a excitation avec UV ou Blue et il ne faut pas oublier que l’échantillon doit être traité avec des RNAses pour que les mesures d’ADN soit correctes.

### Mesure de l’apoptose.

L’apoptose est la morte cellulaire programmée où la cellule passe par un processus hautement régulé pour “mourir”. Les principales caractéristiques sont : condensation de la matière chromatinienne - purge de la matière nucléaire. 

Ce phénomène est souvent suivit d’une dégradation internucléosomale de l’ADN, donnant lieu à un motif distinct en “echelle” dans l’electrophorèse sur gel d’ADN.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%206.png)

La scission de la chromatine aux sites de liaisons nucléosomale crée un grand nombre de rupture de brin dans l’ADN des cellules en apoptose. Les extrêmités cassées peuvent être marquées avec des enzymes in situ la TDT ou désoxy-nucléotidiyl transferase terminale.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%207.png)

### Le Flux calcique.

Le flux de calcium ionisé intracellulaire est essentiel pour la régulation d’un certain nombre de processus métaboliques cellulaires.

Le calcium intracellulaire est le plus souvent lié à un certain nombre d’organites cytoplasmiques, y compris les mitochondries et le reticulum endoblastique.

Les sondes utilisées pour mesurer le flux de calcium intracellulaire sont par exemple **indo-1**, fluo-3, fura-red.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%208.png)

Indo-1 décale son spectre d’émission en présence de Ca2+, compensant ainsi la variabilité biologique de la concentration de Ca2+ dans différentes cellules. 

### Détection de petites particules.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%209.png)

### Sex selection.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%2010.png)

### Transfert d’énergie par résonance de fluorescence (FRET).

Un donneur fluorescent est excité à sa longueur d’onde d’excitation spécifique. Par un mécanisme de couplage dipôle-dipôle, l’énergie d’excitation est alors transférée de manière non radiative à une seconde molécule. Et le donneur revient à l’état fondamental électronique. **FRET permet de mesurer la relation spatiale entre deux molécules.**

La protéine fluorescente verte GFP est une protéine composée de 238 AA de la méduse *Aequorea victoria* qui devient verte lorsqu’elle est exposée à la lumière bleue.

Le gène GFP est fréquemment utilisé en tant que rapporteur de l’expression génique.

La plupart des petites molécules fluorescentes comme le FITC sont fortement phototoxiques lorsqu’elles sont utilisées dans des cellules vivantes.

La GFP est généralement beaucoup moins nocive lorsqu’elle est éclairée dans des cell vivantes.

CFP et YFP = variantes cyan et jaune de la GFP.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%2011.png)

### Dosage de cytokines multiplexées.

Dosages simultanés : IL1B - IL4 - IL6 - IL10 - IL12 - IFNY-TNFa.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%2012.png)

Chaque petit point représente 1 ELISA, c’est une application qui est faite pour les cytokines, les phosphoprotéines, les hormones, les SNPS.

## C. Le TRI.

Afin de pouvoir trier les particules dans un FMC, il faut faire vibrer la buse avec un quartz électrique (100 kHz), ce qui va permettre la formation de gouttelette. On va ensuite trier individuellement les cellules dans des plaques multi-puits

### Récupération / Rendement / Pureté.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%2013.png)

Le tri à grande vitesse sert dans la recherche pour l’isolement des cellules souches, autres évènements rares, clonage de cellules hautement expressives, tri des chromosomes, tri des cellules foetale…

Dans l’industri pour le tri des spermatozoïdes XY pour le sexage des animaux, criblage à huit débit pour les nouveaux médicaments.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%2014.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%2015.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%2016.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%2017.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%2018.png)

![bubble-chat.png](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/bubble-chat.png)

$\Large\texttt{Commentaires}$

---

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%2019.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%2020.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%2021.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%2022.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220909%20-%20Cytométrie%20de%20flux/Cytométrie%20de%20flux%208ab268b5a1e14ed1b625dfd08615c975/Untitled%2023.png)

---

$\Large\texttt{Fin de page}$
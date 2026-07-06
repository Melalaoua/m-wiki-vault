---
Date : October 7, 2022 10:19 AM
---
tags:: #academia/master, #master/Techniques, #master/génétique 

# High throughput sequencing technologies, technological environment and applications

Le séquençage, c’est trouver l’ordre des nucléotides sur un fragment d’ADN. Trouver l’ordre des nucléotides permet de déterminer l’ordre des acides aminés présents et donc avoir des informations sur une séquence protéique et éventuellement sur sa structure. Une modification au niveau de l’ADN peut provoquer un changement au niveau de la protéine et donc changer sa fonction. Comprendre la séquence d’ADN, permet de comprendre comment fonctionnent les maladies génétiques, et d’identifier une mutation qui cause une maladie.

PCR : Capacité de multiplier l’ADN quasi-indéfiniment. C’est une découverte majeure qui a permis le développement des premiers séquenceurs.

Découverte du séquençage à haut débit : Pyroséquençage

**Le génome humain :**

- 46 Chromomsomes.
- 2 mètres d’ADN nucléaire par cellule.
- 3 milliards de paires de bases.
- Approximativement 20 000 gènes.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled.png)

# I. Technologies.

## A. Sanger Sequencing.

Première technique de séquençage développée, qui fut le protocole de référence pendant plus de 30 années. Certains laboratoires continuent à l’tuliser principalement pour valider des mutations identifiées par séquençage de novo. Certains continue aussi de l’utiliser car c’est une méthode fiable, qui permet d’avoir une validation indépendante.

La technique repose sur la modification de nucléotides, notamment les **ddNTP**, où le groupe OH est enlevé.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%201.png)

Lorsqu’un ddNTP est intégré lors de la synthèse d’un brin d’ADN, ce dernier provoque l’arrêt de la synthèse. (car il manque le groupe OH sur lequel se fixe le nucléotide suivant).

En pratique, on part de la séquence d’ADN à séquencer, on la dénature (souvent par la chaleur), puis ont vient hybrider un primer d’initiation de la réaction de séquence, marqué radioactivement.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%202.png)

### Méthode automatisée du Sanger.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%203.png)

Cette technique a été améliorée en enlevant la radioactivité et ils utilisent maintenant des ddNTP marqués avec des fluorophores différents. En remplacant le groupement radioactif par les marqueurs plus récents, ils peuvent directement faire une seule réaction au lieu de 4. Ils utilisent ensuite un séquençeur automatique avec un laser, pour lire la taille des fragments, et qui va détecter chaque signal de couleur. Lorsque chaque fragment passe, il y a un pic par nucléotide, l’interprétation peut donc déjà être automatisée. Mais il reste toujours l’étape du gel qui est fastidieuse. (grand gel de polyacrylamide). 

### La méthode actuelle automatisée.

La technique a été encore plus améliorée en ne migrant plus dans un gel mais dans **un capillaire**. Un détecteur se trouve à la fin de la réaction et qui permet de détecter les fragments lorsqu’ils passent devant.

La migration se fait de la cathode vers l’anode. Dès qu’un fragment passe il y a une détection automatique. La lecture est **automatique** et peut aller jusqu’à **96 échantillons en parallèle**.  

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%204.png)

C’est ce type de machine qui a été utilisée pour le séquençage du génome humain. Ce type de machine peut faire environ des reads de 700 à 800 pdb (et 96 échantillons en parallèle) soit 67 200 pdb séquencées par jours.

## B. Next generation sequencing (NGS).

4 types de NGS existaient :

- Pyrosequencing (454 - Roche).
- Sequencing by synthesis (illumina).
- Sequencing by ligation (SOLiD - Life technologies).
- Ion semiconductor sequencing.

La Roche n’existe plus, SolId non plus, il ne reste donc que **Illumina qui détient 80% du marché et aussi le ion semiconductor sequencing**.

### Fonctionnement.

Ce qui change, par rapport au Sanger, c’est que le séquençage ne se fait plus sur un brin d’ADN à la fois, mais un **séquençage en parallèle**. Des millions de fragments sont séquencés en parallèle. 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%205.png)

A partir d’un ADN de départ, il est fragmenté en morceaux (mécanique ou enzymatique) et séquencage de tous les morceaux en parallèle. On aligne ensuite nos séquences sur un génome de référence. C’est après cette alignement qu’on déduit l’ADN de départ.

Au vu de la capacité de séquençage énorme, il y a des codes-barres spécifiques de chaque échantillons. Le séquençage de millions de séquences en parallèle, une petite séquence ADN est ajouté à l’ADN du patient séquencé durant le séquençage en parallèle.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%206.png)

Ce barcoding permet de séquencer plusieurs échantillons de différents patients ensemble dans un seul tube. Une fois que tout est séquencé, il y a séparation informatique des différents reads selon le barcode. (**demultiplexage)**

### NGS vs. Sanger.

En prenant le plus efficace de chacun de ces deux types de séquenceurs, jusqu’à 3 millions fois plus de données peuvent être séquencées et couter jusqu”à 250 000 fois moins cher en NGS.

Ces chiffres montrent que l’on peut accéder, de nos jours, au séquençage de génomes humains à moindre coût et c’est accessible à beaucoup plus de laboratoires qu’avant.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%207.png)

### Différentes étapes du processus de séquençage.

---

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%208.png)

Comment préparer l’ADN ? Comment l’enmener au séquenceur et comment le séquençage se déroule t’il ?

**Experimental design.**

L’étape primordiale, il faut se poser les questions qui paraissent assez basique mais qui doivent être adressée pour pouvoir progresser. Exemple : est-ce qu’on a la bonne technologie ? Est-ce que la qualité et quantité de matériel génétique de départ est suffisante ? Quel type de sequençage est requis ici ? Quelles informations sont recherchées ? Quel est l’objet de référence ? Nombre d’échantillons à séquencer ? Quelle sera la couverture de la séquence ? Lorsque l’on fait du séquençage, il est important de **planifier ses manipulations.** 

**Isolement de l’ADN/ARN.**

l’ADN (ou l’ARN) doit être isolé, on réalise des contrôles qualités via une mesure de la pureté en **absorbance 260 nm. Un rapport  $\dfrac{A260}{A280}$** est fait (doit être compris entre 1.8 et 2.0). Ensuite, deux techniques sont utilisées pour vérifier la qualités de nos AN :

**ADN :** 

Une quantification par la fluorescence qui est très précise, utilisant des intercalants fluorescents et qui permet de mesurer l’ADN double brin puis analyse par gel d’agarose afin de vérifier la présence de smir ou non.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%209.png)

**Library preparation.**

Une banque de clonage est réalisée par le clivage de l’ADN génomique (via ultrason en général, ou enzymatique). 

Si on veut séquencer qu’un seul fragment on réalise une librairie classique qui consiste à utiliser une amorce forward et reverse (paired-end sequencing**)** et sinon une librarie barcodées constituées de différents morceaux d’ADN génomiques.

**RNA :**

On mesure la quantité d’ARN ribosomale 28S et 18S, c’est en fonction de ce profil si l’ARN est en bonne qualité. Un ARN est de bonne qualité si son RIN est au dessus de 8.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2010.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2011.png)

Lorsqu’on prépare une librairie comme ça, on va forcément préparer tout le génome (3Gb), mais on peut parfois être intéressés par une plus petite partie du génome. Comment faire pour séquencer uniquement cette zone ?

⇒ Une fois que la librairie de séquençage est prête, on va mélanger ces fragments à des sondes ARN biotinylées, avec des séquences qui vont s’hybrider spécifiquement à notre/nos séquence(s) d’intérêt.  

Des billes de streptavidine vont s’hybrider à nos séquences d’intérêts qu’on triera avec un aimant, on dégrade l’ARN hybridé par des Rnases.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2012.png)

Pour les machines de secondes génération, une étape d’amplification est nécessaire, 

**Amplification PCR.**

1. **Emulsion PCR.**
    
    Présence de fragments complémentaires sur une bille, qu’on mélange avec nos fragments d’ADN générés lors de notre étape de librairie. On génère des gouttelettes qui vont contenir systématiquement une bille et un fragment. On réalise notre PCR sur chaque gouttelette qui va amplifier le fragment sur la bille.
    
    ![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2013.png)
    

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2014.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2015.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2016.png)

1. **Sequencing by synthesis (illumina).**
    
    
    On dénature l’ADN pour directement le déposer sur la lame de séquençage présentant à sa surface des séquences complémentaires à P1 ou P2, les fragments vont s’hybrider à un adaptateur, et l’autre partie va s’hybrider à un autre adaptateur, formant une hybridation en pont.
    
    Il y a génération de colonies d’ADN reconnaissable par la formation de spot autour du site original d’hybridation.
    
    On insère des primers qui vont s’hybrider à la séquence P libre de nos ADN néo-synthétisés. On incorpore ensuite des nucléotides fluorescent qui vont emettre des longueur d’ondes lors de leurs incorporation 
    
    ![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2017.png)
    
    ![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2018.png)
    
    ![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2019.png)
    
    ⏫un peu flou, voir des vidéos c’est beaucoup plus facile que ça en a l’air.⏫
    

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2020.png)

### Ion semiconductor Sequencing (Ion torrent - Life technologies).

Pas besoin de camera pour obtenir des images, donc pas de fluorophores. La technique repose sur des caractéristiques chimiques lors de l’élongation. Relargage de ions hydrogènes lors d’incorporation de base  qui va modifier le pH. On transforme le relargage en signal électrique.

Comment faire pour être sûr de ce qui est lu ?

Réalisation de cycle de séquençages ou, dans un premier cycle, on met la polymérase, le mélange réactionnel et seulement une base, on répète l’action plusieurs fois.

Ci-dessous le workflow.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2021.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2022.png)

- Pas besoins de nucléotides marqués par des fluorophores.
- Petite machines, pas besoin d’optiques, pas de stockage d’images.
- Très rapides environ 100 millions de lectures en quelques heures.
- **Taux d’erreur élevé dans les zones de répétitions élevées d’un même nucléotide.**

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2023.png)

## C. Third generation sequencing.

Déjà présente dans les laboratoires, et qui peut être en deux types d’approches, qui vont venir **supprimer l’étape d’amplification** :

- Pacific Bioscience : séquençage par synthèse comme illumina, mais pas d’amplifications nécessaire. Assez sensible pour mesurer des signaux provenant de molécule unique : Single-molecule-real-time SMRT

- Oxford Nanopore : même idée, on séquence une simple molécule.

1. Pas de PCR requis.
2. Construction de librairie simple.
3. Pas de synchronisation.

### SMRT : Pacific Biosciences.

Cette technique implique une plaque avec des trous dans lesquels on retrouve une seule polymérase immobilisée.

A chaque fois qu’une base est incorporée, un fluorophore est relarguée qui va émettre un signal dans la partie basse du puit. On lit l’élongation “en direct” à chaque incorporation.

Lecture longue jusqu’à **30 000 bases d’un coup**.

Machine très chere (850K) et composants très cher. Taux d’erreur élevé.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2024.png)

### Oxford nanopores.

Utilise des nanopores, comme des canaux à travers des bicouches lipidiques. Mesure de la différence de potentiel entre les deux côtés du canal. Lorsque le fragment d’ADN traverse le canal, la différence de potentiel est enregistrée, spécifique à la base.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2025.png)

# II. Applications.

On peut diviser les approches en deux grands catégories :

- à gauche, on s’intéresse vraiment à la séquence. **L’intérêt est de découvrir des variations dans la séquence.** Un assemblage des reads est réalisé, qui est comparé à un génome de référence pour déceler de potentielles mutations.

- à droite : **Tag analysis**. L’intérêt est de ne pas seulement utiliser l’information de séquence, mais aussi le nombre de fois que la séquence a été vue. Porte un intérêt fort pour l’expression du gène (**RNA-seq**).

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2026.png)

### Résumé des techniques en fonction de l’état du génome.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2027.png)

Le séquençage haut-débit ne concerne pas juste l’information de séquence.

[https://bbb-prod-rp.unistra.fr/playback/presentation/2.3/e046abe9228f837053ad77dfaa16cfe3a4c8c331-1665554745477](https://bbb-prod-rp.unistra.fr/playback/presentation/2.3/e046abe9228f837053ad77dfaa16cfe3a4c8c331-1665554745477) à -20 minutes.

![bubble-chat.png](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/bubble-chat.png)

$\Large\texttt{Commentaires}$

---

Lecture de la séquence de bas en haut.

<aside>
⚠️ Méthode très longue et fastidieuse.

</aside>

- Coût important.
- Débit limité.
- Long.

10aine d’année pour séquencer le génome humain et 3Milliards de dollars.

### Economic trend.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2028.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221007%20Séquençage%20ADN/Séquençage%20ADN%20(attention)%202cc0f235f4e34acc914262220145d280/Untitled%2029.png)

---

$\Large\texttt{Fin de page}$
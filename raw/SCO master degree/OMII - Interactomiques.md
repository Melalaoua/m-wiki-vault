tags:: #master/Omiques 
enseignant:: Anne.Friedrich@unistra.Fr

>[!INFO]
> Installer cytoscape

## Introduction.
---
Au niveau intra/inter-cellulaire, il existe une multitudes d'interactions entre les différents acteurs cellulaires. Ce cours va se concentrer sur les interactions au sein même des cellules.

Les interactions vont concerner tout types d'éléments constitutifs de la cellule : séquence ADN, ARN, Lipides, Protéines, métabolites... Toutefois, nous aborderons que les interactions protéines.

L'ensemble des interactions entre protéines vont permettre l'activité au sein de la cellule. Du gène à la protéine, on a un niveau de complexité assez dense d'interactions à chaque niveau.

Les protéines ont souvent multiples rôles au niveau de la cellule, variant en fonction des différentes conditions.
![[Pasted image 20230921154541.png]]

Une protéine n'agit jamais seule, mais interagit avec d'autres macromolécules pour assurer sa (ou ses) fonction(s). 
- Régulation des réseaux métaboliques.
- Reconnaissance immune.
- Réplication de l'ADN.
- Progression à travers le cycle cellulaire.
- Transduction de signaux.
- Synthèse protéique.
- Régulation des enzymes et hormones.
- etc...

> [!QUOTE]
> **INTERACTOME :**
> A complete list of physical interactions mediated by all proteins in an organism.

L'interactome est **dynamique** (variable d'une cellule à l'autre, d'une condition à l'autre), et peut aussi avoir lieu entre organismes (hôte-pathogène).

Le nombre de gène n'est pas proportionnel à la complexité de l'organisme en question = ==paradoxe de la valeur g==.


## Diversité des interactions protéine-protéine (IPPs)
---
### Une diversité structurale.

- Au niveau des interactions, les protéines peuvent s'associer en ==oligomères== (**homodimères ou hétérodimères**). 
- On peut observer des **associations isologues** (surface de contact identique) ou **hétérologues**.
![[Pasted image 20230921154905.png]]


### Une diversité fonctionnelle. 

==IPPs obligatoires== :
- Les protéines ne sont pas stables indépendamment.
- Les protéines ne sont pas fonctionnelles indépendamment.
=> L'interaction est nécessaire à la stabilité/fonction.
ex: gros complexes protéiques (ADNp, RNAp, ribosome)

==IPPs non-obligatoires== :
- Les protéines sont stables indépendamment.
- Les protéines sont fonctionnelles indépendamment.
=> L'interaction est responsable d'une action.
ex: complexes antigènes-anticorps, enzyme-inhibiteur, complexes de signalisation intracellulaire, etc...


### Une diversité dynamique. 
![[Pasted image 20231023162929.png]]
- Les ==interactions P-P permanentes==. Existent que dans le cadre d'un complexe. **Les IPPs obligatoires sont permanents par définition**. 
- Les ==IPPs transitoires== : protéines qui s'associent et se dissocient in vivo. **Les IPPs non-obligatoires peuvent être transitoires ou permanentes.**


### Une interaction ne veut pas toujours dire contact direct.

Dans le cadre de complexe protéique :
- Détection des partenaires impliqués dans un complexe.
- L'ensemble des protéines détectées au sein de ce complexe ne sont pas toutes en contact les unes avec les autres.

Les interactions fonctionnelles : Protéines impliquées dans une même voie métabolique / Un même réseau de régulation.


## Méthodes de détection d'IPPs.
---
Les méthodes expérimentales de détection des interactions physiques sont caractérisés par le type d'interaction (**binaire** et **complexe protéiques**).
![[Pasted image 20231023163323.png]]


<u>*Tableau de résumé des différentes techniques pour détecter les interactions.*
</u>
![[Pasted image 20230921155843.png]]


### <u>TAP-Tag. Tandem Affinity Purification</u>
Méthode de purification de complexes protéiques par colonne d'affinité puis ensuite une détermination des composants du complexes.

2 étapes : ==immunoprécipitation== (double purification par des colonnes d'affinité) et ==[[Spectrométrie de masse|spectrométrie de masse]]==

![[Pasted image 20230921160103.png]]

#### **Avantages :**
Méthode qui **==maintien le niveau d'expression physiologique==** de la protéine, en condition natives et applicable de façon systématique. C'est une technique spécifique des complexes mettant en lumière des interactions permanentes.

**Quelle interactions sont identifiées par le TAP-tag ?**
- Interactions permanentes & complexes (transitoires non détectées).
- Beaucoup de faux-positifs.

**Problèmes**
- Conformation.
- Gènes essentiels
- Très petites protéines
- Protéines non solubles.



### <u>Double hybride dans la levure.</u>

![[Pasted image 20230921160426.png]]
Marquage de protéine appât et protéine proie avec Domaine activation pour l'un, et domaine de transcription pour l'autre. Si les deux protéines interagissent : transcription du gène.

- La protéine appât X (dont on veut identifier les interacteurs) est fusionnée au domaine de fixation à l'ADN **DF** d'un facteur de transcription.
- Les protéines proies Y (interacteurs potentiels) sont fusionnées au domaine d'activation de la machinerie basale de transcription **DA** d'un facteur de transcription.
- Les protéines fusions sont exprimées dans des cellules de levure contenant un gène rapporteur dont l'expression est placée sous le contrôle du site de fixation pour le domaine de fixation à l'ADN **DF.**

![[Pasted image 20230921160708.png]]

Lorsque la protéine proie Y est capable d'interagir avec la protéine appât X, le domaine d'activation se retrouve à proximité du promoteur du gène rapporteur et la transcription a lieu.

**A savoir** : en pratique, plusieurs gènes rapporteurs (souvent 3) sont testés en parallèle pour augmenter la fiabilité des résultats.

**Quelles sont les interactions identifiées ?**
- Interactions permanentes.
- Interactions transitoires dont les interactions enzyme-substrat (ex: 10 à 40% des interactions kinase-substrat)
- Interactions qui n'existent pas physiologiquement.

Taux de faux positifs estimé à 24-51%
Taux de faux négatifs à 45-90%

#### **Forces et limites du double hybride.**
**Avantages**
- Analyse des interactions dans un environnement cellulaire eucaryote.
- Interactions faibles et/ou transitoires détectables grâce à l'amplification du signal par le gène rapporteur.
- Pas d'étape de purification nécessaire.
- Concept permet de mettre au point de nombreuses variantes.

**Inconvénients.**
- Fort taux de positifs.
- Limité à un sous-domaine de l'interactome complet
- Très peu d'informations sur la dynamique des IPP



### Méthode par marquage de proximité.
---
- Techniques de marquage de proximité par des systèmes enzymatiques (BioID, APEX)
- Repose sur la fusion d'une protéine d'intérêt à une enzyme qui, active, diffuse un produit réactif qui se lie aux protéines d'intérêt et leurs interactions.
-> Marquage de proximité covalent : permet de purifier et d'identifier les interactants.
-> Marquage réalisé sur plusieurs heures : permet de révéler des interactions transitoires.

- BioID : proximity-dependant biotinylation identification.
- APEX : engineered ascorbate peroxidase.

![[Pasted image 20230921162113.png]]




## Méthodes de prédiction d'IPPs.
---

### Rosetta Stone.
Basée sur la **comparaison des protéomes** de 2 organismes. Les gènes impliqués dans un même complexe ou une même voie métabolique peuvent fusionner au cours de l'évolution.

Si une protéine constituée de 2 domaines fusionnées dans l'organisme A est représentée par 2 protéines différentes dans l'organisme B => Ces 2 protéines interagissent dans l'organisme B.

![[Pasted image 20230921162607.png]]

![[Pasted image 20230921162619.png]]

### Co-évolution des séquences.

- Evolution simultanée de 2 partenaires par pression de sélection réciproque.
- Beaucoup étudiée dans le cadre de relation hôte/parasite => co-évolution d'organismes.
- Applicable à 2 protéines interagissantes (physiquement).

![[Pasted image 20230921162909.png]]

### Position des gènes.
Corrélation entre gènes voisins pour l'inférence de liens fonctionnels. On constate une **synténie** (conservation de l'ordre des gènes) très faible pour deux génome éloignés

Sur le schéma ci-dessous : deux gènes (bleu et jaune) sont voisins dans plusieurs génomes => lien fonctionnel peut être inféré entre les protéines pour lesquelles ces gènes codent.

![[Pasted image 20230921163042.png]]

- Méthode robuste pour les génomes procaryotes.
- Peut aussi être appliquée aux gènes eucaryotes dans le cas de gènes co-régulés.


### Profils phylogénétiques.
LEs protéines qui intéragissent tendent à être **co-présentes/co-absentes** dans les génomes.

![[Pasted image 20230921163155.png]]


### Bilan pour les méthodes in silico.
**Avantages : **
- Coût réduit.
- La puissance de ces méthodes augmente avec le nombre de génomes disponibles.

**Inconvénients:**
- Pas toutes applicables à tous les organismes.
=> Restriction aux génomes procaryotes pour la méthode de la "position des gènes".

- Les difficultés à identifier les "vrais" orthologues.
- La répétition de certains motifs dans de nombreuses protéines (ex zinc finger) pour "Rosette Stone"
- Le lien entre les protéines n'est pas forcément direct.
=> Mise en évidence d'interactions fonctionnelles, mais pas forcément d'interactions physiques.

Les 4 dernières méthodes étudiées peuvent être combinées pour augmenter la confiance dans le résultat.

## Analyse des interactomes.

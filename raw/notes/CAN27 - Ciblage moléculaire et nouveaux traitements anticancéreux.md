tag:: #master/cancérologie 
date:: 26/04/2023
enseignant:: Pr. KURTZ


Introduction : 
TTT du cancer historiquement : [[CAN23 - Chimiothérapies cytotoxiques et mécanismes de résistance|chimiothérapie]] = toxique pour cellules tumorales ET saines.
De plus en plus de thérapies ciblées : trouver la lésion moléculaire à l'origine du cancer pour **cibler spécifiquement les cellules tumorales**
=> **Meilleur rendement**  de molécules par rapport aux chimiothérapies classiques (criblage aléatoire = très long, les molécules de chimio utilisées actuellement datent des années 60).
=> Champ d'action des thérapies ciblées :
	- Récepteurs de facteur de croissance
	- Autre récepteurs +/- spécifiques des cellules tumorales.
	- Chaîne de transduction du signal (ligand/Rc/cascade intracellulaire).
	- Régulation de la réponse immunitaire B et T.
	- Autres : catabolisme des protéines, métaoblisme osseux...


### I. Différents sites d'action sur la cascade de signalisation.
---
On peut cibler soit le **ligand**, soit le **récepteur** lui-même, soit la **cascade de signalisation intracellulaire**.
Exemple de voies : [[CAN04 - Récepteurs membranaires, transduction des signaux mitogènes et antiprolifératifs, et cancers|PI3K/AKT]]/[[Autophagie|mTOR]] (historiquement, de moins en moins ciblées), [[Les différentes familles de protéines RAS|Ras]]

#### A. Bloquer le ligand.
On prend l'exemple de VEGF.
Action du [[CAN19 - Microenvironnement Tumoral|VEGF]] sur les cellules endothéliales : prolifération, perméabilité, invasion, migration, survie, activation => induit une **néo-angiogénèse.**

Autres rôles :
- Lutte contre l'hypoxie intratumorale (switch angiogénique au-delà d'une certaine taille). => Augmentation de la microdensité vasculaire intratumorale (élevée = mauvais pronostic). *Note : la quantité de VEGF est proportionnelle à la microdensité vasculaire (donc valeur pronostique)*
- Invasion des cellules tumorales (par la néo-angiogénèse).
- Leger effet immunosuppresseur local.

Dans le cas d'une tumeur, la néovascularisation est de mauvaise qualité avec des vaisseaux "aboutis" et des vaisseaux anormaux trop perméables, induisant une augmentation de la pression interstitielle => mauvaise diffusion de la chimiothérapie.
Cibler VEGF par des anti-angiogéniques de type bevacizumab pour empêcher sa fixation sur VEGFR permetrait donc d'améliorer la diffusion de la chimiothérapie.

##### Etude comaparative du cancer du colon métastatique.
Chimio seule versus chimio + bevacizumab (anti-VEGF).
- Augmentation significative de la survie, c'est la première preuve qu'ajouter une thérapie ciblée à une chimiiothérapie améliore les résultats.

Critique : Si on baisse la néovascularisation, on pourrait imaginer que les molécules de chimiothérapies ne sont pas acheminées jusqu'à la tumeur. Paradoxalement, cela marche mieux, pourquoi ? La néovascularisation tumorale est constituée de vaisseaux "aboutis" et de vaisseaux anormaux, et ces derniers seront les plus déstabilisés par les anti-angiogéniques. Donc les vaisseaux "aboutis" continuent d'acheminer la chimiothérapie. A plus forte dose cependant, tous les vaisseaux seront touchés => moindre diffusion de la chimio.

**Toxicité des anti-angiogéniques** : peuvent induire une HTA par baisse globale du nombre de vaisseaux.

Cependant, le bevacizumab **n'est pas aussi efficace sur tous les cancers** : 
- Efficacité relative : sein métastatique (pas d'impact sur la survie), ovaire.
- Essais négatifs : colon en adjuvant (prévention de récidive/métastases), prostate

*Note : Si les tumeurs sont trop petites, il n'y a pas d'hypoxie (la diffusion de l'O2 suffit), donc pas de néoangiogénèse nécessaire. A ce moment, les anti-angiogéniques sont inutiles.*
Alternative au bevacizumab : aflibercept = VEGF trap = protéine reproduisant le domaine extracellulaire de VEGFR => essais concluants.


#### B. Bloquer le récepteur.
##### 1. Exemple du cancer du sein.
###### **Physiopathologie : 
15-20% des cancers du sein surexpriment HER2.**
- HER2 = Récepteur aux facteurs de croissance qui **n'a pas de ligand**, mais qui peut faire des **[[CAN08 - Physiologie des récepteurs nucléaires|hétérodimères avec d'autres récepteurs]]** possédant des ligands (HER1/3/4 + ERBB1/3/4), augmentant leur affinité pour ces derniers (en dévoilant le site de liaison) et ralentissant leur dissociation. On dit qu'ils sont **partenaires**.
- **Activation forte et prolongée** des voies de transduction si amplification HER2.
- HER2 = facteur pronostique et prédictif de l'efficacité d'anti-HER2 (**rechercher l'amplification**).

Il s'agit donc de cibler HER2, présent dans de nombreux tissus mais amplifié seulement dans certains cancers du sein (génotypage de la tumeur) via des **anticorps monoclonaux**.

Trastuzumab (HERCEPTIN) :
	Se fixe sur le domaine IV de HER2 et **empêche l'activation** des voies de signalisation independamment de la présence d'un ligand.
	Attention : HER2/HER4 présent dans les cardiomyocytes (utile à la contraction) => toxicité cardiaque (baisse de FEVG) réversible du trastuzumab.

Pertuzumab :
	Empêche l'hétérodimérisation avec un partenaire de HER.

Etude comparative : trastuzumab + pertuzumab >> trastuzumab (cr double inhibition).

Autres possibilités :
	- **ADCC** via trastuzumab (NK reconnaît trastuzumab via F$\gamma$RIII => perforine granzyme) 
	- ==**Immunoconjugués**== (Pr. KURTZ prédit une explosion dans les années à venir).
		Ac monoclonal se fixant quasi-exclusivement sur les **cellules tumorales + molécule linker + molécule de chimiothérapie** (payload).
		Le linker doit être suffisamment stable pour ne pas se dissocier dans la circulation sanguine, suffisamment instable pour relarguer la molécule de chimiothérapie une fois la cellule cible atteinte.
		**Trastuzumab-emtansine** et à présent **trastuzumab-deruxtecan (efficace +++)**

##### 2. Exemple du cancer du colon.
###### Physiopathologie
La **voie [[CAN04 - Récepteurs membranaires, transduction des signaux mitogènes et antiprolifératifs, et cancers|EGFR]]** est suractivée.
- Rappel de la voie : **==EGFR - Ras - Mek - ERK==**
- Causes possibles de la suractivation de la voie :
	- Surexpression de l'EGF.
	- Activation constitutive de EGFR, Ras...

On cible EGFR à l'aide d'un **anti-EGFR (cetuximab)**, qui prend la place du ligand et bloque la voie. Certains patients répondent au TTT, mais d'autres n'y répondent pas, car ils présentent des **mutations de Ras le rendant constitutivement activé** même en l'absence d'activation d'EGFR. **Il faut donc rechercher une mutation de Ras** dans la bilan pré-thérapeutique, car cela conditionne la molécule utilisée. Dans ce cas, on utilisera plutôt le bevacizumab.
*Mutations les plus fréquentes = mutations de KRAS (40%), surtout la mutation G12C. On essaie de développer des inhibiteurs allostériques contre ces protéines mutées.*


#### C. Bloquer la cascade intracellulaire.
La signalisation intracellulaire repose grandement sur les phosphorylations, assurées par les **protéines kinases**. Or ces dernières ont des rôles variés dans l'organisme, et sont **regroupées en familles** dans ce qu'on appelle le **kinome**. Certaines familles sont essentielles dans l'ensemble des tissus, tandis que d'autres sont plus restreintes aux tumeurs, constituant ainsi des cibles thérapeutiques de choix.

<u>Exemple des inhibteurs des RTK :</u> **Imatinib mésylate (chef de file)**, sorafénib, erlotinib
- Molécules très utiliées dans la [[CAN11 - Anomalies de différenciation hématopoïétique|Leucémie myélode chronique]], bloquent la **protéine de fusion BCR-ABL**.
- Cible le site de fixation intracellulaire de l'ATP du domaine RTK du récepteur. *Rc non activé => site de fixation de l'ATP caché/Rc ativé => site dévoilé.*
- Les inhibiteurs des récepteurs RTK sont des inhibiteurs compétitifs réversibles de l'ATP.
- **Tous les -ibs** ne sont pas équivalents : spécificité, efficacité, toxicité variables.

*Par exemple pazopanib bloque aussi la voie VEGF/VEGFR.*

- Si effet anti-VEGF => effet anti-angiogénique avec possible HTA.
- Si effet anti-EGFR => possibiltié d'un pseudo-acné.
- Sunitinib => possibilité de toxicité cutanée (hyperkératose) et muqueuse (aphtes++), lbanchiement des poils.
**Retenir : moins une thérapie est spécifique, plus elle est toxique**.

Dans le mélanome : mutations de Raf+++ (mutations BRAF dans 50% des cas).
*Note : Raf est muté dans 7% des cancers humains*

<u>Etudes comparatives :</u>
- Survie sans rechute : 
	- Chimiothérapie Vs. anti-BRAF => HR = 0.30 (= 70% de réduction du risque de rechute).
	- Chimiothérapie Vs. anti-MEK => HR = 0.45

- Survie sans décès.
	- Anti-BRAF Vs. anti-BRAF + Anti-MEK => HR = 0.69 (=31% de réduction du risque de **décès**).

- **Survie globale : non atteinte (chimiothérapie Vs. 17.2 mois (anti-BRAF + anti-MEK)**.

### II. Inhiber la réparation de l'ADN.
---
Il existe plusieurs mécanismes de réparation de l'ADN, tel que [[CAN09 - Mécanismes de réponse cellulaire aux dommages dans l'ADN|BER, NER ou la réparation homologue]]. Les protéines BRCA, au même titre que d'autres protéines telles que PALB2 et RAD51, font partie du système de réparation homologue.

Dans le cancer de l'ovaire, certaines patientes ont hérité de manière constitutionnelle d'un allèle de BRCA2 non fonctionnel puis perdent le second allèle initialement sain sur au moins une cellule qui sera la cellule souche de cancer. L'hétérozygotie est perdue.

La survie des cellules cancéreuses et la réparation de l'ADN repose donc uniquement sur NER. NER nécessite la molécule PARP pour lui signaler les sites de coupures de l'ADN. PARP fixe des poly-ADP-ribosyle sur les sites de cassure pour permettre la fixation de NER.
== C'est faux == vérifier dans les autres cours.

#### B. Inhibition de la réparation au travers d'un exemple : les inhibiteurs de la PARP.
L'inhibition de la réparation par recombinaison homologue fait intervenir les inhibiteurs de PARP (poly-ADP-ribose polymérase).

Si l'on inhibe la molécule PARP, on empêche la survie des cellules cancéreuses puisque les deux mécanismes de réparation de l'ADN sont non-fonctionnels. Les cellules accumulent des coupures dans leur ADN, puis meurent.

Ce concept est celui de la léthalité synthétique : deux mutations A et B peuvent être viables pour une cellule portant l'une d'entre elles isolément, mais si la mutation A (KO des deux allèles BRCA) et la mutation B (ici représentée par les inhibiteurs de PARP) sont présentent en même temps dans une cellule, celle-ci meurt.

Nous disposons de test pour connaître le statut des patients vis-à-vis de la réparation homologue.
- Si HR est fonctionnelle, on parle de HRp (proficient).
- Si HR est dysfonctionnelle, on parle de HRd (deficient).
Les inhibiteurs de PARP n'ont d'intérêts que chez les patients HRd. S'ils sont administrés aux patients HRp, leur inefficacité s'explique que les cassures d'ADN non réparée par le blocage de la PARP sont réparées par HR et la survie de la cellule est permise.

La mutation BRCA est également impliquée dans le cancer de l'ovaire (on parle de syndrome ovaires-seins). On s'est rendu compte que les patientes atteintes d'un cancer de l'ovaire BRCA muté sont sensibles au cisplatine. Le cisplatine provoque des adduits (liaisons covalentes) intra et inter brins. Les adduits inter-brins entrainent des cassures de l'ADN.

L'hypothèse expliquant la bonne réponse au cisplatine par certaines femmes et pas d'autre est que les femmes répondantes sont HRd et par conséquent, réparent mal les coupures d'ADN induites par le cisplatine. Chez ces femmes répondantes, on a prédit une bonne réponse des iPARP, ce qui s'est avéré vrai.

On peut maintenant administrer les inhibiteurs de PARP en association avec le BEvalucizumab, ces deux traitements ensemble augmentent la survie sans rechute de manière significative par rapport au placebo.



### Conclusion.
---
Plusieurs questions restent ouvertes:
*Combien de temps faut-il traiter les femmes n'ayant pas présenté de rechute ?
Sur quels critères faut-til évaluer l'efficacité des traitements (durée de survie ? durée sans rechute ? echelle de qualité de vie ?*
*Comment faut-il mesurer ces critères (Scanner, TEP-scanner, autre ?
Comment limiter la pression de sélection induite par ces thérapies ? Une tumeure est un ensemble de plusieurs clones cellulaires sur lesquels s'exerceront une pression de sélection induite par les traitements, avec sélection et survie probable d'éventuels clones résistants et donc rechute de la maladie.*


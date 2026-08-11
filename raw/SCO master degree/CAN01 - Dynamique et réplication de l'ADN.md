tags:: #master/cancérologie 
date::  08/02/2023
enseignant:: Pr. Bournouf


### I. Introduction.
---
Génome de E. Coli et S. cerevisiae de l'ordre du million de paires de bases. Pour l'homme, 3 milliards de paires de bases pour 21000 gènes et **2%** du génome <u>traduit</u> mais **90%** du génome est <u>transcrit</u>.



### II. La réplication bactérienne.
---
3 étapes importantes : **initiation, réplication et terminaison**. L'élongation est le mécanisme principal.

#### A. Initiation.
L'initiation repose sur les propriétés biophysiques de la molécule d'ADN pour l'ouvrir et initier la réplication.

##### 1. ORI.
L'origine de réplication ou **OriC** est la zone où est ouvert l'ADN (on aborde le mécanisme après) et a une taille d'environ **245pb**, au début. La réplication de l'ADN va dans les deux sens, la réplication est dites **bi-directionnelle**. Il y a formation d'une fourche de réplication des deux côtés.
![[Pasted image 20230212162848.png]]

##### 2. Topologie de  l'ADN / Notion de biophysique.
La double hélice d'ADN peut avoir différentes conformations : 

- **==Hélice B==** : forme classique pour l'ADN avec 10,6 résidus par tour, l'hélice est droite de gauche à droite. Brins antiparallèles. Petit et grand sillon.
- **==Hélice A==** : forme courante pour l'ARN. Hélice droite. Grand sillon plus grand par rapport à hélice B. 

![[Pasted image 20230505144637.png]]
>[!TIP]
>Pour différencier hélice A de hélice B, conférer la forme des pentoses. Pour l'hélice A (ARN), le pentose sera en 3' Endo. Pour la B, le sucre sera en 2' ENDO.

- Hélice Z : Hélice guache avec la  chaîne des phosphate brisée par une alternance de dimères pyrimidines-purines. Des anticorps ont été synthétisés pour marquer l'ADN-Z, cela permet de prouver l'existence naturelle de la chapine. On cherche encore l'utilité


##### 3. Torsion de l'ADN.
Un chromosome "relaxé" (non réplicatif) a juste la torsion d'un brin sur l'autre. La fixation d'agents intercalents ou protéine va induire des **supers tours** et donc une tension sur la molécule d'ADN. Pour distinguer le niveau d'enroulement de l'ADN, il est possible de le faire migrer sur un gel d'agarose, plus il migre, plus c'est enroulé. 
Pour enlever les supers tours nous pouvons enlever les agents intercalants ou ouvrir la double hélice. L'ouverture de l'hélice va enlever les tensions introduites par les supers tours.
![[Pasted image 20230505144822.png]]


```
L = T + W
```
- L =  enlacement.
- Twist = torsion/entortillement (nombre de fois qu'un brin passe sur l'autre) = Paire de base totale / paire de bases par tour.
- Writhe : vrillage/torsade (nombre de super-tours).

Le nombre L d'un chromosome au repose est égal au nombre T, qui est le nombre de paires de bases de ce plasmide divisée par le nombre de paire de bases par tour puisque W est nul. T diminue quand l'hélice d'ADN s'ouvre, nous pouvons trouver la quantité de bases qui sont comprises dans la partie ouverte par la figure de droite ci-dessous.


##### 4. Mécanisme de l'initiation.

![[Pasted image 20230212164345.png]]
```start-multi-column
ID: ID_c6a4
Number of Columns: 2
Largest Column: standard
border:off
```

Sur l'OriC on retrouve 4 zones de 9 paires de bases (carrés jaunes) reconnus par la protéine d'initiation DnaA. On retrouve aussi 3 zones riches en A/T (carrés verts).

**DnaA**, grace à l'ATP, se fixe sur les bindings sites jaunes et induit des supers-tours qui vont provoquer une ouverture de l'hélice d'ADN pour compenser la tension causée par le super enroulement. L'ouverture de l'ADN va permettre la fixation de **DnaB (hélicase) et DnaC** qui vont permettre d'ouvrir d'avantage la double hélice.

--- column-end ---

<u>Biophysique.</u>
1. DnaA fixe ATP.
2. DnaA se fixe sur les DnaA boxes (jaune) et  forme un super-tour 
3. -> désenroulement de la double hélice d'ADN.

<u>Biologie</u>
1. Fixation de DnaB et DnaC et ATP pour former le **primosome** - DnaB est une hélicase et DnaC charge DnaB.
2. DnaB interagit et stimule la primase DnaG.
3. L'holoenzyme s'associe au primose via tau => formation de la fourhce de réplication.

=== end-multi-column






#### B. Elongation.

![[Pasted image 20230212164925.png]]
Fourche de réplication avec le brin direct ou "**leading**" (brin de gauche) et le brin retardé ou "**lagging**" (brin de droite).

Nous pouvons observer les différentes protéines qui interviennent dans le complexe réplicatif dont une DnaB (l'hélicase qui est un héxamere qui utilise l'ATP), une primase avec une ARN polymérase mais parfois peut être une ADN polymérase, cette ARN primase permet de générer le primer permettant ainsi la fonction normale de l'ADN polymérase, noter que le brin retardé génère des fragments plus courts par la progression de l'hélicase qui va en sens oppoosé de la réplication du brin retardé générant ainsi des **fragments d'Okazaki** (1000 nt), donc la réplication dans le brin retardée est saccadée, les ADN polymérases (pol III core), un anneau de réplication ($\beta$) et le Clamp loader (Complexe $\gamma$) qui est le cerveau du réplisome.

##### a. l'hélicase.
C'est une enzyme qui lie l'ATP pour ouvrir l'ADN au fur et à mesure que le réplisome progresse.
- 6 ATPs -> ADP : oure la Double hélice (1000 n/s) elle travaille plus vite que l'ADN polymérase.
- Activité hélicase : 3' -> 5' (fourche) (sens de réplication du brin retardé est 5" -> 3').
- Interagit avec t (sous unité de la polymérase).
- Poison de la protéine : Norfloxacine, étoposide, ténoposide.

##### b. La primase.
ARN polymérase qui reconnait systématiquement des séquences GTC sur la matrice 
- Syntéhtise les amorces d'ARN sur brin retardé.
- Reconnaît la séquence 5'GTC sur la matrice.
- Lie DNAB et SSB (protéines structurelles qui stabilisent l'ADN lorsqu'il est ouvert).
- Recyclée (100/cell).


##### c. Pol III holoenzyme.
Enzyme de réplication qui est constituée de trois constituants : la polIII core, le clamp loader $\gamma$ et de la clamp $\beta$ . Le tout est divisé en 10 sous unités mais on va s'intéresser à chaque élément individuellement.

Le core enzyme possède 3 sous-unités, la sous unités catalytique $\alpha$, la sous-unité exonucléase $\epsilon$ puis une sous-unité $\theta$, son rôle n'est pas très clair. vraisembablement elle fait le lien entre alpha et epsilon.

Le complexe $\gamma$ (clamp loader) a plusieurs protéines, la **protéine $\tau$** qui est la plus importante, elle va lier la sous-unité $\alpha$ de la polymérase. Il y a 2 protéines $\tau$ par complexe $\gamma$, elle permet donc de coordonner les deux polymérases au même temps.

La protéine $\beta$ est chargée par le complexe $\gamma$ sur l'ADN, elle est un hmodimère de deux protéines uqi vont être enchâssées tête-bêche. Les protéines $\delta$ et $\delta$' du complexe $\gamma$ vont prendre la protéine $\beta$ pour l"ouvrir et la fermer sur l'ADn, comme un cadenas.

Nous trouvons environs 20 polIII holoenzyme par cellule, avec une vitesse de 750 n/s, une processivité (p) de p = 150 000, la procéssivité c'est la propriété d'intégrer un nombre de nucléotides sans se dissocier de l'ADN, sans la protéine $\beta$, la processivité tombe à 10.

#### C. Structure de la SU $\alpha$ de Pol III. Famille C.
Image stéréoscopique, avec une résolution de 2.3 Angstrom d'une polymérase. La structure de l'enzyme polymérase possède un pouce, une paume et des doigts. Chez la polymérase, la SU alpha, le domaine doigts est extrêmement développé. Cette SU alpha a un domaine supplémentaire, polymérase et histidinol phosphatase (PHP). Domaine peut avoir une activité pyrphosphatase, un pyrophosphate correspond à deux phosphates, c'est le produit de l'inclusion d'un nucléotide, le triphosphate utilisé pour inclure le nucléotide, le triphosphate, libère le pyrophosphate. Si on arrive à casser le pyrophosphate en deux phosphates, on favorise la polymérisation.


#### D. Complexe $\gamma$
Le complexe $\gamma$ est composé de sous-unités $\gamma$ et sous unités $\tau$. Les sous unités sont codées par le même gène sauf que tau est plus étendu. Il asure la cohésion ded la fourche via tau entre les deux cores, le complexe $\gamma$ et l'hélice DNAB.


#### E. La protéine $\beta$ / Anneau $\beta$ (DNA clamp)
Nous voyons dans l'image 2 sous-unités (en gris en bleu), ce sont des homodimères collés tête bêche. Les cercles en rouge (dia 19) ce sont les sites d'intéreaction des ADN polymérases avec cet anneau. L'interaction est obligatoire sinon la réplication ne peut pas se faire, la bactérie va mourir.

#### F. Interaction Anneau B - Polymérase alpha.
Vert : anneau B.
jaune : SU epsilon.
Orange : SU alpha.
Cyan : protéine tau.

La polymérase alpha interagit avec l'anneau Beta dans une poche hydrophobe.

La structure est expliquée mais elle ne rajoute pas d'informations nouvelles.


#### G. dynamique du réplisome d'E. coli
Nous voyons une fourche de réplication avec les deux brins, leading et lagging, l'hélicase (DnaB), la primase (DnaG) et le complexe gamma.

Le complexe $\gamma$, avec ses SU delta et delta', va prendre l'anneau $\beta$ et le fixer sur le duplex ARN-ADN, la SU $\tau$ qui s'occupe du brin lagging va rapprocher la polymérase qui a fini de synthétiser le fragment d'okazaki précédent. Dans le brin leading nous ne rencontrons pas ces étapes puisque la polymérase n'a pas besoin de se détacher.
![[Pasted image 20230213190521.png]]


### III. Modèles de réplication eucaryotes.
---
#### A. Fourche de réplication eucaryote.
Chez les eucaryotes, tout est plus complexe, ils possèdent plus de polymérase (tableau dia 28).
Pour la réplication, il y a toujours 3 polymérases qui interviennent : une primase et une polymérase pour chaque brin (donc 2). Chez les eucaryotes, il y a **50 000 ORI** par cellule contrairement aux bactéries où il y en a qu'une. Aucune polymérase eucaryote peut interagir avec un anneau bactérien et inversement. L'anneau eucayorte est **PCNA**, sous forme de trimère.

La purification de complexe réplicatifs chez S. cerevisiae permet d'identifier une hélicase composée de dix protéines, deux polymérases différentes qui travaillent sur l'ADN. Pour le brin leading la polymérase $\epsilon$ et pour le brin lagging la polymérase $\delta$.
RPC (replisome progresison complex = CMH + Claspin, TIPIN, TIM, Mcm10, AND1).
RPA = SSB de E. Coli.
CAF-1 etc.. : facteurs de régulation de la chromatine.

![[Pasted image 20230212171404.png]]

#### B. Polymérases Principales.
Les 3 sont :
- **Polymérase $\alpha$** : peu fidèle et peu processive (interaction avec pol $\delta$)
- **Polymérase $\delta$** : lagging strand
- **Polymérase $\epsilon$ :** leading strand.

Les polymérases ne sont pas reliées entre elles mais via une autre protéine, **Ctf4.**

![[Pasted image 20230213191422.png]]


#### C. Modèle d'assemblage du Réplisome eucaryote.
Le complexe de réplication est reconnu par ORC par la protéine cdc6, ce complexe permet à les deux hélicases de se lier à l'ADN puis plusieurs protéines interagissent et finalement l'ouverture de l'ADN et entrée de la primase. Nous pouvons voir une grande ressemblance entre les deux modèles (Euc et Bactérien).
![[Pasted image 20230505145645.png]]

1. Charge de l'hélicase : Le complexe ORC-Cdc6 se lie à ORI recrute l'hélicase.
2. Charge de facteurs acessoires : formation du complexe de pré-initiation. Recrute des facteurs transitoires et permanents (Cdc45-Gins et pol$\epsilon$).
3. Réarrangement et activation de l'hélicase : Mcm10 et RPA activent l'hélicase : ouverture de l'hélice d'ADN (ATP).
4. Priming : la primase synthétise l'ARN qui est élongué par Pol$\epsilon$


#### D. Quelle est la structure en 3D du réplisome ?
![[Pasted image 20230505150103.png]]
Hypothèses : 
- A : Le brin leading fait une boucle via le complexe GINS, couvrant 40 nts.
- B : Le brin leading entre directement dans la pol epislon, couvrant 20 nts.

Après l'analyse de structure d uréplisome chez S. cerevisiae, le brin leading doit faire un coude pour repasser dans la pol $\epsilon$, donc l'hypothèse A est la plus vraisemblable mais en 2018 l'hypothèse s'infirme.

#### E. Cinétique du réplisome leading.
La vitesse d'incorporation augmente avec PCNA.
1. Défini les éléments d'un réplisome efficace.
2. Rôle de pol $\delta$ dans la synthèse du brin leading avant que pol $\epsilon$ n'intervienne.
3. Pol est plus efficace car elle active l'hélicase.
![[Pasted image 20230505150115.png]]


### IV. Modèle d'incorporation de nucléotide par une ADN polymérase.
---
#### A. ADN polymérase.
On connait 7 classes d'ADN polymérase chez les eucaryotes.
La structure des polymérases (dia 42) est universelle, elle contient le pouce, la paume (site actif) et les doigts. Elle contient également un domaine exonucléase, lors de la délétion d'une base. Des interrogations de la part des scientifiques surviennent pour comprendre comment l'ADN passe du site actif (paume) au site de l'exonucléase.

Bien que comportant une structure universelle, les ADN polymérases restent très différentes dans leurs structures (dia 41). 
Les ADN polymérases Y nous intéressent en cancérologie puisqu'elles sont créatrices de mutations, on remarque que le domaine doigt est petit et qu'il ne participe pas à la stabilité de la structure. Elles ont donc développé un domaine petit doigt supplémentaire et distinct. Il a comme rôle de maintenir le brin d'ADN sur la polymérase.
![[Pasted image 20230219134157.png]]

Intérêt en cancérologie pour les polymérases Y car elles sont créatrices de mutations, son domaine doigt est petitet ne participe pas à la stabilité de la structure. Il maintient l'ADN sur la polymérase.

![[Pasted image 20230219134254.png]]



##### 1. Modélisation de l'ADN polymérase.
Le site actif, la paume, contient cinq sous domaines, caractérisés par le site de ==pré-insertion== qui est compris entre l'hélice O et O1. C'est au niveau du ==site d'insertion== que les nucléotides vont être insérés. Le site catalytique permet la formation de la liaison covalente. Le site de post-insertion vérifie que l'appareillement est correct (bonne base).

Si il y a un **mismatch**, les interactions empêchent le brin de progresser dans le site actif. C'est comme ça que la polymérase sait si un mauvais nucléotide a été incorporé, dans ce cas, le brin fait un retour en arrière et il y a une activité exo-nucléase.
Il reste des interrogations pour savoir comment est sélectionné le nucléotide, puisque le brin modèle n'est pas dans le site actif et la polymérase ne sait donc pas quel est le nucléotide complémentaire au brin modèle.

Ratio d'une erreur d'appareillement / 10 bases. L'adaptation au site actif est l'étape la plus importante pour permettre la fidélité de l'ADN aux polymérases (dia 49).

#### B. Cristallographie cinétique (dia 51).
Au temps 0, on a un nucléotide avec ses 3 phosphates et un magnésium dans le site actif. A ce moment l'extrémité OH du sucre est éloignée du phosphate, il n'y a pas de possibilité d'interaction.
![[Pasted image 20230505150424.png]]
Au second temps, on a 2 magnésiums dans le site actif et une molécule d'eau apparaît. La molécule d'eau va récupérer le proton du pont hydroxyle du sucre. Cela active la réaction qui permet un mouvement dû à la chélation d'un magnésiume ce qui change l'agencement des résidus et se rapproche du groupement phosphate et cela permet l'attaque électrophile sur le phosphate. L'attaque électrophile implique la perte du pyrophosphate, la perte de celui-ci accorde la présence d'un 3e magénsium. Ce 3e magnesium est important pour ouvrir l'hélice O et ainsi ouvrir le site actif.

La cristallographie fait apparaître une densité électronique (en vert) qui nous permet de reconstruire les molécules. On peut avoir donc une augmentation de la densité électronique qui correspond à la création d'une liaison covalente entre l'oxygène et le phosphate (dia 52).
Cette etude a permis de préciser le positionnement du système dans un état inactif et de comprendre le rôle du 3e magnésium.

Pas important à retenir.

#### C. Modèle de fonctionnement du site actif.
Comme dit précédemment le brin template n'est pas dans le site actif, il est compris entre l'hélice O et l'hélice O1. 
L'hélice O content une tyrosine qui est importante car elle empêche le nucléotide de rentrer dans le site d'insertion. Cependan quand l'hélice est réclinée (open dans le schéma) la tyrosine n'netre pas en opposition à l'entrée d'un nucléotide. 

Le nucléotide qui va être inséré dans le brin syntéhtisé rentre dans le site actif en emportant avec lui un magnésium.

Le nucléotide comporte 3 phosphates qui sont des charges négatives, l'hélice O est essentiellement positive et va être attirée vers le nucléotide. Cela va induire un mouvement vers le haut de l'hélice qui va bloquer le site d'insertion. Si tout se passe bien un 3eme magnesium libère le site d'insertion qui permet la libération d'un pyrophosphate.

Toutes ces étapes permettent le contrôle du procédé.

#### D. Réplication d'un ADN endommagé : mécanisme de translésion.
Les cellules sont soumises aux stress, il y a 2 possibilités quand un ADN est endommagé soit il y a **réparation**, soit il y a une **tolérance des dommages**.
![[Pasted image 20230505150512.png]]
##### 1. Tolérance des dommages.
Il y a 2 voies, une voie d'**évitement de la lésion** (DA) qui fait intervenir des processus de recombinaison. 
La Seconde voie correspond à la synthèse translésionnelle (TLS). Une polymérase est capable d'insérer un nucléotide malgré la lésion dans le brin matrice. Il peut y avoir une erreur qui conduit à une mutation.

##### 2. Système SOS chez les bactéries.
![[Pasted image 20230505150615.png]]
Quand l'ADN n'est pas lésé, les gènes SOS chez les bactéries sont réprimés par des régulations.
Lorsque l'ADN est lésé les gènes SOS sont induits (dia 58). Il y a une cinétique particulière tous les gènes ne sont pas transcrits au même moment.

![[Pasted image 20230505150654.png]]
Pour la chronologie des évènements, il y a tout d'abord formation d'une lésion, il y a liaison d'une protéine (RecA) sur les ADN simple brin (caractérise une lésion) qui va activer le système SOS et protéger l'ADN. Via le système SOS, on évite les mutations de la TLS. La TLS est convoqué en dernier sur un laps de temps court ce qui réduit les possibilités de mutations.

###### a. Article et étude sur la TLS et le système SOS.
A présent le docteur souhaite nous parler d'un article qui présente le poids de la TLS dans la reconstruction d'ADN lésé. 

Ils ont utilisé le système LacZ qui permet, lorsque la protéine est active, de donner une coloration bleue à la cellule. Ce système a été intégré à un chromosome.
Dans un premier essai ils ont inactivé lacZ (brin blanc) tandis que sur l'autre brin lacZ reste actif. On observe après réplication des bactéries bleutées. 
![[Pasted image 20230505150844.png]]


Dans un second essai ils ont cette fois-ci induit une lésion sur le brin où lacZ est actif (bleu). Cette lésion fait intervenir le système TLS, après filiation on observe que les bactéries bleutées correspondent à une correction des lésions sans erreur. Sinon les bactéries comportant une erreur ne se divisent pas.
![[Pasted image 20230505150913.png]]


Ils ont par la suite comparé différentes lésions (dia 62) : les lésions non-bloquantes qui ne bloquent pas la polymérase (donc TLS) et des lésions bloquantes.
![[Pasted image 20230505150927.png]]
Les conclusions sont que la polymérase a du mal à passer la lésion mais quand elle passe la lésion elle le fait sans erreur.


Avec le système SOS, la proportion de TLS augmente et avec peu de mutation.
Dans l'avant dernière ligne, RecA est supprimé donc il n'y a plus de possibilité d'induction de SOS et donc de TLS. Et il y a moins de 50% de survie car toutes les lésions se font par évitément (DA). 
Dans la dernière ligne ils ont augmenté la concentration en polymérase V qui induit le système SOS, à nouveau les chiffres montrent une bonne survie et peu de mutation.
![[Pasted image 20230505151001.png]]
L'intervention de TLS joue souvent un rôle positif même si des mutations peuvent être occasionnées.

#### E. Mécanisme de TLS chez les procaryotes.
Lors de lésion la polymérase se dissocie de l'ADN double brin. 
Puis un filament de RecA va se lier à l'ADN simple brin. C'est par la liaison de RecA ce qu'on appelle le signal SOS.
Puis au bout de 45 minutes, 3 polymérases vont être synthétisées, il s'agit de pol II, IV et V.
Les 3 polymérases essaient de réparer la liéson, si la liéson persiste, [[CAN06- Les morts cellulaires.pdf|apoptose]].
Si la lésion est réparée, la polymérase réplicative se liera à l'ADN et continuera la réplication.
Les caractéristiques des polymérases TLS sont le fait qu'elles n'ont pas de correction de lecture, peu processive (n'insère que quelques nucléotides).

#### F. Mécanisme de la TLS chez les eucaryotes.
Chez les eucaryotes, il n'y a pas de synthèse SOS.
Il y a dans un premier temps ubiquitination de PCNA (dia 76), qui est l'anneau de réplication eucaryotes. 
Si une protéine est liée par la lysine 48 de la protéine, elle va être dégradée. Or dans le système décrit PCNA est monoubiquitiné à la lysine 63 qui conduit à un mécanisme sans erreur, mais actuellement pas connu.

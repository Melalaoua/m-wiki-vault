tags:: #master/cancérologie 
date:: 27/03/2023
enseignant:: Pr. COTTARD

### I. Cellules souches
#### A. Qu'est ce qu'une cellule souche ?
Les cellules souches sont des cellules qui permettent de remplacer les cellules qui meurent par de nouvelles cellules. Ces cellules sont indifférenciées et vont être capable de se différencier en un seul type cellulaire, on les appelle ==unipotentes== (par exemple les cellules souches du muscle, qui s’appellent les cellules satellites, vont donner la cellule musculaire) ou sont capables de donner plusieurs types cellulaires (comme pour les cellules souches de l’intestin qui peuvent donner des entérocytes, cellules de Paneth ou cellules neuroendocrines) et sont des cellules souches ==multipotentes==. Une autre caractéristique des cellules souches est la capacité d’auto-renouvellement qui peut se faire par division asymétrique ou asymétrie de population.

La ==division asymétrique== implique qu'une cellule souche, lors de sa division, produit à la fois une autre cellule souche et un progéniteur qui se multipliera et se spécialisera. Dans une **asymétrie de population**, il y a plusieurs cellules souches dans un environnement spécifique appelé niche qui permet de maintenir les caractéristiques de ces cellules. Une cellule peut quitter la niche en réponse à des signaux spécifiques et commencer à se multiplier et se spécialiser, tandis que le reste de la niche reste indifférencié.
![[Pasted image 20230331102109.png]]


#### B. Concept de niche intestinale.

Dans l'intestin, il existe deux importantes voies de signalisation : ==la voie Wnt==, qui est essentielle pour le renouvellement des cellules souches, et la ==voie BMP==, qui joue un rôle dans la différenciation cellulaire. Les deux voies fonctionnent selon un gradient. 

![[Pasted image 20230511185201.png]]

En bas de la crête intestinale, le signal Wnt est très fort, ce qui maintient les propriétés des cellules souches. Plus on se rapproche du haut de la crypte, plus le signal BMP est important, ce qui favorise la différenciation cellulaire. Selon le signal reçu, la cellule peut maintenir son état de cellule souche ou se différencier sous l'effet de BMP. Ces signaux sont fournis par les cellules mésenchymateuses environnantes.


#### C. Identification des cellules souches. Marquage de lignage cellulaire (==**lineage tracing**==).

![[Pasted image 20230511185451.png]]
Les cellules souches intestinales sont identifiées grâce à la présence d'un marqueur spécifique appelé **Lgr5**. Pour suivre la descendance de ces cellules, on utilise des modèles de souris transgéniques creERT2. 

L'expression de creERT2 est régulée par un promoteur spécifique. Pour étudier l'intestin, on active l'expression de creERT2 grâce au promoteur Lgr5. Les souris possèdent également un autre promoteur, Rosa26, qui est présent dans toutes les cellules, ainsi qu'un gène LacZ codant pour la bêta-galactosidase. Un codon STOP est placé en amont de LacZ et est flanqué de sites FloxP qui sont reconnus par creERT2. 

Ainsi, creERT2 n'est exprimé que dans les cellules qui expriment Lgr5, c'est-à-dire les cellules souches. Lorsque le tamoxifène est administré, il se fixe sur creERT2 et permet la délétion du codon STOP, activant l'expression de LacZ uniquement dans les cellules Lgr5. Les progéniteurs issus de ces cellules souches auront également l'expression de LacZ, mais pas celle de Lgr5, car ils ne sont plus des cellules souches. 

Les scientifiques ont découvert que ces cellules souches peuvent donner naissance à tous les types cellulaires de l'intestin. L'activité de la bêta-galactosidase permet de suivre la descendance de ces cellules souches et de comprendre comment elles se différencient en différents types cellulaires dans l'intestin.


### II. Cellules souches cancéreuses (CSCs).
---
#### A. Caractéristiques des cellules souches cancéreuses.
Les **cellules souches cancéreuses ont les mêmes caractéristiques que les cellules souches normales** :
- ==Capacité d’auto renouvèlement qui va maintenir le pool de CSCs==
- ==Capables de reproduire l’hétérogénéité tumorale==
- ==Voies de signalisation et marques similaires==

Les premières cellules souches cancéreuses identifiés sont dans la leucémie myéloïde aigue qui ont un profil souche normale identique aux cellules souches hématopoïétiques.
La diapositive 10 est présentée à titre d'exemple pour illustrer qu'il existe des marqueurs spécifiques pour plusieurs types de cellules cancéreuses, tels que CD44. Cependant, chaque cellule souche cancéreuse possède également ses propres marqueurs spécifiques.

#### B. Identification des cellules souches cancéreuses.
![[Pasted image 20230511185847.png]]
L'article présenté dans la diapositive 11 montre que la technique de traçage de la lignée a permis de démontrer que Dclk1 est un marqueur des cellules souches cancéreuses, et non des cellules souches normales. Cette technique a été utilisée sur des souris Apc Min, dans lesquelles une mutation d'Apc entraîne une activation constitutive de la voie Wnt/β-caténine, provoquant le développement d'adénomes dans le colon. Les chercheurs ont utilisé le contrôle creERT2 sous contrôle de Dclk1, de sorte que toutes les cellules exprimant Dclk1 exprimaient également Cre, ce qui permettait l'élimination du codon STOP dans les gènes avec le promoteur ubiquitaire Rosa26, permettant ainsi l'expression de la beta-galactosidase. Par coloration, les chercheurs ont détecté ces cellules dans quelques endroits correspondant aux adénomes, confirmant que Dclk1 est exprimé spécifiquement dans les cellules souches cancéreuses.


### III. Hétérogénéité intra-tumorale.
---
Au sein d'une même tumeur, il y a la présence des cellules cancéreuses avec différentes caractéristiques en termes de :
- Morphologie.
- Index prolifératif.
- Profil d'expression génique.
- Sensibilité aux traitements.

#### A. Modèles qui expliquent l'hétérogénéité intra-tumorale et la croissance tumorale.
##### <u>1. Modèle stochastique.</u> 
Le modèle en question suppose que chaque cellule tumorale acquiert des mutations de manière aléatoire, créant ainsi des clones tumoraux distincts. De plus, toutes les cellules tumorales ont la capacité de s'autorenouveler et de donner naissance à des progéniteurs différents. En fonction de l'avantage prolifératif, un clone particulier est sélectionné. Ce modèle suppose que toutes les cellules tumorales sont équipotentes, c'est à dire qu'elles ont la même capacité à s'autorenouveler.


##### <u>2. Modèle hiérarchique / Modèle des cellules souches cancéreuses.</u>
Le modèle stipule qu'une CSC est capable de s'autorenouveler pour maintenir la population de cellules cancéreuses, tout en donnant naissance à une cellule progénitrice qui peut se différencier et proliférer. La majorité de la masse tumorale est constituée de cellules non-souches. Il s'agit d'un processus **unidiectionnel** dans lequel les cellules cancéreuses peuvent évoluer vers des cellules différenciées, mais les cellules différenciées ne peuvent pas revenir à l'état de CSC.

##### <u>3. Modèle réactualisé / Modèle de plasticité cellulaire.</u>
Contrairement à  ce qui a été initialement décrit, ce modèle est en fait **bidirectionnel**. Les CS peuvent donner naissance à des progéniteurs qui se différencient, mais les cellules différenciées peuvent également se transformer en CSC , selon le concept de **plasticité cellulaire**. 

Les CS peuvent donner naissance à des cellules qui se différencient et deviennent cancéreuses, et des cellules différenciées peuvent acquérir des mutations et des altérations qui les font devenir des CSC. Ce phénomène explique l'hétérogénétié intra-tumorale observée ddans certains types de cancers.


#### B. Origine des CSC.
Les CSC peuvent provenir de différents types de cellules, notamment de cellules différenciées qui acquièrent des mutations, de CS normales qui subissent une altération permettant une prolifération accrue, ou encore de progéniteurs. En d'autres termes, une cellule souche cancéreuse peut émerger à partir de n'importe quel type de cellule.


### IV. Mécanismes responsables de la plasticité cellulaire.
---
La plasticité cellulaire peut être induite par des **facteurs intrinsèques.**
- [[CAN10 - Mécanismes de la cancérogénèse|Altération génique]].
- [[CAN17 - Biologie de l'invasion et de la métastase - Transition épithélio-mésenchymateuse|Transition epithélio-mésenchymateuse EMT]]
- [[CAN14 - Epigénétique et cancer|Modifications épigénétiques]]
- ....
Et par des **facteurs extrinsèques** :
- [[CAN19 - Microenvironnement Tumoral|Microenvironnement tumoral]].
- [[CAN29 - Immunothérapie|Thérapies cancéreuses]].

Il y a une interconnexion entre ces mécanismes pour la formation d'une tumeur et l'hétérogénéité des cellules au sein de cette tumeur.

#### A. Altérations géniques.
Les voies de signalisation impliquées dans la plasticité tumorale sont similaire à celles impliquées dans le maintien des caractéristiques des cellules souches dans les tissus normaux, telles que la **[[CAN04 - Récepteurs membranaires, transduction des signaux mitogènes et antiprolifératifs, et cancers#IX. La voie de signalisation de Wnt.|voie Wnt, la voie NOTCH]], la voie Sonic HedgeHog et la voie HIPPO.** Une seule voie de signalisation peut être suffisante pour induire la plasticité tumorale.


![[Pasted image 20230511190515.png]]
Par exemple, la surexpression de la voie NF-kB peut entraîner une activation constitutive de la voie B-caténine, conduisant à la formation d'adénomes chez la souris. Cette étude, illustrée dans la dia 19, a également montré que les adénomes se formaient à la base et au sommet des cryptes, indiquant que la voie NF-kB est impliquée non seulement dans l'expression des gènes impliqués dans les caractéristiques des CS, mais aussi dans la dédifférenciation et la transformation de cellules différenciées en CSC.


![[Pasted image 20230511190737.png]]
Un autre exemple de la plasticité tumorale est observée dans le cancer de la prostate, où la **surexpression des gènes PTEN et p53** est impliquée dans les caractéristiques des cellules souches tumorales. Le gène p53, muté dans la moitié des cancers sporadiques, agit comme un suppresseur de tumeur (cf [[CAN05 - Régulation du cycle cellulaire]]), est activé  en réponse à des phénomènes d'hypoxie, de stress oxydatif, ou de privation de nutriments. 

L'activation de p53 peut arrêter le cycle cellulaire ou induire l'apoptose (cf [[CAN06 - Les morts cellulaires]]), tout en inhibant les propriétés des cellules souches. En cas de perte de p53, la répression des caractéristiques des CS est levée et les marqueurs des CS sont exprimés. Dans le cancer de la prostate, la coopération entre la mutation des gènes p53 et PTEN peut conduire à la transformation des cellules épithéliales prostatiques en progéniteurs multipotents et à leur transition épithélio-mésenchymateuse.


#### B. Transition épithélio-mésenchymateuse.
cf [[CAN17 - Biologie de l'invasion et de la métastase - Transition épithélio-mésenchymateuse
]]
![[Pasted image 20230511190838.png]]
LA TEM est un phénomène qui permet aux cellules épithéliales d'acquérir un phénotype mésenchymateux. Les cellules épithéliales expriment des marqueurs tels que l'E-cadhérine. Lorsqu'elles subissent la TEM, elles acquièrent des marqueurs mésenchymateux tels que la **N-Cadhérine, la vimentine, SNAIL, ZEB1, TWIST.** Les cellules cancéreuses peuvent exprimer à la fois des marqueurs épithéliaux et mésenchymateux. La TEM est **réversible** et les cellules mésenchymateuses peuvent devenir épithéliales grâce aux processus appelé **Transition Mésenchymo-Epithéliale (MET)**.

![[Pasted image 20230511191035.png]]
Dans le cancer de la prostate, les cellules subissent une TEM pour acquérir des propriétés nécessaires à l'invasion et la migration, telles que la sécrétion des métalloprotéinases qui leur permettent de dégrader la matrice extracellulaire et passer dans les vaisseaux sanguins. Une fois dans les vaisseaux sanguins, les cellules passent de leur phénotype mésenchymateux à une phénotype épithelial par MET lorsqu'elles arrivent à un site de métastases tel que l'os.


![[Pasted image 20230511191106.png]]
Des études ont montré que l'activation de **l'expression des marqueurs SNAIL et TWIST1** et le traitement des cellules épithéliales avec TGF-$\beta$ peuvent induire une TEM. Ces cellules acquièrent alors un phénotype mésenchymateux, une diminution de l'E-cadhérine et une augmentation de la N-cadhérine et de la vimentine.
![[Pasted image 20230511191215.png]]
![[Pasted image 20230511191240.png]]
En plus, ces cellules ont développé le profil de CS normales, suggérant que la **TEM est impliquée dans l'acquisition des caractéristiques des cellules souches.**



++++
Des marqueurs tels que ZEB1, SNAIL, TWIST et SLUG sont associés à la TEM ainsi qu'à l'augmentation des caractéristiques des cellules souches. TWIST est associé à l'expression de **Bmi-1**, qui participe au **maintien de la pluripotence**. 
![[Pasted image 20230511191502.png]]


Bmi-1 est également contrôlé indrectement par ZEB1, qui inhibe le miR-200, qui normalement dégraderait le Bmi-1. En activant ZEB1, l'activité inhibitrice de miR-200 sur Bmi-1 est réprimée, et la pluripotence est activée.
![[Pasted image 20230511191556.png]]


![[Pasted image 20230511191627.png]]
Le même principe fonctionne pour SNAIL et SLUG, qui participent à l'augmentation de Nanog, KLF4 et TCF4, tous imliqués dans les caractéristiques des cellules souches cancéreuses.

Enfin, l'acquisition de propriétés de cellules souches permettrait d'initier la formation d'une nouvelle tumeur au niveau du site de métastase, car pour former une métastase, les cellules doivent avoir des propriétés de CS.


#### C. Régulation épigénétique.
L'épigénétique est un mécanisme par lequel l'expression des gènes est modifiée sans affecter la séquence d'ADN. Cette modification peut inclure des **changement dans les histones, la méthylation de l'ADN et la régulation par les micro-ARNs** (cf [[Régulation de l'expression des gènes eucaryotes]])

Plusieurs études ont montré que certaines protéines sont surexprimées dans les cancers et participent au maintien des caractéristiques des cellules souches cancéreuses. Par exemple, la protéine **LSD1** (lysine-specific demethylase 1) est associée à la surexpression de marqueurs des cellules souches, tels que SOX2 et OCT4, et participent au maintien des propriétés de CSCs. Le traitement des cellules cancéreuses avec TGF-$\beta$ augmente l'expression de LSD1, ce qui favorise l'activation de la transcription et la diminution de la répression transcriptionnelle, contribuant ainsi au maintien des propriétés de CSCs.

De même, la protéine **EZH2** (Enhancer of zeste homolog 2) participe au maintien de caractéristiques des cellules souches cancéreuses en régulant l'expression de différents gènes, tels que SOX2, NANOG et E-cadhérine. Cette régulation peut favoriser la transition épithéliale-mesenchymateuse (TEM) et la propagation des cellules cancéreuses.

En outre, la réactivation de voies de signalisation telles que NOTCH ou Wnt peut être due à des mécanismes épigénétiques, tels que l'hyperméthylation des promoteurs de gènes qui régulent négativement ces voies.

Enfin, les cellules cancéreuses non-CSCs peuvent acquérir des propriétés de cellules souches par modification de la marque d'histone sur le gène ZEB1 en réponse à un traitement avec TGF-$\beta$

==**Régulation par les micro-ARNS : miR-200 et miR-34**==
Une cellule peut acquérir la pluripotence par l'activation du gène ZEB1, qui peut être inhibé par les miARN 200 et 34. Inversement ces deux miRna peuvent être inhibés par ZEB1 et BMI-1, qui sont nécessaires pour maintenir la pluripotence. En activant le ZEB1 par des mécanismes épigénétiques, on peut bloquer l'effet inhibiteur des miR-200 sur BMI1 et favoriser la pluripotence cellulaire.
![[Pasted image 20230331111524.png]]
D'autre part, le miR-34 peut inhiber les marqueurs de CS tels que NANOG et SOX2, qui sont régulés par le gène suppresseur de tumeur p53. Cependant, la suppression de p53 est courante dans la plupart des tumeurs, entraînant une diminution de l'expression des miR-34 et, par conséquent, une augmentation des marqueurs de cellules souches tels que BMI1, ZEB1, SNAIL, NANOG, SOX2. Ces marqueurs sont associés aux cellules souches cancéreuses.

#### D. Microenvironnement tumoral.
Une tumeur se définit par une intraction réciproque entre :
- Les cellules épithéliales cancéreuse
- Le microenvironnement tumoral :
	- Composante celluaire (cellules immunitaires, cellules endothéliales, cellules mésenchymateuses, fibroblastes associés aux cancers, ...).
	- Composante non-cellulaire (cytokines, matrice extracellulaire..)

Pour s'adapter au microenvironnement, la cellule tumorale a besoin d'une plasticité qui est aussi induite par ce microenvironnement.

Exemples : 
1. ==Activation de la voie WNT par les myofibroblastes au niveau du cancer du colon==.
	Les myofibroblastes environnants peuvent sécréter de l'HGF (facteur de croissance hépatocytaire) qui se lie aux récepteurs c-MET présents sur les cellules cancéreuses. Cela entraîne la phosphorylation des protéines AKT et GSK3-beta, qui normalement maintiennente la beta-caténine dans le cytoplasme. Toutefois, si ces protéines sont phosphorylées, elles deviennent inactives, ce qui permet à la bêta-caténine de migrer vers le noyau et d'induire l'expression de gènes impliqués dans la clonogénicité et les caractéristiques des CSC. Par conséquent, le microenvironnement peut induire la voie WNT/bêta-caténine, qui favorise les caractéristiques des CSCs.
	
	
2. ==Inflammation et plasticité.==
	Les **macrophages** qui sont présentsdans les tumeurs cancéreuses dans les tumeurs cancéreuses ont leur voie NF-kB activée, ce qui entraîne la sécrétion de cytokines telles que l'IL-6, l'IL-8 et le Csf2. Ces cytokines ont un effet sur les cellules cancreuses en leur conférant des caractéristiques similaires à celles des cellules souches cancéreuses. cf [[Immunité anti-tumorale]]
	![[Pasted image 20230331112315.png]]
	
	Un autre exemple est lié à la chimiothérapie. Après une chimiothérapie, les macrophages vont sécréter de l'oncostatine M, qui maintient les propriétés des CSCs. La voie de signalisation de l'oncostatine M coopère avec la voie TGF$\beta$ pour former le complexe STAT3-SMAD3 qui se transloque  dans le noyau et participe à la TEM ainsi qu'au maintien des CSCs. Par conséquent, les traitements et le microenvironnement tumoral peuvent agir ensemble pour favoriser la palsticité cellulaire.
	
	
3. ==Hypoxie et plasticité.==
	Lorsque la tumeur commence à se développer, des phénomènes d'hypoxie peuvent survenir, ce qui conduit à une plasticité des cellules tumorales qui doivent s'adapter à leur environnement. L'expression des **facteurs HIF-1$\alpha$ et HIF-2$\alpha$** est associée à l'auto-renouvellement et à la propagation des CSCs CD133+ dans l'hypoxie. Ces facteurs sont impliqués dans diverses voies telles que NOTCH, OCT4, les transporteurs ABC (qui permettent aux cellules cancéreuses de résister aux thérapies en éjectant le traitement) et hTERT (impliqué dans l'activité télomérase qui permet d'augmenter la durée de vie de la cellule en évitant le racourcissement des télomère). Les facteurs d'hypoxie peuvent également contribuer à la plasticité des cellules non-CSCs.


#### E. Thérapies cancéreuses.
Les traitements tels que la [[CAN23 - Chimiothérapies cytotoxiques et mécanismes de résistance|chimiothérapie]], la [[CAN25 - Effets biologiques des rayonnements ionisants.|radiothérapie]] ou la [[CAN27 - Ciblage moléculaire et nouveaux traitements anticancéreux|thérapie ciblée]] ont pour obecjtif d'agir sur la tumeur. Cependant au sein de cette dernière, une population de cellules souches résiste à ces traitements. En conséquence, les traitements peuvent éliminer les cellules tumorales normales mais les CSCs peuvent survivre, proliférer et régenérer la tumeur. Par aileurs, ces thérapies peuvent induire l'acquisition de propriétés de CS par les cellules tumorales pour leur permettre de s'adapter. Comme cela c'est produit avec l'oncostatine.


tags:: #master/cancérologie 
date:: 08/03/2021
enseignant:: Pr. Dantzer

cf [[La réplication. pt II (les différents mécanismes de réparations de l'ADN)]]

L'ADN est la seule molécule biologique réparée. **Plus de 100 gènes** sont nécessaires à la réparation de l'ADN. Même dans les organismes à petits génomes. Une réparation inadéquate conduit au cancer. 

L'équilibre se fait grâce à des **senseurs de dommages**, des **mécanismes de signalisation** et de **réparation**.

La réparation est corrélée avec un **[[CAN05 - Régulation du cycle cellulaire|arrêt du cycle cellulaire]]** (pour éviter la transmission à la descendance), une **inhibition de la [[CAN03 Transcription et Cancer|transcription]]**, de la **[[CAN01 - Dynamique et réplication de l'ADN|réplication]]** et de la mitose, ce qui permet à la réparation d'avoir le temps de se faire.


### I. Processus de réparation.
---
#### A. Réparation directe par réversion.
C'est une réparation directe : une seule enzyme est capable de réparer la lésion.

##### 1. Via l'intervation de la protéine MGMT : mécanisme suicidaire
Enzyme présente chez l'Homme : **MGMT**. 
![[Pasted image 20230509140245.png]]
MGMT prends en charge les **méthylations de base** (ex: méthylation de la guanine) via une **réparation directe** en réponse à une exposition des cellules à des **agents cytotoxiques** comme par ex. le temozolomide (traitement anti-cancéreux générant des méthylations de guanine).

Une méthylation de ce gène a été identifiée dans certains [[CAN13 - Prédisposition héréditaire aux cancers digestifs et polyposes.|polypes colorectaux atypique]]s et dans les glioblastomes, induisant sa répression. La protéine est absente dans la cellule tumorale et les lésions type méthylation de guanine ne sont pas réparées. **L'hyperméthylation** de ce gène dans les cellules tumorales représente ainsi un **marqueur de bon pronostic pour un traitement au temozolomide**.

##### 2. Via photo réactivation.
![[Pasted image 20230509140351.png]]
N'existe pas chez l'Homme ni les mammifères placentaire. Présent dans la levure. Prends en charge les dommages causés par UV, notamment les CPD (cyclobutane pyrimidine dimères. Cette réparation est médiée par les photolyases (2 types sont bien connus) qui utilisent la flavine réduite comme donneur d'électron permettant de scinder le dimère de pyrimidine.
cf [[Dommages à l’ADN signalisation et réponses]]


![[Pasted image 20230509140421.png]]

#### B. Réparation par excision de la région endommagée.
Excision : retrait de la partie ADN lésée. BER et NER

##### 1. BER/SSBR : Base excision Repair / Single strand break repair.
BER : réparation par excision de base
SSBR : réparation des cassures simples brins.
Ce sont les mêmes protéines de réparation qui interviennent.

###### A. Lésions réparées par le BER et leurs causes.
Les dommages de base (exemple : 8oxoG, cassure simple brin, site abasique, ...) créés par des désintégrations spontanées de liaisons chimiques dans l'ADN, des sous-produits du métabolisme cellulaire normal, ou des agents environnementaux.

==Désintégration spontanée de liaisons chimiques dans l'ADN :==
![[Pasted image 20230509140728.png]]
- Hydrolyse spontanée de nucléotides générant des **sites abasiques** non intructifs. Cette désintégration a lieu à raison de : **plusieurs milliers de purines** par génome par jour. Plusieurs centaines de pyrimidines.
- Désaminations spontanées.


==Sous-produits du métabolisme cellulaire normal :==
![[Pasted image 20230509140738.png]]
- Oxydation par des espèces réactives oxygénées (ROS) qui dérivent de la répisration oxydative et de la peroxydation des lipides.
- Méthylations : production de 3-methylAdénine par la S-adénosylméthionine.


==Agents environnementaux :==
- UVA (360 nm) ou UVB (320 nm) : dommages oxydatifs.
- Radiations ionisantes : dommages oxydatifs, cassures simple et double brin
- Agents chimiques génotoxiques : dommages oxydatifs, bases méthylées.


###### B. Les étapes du BER/SSBR.
- <u>Etape 1 : reconnaissance des lésions :</u> 
	SSBR : via poly(ADN-ribose) polymérase ==la **PARP**==
	BER : via ADN glycosylases

- <u>Etape 2 : Elimination de la base endommagée</u>
	Les ADN glycosylases sont dotées d'une activité APlyases, elles clivent en 5' du site abasique formé.

- <u>Etape 3 : Incision du squelette sucre-phosphate</u> 
	Les **APE** (AP endonuclases) clivent en 3' du site abasique. Dans le cadre d'un BER on génère une cassure simple brin.

- <u>Etape 4 : Elimination du nucléotide abasique.</u>
- <u>Etape 5 : polymérisation de novo via ADN polymérase beta.</u>
- <u>Etape 6 : ligation via ADN ligase.</u>

En réalité, c'est plus complexe selon le type de dommage et l'enzyme le reconnaissant, le cycle cellulaire...

![[Pasted image 20230509140851.png]]

- De nombreux intervenants : presque une ADN glycosylase par type de base alkylée qui est produite, plusieurs AP endonucléases, existence de protéines plateformes comme XRCC1 ou PARP.
- Plusieurs voies de réparation dans le BER :
	- SPR (Short patch repair): remplacement du nucléotide lésé.
	- LPR (Long Patch Repair) : remplacement du nucléotide lésé et de ses voisins en 3'.

Un des premiers éléments reconnaissant la cassure simple brin est la PARP (poly-ADP-ribosyl polymerase). La PARP catalyse une modification post-traductionnelle : la **poly-ADP-ribosylation.**
![[Pasted image 20230509141253.png]]
La PARP catalyse une modification post-traductionnelle : la **poly-ADP-ribosylation.**
Lors d'une cassure dans l'ADN (induite par exemple par des radiations ionisantes), la PARP la reconnait, elle utilise le NAD comme substrat et greffe un polymère branché d'ADP-ribose(PAR) sur des protéines nucléaires acceptrices impliquées dans la réparation.
- 1ere fonction : réguler l'activité des protéines cibles.
- 2eme fonction : PARP s'auto-ADP-ribosyl ce qui permet de produire du polymère d'ADP-ribose exactement sur le site de cassure.

*Ceci est mit en évidence par anticorps anti-polyADP ribose couplés à un fluorochrome vert : chaque point vert est un foyer de formation de polyADP-ribose donc de réparation.*

Le **polyADP ribose** sert à la **modification post-traductionnelle des protéines** et à **recruter l'arsenal de protéines de réparation** sur le site de cassure contenant un domaine de liaison au PAR.

![[Pasted image 20230319140941.png]]

La formation de PAR a 2 intérêts :
- **Dose sublétale de cassure :** DNA breaks + seulement quelques cassures, cela active la PARP induisant le BER/SSBR (en réponse aux anti-tumoraux et dans certaines tumeurs) et permet in fine la survie cellulaire.
- **Dose DNA breaks +++:** beaucoup de lésions et donc suractivation de PARP et trop de PAR : in fine mort cellulaire.

*Expérience d'immuno fluorescence : endommagement des cellules du H2O2 (péroxyde d'hydrogène) ou trait de laser + marquage anti-ADP-ribose (rouge) et DAPI (bleu).*
![[Pasted image 20230509141642.png]]
Dès qu'il y a des lésions la cellule apparaît en rouge (car reconnue par l'anti-ADP-ribose).


###### Résumé
**Le poly-ADP-ribose est recruteur de protéines.** Il est produit sur le site de  cassure par la PARP et sert à recruter d'autres protéines de réparation ayant des domaines de liaison au PAR (ex : XRCC1).
![[Pasted image 20230509141634.png]]
*Aujourd'hui, plus de 10 domaines de liaison au poly-ADP-ribose identifiés.*

###### Pathologies associées.
On a très peu d'évidence d'association entre des mutations des protéines du BER et le développement d'un cancer car ce système de réparation joue un rôle fondamental dans le développement embryonnaire (mutation de BER = problème embryonnaire = pas de survie adulte = pas de développement de cancer).

###### Particularités des cassures simple brin (SSB).
C'est une lésion produite fréquemment de manière **endogène** (10-10000 / jour / génome) en réponse aux ROS, désintégration de sucres oxydés, produit du BER, erreur de la topoisomérase I.

La topoisomérase I (dérouler la structure de l'ADN, cf [[CAN01 - Dynamique et réplication de l'ADN]]) génère transitoirement des cassures simples brins et effectue par la suite une religation. Cette activité de cassure-déroulement-religation dépend d'une fixation covalente de la topoisomérase I à l'ADN.

**Camptothecin** est un anti-cancereux qui inhibe la topo1 en empêchant la religation, laissant donc les cassures simples brins. Dans ce cas là ;
- TDP1 (tyrosyl phosphodiestérase) intervient, elle permet le relargage de la topoI.
- Formation d'une coupute non ligable 3'P5'OH
- La PARP et donc aussi toutes les autres protéines de réparation (XRCC1, ADN ligase III) sont recrutées.
- La protéine PNK intervient pour reformer des extrêmités liables et permettre intervention des ADN ligases.


##### 2. NER (Nucleotid excision repair).
NER : retrait d'une région d'ADN.

###### a. Lésions réparées par le NER et leurs causes.
NER prend en charge les dommages induits par les UVs, hydrocarbures, polycycliques aormatiques, rendant l'ADN non fonctionnel -> **retrait d'une séquence d'ADN** (jusqu'à 1000 nucléotides).
![[Pasted image 20230509141905.png]]
Effets des UVs : **CPD (*dimères de cyclobutane pyrimidine*) et 6-4PPs (*photoproduits pyrimidine pyrimidone*)
![[Pasted image 20230509141919.png]]

###### B. 2 sous-voies de réparation.
- **GG-NER** = Global genome NER : répare les lésions sur tout le génome
- **TC-NER** = Transcription-coupled NER : prend en charge les lésions qui bloquent l'ARN pol II.

###### C. Etapes.
![[Pasted image 20230509141939.png]]
- <u>Etape 1 :</u> reconnaissance de la lésion (CPDs/6-4PPs) : XPC-R23 se fixe et permet le recrutement d'un complexe multiprotéique de réparation favorisant l'ouverture du brin d'ADN.
- <u>Etape 2 :</u> excision de la région comportant la lésion. Protéine **XPG** = coupe en 3' de la lésion (grosse lésion, presque 1k).
- <u>Etape 3 :</u> polymérisation de la breche. ADN polymérase delta/epsilon = les mêmes que la réplication. Protéine RPA protège le bout d'ADN simple brin en attendant que la polyméraisation se réalise.   
![[Pasted image 20230509142013.png]]


###### d. Cas particulier du TC-NER.
Il fait intervenir qq autres protéines, uniquement lorsque la lésion bloque l'avancée de la transcription  : CS1/CSB (mutation = syndrôme de cockayne) et BRCA1/BRCA2 (mutation = cancer du sein et de l'ovaire).
![[Pasted image 20230509142038.png]]

###### E. Pathologies associées.
![[Pasted image 20230320161753.png]]![[Pasted image 20230320161759.png]]


##### 3. Mismatch repair (MMR).
###### a. Lésions conercnées par le MMR.
Les mésappariements = lésions ne respectant pas la correspondance A-T, C-G : 
- Le plus souvent produits lors de la **réplication**. Celui-ci se fait sur le brin néosynthétisé, mais les mécanismes dereconnaissance de celui-ci (par rapport au brin matrice) ne sont pas encore résolus chez l’Homme.
- Ou bien lors de la **recombinaison homologue** (qui nécessite une polymérisation)
- Ou par des agents endommageant dont les dommages sont considérés comme des mismatchs notamment :
	- **Agents alkylants** : TMZ, **temozolomide** = agent de chimiothérapie qui vont formation d’O6-méthylguanine et O6MeG/T ou O6MeG/C sont considérés comme des mésappariements.
	 - **6-thioguanine TG :** utilisée dans le traitement des leucémies ou comme immunosuppresseurs (greffes): production de 6MeT et mismatch 6MeT/T
	- **Cisplatine :** agent de chimiothérapie pour les cancers des testicules et des ovaires induisant un pontage intra-brin 1,2 GpG considéré comme un mismatch
	- En revanche, la réparation est « futile » car uniquement sur le brin néosynthétisé. Le MMR bloque alors le cycle cellulaire et conduit à l’apoptose de la cellule cancéreuse. Ces chimiothérapies sont inefficaces en cas de déficit du MMR.
	  
	- En résumé, le temozolomide est efficace sur les cellulescancéreuses :
		▪ déficientes en MGMT
		▪ proficientes en MMR.


###### b. Etape du MMR.
Etape 1 : Reconnaissance du mismatch
hMutSα = hétérodimère hMSH2-hMSH6 (h pour human) recrutant un deuxième hétérodimère hMutLα (hMLH1-hMLH2) permettant la translocation du complexe (tétramérique) autour de la lésion.

Etape 2 : Collision du complexe avec la fourche de réplication. C’est-à-dire avec un gap de fragment d’Okazaki et la protéine PCNA (facteur de processivité cf:CAN01) entraînant le recrutement de l’exonucléase Exo1 qui digère le brin en direction du mismatch.

Etape 3 : plusieurs cycles de digestion - recrutement du complexe MMR jusqu’à avoir digéré la lésion (le simple brin est protégé par RPA).

Etape 4 : Resynthèse du brin complémentaire et ligation
Par la polymérase delta (interagissant avec PCNA) et une DNA ligase


###### c. Maladies associées au MMR
Le cancer colorectal héréditaire sans polypose (HNPCC) est dû à des défauts des protéines MLH1, MSH2, MSH6...
Attention pour son traitement car certains anticancéreux seront inefficaces.



#### C. Réparation des coupures double-brin.
A savoir que les cassures double-brin sont les lésions de l'ADN les plus cytotoxiques.

###### 1. Recombinaison homologue (RH).
Pour ce mécanisme, l’existence d’un brin homologue est indispensable donc elle se fait principalement en phase S ou G2. Elle est fidèle et présente chez les mammifères comme les levures
![[Pasted image 20230509142453.png]]
• Etape 1 : Digestion Le complexe RMN (MRE11-NSB1-RAD50) a une activité exonucléase 5’→3’ et forme des extrémités 3’. Le simple brin formé est protégé par des RPA.

• Etape 2 : Recrutement des ATPases (RAD51, RAD52, RAD54) par RPA. RPA et RAD52 facilitent la formation du filament RAD51. Les protéines BRCA1 et 2 sont aussi recrutées à cette étape et agissent avec RAD51.

• Etape 3 : Actions des ATPases
RAD51 et 54 recherchent l’homologie de séquence et échangent les brins de façon à former les jonctions de Holliday (cf figure)

• Etape 4 : Résolution des jonctions de Holliday par des résolvases.


###### 2. Réparation non homologue (NHEJ)
Cette réparation est infidèle et résulte parfois en des gains ou pertes de fonction (par insertion, délétions et décalage du cadre de lecture).
En revanche, elle n’a pas besoin de brin homologue et peut avoir lieu dans toutes les étapes du cycle cellulaire. Elle est la plus active en G1.
![[Pasted image 20230509142527.png]]

Etape 1 : Rapprochement des extrémités non ligables Par la protéine KU (ATPase/hélicase).

• Etape 2 : Recrutement d’enzymes facilitant la formation d’extrémités franches et ligables La protéine KU recrute :
	- La DNA PKcs (DNA-dependent protein kinase, catalytic subunit) qui recrute elle-même la protéine Artémis (nucléase favorisant la formation d’extrémités franche).
	- XRCC4 qui recrute la DNA ligase IV et PNK (favorisant la formation d’extrémités ligables).


La réalité est plus complexe que ces deux étapes : il y a des protéines initiatrices qui activent les voies de la recombinaison homologue et non homologue.

Une des protéines de détection des cassures double brin est initiatrice des mécanismes de réparation est la protéine ATM. Elle est mutée dans le syndrome ataxie télangiectasie.

ATM active également p53 ce qui permet le blocage du cycle cellulaire.


###### 3. Maladies associées à la réparation des cassures double-brin
![[Pasted image 20230509142642.png]]
Le défaut de réparation des cassures double-brin provoque entre autres une instabilité génomique par aberrations chromosomiques.

Ataxie-télangiectasies : mutation protéine ATM (=PI3K) 
➔ Immunodéficience, neurodégénération et prédisposition aux lymphomes.

• Syndrome de Nijmegen : (AT-like) mutation de Nsb1 (qui fait partie du complexe de la Nsb1/Mre11/Rad50 de la recombinaison homologue)
➔ Immunodéficience, microcéphalie et prédisposition aux lymphomes

• BRCA1/2 : anomalies de la recombinaison homologue

• Syndrome de Werner : mutation de la protéine WRN avec défaut de la RH, de la NHEJ et de la synthèse translésionnelle

• Syndrome de Bloom : mutation d’un cofacteur de l’ADN pol II et donc des voies RH et NHEJ


#### D. Passage de lésion.
Deux possibilités :
• Synthèse translésionnelle : échange de polymérase (réplicative → hautement mutagène)
• Echange de brin (template swicth) : autre mécanisme non abordé
![[Pasted image 20230509142818.png]]

###### 1. Synthèse translésionnelle (TLS)
![[Pasted image 20230509142855.png]]
**<u>a. Principe</u>**
Lorsqu’une lésion vient bloquer la réplication, il y a remplacement de la polymérase réplicative (delta, epsilon) par une polymérase de la TLS. Une fois la lésion répliquée, il y a de nouveau échange et la réplication se poursuit avec les polymérases réplicatives.
On parle de réparation mutagène, la lésion est fixée si aucun autre mécanisme ne répare ensuite.

<u>b. Acteurs.</u>
Pour rappel, il existe 4 classes de polymérases dont les noms et rôles sont précisés ci-contre :

Les ADN polymérases de la famille Y : iota, êta, kappa, rev1 sont celles de la TLS, elles ont :
- 5 domaines conservés
- Peu de fidélité : taux de mismatch à 10-2
(alors que pol delta : 10-5)

- Faible activité exonucléase (qui fait
qu’elles ne reviennent pas en arrière corriger leurs erreurs).
- Faible processivité (elle se détachent
souvent, elles sont distributives).

###### 2. Pathologies XPV.
On a remarqué qu’une mutation du gène XPV entraînait une mauvaise réplication de l’ADN endommagé aux UV mais un NER normal.
➔ Ce gène ne code pas pour une protéine XP du NER mais pour l’ADN polymérase translésionnelle êta qui est capable de répliquer un dimère TT modifié par les UV (CPDs) en incorporant AA en face.

➔ En son absence (XPV muté), une autre TLS est impliquée et mis-incorpore en face de ces
lésions, il y a donc induction de mutations.

Un défaut d’une polymérase infidèle peut donc favoriser le développement de mutations, ce qui en fait bien un mécanisme de « réparation ».


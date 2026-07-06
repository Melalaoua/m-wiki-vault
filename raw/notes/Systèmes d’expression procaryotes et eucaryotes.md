---
Date : September 23, 2022 10:18 AM
---

up:: [[TBMC]]
tags:: #academia/master, #master/Techniques



Une protéine recombinante est une protéine produite par une cellule dont on a modifié l’ADN par recombinaison génétique. On se sert de ces protéines pour :

- En laboratoire : étude fonctionnelle de l’expression de la protéine.
- En entreprise : production de médicaments ou de vaccins (facteurs de coagulation, insuline, interféron, vaccin contre l’hépatite B).
- La clinique : En thérapie génique contre le cancer ou une maladie génétique.

Pour pouvoir exprimer ces protéines recombinantes il faut pouvoir trouver un hôte (ou système) d’expression. On va isoler notre gène d’intérêt et l’insérer dans un vecteur d’expression pour clonage. Cette stratégie confrontée à beaucoup de difficultés et contraintes quand on veut produire de manière optimum :

- Taux d’expression de la protéine conséquent, une bonne cinétique.
- Pouvoir opérer un certains nombre de modifications post-trad, repliement, glycosylation.
- Appliquer des procédés de purification.
- Stable et une certain solubilité.
- Considérations économiques : équipements disponibles, coûts de production.

$\LARGE\textbf{\textsf{Chapitre I.}}\\\Large\textsf{Les vecteurs d'expressions.}$

---

## A. Les plasmides.

Un plasmide est un ADNdb circulaire de 2 à 200kb, un élément extra-chromosomique avec un certains nombres de gènes donnant à l’hôte des propriétés supplémentaire (résistance à antibiotiques, ..). Ils ont tous une ORI qui a la particularité de se répliquer de façon autonome, indépendant du chromosome bactériens (dépendent quand même du protéomes).

> **Réplicon :** L’ORI et les éléments de contrôle associés.
**Site de restriction :** Polylinker ou multiple cloning site.
**Gène de résistance à un antibiotique** (marqueur de sélection).
> 

Le réplicon est l’élément génétique qui contrôle le nombre de copies du plasmide que l’on peut avoir dans une souche bactérienne donnée. Le nombre de copie est donc variable, on peut avoir des plasmides :

- A contrôle de réplication stricte : Se répliquent en même temps que le chromosome bactérien et ne sont donc présents qu’à raison d’une ou de **quelques copies par cellules.**
- **A contrôle de réplication relâchée :** Se multiplient dans les cellules jusqu’à que ce que chaque cellule ait en moyenne **10 à 200 copies du plasmides.**

> **Transformation :** Introduction de plasmides dans une bactérie. 
     Réalisé par choc thermique (traitement CaCl2, entré de l’ADN recombinant par choc thermique à 42°C.).
     Ou réalise par choc électrique (électroporation).
⇒ L’efficacité de transformation est inversement proportionnelle à la taille du plasmide. C’est la raison pour laquelle on préfère transformer des plasmides de petites        taille.
> 

<aside>
⚠️ Pour être de bons vecteurs de clonage, les plasmides doivent être petits et se répliquer sous contrôle relâché.

</aside>

### Rappels sur l’opéron lac de E.coli.

En absence de lactose, le répresseur est sous sa forme active. Il va se lier à l’opérateur de l’opéron lactose, bloquant l’accès de l’ARN polymérase au site d’initiation de la transcription. Il y a une régulation négative de la transcription des gènes de l’opéron lactose. Les enzymes nécessaires au métabolisme du lactose ne sont pas synthétisées.

En présence de lactose ou d’analogues **(IPTG)**, l’inducteur se lie au répresseur pour l’inactiver. Cette liaison entraine un changement conformationnel du répresseur qui perd alors son affinité pour l’opérateur. Le site opérateur étant libéré, l’ARN pol peut atteindre le site d’initiation de la transcription et synthétiser l’ARN polycistronique. La production des enzymes nécessaire au métabolisme du lactose est donc dépendante de la présence du substrat.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled.png)

### Plasmides de la famille pUC.

On trouve une **MCS**, site de clonage situé dans le début du gène lacZ. Le gène lacZ code pour la galactosidase avec le promoteur et les séquences régulatrices de l’opéron lac.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%201.png)

**L’insertion d’un fragment d’ADN (max 10kb) détruit le gène lacZ,** la galactosidase n’est plus fonctionnelle.

Sélection des bactéries transformées portant un plasmide recombiné.

On étale les bactéries sur un milieu gélosé avec de l’ampiciline et de l’IPTG (inducteur de l’opéron lac) et la X-gal (sera clivé par la galactosidase et libérant un composé bleu) puis on laisse incuber à 37°C.

On observe ensuite 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%202.png)

### Les plasmides pET/T7.

Ces plasmides sont particuliers, en effet peuvent comprendre un promoteur T7 (promoteur fort) qui est reconnu par l’ARN pol du phage T7.

- En absence d’IPTG, la T7 RNA polymérase est produite à un niveau basal, hors, celle-ci est inhibée par le lysozyme du phage T7 produit en faible quantité à partir d’un autre plasmide.
- Par contre, après induction, l’inhibiteur est en trop faible quantité pour continuer à inhiber la T7 RNA polymérase.

Celle-ci pourra alors transcrire le gène d’intérêt cloné en aval du promoteur T7. Comme seul ce gène est sous la dépendance de ce promoteur, il sera produit en très grande quantité.

Quand on ajoute de l’IPTG dans le milieu de culture des cellules, E coli libère le répresseur de l’opérateur Lac.  L’arn pol T7 située au niveau de ce promoteur dans l’hôte va être produite et va catalyser au niveau de ce plasmide la transcription de l’ADN inséré.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%203.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%204.png)

## B. Les bactériophages.

### Le bactériophage $\lambda$.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%205.png)

Le bactériophage lambda est un virus phage capable d’infecter E. coli. Leur cycle peut être lytique ou lysogénique. Ils ont un ADN db linéaire. Les extrémités d’ADN sont simples brin, complémentaires de douze nucléotides (séquence cos), nécessaire à l’encapsidation. 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%206.png)

La grande région non essentielle est remplacée par un fragment d’ADN étranger (max 20kb).

Il y a ensuite insertion d’ADN étranger dans un gène de sélection (ex: lacZ).

L’ADN recombinant résultant est encapsidé (phage assemblage in vitro, en ajoutant les protéines de la capside et de la queue).

IL y a injection de l’ADN viral recombinant dans la bactérie. L’ADN viral recombinant se circularise et réplique : il y a expression de la protéine recombinant.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%207.png)

## C. Les cosmides (phage + plasmide).

Les cosmides, contrairement au bactériophages, vont permettre d’insérer des fragments de plus grandes tailles. Ce sont des **vecteurs artificiels de clonage** constitués d’un **plasmide hybride** contenant la séquence cos du phage $\lambda$. On peut transférer les gènes d’intérêts dans les cellules par transduction**.** L’assemblage du phage a lieu in vitro en ajoutant les protéines de la capside et de la queue. Les particules virales sont capables d’infecter E. coli.

- Col E1 ori (origine de réplication) : peut se répliquer comme un plasmide dans une cellule.
    
    <aside>
    ⚠️ IL faut prendre l’ORI appropriée à la cellule-hote : 
    - SV40 ori pour les mammifères.
    - Col E1 ori (réplication simple brin) ou Col f1 ori (pour simple brin) chez les procaryotes.
    
    </aside>
    

- Gène de résistance à un antibiotique, pour permettre la sélection de cellules transfectées.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%208.png)

A la différence des plasmides, les cosmides sont encapsidés (capsides de bactériophages). Il faut donc transférer les gènes d’intérêts dans les cellules par transduction. La capside du vecteur obtenu contient alors uniquement le cosmide et non pas le matériel génétique du phage $\lambda$. La séquence COS du bactériophage $\lambda$ est nécessaire à l’encapsidation. Le phage s’assemble in vitro en ajoutant les protéines de la capside et de la queue. Les particules virales sont capables d’infecter E. coli. **L’ADN cloné fait environ 45kb**. La taille d’ADN insérée dans des plasmides est limitée car une grande taille augmente la probabilité d’une recombinaison génique. Les extrêmités cohésives correspondants aux sites cos permettent de résoudre ce problème et d’augmenter la capacité du plasmide.

## D. Les vecteurs viraux.

### Obtention de vecteurs viraux.

1 particule virale est constitué d’une capside protéique renfermant des AN à létat compacté. Les virus reconnaissent à la surface des cellules des récepteurs, la reconnaissance permet l’entrée et libération de leur matériel génétique dans le cytosol.

1 vecteur virale et comme un cheval de Troie, la capside viral, permettant l’entrée dans la cellule, renferme un génome viral recombinannt porteur du transgène. A son entrée dans la cellule, il n’y aura pas de production de nouvelles particules, mais un transfert de l’information contenue dans le transgène.

<aside>
⚠️ Le génome du virus manipulé sous forme d’1 ADN propagé dans une bactérie avant encapsidation.

</aside>

### Vecteur baculovirus.

Ce sont des **virus d’insectes**, enveloppés en forme de bâtonnets (~350nm). L’ADN à l’intérieur est bicaténaire, circulaire, superenroulé d’une taille d’neviron 80 à 200kb.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%209.png)

La région du génome qui code pour la protéine polyhédrine peut être remplacée par un gène d’intérêt (promoteur polyhédrine très actif/fort). La taille de l’insert ne doit pas dépasser 50kb.

Système d’expression :

Cellule d’insecte Sf9 (cellule d’ovaire de larves de Spodoptera frugiperda).

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2010.png)

### Génération de vecteurs dérivés des baculovirus.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2011.png)

### Les retrovirus.

Certains virus, à fort taux de multiplication, comme les **adénovirus**, ne possèdent pas d’éléments leur permettant de maintenir leur génome de manière continue dans la cellule infectée.  En revanche, d’autres virus établissent une infection latente au cours de laquelle leur génome est stabilisé. Dans le cas des **rétrovirus**, le génome pénètre dans le noyau cellulaire ; le processus d’intégration de l’ADN viral est dans la continuité du génome de l’hôte et assure ainsi sa pérenité.

On utilise surtout les lentivirus et les $\gamma$-retrovirus, utilisés chez l’homme dans 200 essais cliniques depuis 1989. Il y avait de vrais succès dans la thérapie génique, notamment pour les patients atteints d’immunodéficiences combinées sévère, mais les essais ont été interrompus à cause des effets secondaires imprévisibles.

On utilises des caractéristiques du cycle réplicatif des rétrovirus : le génome ARN est rétro transcrit en ADN puis est intégré au génome de la cellule infectée. La plupart des vecteurs rétroviraux ont été construits à partir d’un rétrovirus de souris, non pathogène pour l’homme : le MLV.

Les retrovirus sont des virus à ARN sb à polarité positive (brin sens), enveloppés qui contiennent des enzymes virales (reverse transcription, intégrase, protéase). La capside contient le génome viral et des enzymes.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2012.png)

### Organisation génomique des rétrovirus.

Les retrovirus ont un cadre de lecture qui code pour les protéines virales, la polymérase et les protéines d’enveloppe. 

Ils ont également une séquence $\Psi$ qui est un signal d’encapsidation. Les LTR, terminaux, sont des signaux de transcription et d’intégration.

### Vecteurs rétroviraux.

Le transgène est placé entre les séquences LTR mais sans impacter la séquence $\psi$ qui est la séquence d’encapsidation qui permettra de produire les pseudo-particules. Le génome viral voit ses gènes gag, pol et env remplacés par la séquence du transgène d’environ 8kb.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2013.png)

### Production de vecteurs rétroviraux.

**Avantages :**

- Tropisme : large choix de protéines d’enveloppe.
- Intégration facile en respectant l’intégrité du transgène.
- Presistance du transgène car intégration dans le génome.
- Faible immunogénicité.

**Désavantages :**

- Taille limité du transgène à 8-9kb.
- Production difficile de hauts titre infectieux.
- Intégration au hasard : risque de perturbation du fonctionnement d’un gène.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2014.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2015.png)

### Les adénovirus.

Ce sont des virus non enveloppés de 70-100 nm . Il en existe plus de 50 sérotypes humains. Leur génome est à ADN linéaire db (30kb). ILs ont un tropisme cellulaire très large chez l’homme et peuvent donner des infections cliniques très variées (rhumes, rhinites, pharyngites, conjonctivites).

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2016.png)

### Etapes précoces du cycle infectieux d’un adénovirus.

Il y a tout d’abord fixation des protéines de capside au niveau du récepteur cellulaire qui induit la phagocytose, la libération de la capside jusqu’au niveau tubulaire, où il y a libération du génome viral au niveau du corps nucléaire.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2017.png)

### Les vecteurs adénoviraux.

Ils servent dans le dvt de thérapies géniques car ils sont efficaces et leur mode de préparation est simple et adaptable à l’échelle indsutrielle. Mais, les études chez l’animal et les essais cliniques montrent les limites et les problèmes de toxicité.

Le génome des adénovirus est à ADN sb et comprends des gènes précoces qui codent pour des protéines régulatrices impliquées dans les étapes précoces de réplication mais codent aussi pour des gènes tardifs qui codent pour des protéines de caspide. 

Les vecteurs sont produits à l’aide d’une lignée cellulaire exprimant un gène viral précoce clé appelé E1 qui permet la réplication d’un adénovirus défectif (substitution du gène E1 par un transgène et sa cassette d’expression).

Ce vecteur conserve la plupart des gènes viraux d'origine mais ne peut pas se répliquer dans des cellules ne possédant pas le gène E1 mais il pourra transporter le transgène jusqu'au noyau des cellules traitées.

**Avantages :**

- Infection efficace de très nombreux types cellulaires, y compris les cellules quiescentes.
- Ne s’intègre pas au génome cellulaire : ne perturbe pas le génome de la cellule hôte.
- Production de hauts titres infectieux.

**Désavantages :**

- Taille limitée du transgène : 8-9kb maximum.
- Expression du transgène transitoire (15 jours max) parce que l’ADN ne s’intègre pas dans l’ADN de la cellule hôte.
- Expression de protéines virales par la cellule infectées :réponse immunitaire de l’hôte.

### Vecteurs AAV.

Les virus associés à l’adénovirus (adeno-associated virus, AAV) :

- Petite taille, largement présents dans les pop. humaines, sans conséquences pathologiques connues.
- Résistent à des conditions extrêmes de pH et de T°, aux détergents, +/- aux solvants: facilite les étapes de purification et de formulation galénique.
- Peuvent infecter des cellules d’origines tissulaires diverses et stabilisent leur génome par intégration dans un chromosome.
- Ne peuvent pas accomplir leur cycle réplicatif seuls et se comportent en parasites de l’adénovirus.

**Production de vecteurs AAV.**

Le vecteur comprend les origines de la réplication et la séquence signal d’encapsidation $\psi$ de l’adénovirus et de l’ADN étranger (jusqu’à 30kb).

Le vecteur et l’AdV auxiliaire ($\Delta$e1) sont propagés dans les cellules 293/E1+.

L’AdV aux founit en trans toutes les protéines régulatrices et structurales sauf E1.

Le signal $\psi$ est excisé par la recombinanse Cre : les particules correctement encapsidées sont des particules contenant le vecteur recombinant.

Il y a ensuite purification du surnageant cellulaire afin d’éliminer les particules de virus contenant le vecteur auxiliaire.

Les avantages de ce nouveau modèle est qu’on a une grande capacité de clonage, une faible
immunogénicité car ils n’ont pas d séquence codantes virales. L’expression du transgène se
fait à long terme et les vecteurs sont moins dangereux pour l’hôte.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2018.png)

$\LARGE\textbf{\textsf{Chapitre II.}}\\\Large\textsf{Les systèmes d'expression procaryotes.}$

---

La plupart des souches utilisées sont des souches E. coli.

**Avantages :**

- Expression rapide des protéines.
- Génétique très bien connue.
- Nombreux outils de clonage commerciaux (beaucoup de vecteurs et de souches disponibles).
- Facile à cultiver en masse.
- Expression élevée (plusieurs g/L de protéines recombinante).

**Inconvénients :**

- Faible potentiel de sécrétion.
- Accumulation de protéines recombinantes dans des corps d’inclusion (difficiles à solubiliser).
- Présence d’endotoxine bactérienne.
- Pas de modifications post-traductionnelles : activité biologique différente de la protéine native.

$\LARGE\textbf{\textsf{Chapitre III.}}\\\Large\textsf{Les systèmes d'expression eucaryotes.}$

---

Les eucaryotes possèdent un RE et l’appareil de golgi, on peut donc procéder à des modifications post-traductionnelles comme la protéolyse, la formation d’un pont disulfure, l’oxydation des méthionines, la désamination de l’asparagine, l’ajout de lipides ou encore la glycosylation (N- et O-glycosylation). 

**La glycosylation :** 

Influence les propriétés des protéines et leur activité, leur solubilité, la modulation de la demi-vie, leur stabilité, leur immunogénicité ou encore la protection contre la protéolyse. 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2019.png)

<aside>
⚠️ Si la glycosylation est indispensable, la protéine d’intérêt doit être exprimée dans des cellules eucaryotes.

</aside>

**Les O-glycosylation :**  Ajout d’un monosaccharide sur un oxygène du groupement hydroxyle. Pour la N-glysoylation, le N signifie que le glycane est attaché de manière covalente à l’azote du groupement amide d’une asparagine. Le sucre immédiatement attaché à l’asparagine est la N-acetylglucosamine.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2020.png)

**Les N-glycosylation :** essentiellement co-traductionnelle : le glycane est attaché à la chaîne polypeptidique en cours de biosynthèse et pendant son transport dans le réticulum endoplasmique.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2021.png)

### La Levure.

Il s’agit du modèle eucaryote le plus simple. Le génome contient 16 chromosomes de 200 à 200 kb ainsi que de l’ADN mitochondrial et un **plasmide de 2microns**. La division se fait par bourgeonnement. Leur croissance est rapide. Saccharoymyces cerevisiae et Pichia pastoris sont les deux espèces généralement utilisées.

### Yeast episomal plasmids (Yep).

Les vecteurs utilisés sont dérivés du plasmide de 2 microns et sont appelés **plasmides épisomiques de levure ou Yep**. Quelques Yep contiennent le plasmide de 2 microns en entier, d’autres incluent juste l’ORI. Le 2microns plasmide, comme on l’appelle, est l’un des rares plasmides trouvés dans les cellules eucaryotes.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2022.png)

En pratique, on a un gène de levure normal codant pour une enzyme impliquée dans la biosynthèse des acides aminés. La LEU2 est un marqueur de sélection. Un type particulier d’organisme hôte peut être un hôte mutant auxotrophique qui possède un gène LEU2 non fonctionnel.

**LEU2 = marqueur de sélection.**

Dans ce cas, la levure leu2- est incapable de synthétiser la leucine et ne peut survivre que si cet acide aminés est ajouté dans le milieu de croissance.

Pour sélectionner les levures qui ont intégré le plasmide transformé, il suffit de les cultiver sur milieu minimal, les transformants contiennent une copie du gène LEU2 supportée par un plasmide et sont capables de se développer en l’absence de l’acide aminé.

### Intégration de l’ensemble du plasmide Yep dans l’ADN de levure.

L’intégration se fait par recombinaison homologue. Le mot épisomale indique qu’un Yep peut se répliquer en tant que le plasmide indépendant mais implique également l’intégration dans l’un des chromosomes de levure.

L’intégration se produit parce que le gène porté sur le vecteur comme marqueur de sélection est très similaire à la version mutante du gène présent dans l’ADN chromosomique de levure.

Avec YEp13, par exemple, une recombinaison homologue peut se produire entre le gène du plasmide LEU2 et le gène LEU2 du mutant de levure, provoquant l’insertion du plasmide entier dans l’un des chromosomes de levure.

<aside>
⚠️ Le plasmide peut rester intégré, ou un évènement de recombinaison ultérieure peut l’exciser de nouveau.

</aside>

**Avantages :**

- Modifications post-traductionnelles (glysoylations simples, acétylation..).
- Nombreux vecteurs disponibles.
- Faciles à cultiver.
- Absence d’endotoxines.
- Bonne expression (environ 200 mg-g/L).

**Inconvénients :**

- Glycosylation incomplète.
- N-glycosylation : immunogène chez l’homme.
- Mauvais repliement de la protéine produite.
- Sécrétion difficile pour les protéines complexes.

### Les plasmides comme vecteurs d’expression eucaryote.

Les promoteurs forts les plus fréquemment utilisés sont les promoteurs viraux tels que CMV, SV40, les rétrovirus. La BGH pA est un signal de polyadénylation. pUC ori est à l’origine de réplication bactérienne. Ces plasmides contiennent des gènes de résistance à l’ampiciline et à la néomycine.

Ce plasmide va entrer dans la cellule eucaryote par **transfection** (phosphate de calcium, liposomes cationiques ou électroporation). La transfection peut être **transitoire** (analyse de l’expression de la protéine recombinante après 24-72 heures, perte du plasmide au cours des divisions cellulaires) ou **stable** (expression de la protéine à long terme, le plasmide s’intègre au niveau chromosomique, sélection des clones possédant le plasmide grâce à leur résistance à un antibiotique).

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2023.png)

### Cellules mammifères.

**Avantages :**

- Nombreux vecteurs d’expression disponibles, lignées cellulaires.
- Activités biologique de la protéine recombinante similaire à celle de la protéine native.
- Modifications post-traductionnelles de mammifère.
- Profil de glycosylation complet, proche de celle retrouvée chez l’homme.

**Inconvénients :**

- Culture des cellules difficile et coûteuse.
- Croissance lente.
- Cellules recombinées peu stables (perte du plasmide).
- Faible rendement (de l’ordre de 10 mg/L de culture) comparées aux procaryotes.

### Cellules d’insectes.

**Avantages :**

- Croissance rapide des cellules en suspension.
- Bons rendements de production (de l’ordre de g/L de culture).
- Modifications traductionnelles poussées :
    - Assemblage de complexes oligomériques.
    - Formation de ponts disulfures.
    - Repliement.

**Désavantages :**

- Glycosylation limitée.
- Cycle lytique du virus (expression de la protéine recombinante est transitoire).

$\LARGE\textbf{\textsf{Chapitre IV.}}\\\Large\textsf{Purification des protéines recombinantes.}$

---

### Protéines de fusion.

Il s’agit d’une protéine issue d’un gène chimère (combinaison de deux gènes différents). La protéine d’intérêt est généralement fusionnée à une étiquette/TAG permettant la purification de la protéine recombinante.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2024.png)

Les systèmes les plus utilisés sont His6-Tag, la glutathion-S-transférase (GRT) sur une colonne de glutathion-agarose ou encore la protéine liant le maltose (Maltose-Binding-Protein, MBP) sur une colonne d’amylose. Le clivage de la protéine de fusion peut se faire par entérokinase ou par thrombine.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2025.png)

$\LARGE\textbf{\textsf{Chapitre V.}}\\\Large\textsf{Exemples d'application.}$

---

L’expression d’une protéine recombinante peut servir pour des études fonctionnelles comme **l’intéraction avec d’autres protéines, la localisation subcellulaire**.

### Fusion avec un gène rapporteur.

Si le plasmide contient le gène GFP, on peut visualiser l’expression de la GFP par microscopie de flurorescence. Si le plasmide contient le gène de la luciférase (enzyme), on peut quantifier l’expression de la protéine recombinante en ajoutant de la luciférine. L’intérêt est que quand la protéine d’intérêt va être produite dans le système d’expression, le gène rapporteur va être exprimé et on va pouvoir visualiser l’expression de la protéine soit pour quantifier, soit pour localiser.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2026.png)

### Système d’expression de protéine recombinantes.

On l’utilise beaucoup pour la production de médicaments ou de vaccins notamment le vaccin HPV contre le cancer du col de l’utérus. Le HPV possède un DNAdb de 8kb, circulaire, super-enroulé. La capside virale possède deux protéines : L1 (protéine majeure de la capside) et L2 (protéine mineure). Ce sont nos deux protéines d’intérêts.

Le vecteur de thérapie génique serait idéal s’il répond aux critères suivants  :

- Facile à administrer, injectable.
- Production facile et reproductible à haute concentration.
- Expression tissu-specifique.
- Non reconnu par le système immunitaire.
- N’induisant pas de réponse inflammatoire.
- N’induisant pas de pathologie.
- Expression génique à long terme par insertion dans le génome ou expression épisomique persistante.

![bubble-chat.png](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/bubble-chat.png)

$\Large\texttt{Commentaires}$

---

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2027.png)

**Exemple : sérotypes Adv2 et Adv5.**

Ces adénovirus sont des vecteurs de première génération, on a remplacé la partie de la région E1 (essentielle pour la réplication virale) et une petite partie de la région E3 par le transgène. On produit ces vecteurs dans des lignées cellulaires modifiées exprimant E1. En sortant de ces lignées cellulaires, on produit de grande quantité de particules virales infectieuses non réplicatives. Puis on infecte des cellules cibles et on exprime le transgène intégré.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2028.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2029.png)

**La recombinaison homologue peut se produire entre le gène du plasmide LEU2 et le gène LEU2 du mutant de levure.**

### Exemple gène rapporteur.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2030.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Systèmes%20d’expression%20procaryotes%20et%20eucaryotes/Systèmes%20d’expression%20procaryotes%20et%20eucaryotes%2028268d08759047cabf74f117bed376c2/Untitled%2031.png)

---

$\Large\texttt{Fin de page}$
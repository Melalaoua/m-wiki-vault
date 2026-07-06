---
Date : September 23, 2022 11:04 AM
---

up:: [[TBMC]]
tags:: #academia/master, #master/Techniques




## Introduction.

Le terme de protéome a été défini en 1996 par Wilkins : ***A proteome is the entire protein complement expressed by a given biological system in given conditions.***

L’analyse protéomique, c’est l’analyse de l’ensemble des protéines exprimées par un type cellulaire, un tissu ou un fluide biologique (sang, urine), à un instant donné. On va plus précisément déterminer l’identité des protéines, leur abondance, leur modifs post trad. 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Spectrométrie%20de%20masse/Spectrométrie%20de%20masse%20f4bd033b6db34179a0da0546c04996af/Untitled.png)

<aside>
📎 Attention, il faut faire la distinction entre protéome et génome. Le génome d’un individu restera toujours le même, tandis que le **protéome est exprimé à un instant donné**.

</aside>

On ne peut pas utiliser l’ADN, ni le mRNA (cf. transcription + traduction) pour doser la quantité de protéines pour la simple raison que : 

- Déjà l’ADN d’une cellule va être sous forme inactive/active (chromatine) et va pouvoir être transcrit plusieurs fois.
- Les mRNA (codant pour protéines) peuvent être accumulé, traduit plusieurs fois, stockés, …

Les protéines vont très souvent **interagir** entre elles pour former une complexosome. On va pouvoir étudier le produit final résultant des différentes interactions en piégant une protéine via un anticorps, on capturera les autres protéines en interaction dans le même processus.

$\LARGE\textbf{\textsf{Chapitre I}}\\\Large\textsf{Du génome au protéome.}$

---

## A. Même génome… différents protéomes.

Sur l’image du dessus on peut constater un nombre énorme de protéines, 5 millions de protéines, pour 20 000 gènes codants. Comment ?

Une protéine avec la même séquence en AA qu’une autre va se différencier de cette dernière via des modifications post-traductionnelles : phosphorylation, …

L’étude du protéome permet de voir ces modifications, une réelle dynamicité du protéome existe et est observable.

<aside>
📎 La chenille et le papillon ont le même génome, mais pas le même protéome.

</aside>

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Spectrométrie%20de%20masse/Spectrométrie%20de%20masse%20f4bd033b6db34179a0da0546c04996af/Untitled%201.png)

## B. Analyse des protéomes et des transcriptomes.

### Pourquoi analyser les protéomes alors qu’analyser le transcriptome semble plus facile ?

Il n’y a pas de **relation de proportionnalité** entre le taux d’ARN et le taux de protéines. 

### Pourquoi peut-on analyser plus facilement les protéomes aujourd’hui ?

Il y a un enrichissement permanent des banques de données, les techniques de séparation des protéines s’améliorent, les outils de bio informatiques se développent et surtout la spectrométrie de masse s’améliore (résolution, vitesse de scan, …).

- Les banques de données protéiques sont de plus en plus riches.
- Les Techniques de séparation, de la preparation d’échantillons à la chromatographie s’améliorent de plus en plus.
- **Spectrométrie de masse : la résolution s’améliore et la vitesse de scan de plus en plus rapide.**

$\LARGE\textbf{\textsf{Chapitre II.}}\\\Large\textsf{La spectrométrie de masse.}$

---

La spectrométrie de masse permet la **détermination précise et sensible de la masse d’un analyte**. Cette information peut être utilisée pour déterminer l’identité et l’état chimique de la molécule d’intérêt. Les spectromètres de masse fonctionnent en convertissant les molécules d’analytes en formes chargées gazeuses. Grâce a l’application des potentiels électrostatiques, le rapport de la masse de chaque ion à sa charge (m/z) peut être mesuré.

C’est une méthode de mesure des rapports **masse sur charge (m/z)** de molécules individuelles et ionisées (**spectrométrie de masse moléculaire)** ou de complexe non covalents ionisés (spectrométrie de masse supramoléculaire). La molécule doit être ionisée car on travaille sur des champs électrostatiques (les molécules seront guidées par des courants électriques chargés + ou -).

## A. L’instrument : le spectromètre de masse.

### Fonctionnement.

Un spectromètre de masse mesure la masse de molécules isolées. Bien qu’une grande variété de techniques soit utilisée par les spectromètres de masse employés dans la pratique actuelle, tous comprennent trois composants essentiels : la source d’ions, l’analyseur de masse, et le détecteur.

1. **Volatiliser : c’est le rôle de la source.**
    
    Séparer les molécules les unes des autres : on passe de l’état de matière condensée à un état gazeux.
    
2. **Ioniser : c’est aussi le rôle de la source.**
    
    Transformer les molécules en ions: car un spectro de masse fonctionne grâce à des champs électriques.
    
3. **Mesurer les rapports m/z : c’est le rôle de l’analyseur.**
    
    La masse mol est calculée à partir du rapport masse/nb de charge (m/z).
    

La source permet l’obtention d’ions en phase gazeuse. L’interface, c’est une pièce entre la source et l’analyseur qui focalise (condense) et transmet les ions. 

La source est à pression atmos et l’analyseur à $10^{-12}$ atm. 

L’interface permet donc de réduire la pression avant d’arriver dans l’analyseur.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Spectrométrie%20de%20masse/Spectrométrie%20de%20masse%20f4bd033b6db34179a0da0546c04996af/Untitled%202.png)

### Les différents types de spectromètre de masse.

Les traits verticaux représentent les lentilles, qui permettent de guider les ions de la source, vers l’analyseur. 

V montre le différentiel de potentiel créé pour diriger les ions.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Spectrométrie%20de%20masse/Spectrométrie%20de%20masse%20f4bd033b6db34179a0da0546c04996af/Untitled%203.png)

### **Les techniques d’ionisation douce.**

L’obtention de la *******************source d’ions******************* représente la première étape critique dans l’analyse par spectrométrie de masse : la conversion de l’analyte en ions en phase gazeuse (ionisation). Jusqu’à récemment, les protéines ne pouvaient  pas être ionisées efficacement en raison de leurs poids moléculaires élevés et de leur faible volatilité. Cependant, le développement de techniques comme la ************************désorption/ionisation laser assistée par matrice (MALDI) et l’ionisation par électronébulisation (ESI)*** a permis de franchir cette importante barrière. 

En MALDI, l’analyte est évaporé à sec en présence d’un composé aromatique volatile (la matrice) qui peut absorber la lumière à des longueurs d’onde spécifiques. Une impulsion laser réglée sur l’une de ces longueurs d’onde excite et vaporise la matrice, convertissant une partie de l’analyte en constituant de la phase gazeuse. Les collision gazeuses qui en résultent permettent un transfert de charge intermoléculaire, ce qui ionise l’analyte.

En ESI, une solution de l’analyte est passée à travers une buse chargée électriquement. Des goutteletttes de l’analyte maintenant chargées, sortent de la buse dans une chambre à très basse pression, ce qui provoque l’évaporation du solvant et fournit finalement l’analyte ionisé.

---

Les ions d’analyte nouvellement formés entrent alors dans l’analyseur de masse, où ils sont différenciés sur la base de leurs rapports de masse-charge. Il y a un certain nombre de différents types d’analyseurs de masse. Dans cet exposé, nous considérerons une des plus simples, **l’analyse de masse par temps de vol** **(TOF)** dans lequel les ions sont accélérés à travers une chambre allongée sous un potentiel électrostatique fixe. Si on considère deux ions de charge nette identique, l’ion le plus petit mettra moins de temps à parcourir la chambre que l’ion le plus grand. La masse de chaque ion peut être déterminée en mesurant le temps requis pour chaque ion pour traverser la chambre.

### Spectrométrie de masse MALDI-TOF.

L’action de la source d’ions et de l’analyseur de masse permet une mesure très sensible de la masse d’ions potentiellement massifs comme ceux dérivés des protéines. Prenons l’exemple d’une source ions MALDI couplée à un analyseur de masse TOF : le spectromètre de masse MALDI-TOF. 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Spectrométrie%20de%20masse/Spectrométrie%20de%20masse%20f4bd033b6db34179a0da0546c04996af/Untitled%204.png)

Les ions en phase gazeuse produits par la source d’ions MALDI passent directement dans l’analyseur TOF, où les rapports masse-charge sont enregistrés. Dans la figure ci-dessous,  le spectre de masse MALDI-TOF d’un mélange de 5 pmol d’insuline et de 5pmol de B-lactoglobluline est représenté. Les masses déterminées par MALDI-TOF sont 5733.9 et 18 364, respectivement. Une comparaison avec les valeurs calculées de 5733.5 et 18388 montre que la MALDI-TOF est sans aucun doute un moyen précis de déterminer la masse des protéines.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Spectrométrie%20de%20masse/Spectrométrie%20de%20masse%20f4bd033b6db34179a0da0546c04996af/Untitled%205.png)

### **Les outils de l’analyse protéomique.**

On a pu parlé auparavant dans les TD de bioinfo ou en TBMC de la dégradation d’Edman présentée comme la méthode permettant d’identifier la séquence d’un peptide. La spectrométrie de masse de fragments peptidiques est une alternative à la dégradation d’Edman comme moyen de séquençage des protéines. Les outils d’analyse (TOF, Q, orbitrap, ..) permettent d’accéder à la séquence des peptides avec la **spectrométrie de masse en tandem** nommé **MS/MS.**

Les ions des protéines qui ont été analysés par un spectromètre de masse, nommé les ********************************ions précurseurs********************************, peuvent être coupés en plus petites chaînes peptidiques par bombardement avec des atomes d’un gaz inerte comme l’hélium ou l’argon. Ces nouveaux fragments, ou **********************************produits ioniques**********************************, peuvent être passés à travers un second analyseur de masse pour réaliser une caractérisation de masse supplémentaire. 

**⇒ L’utilisation de deux analyseurs de masses organisés de cette façon est appelée *spectrométrie de masse en tandem*.**

⇒ Le système mesure la masse de la molécule et, 2-3 ms ensuite, va fragmenter un ion en appliquant une énergie telle que la molécule va vibrer et se fragmenter au niveau de la liaison peptidique.

<aside>
📎 On peut également appliquer cette méthode à un mélange de protéines, que l’on digère avec une enzyme et on analyse la “soupe de peptides” obtenue.

</aside>

Fait important, les **fragments produits ioniques** (issus du précurseur) sont formés d’une façon chimiquement prévisible qui peut fournir des indices sur la séquence d’acides aminés de l’ion précurseur. Pour les analytes peptidiques, les produits ioniques peuvent être formés de telle sorte que des résidus de certains acides aminés sont clivés de l’ion précurseur. Ainsi une famille d’ions est détectée ; chaque ion représente un fragment du peptide d’origine ayant subi un soustraction d’un ou plusieurs acides aminés à une extrémité.

Les figures à droite nous montre un spectre de masse représentatif d’un peptide fragmenté. Les différences de masse entre les produits ioniques indiquent la séquence d’acides aminés de l’ion pepetide précurseur. 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Spectrométrie%20de%20masse/Spectrométrie%20de%20masse%20f4bd033b6db34179a0da0546c04996af/Untitled%206.png)

## B. Analyse des protéines : la protéomique.

A droite, à un échantillon de S. cerevisiae qui contient environ 6000 protéines. On va répliquer ce dernier pour résulter en plus de 60 000 protéines que l’ont va séparer par HPLC (chromatographie liquide).

On obtient pas 60 000 pics, on effectue une spectro de masse (après fragmentation des peptides) et on effectue une interprétation des données dans une BDD.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Spectrométrie%20de%20masse/Spectrométrie%20de%20masse%20f4bd033b6db34179a0da0546c04996af/Untitled%207.png)

### Des protéines particulières peuvent être identifiées par spectrométrie de masse.

La combinaison de la spectrométrie de masse avec les techniques chromatographiques et de clivage peptidique et décrites précédemment dans en TBMC permet une identification très sensible des protéines dans les mélanges biologiques complexes.

Quand une protéines est clivée par des procédés chimiques ou enzymatiques, une famille spécifique et prévisible de fragments peptidiques est formées. Nous avons appris que chaque protéines possède une séquence unique d’aminoacides précisément définie. Par conséquent, l’identité des peptides individuels formés à partir de cette réaction de clivage et, surtout, de leurs masses correspondantes, 

est une signature distincte de cette protéine particulière.

Le clivage de protéines, suivie d’une séparation chromatographique et d’une spectrométrie de masse, permet une identification et une quantification rapide de ces signatures, même si elles sont présentes à des concentration très faibles.

---

Comme exemple de la puissance de cette approche protéomique, considérons l’analyse du complexe du pore nucléaire de la levure qui facilite le transport des grosses molécules vers et hors du noyau. Cet énorme complexe macromoléculaire a pu être purifié à partir des cellules de levure sous une forme intacte en utilisant avec grand soin des techniques appropriées. 

→ Le complexe purifié a été fractionné par **HPLC**, puis par **électrophorèse en gel**. Les bandes individuelles du gel ont été isolées, clivées par la trypsine, et analysées par **spectrométrie de masse MALDI-TOF**. 

Les fragments produits ont été comparés à la masse correspondant aux séquences d’AA déduites des séquences ADN du génome de la levure comme cela est illustré dans la figure ci-dessus. 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Spectrométrie%20de%20masse/Spectrométrie%20de%20masse%20f4bd033b6db34179a0da0546c04996af/Untitled%208.png)

Un total de 174 protéines a été identifié de cette manière. On a pu confirmer par d’autres méthodes que 40 de ces protéines étaient effectivement des composants du complexe du pore nucléaire. Beaucoup de ces protéines n’avaient pas pu être identifiées préalablement comme étant associées au complexe du pore nucléaire, malgré des années de recherche. 

En outre, nous pouvons penser que les méthodes de spectro de masse sont suffisamment sensibles pour avoir détecté tous les composants du pore pourvu qu’ils aient été présents dans l’échantillon utilisé. 

### Identification des protéines.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Spectrométrie%20de%20masse/Spectrométrie%20de%20masse%20f4bd033b6db34179a0da0546c04996af/Untitled%209.png)

### Protéines à peptides.

On coupe les protéines à l’aide d’enzyme (**trypsine).**

Les peptides seront plus facile à analyser et fragmenter en MS/MS. L’analyse et le séquençage des peptides pour identifier les protéines aussi.

### Différentes applications.

- Caractérisation de marqueurs pathologiques (cibles diagnostiques).
    - Cancers,
    - Maladies neurologiques.
    - Cardiomyopathie.

- Analyse pharmaco-toxicologique.
    - Analyse différentielle (avec et sans médicaments) du protéome de différents tissus ou de fluides.
    - Analyse différentielle sur une famille de protéines (du foie pr ex.).

- Recherche de cibles primaires.
    - Bactériennes (protéines ribosomales, de la synthèse, des voies métaboliques…
    - Cibles thérapeutiques (cancer, maladie neuro).

- Analyse variétale en agronomie.

Bon ca soule, faut juste lire les très bonnes notes de cours ici :

⇒ [https://docs.google.com/document/d/1OeHGYUYvWsCLpjRAoH6f_23kAnCCRGvv/edit?rtpof=true](https://docs.google.com/document/d/1OeHGYUYvWsCLpjRAoH6f_23kAnCCRGvv/edit?rtpof=true)

![bubble-chat.png](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Spectrométrie%20de%20masse/Spectrométrie%20de%20masse%20f4bd033b6db34179a0da0546c04996af/bubble-chat.png)

$\Large\texttt{Commentaires}$

---

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Spectrométrie%20de%20masse/Spectrométrie%20de%20masse%20f4bd033b6db34179a0da0546c04996af/Untitled%2010.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20220923%20Spectrométrie%20de%20masse/Spectrométrie%20de%20masse%20f4bd033b6db34179a0da0546c04996af/Untitled%2011.png)

De nos jours, on travaille plus sur des Q-TOF et Q-Orbitrap.

---

$\Large\texttt{Fin de page}$
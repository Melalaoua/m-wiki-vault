---
Date : October 4, 2022 8:06 AM
---

up:: [[ImmunoHD]]
tags:: #academia/master, #master/ImmunologieHD



# *Exemple 1 d’étude omique en immunologie.*

*Le premier exemple c’est une étude faite dans le cadre du COVID.* 

# Identification of driver genes for critical forms of COVID-19 in a deeply phenotyped young patient cohort.

L’infection par le virus Sars-Cov-2 (ou par tout autre virus),  entraîne différents niveau de gravité de maladie, variable selon les personnes, une personne pouvait développer différent niveaux de sévérités de symptômes. Certaines personnes nécessitent d’être hospitalisées et d’avoir un apport d’oxygène et développement formes très graves (syndrome de détresse respiratoire aigü). A ce jour, nous n’arrivons toujours pas à expliquer pourquoi pour deux personne de même age, sexe, etc l’une développe des formes graves, et que l’autre non ? L’étude scientifique qui va suivre vis à répondre à cette question en étudiant plusieurs types de cas.

**Why do some young (<50y) patients, with no co-morbidities end-up developing a life threatening Acute Respiratory Distress Syndrome upon SARS-Cov-2 infection ?**

Pour réponde à ça, voilà les critères d’inclusion : uniquement moins de 50 ans sans co-morbidité, selection et étude faite lors de la première vague à Strasbourg

3 groupes : 

- Le groupe des patients critiques (47 personnes) : patients ayant besoin d’une ventilation mécanique en ICU.(réanimation)
- Le Groupes des **patients non-critiques (25 personnes) :** Hospitalisés dans un secteur conventionnel.
- Groupe **contrôle** : pas infectés mais qui matchent sur l’âge et le sexe des autres groupes.

### Multi-omics study design.

La stratégie de l’étude est de, pour ces 3 groupes de personnes, prélever différents liquides :

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled.png)

- **PBMC** (peripheral blood mononuclear cells) : cellules mononuclées du sang, comprend toutes les cellules immunitaires du sang. On va en général travailler sur ce support. Le sang d’un patient et prélevé et purifié par un gradient de densité.
- Plasma et Serum : la différence entre les deux ?
    - **Plasma :** Tube avec un anti-coagulant qui sera **plus riche en protéines.**
    - Serum : Sur un tube sec (à température ambiante) : la coagulation aura lieu et il y aura formation de caillot, on centrifuge.
    
    Pas vraiment de différence entre les deux, le plasma est plus riche en protéines (utile pour une étude protéomique).
    
- Sang total ; anticoagulant et non traité.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%201.png)

Les scientifiques ont effectué différentes analyses sur les prélèvements :

- PBMC : on étudie avec des méthode de résolution importante : **CITOP pour immunophenotyping et RNAseq pour obtenir transcriptome des cellules.**
- Plasma et serum : multiplex cytokine profiling (on observe toute les cytokines, pro- et anti-inflammatoire).

Le fil rouge de l’étude est de comprendre pourquoi des patients ayant des profils médicaux similaires, développent des formes très différentes de maladie via une infection au COVID-19.

<aside>
📎 Ces analyses vont servir à identifier des voies de signalisation, des gènes candidats (gènes drivers) qui vont provoquer cet état inflammatoire aigu.

</aside>

Les données par RNA-seq vont servir pour des approches statistiques ****afin d’essayer de déceler des signatures statistiques qui permettraient de classifier au mieux les patients critiques et non-critiques. Le but est de trouver la signature qui sépare le mieux ces deux populations. 

---

### Immune profiling.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%202.png)

La première approche, c’est **l’immunophenotyping couplé à une cytométrie de masse.** On utilise des anticorps dirigés vers des marqueurs spécifiques de populations immunitaires. Cette immunophenotyping a permit de distinguer 37 populations différentes, le niveau de détail est important.

<aside>
📎 Méthode cytométrie couplée à spectrométrie de masse. Pas besoin de flurophore (utilise des Ac lié à des métaux lourds). Une fois le marquage fait : spectromètre qui mesure la masse de chaque métaux.

</aside>

### Global view of the cellular profiles.

La première chose regardée : est-ce que globalement il y a une **lymphopénie** chez les patients critiques ? 

⇒ Ils observent que c’est le cas.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%203.png)

Ils ont ensuite cherché à savoir si il y a une signature t-SNE différente chez les différents groupes. 

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%204.png)

Il y a bien une signature spécifique à chaque groupe.

### La réponse en interféron de type I.

La réponse en interferon de type I est grandement impactée chez les patients critiques, comme le démontrent ces résultats.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%205.png)

Le nombre de pDC, plus grandes sécrétrices en interféron, est plus faible chez les patients critiques. 

Un défaut en IFN$\alpha$ réduit drastiquement au fur et à mesure des jours chez ces même patients.

Enfin, deux patients en conditions critiques possèdent des **anticorps anti-IFN$\alpha$, bloquant la réponse antivirale.**

$$
Cytokine\ storm.
$$

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%206.png)

En dosant les cytokines chez les différentes populations, ils ont pu voir par technique luminex un dosage de plusieurs cytokines en même temps et donc un phénomène cytokines storm chez les patients critiques.  Les quantités de cytokines pro-inflammatoires étaient augmentées.

### The immune modifications are independant of the viral infection per se.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%207.png)

Un dosage des anticorps anti-sars-cov-2 a été fait chez les 3 populations, on remarque pas de différences significatives entre les critiques et non critiques.

### Mass-spectrometry-based plasma proteome profiling.

On peut obtenir un autre niveau d’analyse via la spectrométrie de masse sur PBMC. On observe le PBMC des patients.  

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%208.png)

Cette technique marche sur un très petit volume. Le PBMC est analysé par **NANOLC-MS/MS**. Est-ce que des protéines sont plus exprimées dans un groupe que dans l’autre ?

Avec cette technique, ils ont réussi à doser environ 1000 protéines dans le PBMC. 

Une première analyse de la composante principale permet de voir une bonne ségrégation des 3 groupes.

Ci-dessous la signature protéomique globale. Les 3 groupes ont des signatures un peu commune mais on voit bien des déficiences pour certaines protéines, notamment la **calportectine** qui est un marqueur bien connu de détresse respiratoire.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%209.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%2010.png)

On réalise aussi un **volcano-plot** qui permet de voir toute les protéines exprimée par une cellule comparée à une autre protéine.

- A gauche les protéines down-régulée.
- A droite les protéines up-régulées.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%2011.png)

### Combined transcriptomics and proteomics analysis supports inflammatory pathways associated with critical disease.

On combine toute nos données et on voit ce qui est commun entre différentes approches. En prenant trois types d’approches.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%2012.png)

### Integrated ensemble AI/ML and probabilistic programming discovers a robust gene expression signature that differentiate critical from non-critical patients.

**Comment on détermine une signature transcriptomique via les données en RNA-seq ?**

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%2013.png)

Ils ont réalisé un training data (**machine learning**) sur 80% du set de données obtenus par RNAseq afin d’établir un modèle qui sera testé sur les 20% du dataset restant. **Cette étape est réalisée 100 fois**.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%2014.png)

Voilà les résultat pour 7 algorithmes ML/AI différents (incluant le quantum SVM). 100x test on été réalisés. Ils ont obtenu 600 gènes dont l’expression est bien spécifique à des formes critiques.

### Structural Causal Modeling of top600 most informative genes.

Ils ont réalisés un réseau causal entre les 600 gènes identifiés.

Les gènes les plus à gauche sont des **gènes drivers** : ce sont eux qui activent le signal qui vont jouer sur les gènes à leur droite. Tout ces gènes à gauche sont donc à priorit les plus importants dans des voies de signalisation. Sur les 5 gènes drivers, ils ont observé si l’expression est plus exprimée dans les différents cas de nos 3 populations. C’est le cas.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%2015.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%2016.png)

# What is ADAM9 ?

La protéine ADAM9 est semble t’il la protéine la plus influente et la plus importante dans le déclenchement des cas critique. Quel est son rôle dans le déclenchement d’un tél état de maladie ?

C’est une **protéine membranaire sécrétée dans le milieu par clivage, une métallo-protéase à différents rôles, elle est ubiquitaire et intervient dans beaucoup de voies.** Deux publications étaient connue mettant en lien la protéine ADAM9.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%2017.png)

→ L’une montrait l’implication d’ADAM9 dans l’entrée d’un autre virus.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%2018.png)

→ Une autre étude a étudié l’interactome de toute les protéines virales et qui a montré que ADAM9 interagissait avec les protéines du COVD19.

### ADAM9 protease activity is increased in critical patients.

Ils ont réalise une mesure de l’activité protéolytique de ADAM9 (sa capacité à cliver des protéines). Ils ont mesuré la dose de MICA soluble, le nombre chez les paeitns critiques était plus haut.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%2019.png)

<aside>
⚠️ A priorit ADAM9 est plus active dans les formes critiques.

</aside>

### Infection tests after silencing of ADAM9.

Une étude du rôle d’ADAM9 dans l’entrée du virus est réalisée par les scientifiques.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%2020.png)

Un silencing de la protéine (répression du gène) est réalisé chez une population de cellules, qu’on infecte au COVID-19 (même protocole réalisé pour un contrôle).

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%2021.png)

### eQTL in the promoter of ADAM9.

***eQTL : recherche d’un variant qui a un impact sur l’expression d’un gène.***

Ils ont observé un polymorphisme du gène chez les patients critiques, est-ce que ce polymorphisme explique une expression plus forte de ADAM9 ? (oui)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%2022.png)

### Conclusion de l’étude.

- L’usage de plusieurs techniques d’études omiques permettent une bonne charactérisation chez un groupe de jeune personnes qui ont subit les syndrômes graves de la maladie.
- L’étude a permit d’étudier un grand nombre de changement moléculaires ayant lieu dans le sang des patients atteints d’un syndrome de détresse respiratoire.
- L’usage de AI/ML était très utile dans la charactérisation de la proteine ADAM9.
- ADAM9 est un nouveau potentiel candidat pour diagnostiquer la maladie et une potentielle cible thérapeutique.

## Seconde étude :

Deuxième exemple : complètement différent mais intéret imunologique

Maladie qui est le syndrome hyper IgD qui est auto-inflammatoire

Analyse qui imlpiquait plusieurs techniques omiques.

Maladie rare auto-inflammatoire caractérisée par des épisodes récurrents de fièvres associé à des syndrome inflammatoires un peu moins spcifiques. Dans le cas de ce syndrome hyper IGd à un niveau d’iGD plus élevé dans le sang. Rôle pas bien connue dans cette pathologie.

Au niveau génétique : maladie bien caractérisée : autosomique récessive causée par des variants alléliques d’un gène MVK. Une mutation bien connue pos 377 qui est présente chez de nombreux patients. 

Bien défini alors pourquoi on s’y intéresse ? 

Le cas intéressant identifié c’est lcette famille suivie par des collègues à COlmar qui présentaient un cas d’éhrédité assez classique. La S1 a la mutation hétérozifote mais qui n’est pas malade à l’inverse de S2 ? POurquoi une différence phénotypique ?

Bon cas d’étude pour rélver plus d’acteurs dans cette maladie.

Première chose regardée : est-ce que biologiquement il y a un état inflammatoire dans S2 par rapport S1 ? On dose trois cytokines pro-Inf et montré que effectivement que dans S2 il y a syt plus de cytokines pro-inf . Biologiquement il se passe quelque chose.

On a réaluse une approche multi-moiques : 

- analyse génomique : séquençage d’exome complet.
- RNA-seq
- Protéomique.

Profil multi-omique intégré de chacune des personne.

Première analyse faite : l’exome : faite uniquement sur les parents et les deux soeurs et eventuellement sur le frère sain hétérozygote mais il a refusé.

Contrôle qualité des données d’exome: le point important est surligné; le nombre de variant indentifié par rapport au génom e de ref qui tourne autour de 50 000. Et aussi la profondeur moyenne qui est en général à 100X. Chaque position du génome est vue au moins 100x.

Sur ces données d’exomes : on peut restreindre aux candidats spécifiques soit d’une Soeur ou de l’autre et qui peuvent être impliqué dansl a variation. Etape de filtration pour montrer que dès 50K variants , identifiés chez S2 ou S1, on peut établir à la fin de ces filtres une liste de variants spécifiques à S1 ou S2. Car dans un cas on peut soit trouver dans S2 des variants qui ont augmenté son phénotype ou dans l’autre (S1) des variants qui ont compensé le phénotype sain.

Le soucis du filtre c’est qu’on obtient 2000 variants spécifiques pouvant expliquer le phénotype dans un sens comme dans l’autre. C’est là que ca devient intéressant de faire d’autres omiques.

On ajoute une analyse une transcriptomique et

On prends le sang de ces deux soeurs, pour faire un PBMC et les mettre en culture. On rajoute du LPS d’origine bactérienne qui peut mimer une inflamation.  

D’abord transcriptomique : on effectue des zanalyse différentielle : on regarde ce qui est up-régulé et down régulé. La S1 est toujours en référence. On regarde les gènes les plus exprimés.

Ensuite protéomique : on récupère des extraits protéomiques des PBMC puis séparé par un gel 1D et syst on découpe toute la ligne pour prendre toute les protéines, après digestion tryptique des pepetides, on séapre ça par chromatographie liquide et spectro de masse.

Si on fait ça pour nos deux S1 et S2, on va pouvoir doser chaque protéine et si on compte chaque spectre MS/MS on obtient une analyse quantitative et différentielle entre ces deux soeurs.

D’autres types d’analyses faites pour voir un peu comment ségrégait

MCIA analyse en composante principale qui permet de vérifier une certaine homogénéité sur la gobalité des données.

![bubble-chat.png](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/bubble-chat.png)

$\Large\texttt{Commentaires}$

---

<aside>
⚠️ Dans le up-régulé : deux voies de signalisation importante : une première dans la coagulation et une autre dans la dérégulation des cellules myoglobines.

</aside>

*Rôle ubiquitaire de ADAM9*

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221004%20%20Cours%20d'introduction/Cours%20d'introduction%20852a62d7aff44d589174da5b3bb3fa82/Untitled%2023.png)

Silencing : injection d’un siRNA bloquant le transcrit du gène.

---

$\Large\texttt{Fin de page}$
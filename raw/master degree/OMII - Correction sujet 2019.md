
tags:: #master/Omiques 

1. Donner la définition d'un polymorphisme

- Un polymorphisme est une variation présente dans la population avec une fréquence supérieure à 1% et non bénigne

> Correction : Un polymorphisme en génétique est une variation de la séquence d'ADN qui peut se produire à différents endroits dans le génome. C'est une variation normale et naturelle qui contribue à la diversité génétique d'une population. Il peut avoir un impact sur l'apparence physique d'un individu, sa susceptibilité à certaines maladies ou sa réponse à certains médicaments.


2. Les techniques de séquençage à haut débit permettent de séquencer en parallèle des millions de séquences d’un patient. Parmi les notions importantes, on liste la profondeur de lecture et la couverture. Expliquer ces 2 termes et détailler leur utilité.

- La profondeur de lecture, c'est le nombre de fois qu'une même base à été lue par le séquenceur à une position définie. Plus la profondeur est élevée, plus les résultats à une position donnée est fiable.

> Correction : La profondeur de lecture et la couverture sont deux termes clés en génomique, particulièrement dans le séquençage à haut débit. La profondeur de lecture fait référence au nombre de fois qu'une base particulière est lue pendant le séquençage. Plus la profondeur de lecture est élevée, plus la confiance dans l'identification de cette base est grande. C'est particulièrement utile pour détecter des variantes rares ou des erreurs de séquençage. La couverture, quant à elle, fait référence à la proportion du génome qui a été séquencée. Une couverture de 100% signifie que chaque base du génome a été lue au moins une fois. Plus la couverture est élevée, plus la probabilité de détecter toutes les variantes génétiques est grande. Ces deux termes sont donc essentiels pour évaluer la qualité et la fiabilité d'un séquençage.

3. L'analyse des données issues du séquençage à haut débit requiert l'utilisation de la bioinformatique. Citez les 4 grandes étapes d'une pipleine bioinformatique.


### Sujet N2 - Protéomique.
1. Expliquez brièvement les principes des ionisations Electrospray et MALDI.
- Electrospray : l'analyte traverse, en solution, une buse chargée, ceci a pour conséquence de charger l'analyte qui se transforme à l'état de gaz à la sortie de la buse, ce ioniseur est très utile couplée à une chromatographie liquide.
- MALDI : l'analyte est incorporé avec une matrice, l'excitation de cette matrice par un laser provoque une ionisation de l'analyte à l'état de ion.

>Correction : L'ionisation Electrospray est une méthode qui produit des ions à partir d'une solution liquide. Elle se fait en pulvérisant la solution à travers une pointe métallique sous haute tension pour créer une brume de gouttelettes chargées. Les gouttelettes se réduisent par évaporation jusqu'à ce qu'un ion soit éjecté. Quant à MALDI (Matrix-Assisted Laser Desorption/Ionization), c'est une technique d'ionisation douce utilisée en spectrométrie de masse. Un laser est utilisé pour ioniser les échantillons qui sont mélangés dans une matrice absorbant les UV. L'énergie du laser est absorbée par la matrice et provoque la désorption et l'ionisation de l'échantillon. Les deux sont des techniques d'ionisation douces, ce qui signifie qu'elles peuvent ioniser des molécules sans les fragmenter, ce qui est utile pour l'analyse de molécules grandes et complexes comme les protéines.


2. Schématisez un spectre obtenu par Electrospray-MS d'une protéine d'une part et un spectre obtenu par MALDI-MS d'une protéine d'autre part.

> Correction : L'Electrospray-MS et le MALDI-MS sont deux techniques de spectrométrie de masse utilisées pour analyser les protéines. L'Electrospray-MS te donne un aperçu de la distribution de charge de ta protéine. Plus la protéine est chargée, plus elle sera déviée lors de l'analyse, ce qui se traduit par un rapport m/z (masse sur charge) plus faible sur ton spectre. C'est donc une technique très utile pour comprendre comment ta protéine interagit avec son environnement. D'un autre côté, le MALDI-MS te donne une image plus directe de la masse de ta protéine. Dans cette technique, la protéine est ionisée par un laser et généralement, seule la forme mono-chargée est observée. Donc, tu obtiendras un spectre avec un seul pic majeur qui correspond à la masse de la protéine. Ces deux techniques sont complémentaires car elles te fournissent des informations différentes sur ta protéine. L'Electrospray-MS te donne des informations sur la charge de la protéine, tandis que le MALDI-MS te donne des informations sur la masse de la protéine. En utilisant ces deux techniques, tu peux obtenir une image très complète de ta protéine.

3. Décrivez la stratégie d'identification des protéines à partir de données LC-MS/MS.
> La stratégie d'identification des protéines à partir de données LC-MS/MS est assez complexe. Elle implique l'utilisation de chromatographie liquide couplée à la spectrométrie de masse en tandem (LC-MS/MS). En gros, les protéines sont d'abord digérées en peptides, qui sont ensuite séparés par LC. Chaque peptide est ensuite fragmenté dans le spectromètre de masse pour produire un spectre de masse qui est unique à ce peptide. Ces spectres sont ensuite comparés à une base de données de spectres théoriques dérivés de séquences de protéines connues. Si un match est trouvé, la protéine d'origine peut être identifiée. C'est un processus hautement technique et délicat, mais incroyablement puissant pour l'identification des protéines.

4. 
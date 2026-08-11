

**La nouvelle version de ce document inclut maintenant l’interprétation des CNV intragéniques et des variants de l’ADN mitochondrial.**


==Les recommandations décrites dans ce document ne sont applicables qu’aux gènes clairement impliqués dans la pathologie pour laquelle l’analyse a été effectuée. Si un variant est identifié dans un gène pour lequel le niveau de preuve de son implication dans la pathologie concernée est insuffisant, la classification maximale attribuable à ce variant est « VSI » (Variant de Signification Incertaine)==

Ce document ne s’applique qu’aux maladies à transmission mendélienne et aux maladies mitochondriales.

L’interprétation des résultats consiste à combiner (cf. Annexe 1) ces arguments pondérés afin d’assigner une des 5 classes suivantes au variant étudié : Classe 1 : Variant bénin Classe 2 : Variant probablement bénin Classe 3 : Variant de signification incertaine Classe 4 : Variant probablement pathogène Classe 5 : Variant pathogène


==Introduction de la possibilité d’une « modulation de poids » pour certains arguments== : Dans le cadre de l’évolution des recommandations, la notion de « modulation de poids » a été introduite pour certains arguments. Ainsi, certains items auparavant associés à un poids unique (par exemple PM3 : poids moyen) peuvent actuellement être utilisés avec un niveau de détail supplémentaire en fonction des éléments disponibles, et ainsi une « modulation de poids », avec les conséquences associées à la classification finale du variant (par exemple : le poids « moyen » par défaut de PM3 peut ainsi être modulé en poids fort « PM3_fort » ou faible « PM3_faible »).


==BA1== : Fréquence allélique > 5% (ou définie par le laboratoire). Critère suffisant à lui seul en faveur du caractère bénin du variant. ~~Diminution du seuil pour différentes pathologies (voir tableau 2.)~~

==BS1== : Fréquence allélique trop importante par rapport à la fréquence de la pathologie. ==Demander à Sam pour calcul==

==PM2== : Variant absent des bases de données de populations contrôles (ou très faible fréquence si récessif)
>*Devant l’existence d’un grand nombre de variants très rares mais bénins, les recommandations de ClinGen SVI Working Group (publiées en Septembre 2020 33) proposent de diminuer le poids de PM2 en « faible », accompagné par une modification de calcul final de critères (PVS1 + un PP = classe 4 ou lieu de PVS1 + un PM = classe 4). Comme d’autres modifications futures de calcul ont été évoquées dans ces recommandations, notre GT a décidé que l’implémentation de diminution de PM2 en poids « faible » est encore prématurée.*

![[Pasted image 20240612131347.png]]


==PS4==  ASSOCIER CLINVAR | PS4_moyen | PS4_faible : le variant est présent chez différents patients non-apparentés ET la fréquence allélique de ce variant dans la population générale est compatible avec la prévalence et la pénétrance de la maladie (BS1 n’est pas attribué à ce variant)

PS4 : Prévalence du variant chez les individus atteints significativement supérieure à celle des contrôles • études cas-témoins avec Odd Ratio > 3, borne inférieure de l’intervalle de confiance excluant 1

- En l’absence d’études cas-contrôles, il est possible de moduler le poids de l’argument PS4 en fonction du nombre de patients non-apparentés confirmés avec ce variant : PS4, PS4_moyen (argument modulé en poids modéré, PM), PS4_faible (argument modulé en poids faible, PP). Le nombre de patients nécessaires doit être défini en fonction du gène et de la pathologie étudiés. Pour compter le nombre de patients porteurs du variant, il est nécessaire de consulter l’ensemble des bases données de patients (ClinVar, LOVD, bases spécifique) et faire une recherche bibliographique extensive. Le nombre de patients porteurs du variant en question n’inclut pas le patient en cours d’analyse.

- Il est proposé de n’utiliser l’argument PS4 que pour les gènes responsables des pathologies dominantes et d’utiliser l’argument PM3 pour les pathologies récessives

- Cette façon d’attribuer PS4 n’est possible que si le variant à classer est extrêmement rare dans la population générale. Pour des maladies à pénétrance incomplète ou à révélation tardive, le poids PM2 peut être attribué à un variant même quand il existe quelques occurrences de ce variant en population générale. Ainsi, pour ces variants, il est possible de combiner les scores PM2 et le PS4/PS4_moyen/PS4_faible.

==Suite à la recommandation de ClinGen 6 , les critères PP5 (Source documentée classant le variant comme pathogène) et BP6 (Source documentée classant le variant comme bénin) ont été retirés de la grande majorité des recommandations gène-spécifiques.==



PP4_moyen, PP4 : Phénotype ou histoire familiale spécifique en faveur de la pathologie associée au gène comprenant le variant.
==A voir plus tard==


PM3_fort, PM3, PM3_faible : pour une pathologie à transmission autosomique récessive, un variant observé en trans avec un variant pathogène sur le même gène
==Pour décisionnaire

- L’argument PM3 n’est valable que pour les variants avec une fréquence allélique compatible avec la prévalence et la pénétrance de la maladie (donc à condition que BS1 ne soit pas attribué).

- Tableau 4 : Calcul du score PM3 pour un variant observé en trans avec un variant pathogène dans la situation d’une pathologie de transmission autosomique récessive.
![[Pasted image 20240612133614.png]]


PS2_tres_fort, ==PS2==, PM6, PM6_faible : Variant de novo chez un patient sans antécédent familial (le poids de l’argument est à attribuer en fonction de la confirmation de la paternité/maternité et en fonction de la spécificité du phénotype).
==Première couche agent génétique et seconde couche agent décisionnaire==

- Calcul du score PS2 de novo
![[Pasted image 20240612142535.png]]

- Le critère de novo (PM6 ou PS2) ne peut être utilisé que si le phénotype du patient est concordant.
- • Le critère PS2 peut être modifié en PM ou PP si le variant est en mosaïque avec une représentation tissulaire cohérente avec le phénotype


PP1_fort, PP1_moyen, PP1 : Variant co-ségrégeant avec la pathologie chez plusieurs membres atteints dans la même famille et/ou dans plusieurs familles (le poids de l’argument est à attribuer en fonction du nombre de ségrégations)

- Voir calcul sur pdf.


BS2 : Variant observé chez un individu sain pour une maladie récessive (variant homozygote ou variants hétérozygotes composites), dominante (variant hétérozygote) ou récessive liée à l'X (variant hémizygote chez un garçon), avec une pénétrance complète attendue à un âge précoce.

BS4 : Variant ne ségrégeant pas avec la pathologie chez des apparentés atteints

- • Seuls des individus bien phénotypés peuvent être considérés pour l’attribution du l’argument BS2 (ne pas utiliser les données de population).


PVS1 PVS1_fort PVS1_moyen PVS1_faible : Variant ayant un effet nul prédit (non-sens, frameshift, site canonique d’épissage (±1,2), codon d’initiation de la traduction, délétion d’un ou plusieurs exons hors phase, délétion d’un ou plusieurs exons en phase mais emportant un domaine fonctionnel) dans un gène où la perte de fonction est un mécanisme pathogène connu.
==Si pas de champs OMIM, faire quand même l'analyse par IA, si classification > VSI : rétrograder en VSI
- L’argument PVS1 n’est valable que pour les gènes avec un lien « gène-pathologie » bien établi 
- L’argument PVS1 n’est valable que pour les gènes où la perte de fonction est un mécanisme pathogène connu.
- Si l’intolérance d’un gène aux variants de type « perte de fonction » n’a pas encore été évaluée par un groupe d’experts, elle peut être estimée en utilisant les scores pLI (probability of Loss of function Intolerance) et o/e (observed/expected) disponibles dans gnomAD. Un gène est considéré comme intolérant à la perte de fonction si sa pLi est supérieure ou égale à 0,9. 
- PVS1 ne peut pas être combiné avec l’argument PP3 (Effet d’un variant prédit délétère par l’ensemble des logiciels de prédiction de pathogénicité interrogés). ==PVS1 > PP3==

![[Pasted image 20240612143703.png]]

PM4 : Variant affectant la longueur de la protéine (Indels en phase, perte du codon stop) modulation du poids de l’argument : le poids de l’argument en faveur de la pathogénicité du variant est inversement proportionnel à la taille résiduelle de la protéine.

BP3 : Variant affectant la longueur de la protéine, si l’altération est en phase dans une région répétée sans fonction connue.


PP2 Variant faux-sens dans un gène avec un faible taux de variants faux-sens bénins et dans lequel les variants faux-sens sont un mécanisme fréquemment responsable de la pathologie. 

BP1 Variant faux-sens dans un gène où seuls les variants tronquants sont décrits comme associés à la pathologie. 

BP7 Variant synonyme sans impact prédit sur l’épissage ET pour lequel la séquence nucléotidique n’est pas très conservée chez les vertébrés.

A REMETTRE PS1 : Variant à l’origine du même changement d’acide aminé qu’un variant pathogène connu, sauf si le nouveau variant a un possible effet sur l’épissage. Le poids de l’argument peut être modulé en « modéré » si le variant connu est classe 4.

PM5 Variant à l’origine d’un changement d’acide aminé différent à la même position qu’un variant fauxsens pathogène connu.

Rajouter Interpro  PM1 Variant non-tronquant situé sur un hot spot mutationnel et/ou un domaine fonctionnel critique bien établi exempt de variants bénins.

PP3 Effet d’un variant prédit délétère par l’ensemble des logiciels de prédiction de pathogénicité interrogés.

BP4 Effet d’un variant prédit bénin par l’ensemble des logiciels de prédiction de pathogénicité interrogés.

• PP3 ne peut pas être combiné avec l’argument PVS1.

PS3 Etudes fonctionnelles in vivo ou in vitro bien établies montrant un impact délétère du variant sur le gène ou son produit.

BS3 : Etudes fonctionnelles in vivo ou in vitro bien établies montrent un impact non délétère du variant.
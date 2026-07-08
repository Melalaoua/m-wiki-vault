tags:: #master/Omiques 
enseignant:: C.Carapito


https://www.udacity.com/course/data-analysis-with-r--ud651

nextprot : protéomique sur l'homme dans les maladies
human protéine atlas


Le **protéome** : Un protéome est la totalité des protéines exprimées par un système biologique, à un moment donné, dans des conditions spécifiques.

L'**analyse protéomique** : L'identification, la quantification systématique d'un système biologique (cellules, tissus, organes, fluides biologiques, organisme) à un point donné.

- détermination de l'identité des protéines,
- leur abondances,
- leur modifications post-traductionnelles (glycolyse, phosphorylation, ...)

Connaître le génome d'un organisme n'est pas suffisant, il faut comprendre les mécanismes biologiques, cela passe souvent par l'étude du protéome

![[Pasted image 20231027192521.png]]

L'analyse protéomique est possible de nos jours grâce à 3 révolutions :
1. L'accès aux séquences génomiques de beaucoup d'organismes pour un coût réduit. Les séquences génomiques sont [[GE05+GE07 - Génétique de la bioinformatique|automatiquement annotées]] et les séquences protéiques prédites.
2. Développement de [[Purification des protéines et marquage|techniques de purification]] (électrophorèse, chromatographies, etc...)
3. [[Spectrométrie de masse|Spectrométrie de masse]]

![[Pasted image 20231027192916.png]]

### Différentes approches en protéomiques :
#### L'aproche bottom-up.
1. L'approche bottom-up en protéomique est une méthode d'identification des protéines qui implique leur digestion en peptides avant l'analyse par spectrométrie de masse.
2. Elle est la méthode la plus couramment utilisée en protéomique.
3. Elle permet d'identifier une grande quantité de protéines en une seule fois.
4. Le processus commence par l'extraction des protéines à partir d'un échantillon, suivi par leur digestion en peptides.
5. Ces peptides sont ensuite séparés par chromatographie liquide avant d'être analysés par spectrométrie de masse.
6. Les spectres de masse obtenus sont utilisés pour identifier les peptides, et donc les protéines d'origine.
7. L'approche bottom-up permet une identification précise des protéines, mais elle ne fournit pas d'informations sur leurs modifications post-traductionnelles.
8. C'est une méthode rapide et efficace, mais elle nécessite un équipement sophistiqué et une expertise technique.
9. Elle est souvent utilisée en combinaison avec d'autres techniques de protéomique, comme l'approche top-down, pour obtenir une image plus complète de la protéomique d'un échantillon.
10. Enfin, bien qu'elle soit puissante, l'approche bottom-up a ses limites, notamment le fait qu'elle ne permet pas d'identifier les protéines de faible abondance.

![[Pasted image 20231027193547.png]]


### Stratégie d'identification pour NanoLC-MS-MS.
---
![[Pasted image 20231027193816.png]]


1. Le couplage d'une Chromatographie liquide avec une spectrometre de masse permet de limiter la perte de signal et permet l'analyse de structure plus complexes.
2. Gain en spécificité comparé à la PMF grâce à la fragmentation de l'information
# Edition du génôme.

Date: September 2, 2021 10:32 AM
Semaine: 4
Travaillé ?: Yes
Unité d'enseignement: TIG

Editer un génome c'est effectuer des insertions, des délétions ou des modification du génôme au niveau de sites spécifiques de ce dernier.

L'édition de génôme s'est amplifiée par l'appartion d'une nouvelle biotechnologie : **CRISPR/cas9** ; Clustered Regularly interspaced Short Palindromic Repeats.

Un outil simple et rapide à mettre en oeuvre :

- Reproduire des maladies génétiques chez les animaux modèles.
- Recherche fondamentale (imagerie, contrôle transcriptionnel..).

### Origine du système CRISPR/Cas.

---

Crispr/cas est à l'origine un système de défense immunitaire (50% des bactéries et 90% des arachaeabactéries) équivalent à l'immunité adaptative des vertébrés.

Le système permet d'acquérir une mémoire d'un envahisseur assurant ainsi une défense rapide et robuste de l'organisme lors d'une nouvelle agression par ce même envahisseur.

Il permet de se défendre contre les virus et bactériophages, spécialement guidé par de l'ARN (complémentarité de séquence).

**Organisation du locus CRIPSR-Cas.**

![Untitled](Edition%20du%20ge%CC%81no%CC%82me%20b548b06684c646778922a43458c1a117/Untitled.png)

### Plusieurs types de systèmes CRISPR/Cas.

---

Les systèmes diffèrent en fonction du nombre plus ou moins important de protéines Cas.

![Untitled](Edition%20du%20ge%CC%81no%CC%82me%20b548b06684c646778922a43458c1a117/Untitled%201.png)

### Mise en place de l'immunité CRISPR chez les bactéries.

---

![Untitled](Edition%20du%20ge%CC%81no%CC%82me%20b548b06684c646778922a43458c1a117/Untitled%202.png)

### Le système CRISPR Cas9.

---

![Untitled](Edition%20du%20ge%CC%81no%CC%82me%20b548b06684c646778922a43458c1a117/Untitled%203.png)

### 1ère étape de l'immunité CRISPR/Cas9.

---

La première étape est la **détection et intégration** de l'ADN étranger dans le locus CRISPR ou acquisition.

Lors d'une première infection, un fragment de l'ADN génomique de l'envahisseur, appelé protospacer, est intégré dans le locus CRISPR/cas.

![Untitled](Edition%20du%20ge%CC%81no%CC%82me%20b548b06684c646778922a43458c1a117/Untitled%204.png)

Les protéines **Cas1-Cas2 et Cas 9** sont impliquées dans la **sélection et l'intégration du protospacer**. 

- La protéine Cas9 **reconnaît spécifiquement** dans l'ADN de l'envahisseur un set de nucléotides, le **motif PAM** (NGG) adjacent au protospacer.

- L'intéraction de Cas9 avec le motif PAM permet de sélectionner le protospacer. Ce **motif PAM ne sera pas conservé** dans le locus CRISPR bactérien (ceci évite l'autoimmunité).

---

L'ADN étranger, après détection, est ensuite intégré ou acquis dans le locus CRISPR.

Le protospacer est intégré entre le leader et le premier repeat du locus CRISPR.

<aside>
📎 Il y a ensuite duplication du repeat de façon à conserver une alternance entre repeat et spacer.

</aside>

![Untitled](Edition%20du%20ge%CC%81no%CC%82me%20b548b06684c646778922a43458c1a117/Untitled%205.png)

### 2nde étape de l'immunité CRISPR/Cas9.

---

![Untitled](Edition%20du%20ge%CC%81no%CC%82me%20b548b06684c646778922a43458c1a117/Untitled%206.png)

Suite au clivage, il y a  **production de molécules sentinelles** par formation d'un complexe ribonucléoprotéique composé de la protéine Cas9 et des 2 ARN : le crRNA et le tracrRNA.

La seconde étape consiste à **transcripter le locus CRISPR** qui a précédemment intégré le protospacer de l'ADN étranger.

L'hybride pré-cRNA/tracrRNA est stabilisé par la protéine Cas9 , une RNase III coupe l'ARN au niveau du repeat et raccourci par une exonuclease.

**Molécule sentinelle.**

![Untitled](Edition%20du%20ge%CC%81no%CC%82me%20b548b06684c646778922a43458c1a117/Untitled%207.png)

### 3ème étape de l'immunité CRISPR/Cas9.

---

![Untitled](Edition%20du%20ge%CC%81no%CC%82me%20b548b06684c646778922a43458c1a117/Untitled%208.png)

**Le clivage se fait par l'endonucléase Cas9.**

L'endonucléase Cas9 est constituée de 2 domaines HNH et RvuC ayant une activité nucléase (chaque domaine coupe un brin d'ADN) et d'un domaine de fixation au motif PAM.

<aside>
📎 La molécule sentinelle composée du tracrRNA hybridé au crRNA et de la protéine cas9.

</aside>

Chaque domaine catalytique est représenté par des ronds verts pour le site HNH et rouge pour le RuvC. Le crRNA est hybridé à la séquence cible sur l'ADN. Le motif PAM est indiqué en vert.

![Untitled](Edition%20du%20ge%CC%81no%CC%82me%20b548b06684c646778922a43458c1a117/Untitled%209.png)

### L'outil CRISPR-Cas9 et édition de l'ADN.

---

Le remarquable travail des scientifiques consitait à **adapter** le système CRISPR/Cas9 au système eucaryote. De ce fait ils ont :

- **Ajouté** un **NLS** (signal de localisation nucléaire) à la protéine Cas9.
- **Optimisé** les codons pour avoir une traduction efficace de l'ARN messager dans la cellule eucaryote.
- **Simplifié** le système Cas9 : utilise dorénavant **un seul ARN** : l'ARN guide (**sgRNA : single guide RNA**) composé d'une région s'hybridant à l'ADN (partie du crRNA) et d'une région du tracrRNA permettant à Cas9 de se fixer.

![Untitled](Edition%20du%20ge%CC%81no%CC%82me%20b548b06684c646778922a43458c1a117/Untitled%2010.png)

**Comment un mécanisme qui coupe l'ADN peut-il être utilisé pour muter l'ADN ?**

### L'outil CRISPR-Cas9 et édition de l'ADN.

---

Les machineries de réparation des coupures double brin de l'ADN.

CRISPR/Cas9 se sert de son avantage pour casser les doubles brins en deux quelques nucléotides avant le motif PAM. La réparation de l'ADN fait intervenir deux mécanismes :

![Untitled](Edition%20du%20ge%CC%81no%CC%82me%20b548b06684c646778922a43458c1a117/Untitled%2011.png)

Le Nonhomologous end-joining (**NHEJ**) et le homology-directed repair (**HDR**).

Les NHEJ peuvent être ligaturé sans brins homologues tandis que les cassure HDR requiert un brin matrice.

NHEJ est un mécanisme de réparation très efficace mais susceptible à de fréquentes mutations due à l'insertion ou délétion (INDELS) de nucléotides.

HDR est considéré comme le mécanisme dominant de réparation du fait de sa précision mais souffre d'une efficacité faible.

CRISPR déclenche les mécanisme endogènes de réparation de l'ADN introduisant une modification génomique ciblée. 

### L'outil CRIPSR-Cas9 et édition de l'ADN.

---

On génère un **modèle murin** en une étape par CRISPR/CAS9.

![Untitled](Edition%20du%20ge%CC%81no%CC%82me%20b548b06684c646778922a43458c1a117/Untitled%2012.png)

![Untitled](Edition%20du%20ge%CC%81no%CC%82me%20b548b06684c646778922a43458c1a117/Untitled%2013.png)

### Prix Nobel.

---

Prix Nobel obtenu par **Emmanuelle Charpentier et Jennifer Doudna**. La plupart des pays européens ont ratifié la convention pour la Protection des droits et de la dignité de l'être humain en rapport avec l'application de la biologie et de la médecine qui interdit strictement la manipulation du génome des cellules germinales humaines quand ces manipulations sont dans le cadre de procréation médicalement assistée.

***→ Suite [La transcription des gènes bactériens.](https://www.notion.so/La-transcription-des-g-nes-bact-riens-4d692777832e463fb66f7feb0cd81a84)***
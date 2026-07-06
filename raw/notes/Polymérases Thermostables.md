---
Date : October 19, 2022 8:45 AM
---

up:: [[TBMC]]
tags:: #academia/master, #master/Techniques



# I. Rappels.

### Fonction des polymérases.

Les polymérases assurent la réplication et la maintien du génome, il en existe deux sortes : ADN et ARN polymérases.

### Activité ADN polymérase.

Dans les noyau des eucaryotes, pour la majorité, la polymérase a une action 5’ à 3’.

Elle permet la formation de liaison phosphodiester entre le OH en 3’ et un phosphate en 5”

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/Untitled.png)

### Activité exonucléasique 3’ à 5’.

L’ADN polymérase effectue un ************proofreading************ :

- Si mésappariement, excision du dernier nucléotide inséré en 3’ OH, et nouvelle synthèse. Cette activité permet une copie fidèle du brin.

### Activité exonucléasique 5’ à 3’.

Cette fonction permet de :

- Retirer les nucléotides insérés en 5’ des ADN db et hybrides ARN/ADN.
- Rôles in vivo :
    - Excision des amorces ARN des fragments d’Okazaki du brin secondaire.
    - Excision de TT.

On peut s’en servir à marquer des sondes : ces techniques servent en biologie moléculaire afin de détecter des séquences spécifiques d’ADN.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/Untitled%201.png)

### Polymérases : pourquoi ?

**Hybridation simple :**

- Simplicité, rapidité.
- marquage radioactif, enzymatique, fluorescent.
- Mais une Sensibilité : > $10^4$ copies ce qui est insuffisant.

******Solutions :******

- Amplification du signal (ADN branché) → Méthode type hybridation moléculaire : amplification du signal grace à la polymérase.
- Amplification de la séquence cible (PCR et autres) : moins utilisé (plutôt la PCR).

# II. Polymérases thermostables.

### Polymérase Thermostables : pourquoi ?

Premières amplification d’ADN :

- Polymérase de Klenow : ADN pol de E. coli 5’ → 3’ sans activité polymérase (pour éviter la destruction des fragments néo-synthétissés, mais la fonction de l’ADN pol reste rudimentaire).
- Hybridation et élongation à 37°C : peu spécifique.
- Détruite à chaque dénaturation : ajout d’une enzyme fraiche à chaque cycle.

PCR : K. Mullis en 1983 : amplification d’un facteur de $10^9$ en 30 cycles.

### ADN polymérase thermostables d’eubactéries.

---

Type : **polymérase Taq** (Thermus aquaticus).

- Pas d’activité proof-reading.
- 1/2 vie à 92°C : 2h, et 95°C : 45 min.
- Activité maximale à 72°, 50% à 60°C.
- Activité exonucléasique 5’→ 3’:
    - Marquage par nick translation.
    - PCR temps réel avec sonde TaqMan.
    - PAS d’amplification par déplacement de brin.

La Taq permet une incorporation d’une adénine en 3’ OH : clonage de fragments PCR dans vecteur avec une thymine en 5’.

Incorporation dUTP : système anti-contamination (séquence amplifiée contient des T, en amplifiant, on prends les U et donc l’amplicon ne contient que des bases U). Pour être sûr qu’on a pas pollué la nouvelle réaction, on utilise une méthode qui ne sélectionne que les amplicons à détruire.

---

---

Type : **Polymérase Tli** (Thermus litoralis).

- Activité exonucléasique 3’→5’ : fidélité mais risque de dégradation des amorces.
- PAS d’activité exonucléasique 5’ → 3’ :
    - Amplification par déplacement de brin
    - Pas pour PCR temps réel avec sonde TaqMan.

→ Fragments PCR à bords francs.

→ L’incorporation de dUTP inhibe la PCR.

---

### Fidélité des ADN pol thermostables.

***************Capacité à incorporer le bon nucléotide : activité de relecture.***************

⇒ Taux d’erreur de la Taq : $10^{-3}-10^{-6}$

⇒ La Pfu est 10 fois plus fidèle.

### Amélioration des ADN polymérases thermostables.

- Augmentation de la spécificité : Hot-start, anticorps anti-Taq.
- Amélioration de l’amplification : DMSO, formamide.
- Polymérase modifiées ou chimériques :
    - Activité exonucléase 5’ → 3’ : NH2 terminale.
    - Activité polymérase : C terminale.
- Mélange de polymérases : Taq/Pfu, Taq/Tli

### Bilan des ADN polymérases thermostables.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/Untitled%202.png)

# **III. Principes et applications.**

### PCR.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/Untitled%203.png)

**Rendement de la PCR.**

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/Untitled%204.png)

**Optimisation PCR.**

- Choix des amorces (GC%, dTm, repliement, complémentarité..).
- Choix enzyme : Taq, Tth, Pfu…
- Optimisation tampon, agents chimiques…

### PCR nichée.

### **PCR spécifique d’allèles.**

### RT-PCR.

### Nucleic Acid Sequence Based Amplification.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/Untitled%205.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/Untitled%206.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/Untitled%207.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/Untitled%208.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/Untitled%209.png)

### **PCR en temps réel : pourquoi ?**

⇒ **Besoins :**

- Quantification acides nucléiques.
- Détection mutation.
- Méthodes simples, rapides et reproductibles.

⇒ **Inconvénients de la PCR classique :**

- Analyse en gel, hybridation, ELISA, HPLC…
- DGGE, SSCP…

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/Untitled%2010.png)

**Principe : détection et quantification (semi, relative, absolue) d’un signa fluorescent émis proportionnel à la qte d’ADN amplifié.**

Avantages : 

- Réalisation en tube fermé.
- Gain en rapidité, en temps de manipulation.
- Multiplexage.
- Capacité.
- Quantification +rapide, +précise, +reproductible et plus simple que la PCR.

Inconvénients : 

- Coûts équipement.
- Coût consommables.

Usage d’agents intercalants (**SYBR Green**, BET) ou de sondes (sonde d’hybridation comme FRET, sonde d’hydrolyse comme TaqMan)

### PCR en temps réel : quantification.

Permet de quantifier l’ADN répliqué.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/Untitled%2011.png)

### Technologie SYBR green.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/Untitled%2012.png)

### Sondes de FRET.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/Untitled%2013.png)

### **Sondes TaqMan.**

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/Untitled%2014.png)

![bubble-chat.png](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/bubble-chat.png)

$\Large\texttt{Commentaires}$

---

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/Untitled%2015.png)

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/Untitled%2016.png)

### Ligase chain Reaction.

![Untitled](Pro/Scholar/no01.%20Notes/01%20S1/TBMC/20221019%20Polymérases%20Thermostables/Polymérases%20Thermostables%207932d2ad3e5742cfa551c5a300f5daa1/Untitled%2017.png)

---

$\Large\texttt{Fin de page}$
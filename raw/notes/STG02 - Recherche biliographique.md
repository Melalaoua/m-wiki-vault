tags:: #master/StageS4 


### Mise en contexte (à réserver pour le rapport de stage).

Au sein du Nouvel Hôpital Civil se trouve l'unité de bioinformatique médicale appliquée au diagnostic. L'unité de bioinformatique (UF) est principalement dédiée au traitement des applications de séquençage à haut débit (NGS) des autres unités du pôle de biologie. Les objectifs de l'UF sont les suivants :
-  Assurer et maintenir la routine diagnostique.
- Assurer les développements bioinformatiques à même de soutenir l'évolution des besoins dans les laboratoires et l'implémentation de technologies de pointes en bioinformatique dans le domaine médical.
- Assurer la formation et le support pour ses utilisateurs.
- Assurer la formation et l'encadrement de stagiaires et des internes.
L'UF possède l'accréditation des examens de biologie selon la norme ISO 15189 et les autres normes en vigueur dans les Laboratoires de Biologie Médicale.

L'UF est en étroite interaction avec les différentes unités du pôle de biologie à savoir : département de génétique moléculaire des cancers, génétique oncologique, laboratoire d'hématologie, laboratoire de biochimie et de biologie moléculaire, unité de cytogénétique chromosomique et moléculaire, unité de diagnostic préimplantatoire, unité de génétique de l'infertilité, unité de génétique moléculaire.

La routine diagnostique de l'UF repose principalement sur la pipeline STARK (Stellar Tools from raw sequencing data Analysis to variant  RanKing) qui est un outil dédié à l'analyse des données de séquençage haut-débit et dont l'objectif est d'aider à l'interprétation des résultats pour le diagnostic clinique.

En d'autres termes, STARK récupère les fichiers bcl produits par les séquenceurs pour générer les fichiers fastq  (reads), fichiers BAM (alignements des reads) et les fichiers vcf (appel et annotation des variants) et quelques rapports d'analyse (résumé des résultats obtenus, contrôle qualité, statistiques et traçabilité de l'analyse)


 Ici sont prit en charge différents patients atteints de maladies génétiques rares comme le syndrome de Bardet-Biedl, les déficiences intellectuelles, myopathies, dystrophies, ...


Il existe plus de 7000 maladies rares, touchant 3 millions de Français (4,5%) et responsable de 10% des décès entre 1 et 5 ans. 

Special maladie neuro-sensorielle, neuro-musculaire et neuro-développement

séquençage d'un panel de gène.

pipeline STARK : 
VaRANK :


L'explosion cambrienne [[The Falcon Series of Open Language Models|(Almazrouei et al. 2023)]] des Large Language Models (LLMs), encore en cours aujourd'hui, a été marquée par l'arrivée de chatGPT ([OpenAI, 2022](https://openai.com/blog/chatgpt))  rapidement suivie par son successeur, GPT-4 ([OpenAI, 2023](https://arxiv.org/abs/2303.08774)). Les modèles LLM reposent sur l'architecture transformers ([Vaswani et al, 2017](https://arxiv.org/abs/1706.03762)), les modèles populaires comme GPT, Falcon ([[The Falcon Series of Open Language Models|Almazrouei et al, 2023]]) et plus "récemment" le modèle français Mistral ([[Mixtral of Experts|Jiang et al., 2023]]) sont toutefois constitués que de la partie décodeur de cette architecture, ils sont communément appelés "decoder-only".

Un fort engouement pour les modèles LLM s'est manifesté  depuis la publication de chatGPT. L'intérêt fort suscité a permit la publication de multiples papiers visant à intégrer les LLM dans divers milieux professionnels. 

Ce stage s'inscrit dans cette même démarche d'intégrer les intelligences artificielles dans le milieu médical au Nouvel-Hôpital Civil de Strasbourg, en bioinformatique dans le secteur diagnostique des maladies génétiques rares.


### Large Language Models.
L'explosion récente des modèles LLM a en premier lieu apporté une révolution en Natural Language Processing (NLP), mais ce n'est pas le seul milieu qui a pu profiter de leur apports non considérable (cf. Applications).  

Cette révolution est due à la haute scalabilité de l'architecture transformer ([Vaswani et al, 2017](https://arxiv.org/abs/1706.03762)). L'augmentation de la puissance de calcul des ordinateurs , des quantités croissantes des données mise à disposition pour l'entrainement des modèles et  les modèles transformers naturellement affins pour la multiplication de larges matrices (GeMM, [Zhang et al. 2019](https://arxiv.org/abs/1909.10616)). 

#### Gros modèles, grosses données.
Les LLM sont de très gros modèles de langage,  ayant été entrainés sur des quantités massives de données. Ils prennent en entrée un texte et produisent une prédiction des mots qui suivent l'entrée . L'architecture transformer ([Vaswani et al, 2017](https://arxiv.org/abs/1706.03762)) sur laquelle reposent ces modèles est complexe, mettant en jeu des mécanismes de self-attention, j'invite à une lecture du papier ou les sources indiquées en annexes pour mieux comprendre la particularité de cette architecture.

#### Modèles LLMs "pre-trained"
Les modèles AI pre-trained  ([[Improving Language Understanding by Generative Pre-Training|Radford et al., 2018]]) sont des modèles entrainés sur énormément de données diversifiées, les données ne sont pas liées à un domaine ou une tâche particulière, ils sont "task-agnostic". 

Il est cependant tout à fait possible, et conseillé, d'entrainer en supplément le modèle pre-trained sur des données autour d'un domaine ou d'une tâche précise, comme sur des données de médecine par exemple, dans ce cas là, le modèle est "fine-tuned", la méthode la plus populaire de training et/ou fine-tuning étant le Reinforcement Learning from Human Feedback (RLHF, [[Deep Reinforcement Learning from Human Preferences|Christiano et al, 2017]],[[Training a Helpful and Harmless Assistant with Reinforcement Learning from Human Feedback|Bai et al., 2022]]). 

Les modèles pre-trained seuls ont des performances très élevées lorsqu'ils sont évalués sur des benchmarks  populaires comme le MMLU ([[Measuring Massive Multitask Language Understanding|Hendrycks et al, 2020]]), WebQuestions [Berant et al. 2013](https://www.semanticscholar.org/paper/Semantic-Parsing-on-Freebase-from-Question-Answer-Berant-Chou/b29447ba499507a259ae9d8f685d60cc1597d7d3) . Il existe aussi des benchmark en médecine : PubMedQA ([Jin et al, 2019](https://arxiv.org/abs/1909.06146)), MedQA ([Jin et al, 2020](https://paperswithcode.com/paper/what-disease-does-this-patient-have-a-large)).


#### Emergent abilities.
Un étonnant phénomène a été découvert par la mise en place de modèles LLM de tailles de plus en plus conséquentes qui est l'apparition de capacités émergentes ([[Emergent Abilities of Large Language Models|Wei et al, 2022]]).Une capacité émergente, dans le cadre des IA, est une  capacité absente chez des petits modèles mais présente chez des modèles plus larges.

 Au fur et à mesure que des modèles de plus en plus gros (en nombre de paramètres) sont entrainés sur des données de plus en plus larges (en nombre de tokens, 1000 tokens = 750 mots), le phénomène d'emergent abilities opère à un seuil critique où, une fois ce dernier dépassé, le modèle développe de nouvelles capacités de manière soudaine et non prévisible. Parmis ces capacités on retrouve : arithmétique, réponse aux questions, résumer de texte, etc... Les LLMs développent ces capacités en observant des quantités massives de données, il n'est donc pas étonnant de les voir exceller dans des domaines sur lesquelles ils n'ont pas été entrainés. 
 
![[Pasted image 20240201154436.png]]

### Applications des IA
Les modèles LLM peuvent être en supplément fine-tuned pour répondre à des critères précis. C'est le cas de chatGPT (architecture GPT-3), qui a été fine-tuned pour la discussion. 

Des tentatives d'intégration de GPT-4 ([OpenAI, 2023](https://arxiv.org/abs/2303.08774)) dans divers milieu ont été réalisés, les résultats sont très prometteurs pour la suite. GPT-4 est le modèle le plus puissant connu au moment de la rédaction de ce rapport. 

Ci-dessous je présente certaines applications de LLM dans les champs de la génétique, la médecine et de diverses autres corps de métiers. Ces exemples ne souligne pas assez la diversité et la quantité impressionnantes de tentatives d'application des IA et la révolution de rupture qu'elles peuvent potentiellement devenir, à tout les niveaux de notre société. Toutefois ces exemples viennent soutenir de manière solide la stratégie adoptée pour le stage effectué au NHC de Strasbourg.

#### Génétique.
De récentes études démontre l'efficacité des LLM dans les champs de la génétique. Un modèle a été développé afin de prédire les structures secondaires et tertiaires à partir d'une séquence primaire ([[Evolutionary-scale prediction of atomic-level protein structure with a language model|Lin et al, 2024]]) résultant en la publication d'un atlas de structure protéique prédite issues de 617 millions de séquences protéiques en métagénomique.

#### Clinique.
Beaucoup de recherche a été effectuée dans l'intégration de GPT-4 comme assistant clinique dans le diagnostic clinique de patients ([[Towards Accurate Differential Diagnosis with Large Language Models|McDuff et al, 2023]], [[Accuracy of a Generative Artificial Intelligence Model in a Complex Diagnostic Challenge|Kanjee et al, 2023]], [[Capabalities of GPT-4 on Medical Challenge Problems|Nori et al., 2023]]). GPT-4 est un modèle SOTA depuis son implémentation, beaucoup de modèles open-source parvienne à concurrencer le modèle, sans encore parfaitement atteindre ses performances.

Les résultats de GPT-4 dans ces études sont concluants. Dans le papier [[Towards Accurate Differential Diagnosis with Large Language Models|McDuff et al, 2023]]


### Clinique.



### Secteur Diagnostique

#### Bardet-Biedl




### Système et Projet de Recherche
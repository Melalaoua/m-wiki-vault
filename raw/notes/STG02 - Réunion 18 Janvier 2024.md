tags:: #master/StageS4 

### Recherche bibliographique.

#### Contexte

- A porté exclusivement sur les AI (le bio n'a pas encore été abordé) allant des fondamentaux, modèles, prompting, mais aussi applications des IA dans la médecine.

- La vague d'IA telle qu'on la connaît se concentre principalement sur les LLM, reposant sur l'architecture des [[attention is all you need|transformers]]. Les LLMs sont entrainés sur des quantités massives de données non labellisées et non restreintes qu'à un seul domaine comme on aurait pu le faire dans de l'entrainement supervisé/non-supervisé. Le papier [[Improving Language Understanding by Generative Pre-Training]] démontre qu'un LLM "pre-trained", c-à-d entrainé sur des données non labellisées, présente de meilleurs résultats qu'un modèle qui sera entrainé spécifiquement dans un but précis, sur des données restreintes à la tâche. Le modèle pre-trained est ensuite fine-tuned pour une tâche précise sur des données précises. 

- Ceci peut s'expliquer d'une part par la **scalabilité** de l'architecture Transformers permettant à ces derniers d'êtres entrainés sur des quantités <u>massives</u> de données (ex : [[The Falcon Series of Open Language Models|Falcon]] entrainé sur 3 500 milliards de tokens),  d'une autre part de la mise à disposition de jeu de données de haute qualité sur lesquels entrainés ces LLM (RefinedWeb pour Falcon), et enfin de l'évolution exponentielle de nos méthodes de calculs ([[Loi de Moore]]) permettant d'héberger des modèles de plus en plus puissants.

- Des modèles larges comme les LLM développent des [[Emergent Abilities of Large Language Models|aptitudes émergentes]]



#### 2023 : Explosion Cambrienne de modèles

- Liste des modèles open-source publié en 2023 : ==LLaMA== (by Meta) in February, ==StableLM== (by StabilityAI) and ==Pythia== (by Eleuther AI) in April, ==MPT== (by MosaicML) in May, ==X-GEN== (by Salesforce) and ==Falcon== (by TIIUAE) in June, ==Llama 2== (by Meta) in July, ==StableLM v2 ==(by StabilityAI) in August, ==Qwen== (by Alibaba) and ==Mistral== (by Mistral.AI) in September, ==Yi== (by 01-ai) in November, ==DeciLM== (by Deci), ==Phi-2==, and ==SOLAR== (by Upstage) in December.

![[Pasted image 20240118101303.png|1200]]


#### Applications

- [[Evolutionary-scale prediction of atomic-level protein structure with a language model]]  :  LLM 15B entrainé pour prédire la structure secondaire et tertiaire des protéines, publication d'un atlas de structure protéique prédites à partir de séquence protéique métegénomique  https://esmatlas.com/
![[Pasted image 20240118104140.png]]

- [[Autonomous chemical research with large language models]] : Développement de Co-Scientist - une pipeline reposant sur GPT-4 capable de design, planifier et exécuter des expériences de laboratoire en chimie.
![[Pasted image 20240118104202.png]]

- [[Towards Accurate Differential Diagnosis with Large Language Models]] : LLM reposant sur l'architecture Palm-2
![[Pasted image 20240118110029.png]]
![[Pasted image 20240118110055.png]]
![[Pasted image 20240118110624.png]]

- [[BioGPT Generative Pre-trained Transformer for Biomedical Text Generation and Mining]]

- Evaluation de GPT-4 dans le médical : [[Capabalities of GPT-4 on Medical Challenge Problems]], [[Accuracy of a Vision-Language Model on Challenging Medical Cases]]
![[Pasted image 20240118111124.png]]![[Pasted image 20240118111257.png]]




#### Partie Technique

##### QUEL MODELE CHOISIR ?
- A mon opinion : [[The Falcon Series of Open Language Models]] ou [[Mixtral of Experts]] sont les meilleurs candidats (open-source) :
	- [Falcon ](https://huggingface.co/blog/falcon): Modèle 40B : tourne sur une A6000.
	- [Mistral 7B  et Mistral 7Bx8](https://docs.mistral.ai/models/) ![[Pasted image 20240118114241.png]]
- Explication de la [Quantization](https://huggingface.co/docs/transformers/v4.35.0/llm_tutorial_optimization)
 
##### DATA.
Comment structurer nos données ?
- La base de données relationnelles ne serait que très peu scalable et ne refleterais pas la réalité des relations entre les données.
- Une base de données en [[Knowledge Graph]] ?
- Une base de données  en [[Vector Databases|vecteurs]]

##### LEGAL.
- [[Notes sur l'AI ACT|AI ACT]]

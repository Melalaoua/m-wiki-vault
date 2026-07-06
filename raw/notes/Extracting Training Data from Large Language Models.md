**authors**:: Nicholas Cartini, Florian Tramèr, Eric wallace, Matthew Jagielski, Ariel Herbert-Voss, Katherine Lee, Adam Roberts, Tom Brown, Dawn Song, Ulfar Erlingsson, Alina Oprea, Colin Raffel
**date**::   ```2024-01-06 10:45 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI - vulnerabilities
**sous-groupe**:: #AI/vulnerabilities
**pertinence**:: 6
**links**:: 
**modification date**:: ```Saturday 6th January 2024 10:45:40 ```

```ad-abstract
It has become common to publish large (billion parameter)
language models that have been trained on private datasets.
This paper demonstrates that in such settings, an adversary can perform a training data extraction attack to recover individualtraining examples by querying the language model.
We demonstrate our attack on GPT-2, a language model
trained on scrapes of the public Internet, and are able to extract hundreds of verbatim text sequences from the model’s training data. These extracted examples include (public) personally identifiable information (names, phone numbers, and email addresses), IRC conversations, code, and 128-bit UUIDs. Our attack is possible even though each of the above sequences are included in just one document in the training data. We comprehensively evaluate our extraction attack to understandthe factors that contribute to its success. Worryingly, we find that larger models are more vulnerable than smaller models. We conclude by drawing lessons and discussing possible safeguards for training large language models.
```

## Notes
- Les privacy leakage sont associés à des problèmes d'overfitting.

- Les LLMs sont entrainés sur des quantités massives de données, dédupliquées, parfois utilisée seulement sur une epoch. On peut donc penser que les LLMs ont très peu de risque de leak les données. Ce papier prouve le contraire.

- Ce papier montre que les LLM sont capables de se "souvenir" des données utilisées pour l'entrainement, étant donc vulnérables à des Privacy Leakage. Ceci est très important à prendre en compte pour des entrainer des modèles dans le biomédicale, reposant sur les données cliniques de patients.

- Comment un modèle a une "mémoire" ? Le papier tente une formalisation de la définition de "mémoire" chez les LLM. 
	-  ==Eidetic Memorization of Text== : ce sont les données mémorisées par le modèle bien qu'elles soient apparus que très peu de fois dans les données d'entrainement. Moins la donnée est présente, plus sa mémoire eidetic est forte. 
	- ==Définition de la capacité d'extraction d'une information par un modèle== : Un string s est extractable par un LM si il existe un prefix c tel que :  ![[Pasted image 20240106110922.png]]

- Data secrecy : La forme la plus directe de fuite de données a lieu lorsque les données sont extraites directement depuis le LM qui a été entrainé à partir de données confidentielles. Le papier donne un example avec le modèle d'autocomplétion de Gmail où se dernier a été directement entrainé sur des conversations d'utilisateurs.

- Les LM posent un problème d'infractions de la vie privée lorsque les données mémorisées sont, successivement extraites du modèle, et utilisées en dehors de leur cadre d'utilisation initial.

- 

```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
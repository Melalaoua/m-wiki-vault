**authors**:: [Sander Schulhoff](https://arxiv.org/search/cs?searchtype=author&query=Schulhoff,+S), [Jeremy Pinto](https://arxiv.org/search/cs?searchtype=author&query=Pinto,+J), [Anaum Khan](https://arxiv.org/search/cs?searchtype=author&query=Khan,+A), [Louis-François Bouchard](https://arxiv.org/search/cs?searchtype=author&query=Bouchard,+L), [Chenglei Si](https://arxiv.org/search/cs?searchtype=author&query=Si,+C), [Svetlina Anati](https://arxiv.org/search/cs?searchtype=author&query=Anati,+S), [Valen Tagliabue](https://arxiv.org/search/cs?searchtype=author&query=Tagliabue,+V), [Anson Liu Kost](https://arxiv.org/search/cs?searchtype=author&query=Kost,+A+L), [Christopher Carnahan](https://arxiv.org/search/cs?searchtype=author&query=Carnahan,+C), [Jordan Boyd-Graber](https://arxiv.org/search/cs?searchtype=author&query=Boyd-Graber,+J)
**date**::   ```2024-01-19 10:15 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI - vulnerabilities
**sous-groupe**:: #AI/vulnerabilities  
**pertinence**:: 5
**links**:: https://arxiv.org/abs/2311.16119
**modification date**:: ```Friday 19th January 2024 10:15:54 ```

```ad-abstract
Large Language Models (LLMs) are deployed in interactive contexts with direct user engagement, such as chatbots and writing assistants. These deployments are vulnerable to prompt injection and jailbreaking (collectively, prompt hacking), in which models are manipulated to ignore their original instructions and follow potentially malicious ones. Although widely acknowledged as a significant security threat, there is a dearth of large-scale resources and quantitative studies on prompt hacking. To address this lacuna, we launch a global prompt hacking competition, which allows for free-form human input attacks. We elicit 600K+ adversarial prompts against three state-of-the-art LLMs. We describe the dataset, which empirically verifies that current LLMs can indeed be manipulated via prompt hacking. We also present a comprehensive taxonomical ontology of the types of adversarial prompts.
```

## Notes

- Une prompt est un texte en language naturel qui donne une instruction à suivre aux LLM.

Le Papier définit de manière non exhaustive 6 catégories de Prompt Hacking :

#### Prompt Leaking.
Processus de récupérer la hidden prompt  ([[Ignore Previous Prompt - Attack Techniques For Language Models|papier]]) 

#### Training Data Reconstruction
Exfiltrer les données d'entrainement du modèle. ([[Extracting Training Data from Large Language Models|papier]])


#### Harmful Information Generation
Générer des informations potentiellement dangereuses, le [[Ignore Previous Prompt - Attack Techniques For Language Models|hijacking goal]] est un subset.


#### Token Wasting
L'attaque utilise les tokens de l'hebergeur, lui faisant dépenser argent et/ou ressources de calcul. ([[Prompt Injection attack against LLM-integrated Applications|papier]])



### Résultats du concours.
Je liste que les stratégie réussies

- **Two Token Attack** : ils ont simplement rajouté "key :", le LLM a divulgué sa clé.

- Chinese chracters : un caractère en mandarin possède plus d'informations qu'un caractère en latin.


```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
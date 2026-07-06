**authors**:: Ethan Perez, Douwe Kiela, Kyunghyun Cho
**date**::   ```2024-01-06 09:16 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI - vulnerabilities
**sous-groupe**:: #AI/vulnerabilities  #AI/prompting
**pertinence**:: 2
**links**:: 
**modification date**:: ```Saturday 6th January 2024 09:16:46 ```

```ad-abstract
Pretrained language models (LMs) perform well on many tasks even when learning from a few examples, but prior work uses many held-out examples to tune various aspects of learning, such as hyperparameters, training objectives, and natural
language templates (“prompts”). Here, we evaluate the few-shot ability of LMs when such held-out examples are unavailable, a setting we call true few-shot learning. We test two model selection criteria, cross-validation and minimum description length, for choosing LM prompts and hyperparameters in the true few-shot setting. On average, both marginally outperform random selection and greatly underperform selection based on held-out examples. Moreover, selection criteria often prefer models that perform significantly worse than randomly-selected ones. We find similar results even when taking into account our uncertainty in a model’s true performance during selection, as well as when varying the amount of computation and number of examples used for selection. Overall, our findings suggest that prior work significantly overestimated the true few-shot ability of LMs given the difficulty of few-shot model selection.
```

## Notes
- Ce papier semble décrire une technique d'évaluation des modèles sur une méthode déjà existante : [[Few-shot Prompting]]
 

```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
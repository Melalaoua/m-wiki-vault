**authors**:: [Shunyu Yao](https://arxiv.org/search/cs?searchtype=author&query=Yao,+S), [Jeffrey Zhao](https://arxiv.org/search/cs?searchtype=author&query=Zhao,+J), [Dian Yu](https://arxiv.org/search/cs?searchtype=author&query=Yu,+D), [Nan Du](https://arxiv.org/search/cs?searchtype=author&query=Du,+N), [Izhak Shafran](https://arxiv.org/search/cs?searchtype=author&query=Shafran,+I), [Karthik Narasimhan](https://arxiv.org/search/cs?searchtype=author&query=Narasimhan,+K), [Yuan Cao](https://arxiv.org/search/cs?searchtype=author&query=Cao,+Y)
**date**::   ```2024-01-22 15:41 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI - PROMPTING
**sous-groupe**:: #AI/prompting 
**pertinence**:: 8
**links**:: https://arxiv.org/abs/2210.03629
**modification date**:: ```Monday 22nd January 2024 15:41:57 ```

```ad-abstract
While large language models (LLMs) have demonstrated impressive capabilities across tasks in language understanding and interactive decision making, their abilities for reasoning (e.g. chain-of-thought prompting) and acting (e.g. action plan generation) have primarily been studied as separate topics. In this paper, we explore the use of LLMs to generate both reasoning traces and task-specific actions in an interleaved manner, allowing for greater synergy between the two: reasoning traces help the model induce, track, and update action plans as well as handle exceptions, while actions allow it to interface with external sources, such as knowledge bases or environments, to gather additional information. We apply our approach, named ReAct, to a diverse set of language and decision making tasks and demonstrate its effectiveness over state-of-the-art baselines, as well as improved human interpretability and trustworthiness over methods without reasoning or acting components. Concretely, on question answering (HotpotQA) and fact verification (Fever), ReAct overcomes issues of hallucination and error propagation prevalent in chain-of-thought reasoning by interacting with a simple Wikipedia API, and generates human-like task-solving trajectories that are more interpretable than baselines without reasoning traces. On two interactive decision making benchmarks (ALFWorld and WebShop), ReAct outperforms imitation and reinforcement learning methods by an absolute success rate of 34% and 10% respectively, while being prompted with only one or two in-context examples. Project site with code: [this https URL](https://react-lm.github.io)
```

## Notes
Voir [[ReAct]]

![[Pasted image 20240122154531.png]]

![[Pasted image 20240122154724.png]]



```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
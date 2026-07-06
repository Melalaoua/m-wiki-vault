**authors**:: [Fábio Perez](https://arxiv.org/search/cs?searchtype=author&query=Perez,+F), [Ian Ribeiro](https://arxiv.org/search/cs?searchtype=author&query=Ribeiro,+I)
**date**::   ```2024-01-19 10:24 ```
**tags**::  #papiers/stageS2 
**groupe**:: AI - vulnerabilities
**sous-groupe**:: #AI/vulnerabilities 
**pertinence**:: 5
**links**:: https://arxiv.org/abs/2211.09527
**modification date**:: ```Friday 19th January 2024 10:24:11 ```

```ad-abstract
Transformer-based large language models (LLMs) provide a powerful foundation for natural language tasks in large-scale customer-facing applications. However, studies that explore their vulnerabilities emerging from malicious user interaction are scarce. By proposing PromptInject, a prosaic alignment framework for mask-based iterative adversarial prompt composition, we examine how GPT-3, the most widely deployed language model in production, can be easily misaligned by simple handcrafted inputs. In particular, we investigate two types of attacks -- goal hijacking and prompt leaking -- and demonstrate that even low-aptitude, but sufficiently ill-intentioned agents, can easily exploit GPT-3's stochastic nature, creating long-tail risks. The code for PromptInject is available at [this https URL](https://github.com/agencyenterprise/PromptInject).
```

## Notes

Our work highlights the importance of studying prompt injection attacks and provides insights on
impacting factors. We believe that our work can help the community better understand the security
risks of using LLMs and design better LLM-powered applications. Our main contributions are the
following:
1. We study prompt injection attacks against LLMs and propose a framework to explore such attacks.
2. We investigate two specific attacks: goal hijacking and prompt leaking.
3. We provide an AI x-risk analysis of our work (Appendix A).

![[Pasted image 20240119102731.png]]



```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
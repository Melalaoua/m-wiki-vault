**authors**:: [Takeshi Kojima](https://arxiv.org/search/cs?searchtype=author&query=Kojima,+T), [Shixiang Shane Gu](https://arxiv.org/search/cs?searchtype=author&query=Gu,+S+S), [Machel Reid](https://arxiv.org/search/cs?searchtype=author&query=Reid,+M), [Yutaka Matsuo](https://arxiv.org/search/cs?searchtype=author&query=Matsuo,+Y), [Yusuke Iwasawa](https://arxiv.org/search/cs?searchtype=author&query=Iwasawa,+Y)
**date**::   ```2024-01-23 10:28 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI - PROMPTING
**sous-groupe**:: #AI/prompting 
**pertinence**::  5
**links**:: https://arxiv.org/abs/2205.11916
**modification date**:: ```Tuesday 23rd January 2024 10:28:43 ```

```ad-abstract
Pretrained large language models (LLMs) are widely used in many sub-fields of natural language processing (NLP) and generally known as excellent few-shot learners with task-specific exemplars. Notably, chain of thought (CoT) prompting, a recent technique for eliciting complex multi-step reasoning through step-by-step answer examples, achieved the state-of-the-art performances in arithmetics and symbolic reasoning, difficult system-2 tasks that do not follow the standard scaling laws for LLMs. While these successes are often attributed to LLMs' ability for few-shot learning, we show that LLMs are decent zero-shot reasoners by simply adding "Let's think step by step" before each answer. Experimental results demonstrate that our Zero-shot-CoT, using the same single prompt template, significantly outperforms zero-shot LLM performances on diverse benchmark reasoning tasks including arithmetics (MultiArith, GSM8K, AQUA-RAT, SVAMP), symbolic reasoning (Last Letter, Coin Flip), and other logical reasoning tasks (Date Understanding, Tracking Shuffled Objects), without any hand-crafted few-shot examples, e.g. increasing the accuracy on MultiArith from 17.7% to 78.7% and GSM8K from 10.4% to 40.7% with large InstructGPT model (text-davinci-002), as well as similar magnitudes of improvements with another off-the-shelf large model, 540B parameter PaLM. The versatility of this single prompt across very diverse reasoning tasks hints at untapped and understudied fundamental zero-shot capabilities of LLMs, suggesting high-level, multi-task broad cognitive capabilities may be extracted by simple prompting. We hope our work not only serves as the minimal strongest zero-shot baseline for the challenging reasoning benchmarks, but also highlights the importance of carefully exploring and analyzing the enormous zero-shot knowledge hidden inside LLMs before crafting finetuning datasets or few-shot exemplars.
```

## Notes

- Papiers qui fusionne le [[Zero-shot Prompting]] au [[Chain-of-Thought Prompting]].

![[Pasted image 20240123103436.png]]


```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
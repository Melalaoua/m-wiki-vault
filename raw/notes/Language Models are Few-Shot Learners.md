**authors**:: [Tom B. Brown](https://arxiv.org/search/cs?searchtype=author&query=Brown,+T+B), [Benjamin Mann](https://arxiv.org/search/cs?searchtype=author&query=Mann,+B), [Nick Ryder](https://arxiv.org/search/cs?searchtype=author&query=Ryder,+N), [Melanie Subbiah](https://arxiv.org/search/cs?searchtype=author&query=Subbiah,+M), [Jared Kaplan](https://arxiv.org/search/cs?searchtype=author&query=Kaplan,+J), [Prafulla Dhariwal](https://arxiv.org/search/cs?searchtype=author&query=Dhariwal,+P), [Arvind Neelakantan](https://arxiv.org/search/cs?searchtype=author&query=Neelakantan,+A), [Pranav Shyam](https://arxiv.org/search/cs?searchtype=author&query=Shyam,+P), [Girish Sastry](https://arxiv.org/search/cs?searchtype=author&query=Sastry,+G), [Amanda Askell](https://arxiv.org/search/cs?searchtype=author&query=Askell,+A), [Sandhini Agarwal](https://arxiv.org/search/cs?searchtype=author&query=Agarwal,+S), [Ariel Herbert-Voss](https://arxiv.org/search/cs?searchtype=author&query=Herbert-Voss,+A), [Gretchen Krueger](https://arxiv.org/search/cs?searchtype=author&query=Krueger,+G), [Tom Henighan](https://arxiv.org/search/cs?searchtype=author&query=Henighan,+T), [Rewon Child](https://arxiv.org/search/cs?searchtype=author&query=Child,+R), [Aditya Ramesh](https://arxiv.org/search/cs?searchtype=author&query=Ramesh,+A), [Daniel M. Ziegler](https://arxiv.org/search/cs?searchtype=author&query=Ziegler,+D+M), [Jeffrey Wu](https://arxiv.org/search/cs?searchtype=author&query=Wu,+J), [Clemens Winter](https://arxiv.org/search/cs?searchtype=author&query=Winter,+C), [Christopher Hesse](https://arxiv.org/search/cs?searchtype=author&query=Hesse,+C), [Mark Chen](https://arxiv.org/search/cs?searchtype=author&query=Chen,+M), [Eric Sigler](https://arxiv.org/search/cs?searchtype=author&query=Sigler,+E), [Mateusz Litwin](https://arxiv.org/search/cs?searchtype=author&query=Litwin,+M), [Scott Gray](https://arxiv.org/search/cs?searchtype=author&query=Gray,+S), [Benjamin Chess](https://arxiv.org/search/cs?searchtype=author&query=Chess,+B), [Jack Clark](https://arxiv.org/search/cs?searchtype=author&query=Clark,+J), [Christopher Berner](https://arxiv.org/search/cs?searchtype=author&query=Berner,+C), [Sam McCandlish](https://arxiv.org/search/cs?searchtype=author&query=McCandlish,+S), [Alec Radford](https://arxiv.org/search/cs?searchtype=author&query=Radford,+A), [Ilya Sutskever](https://arxiv.org/search/cs?searchtype=author&query=Sutskever,+I), [Dario Amodei](https://arxiv.org/search/cs?searchtype=author&query=Amodei,+D)
**date**::   ```2024-01-17 11:57 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI - PROMPTING
**sous-groupe**:: #AI/prompting 
**pertinence**:: 6
**links**:: https://arxiv.org/abs/2005.14165
**modification date**:: ```Wednesday 17th January 2024 11:57:21 ```

```ad-abstract
Recent work has demonstrated substantial gains on many NLP tasks and benchmarks by pre-training on a large corpus of text followed by fine-tuning on a specific task. While typically task-agnostic in architecture, this method still requires task-specific fine-tuning datasets of thousands or tens of thousands of examples. By contrast, humans can generally perform a new language task from only a few examples or from simple instructions - something which current NLP systems still largely struggle to do. Here we show that scaling up language models greatly improves task-agnostic, few-shot performance, sometimes even reaching competitiveness with prior state-of-the-art fine-tuning approaches. Specifically, we train GPT-3, an autoregressive language model with 175 billion parameters, 10x more than any previous non-sparse language model, and test its performance in the few-shot setting. For all tasks, GPT-3 is applied without any gradient updates or fine-tuning, with tasks and few-shot demonstrations specified purely via text interaction with the model. GPT-3 achieves strong performance on many NLP datasets, including translation, question-answering, and cloze tasks, as well as several tasks that require on-the-fly reasoning or domain adaptation, such as unscrambling words, using a novel word in a sentence, or performing 3-digit arithmetic. At the same time, we also identify some datasets where GPT-3's few-shot learning still struggles, as well as some datasets where GPT-3 faces methodological issues related to training on large web corpora. Finally, we find that GPT-3 can generate samples of news articles which human evaluators have difficulty distinguishing from articles written by humans. We discuss broader societal impacts of this finding and of GPT-3 in general.
```

## Notes
- [[Few-shot Prompting]]


![[Pasted image 20240119143351.png]]

![[Pasted image 20240119143505.png]]


```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
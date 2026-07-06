**authors**:: [Xin Cheng](https://arxiv.org/search/cs?searchtype=author&query=Cheng,+X), [Di Luo](https://arxiv.org/search/cs?searchtype=author&query=Luo,+D), [Xiuying Chen](https://arxiv.org/search/cs?searchtype=author&query=Chen,+X), [Lemao Liu](https://arxiv.org/search/cs?searchtype=author&query=Liu,+L), [Dongyan Zhao](https://arxiv.org/search/cs?searchtype=author&query=Zhao,+D), [Rui Yan](https://arxiv.org/search/cs?searchtype=author&query=Yan,+R)
**date**::   ```2024-01-22 14:30 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI - PROMPTING
**sous-groupe**:: #AI/prompting 
**pertinence**:: 7
**links**:: https://arxiv.org/abs/2305.02437
**modification date**:: ```Monday 22nd January 2024 14:30:15 ```

```ad-abstract
With direct access to human-written reference as memory, retrieval-augmented generation has achieved much progress in a wide range of text generation tasks. Since better memory would typically prompt better generation~(we define this as primal problem). The traditional approach for memory retrieval involves selecting memory that exhibits the highest similarity to the input. However, this method is constrained by the quality of the fixed corpus from which memory is retrieved. In this paper, by exploring the duality of the primal problem: better generation also prompts better memory, we propose a novel framework, selfmem, which addresses this limitation by iteratively employing a retrieval-augmented generator to create an unbounded memory pool and using a memory selector to choose one output as memory for the subsequent generation round. This enables the model to leverage its own output, referred to as self-memory, for improved generation. We evaluate the effectiveness of selfmem on three distinct text generation tasks: neural machine translation, abstractive text summarization, and dialogue generation, under two generation paradigms: fine-tuned small model and few-shot LLM. Our approach achieves state-of-the-art results in four directions in JRC-Acquis, XSum (50.3 ROUGE-1), and BigPatent (62.9 ROUGE-1), demonstrating the potential of self-memory in enhancing retrieval-augmented generation models. Furthermore, we conduct thorough analyses of each component in the selfmem framework to identify bottlenecks and provide insights for future research.
```

## Notes

![[Pasted image 20240122143504.png]]

```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
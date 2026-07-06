**authors**:: [Trevor Gale](https://arxiv.org/search/cs?searchtype=author&query=Gale,+T), [Deepak Narayanan](https://arxiv.org/search/cs?searchtype=author&query=Narayanan,+D), [Cliff Young](https://arxiv.org/search/cs?searchtype=author&query=Young,+C), [Matei Zaharia](https://arxiv.org/search/cs?searchtype=author&query=Zaharia,+M)
**date**::   ```2024-01-17 15:42 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI
**sous-groupe**:: #AI/training , #AI/hardware 
**pertinence**:: 8
**links**:: https://arxiv.org/abs/2211.15841
**modification date**:: ```Wednesday 17th January 2024 15:42:39 ```

```ad-abstract
We present MegaBlocks, a system for efficient Mixture-of-Experts (MoE) training on GPUs. Our system is motivated by the limitations of current frameworks, which restrict the dynamic routing in MoE layers to satisfy the constraints of existing software and hardware. These formulations force a tradeoff between model quality and hardware efficiency, as users must choose between dropping tokens from the computation or wasting computation and memory on padding. To address these limitations, we reformulate MoE computation in terms of block-sparse operations and develop new block-sparse GPU kernels that efficiently handle the dynamism present in MoEs. Our approach never drops tokens and maps efficiently to modern hardware, enabling end-to-end training speedups of up to 40% over MoEs trained with the state-of-the-art Tutel library and 2.4× over DNNs trained with the highly-optimized Megatron-LM framework.
```

## Notes
- Technique de training des [[A Review of Sparse Expert Models in Deep Learning|SMoE]]


```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
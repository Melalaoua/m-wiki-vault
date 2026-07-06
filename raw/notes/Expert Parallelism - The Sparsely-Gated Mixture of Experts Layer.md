**authors**:: [Noam Shazeer](https://arxiv.org/search/cs?searchtype=author&query=Shazeer,+N), [Azalia Mirhoseini](https://arxiv.org/search/cs?searchtype=author&query=Mirhoseini,+A), [Krzysztof Maziarz](https://arxiv.org/search/cs?searchtype=author&query=Maziarz,+K), [Andy Davis](https://arxiv.org/search/cs?searchtype=author&query=Davis,+A), [Quoc Le](https://arxiv.org/search/cs?searchtype=author&query=Le,+Q), [Geoffrey Hinton](https://arxiv.org/search/cs?searchtype=author&query=Hinton,+G), [Jeff Dean](https://arxiv.org/search/cs?searchtype=author&query=Dean,+J)
**date**::   ```2024-01-17 15:54 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI
**sous-groupe**:: #AI/hardware
**pertinence**:: 5
**links**:: https://arxiv.org/abs/1701.06538
**modification date**:: ```Wednesday 17th January 2024 15:54:19 ```

```ad-abstract
The capacity of a neural network to absorb information is limited by its number of parameters. Conditional computation, where parts of the network are active on a per-example basis, has been proposed in theory as a way of dramatically increasing model capacity without a proportional increase in computation. In practice, however, there are significant algorithmic and performance challenges. In this work, we address these challenges and finally realize the promise of conditional computation, achieving greater than 1000x improvements in model capacity with only minor losses in computational efficiency on modern GPU clusters. We introduce a Sparsely-Gated Mixture-of-Experts layer (MoE), consisting of up to thousands of feed-forward sub-networks. A trainable gating network determines a sparse combination of these experts to use for each example. We apply the MoE to the tasks of language modeling and machine translation, where model capacity is critical for absorbing the vast quantities of knowledge available in the training corpora. We present model architectures in which a MoE with up to 137 billion parameters is applied convolutionally between stacked LSTM layers. On large language modeling and machine translation benchmarks, these models achieve significantly better results than state-of-the-art at lower computational cost.
```

## Notes



```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```
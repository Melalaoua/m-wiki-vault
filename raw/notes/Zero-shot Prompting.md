tags:: #thelaboratory/AI 


Les larges LLMs de nos jours  comme GPT-3 sont entrainés à suivre des instructions et sont aussi entrainés sur de larges quantités de données, ils sont donc capables de réaliser des tâches "zero-shot".

*Prompt*
```
Classify the text into neutral, negative or positive.
Text : I think the vacation is okay.
Sentiment : 
```

*output*:
```
Neutral
```

Il faut noter que dans notre prompt on a pas donné d'exemples, le LLM comprend directement le mot "sentiment" - c'est du zero-shot.

> Next [[Few-shot Prompting]]
> Prev [[Prompt Techniques]]

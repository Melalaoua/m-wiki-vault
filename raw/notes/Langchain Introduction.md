tags:: #thelaboratory/AI 


## Générer du texte.
==

### Text completion.
---
```python
from langchain.llms import OpenAI

llm = OpenAI(temperature=0.9)
text = "Ecris moi le plan d'un article sur les jeux vidéos."

print(llm(text))
```


### Templates.
---
C'est le business de compagnies comme Jasper, CopyAI. Ils ont un stock de templates servant différents buts comme l'écriture de blog, email, lettres..

Tu peux choisir des parmis ces templates et entrer ton input afin de générer le contenu voulu.

Exemple.
```python
from langchain.prompts import PromptTemplate

prompt = PromptTemplate(
		input_variables=["topic"],
		template = "Ecris moi le plan d'un article sur {topic}",
)

print(prompt)
```


### Chaînes.
---
Entrons dans le vif du sujet, les chaînes. Elles sont responsables du flux de donnés entier à l'intérieur de Langchain. Dans l'exemple ci-dessous, on va utiliser la chaine LLMChain. Il y a une multitudes de chaînes, on en discute plus tard.

LLMChain prends en input le prompt du template créé juste avant et le remplis de manière dynamique avec notre/nos variable(s) avant de la passer dans, pour l'exemple suivant, l'API openAI.

```python
from langchain.chains import LLMChain

chain = LLMChain(llm=llm, prompt=prompt)
```

Maintenant que nous avons créer notre template et notre chain. Nous pouvons maintenant insérer n'importe quelle sujet que nous voulons pour générer notre plan. 

```python
print(chain.run(topic = "Zelda"))
```


Maintenant on va faire étendre notre chaîne à plusieurs inputs : 
```python
prompt = PrompTemplate(
		input_variables = ["topic", "audience", "tone"],
		template = """Génère une introduction pour un article de blog 
		à partir du titre, l'audience et un ton de voix défini.
		
		Titre du blog : {title}
		Audience : {audience}
		Ton de voix : {tone}
		 
		"""
)

chain = LLMChain(llm = llm, prompt=prompt)

print(chain.run(title="Les activités à Toronto", audience = "Millenials", tone = "Chaleureux"))
```


### Multiples opérations.
---
L'objectif des chaînes, c'est de pouvoir faire plusieurs opérations l'une après l'autre, le résultat d'une opération servant de support pour l'opération suivante.

Par exemple, on veut générer le plan d'un article de blog pour un sujet donné et ensuite utiliser ce plan pour écrire l'article

```python
from langchain.prompts import PromptTemplate
prompt = PromptTemplate(
			input_variables = ["topic"],
			template = "Ecris moi un plan d'un article sur {topic}"
)

llm = OpenAi(temperature = 0.9, max_tokens = -1)
chain = LLMChain(llm = llm, prompt=prompt)

second_prompt = PromptTemplate(
			input_variables = ["outline"],
			template = """
			Ecris moi un article en te basant du plan suivant.

			Plan = {outline}
			"""
)

chain_two = LLMChain(llm=llm, prompt=second_prompt)
```

On a nos deux chaînes de créées, 

```python

from langchain.chains import SimpleSequentialChain

overall_chain = SimpleSequentialChain(chains = [chain, chain_two], verbose=True)

#Run the chain specifying only the input variable for the first chain.
catchphrase = overall_chain.run("Toronto")

print(catchphrase)
```
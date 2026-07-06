tags:: #thelaboratory/AI 


Suite du tutoriel sur [[Langchain]]

On a vu les chaines dans [[Langchain Introduction]]. On va donc revoir pas mal de choses.

### LLMChain.
---
La plus basique des chaine dans Langchain, prend un prompt template en entrée, formatte le et renvoie la réponse du LLM.

#### Quel est l'avantage d'utiliser cette chaîne ?
Utiliser des templates en input permet de générer des prompts de manière dynamique à communiquer au LLM.

```python
from langchain.llms import OpenAI
from langchain.prompts import PromptTemplate

import os
os.environ["OPEN_API_KEY"] = ""

llm = OpenAI(temperature = 0.5)
prompt = PrompTemplate(
			input_variables=["topic"],
			template = "Give me a tweet idean on {topic}"
)
```

```python
from langchain.chains import LLMChain
chain = LLMChain(llm=llm, prompt=prompt)


# Run the chain only specifying the input variable
print(chain.run("AI"))
```


Faisons la même chose avec plusieurs variables
```python
prompt = PromptTemplate(
			input_variables=["topic", "topic2"],
			template = "Give me a tweet idea on {topic1} and {topic2}"
)

chain = LLMChain(llm=llm, prompt=prompt)
print(chain.run({'topic1':'AI', 'topic2':'NLP'}))
```


### Sequential Chain.
---
Une chaine sequentielle fonctionne en combinant deux, ou plus, chaines ensemble. Par example on peut prendre l'output d'une chaine et le passer directement dans une seconde chaine, de manière sequentielle.

```python
llm = OpenAI(temperature = .7)
template = """Write a blog outline given a topic

Topic : {topic}
"""

prompt_template = PromptTemplate(input_variables=["topic1"], template=template)
outline_chain = LLMChain(llm=llm, prompt=prompt_template, output_key="outline")
```

On créer ensuite une autre LLMChain qui va prendre l'output de la première et générer un article de blog basé sur l'outline générée.

```python
llm = OpenAI(temperature=.7)
template= """Write a blog article based on the below outline.

Outline:{outline}

prompt_template = PromptTemplate(input_variables["outline"], template=template, output_key ="article")
```


Maintenant, connectons nos deux chaînes en utilisant SequentialChain.

```python
from langchain.chains import SequentialChain

overall_chain = SequentialChain(
				chains = [outline_chain, article_chain],
				input_variables=["topic"]
				output_variables["outline", "article"],
				verbose=True
)
```

```python
overall_chain({"topic": "Deep Learning"})
```


### Retrieval QA Chain.
---
Vu dans [[Langchain Indexage]]

Les chaines retrieval QA sont considérées comme les plus importantes car elles font du questions/reponses sur notre document.

Les documents fournis peuvent être des pdf, pages web, vidéos youtube, document notion, etc...

```python
from langchain.document_loaders import TextLoader
from langchain.embeddings.openai import OpenAIEmbeddings
from langchain.llms import OpenAI
from langchain.text_splitter import CharacterTextSplitter
from langchain.vectorstores import Chroma

loader = TextLoader("your_document", encoding="utf8")
documents = loader.load()
text_splitter = CharacterTextSplitter(chunk_size=1000, chunk_overlap=0)
texts = text_splitter.split_documents(documents)
```

Maintenant, crééons nos embeddings.
```python
embeddings = OpenAIEmbeddings()
docsearch = Chroma.from_documents(texts, embeddings)
```

Au tour de RetrievalQA qui peut opérer nos Q&A sur notre document.
```python
from langchain.chains import retrievalQA

qa = RetrievalQA.from_chain_type(llm=OpenAI(), chain_type="stuff", retriever=docsearch.as_retriever())

query = "Question sur le document"

qa.run(query)
```


### LoadSummarize chain.
---
C'est la chaine fondamentale pour faire des résumés de documents.

L'algorithme fonctionne ainsi : Premièrement, il divise l'input en entier en petits morceaux. Il créer ensuite un résumé de chaque morceaux. Et ensuite un résumé des résumés est effectué.

```python
from langchain import OpenAI, PromptTemplate, LLMChain
from langchain.text_splitter import CharacterTextSplitter
from langchain.chains.mapreduce import MapReduceChain
from langchain.prompts import PromptTemplate
from langchain.docstore.document import Document

llm = OpenAI(temperature=.7)

text_splitter = CharacterTextSplitter()

with open("your_document") as f :
	document = f.read()

texts = text_splitter.split_text(document)

docs = [Document(page_content=t) for t in texts]
```

Maintenant, créons notre load_summarize chaine avec un map reduce. Il existe d'autres chaines.

```python
from langchain.chains.summarize import load_summarize_chain
chain = load_summarize_chain(llm, chain_type = "map_reduce")
chain.run(docs)
```


### Router Chain.
---
Router chain est utile lorsque nous avons plusieurs chaines pour différentes tâches et l'on souhaite les invoquer en fonction de notre input

Par exemple : on a deux LLMChain, l'une est bonne en physique l'autre est bonne en maths. Si on pose une question, la router chaine peut comprendre notre intention et nous rediriger vers la bonne chaine.

```python
from langchain.chains.router import MultiPromptChain
from langchain.llms import OpenAI
from langchain.chains import ConversationChain
from langchain.chains.llm import LLMChain
from langchain.prompts import PromptTemplate

physics_template = """
You are a very smart physics professor. \

You are great at answering questions about physics in a concise and easy to understand manner. \

When you don't know the answer to a question you admit that you don't know.

  

Here is a question:

{input}
"""

math_template = """
You are a very good mathematician. You are great at answering math questions. \

You are so good because you are able to break down hard problems into their component parts, \

answer the component parts, and then put them together to answer the broader question.

  

Here is a question:

{input}
"""

prompt_infos = [
	{
		"name" : "physics",
		"description" : "Good for answering questions about physics",
		"prompt_template" : physics_template
	},
	{
		"name" : "math",
		"description" : "Good for answering math questions",
		"prompt_template" : math_template
	}
]

destination_chains = {}
for p_info in prompt_infos:
	name = p_info["name"]
	prompt_template = p_info["prompt_template"]
	prompt = PromptTemplate(template=prompt_template, input_variables=["input"])
	chain = LLMChain(llm=llm, prompt=prompt)
	destination_chain[name] = chain

defaultchain = ConversationChain(llm=llm, output_key="text")

from langchain.chains.router.llm_router import LLMRouterChain, RouterOutputParser
from langchain.chains.router.multi_prompt_prompt import MULTI_PROMPT_ROUTER_TEMPLATE

destinations = [f"{p['name']} : {p['description']}" for p in prompt_infos]
destinations_str = "\n".join(destinations)
router_template= MULTI_PROMPT_ROUTER_TEMPLATE.format(destinations=destinations_str)

router_prompt= PromptTemplate(
			template = router_template,
			input_variables["input"],
			output_parser = RouterOutputParser()
)

router_chain = LLMRouterChain.from_llm(llm, router_prompt)

chain = MultiPromptChain(
		router_chain = router_chain,
		destination_chains = destination_chains,
		default_chain = default_chain,
		verbose = True
)

print(chain.run("What is black body radiation?"))
```

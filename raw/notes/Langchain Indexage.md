tags:: #thelaboratory/AI 


Suite d'un tutoriel sur [[Langchain]]

Il est possible avec langchain de diviser un document en plusieurs morceaux et entrainer le chatbot dessus. Quand un utilisateur pose ensuite des question, seulement les informations importantes sont récupérées et transmises à ChatGPT.

On a vu ce qu'était un embedding dans [[Langchain Models]]

### Vector db.
---
Une fois que l'on a crée les embeddings pour notre entrée, on a besoin de les stocker quelque part afin de réaliser des requêtes rapides.

Les bases de données traditionnelles ne sont pas designed pour ce genre de tâche. Ainsi, il nous faut une base de donnée spécialisée : une bases de données de vecteurs.

Langchain utilise chroma db par défaut, c'est gratuit et utilisable localement.

1. L'utilisateur pose une question.
2. A recherche de similarité est effectuée pour identifier toutes les données similaires.
3. L'utilisateur pose une question combiné à tout les embeddings trouvés, c'est ensuite passé  à ChatGPT.


### Document loader.
---
Langchain a une fonction d'import de document qui permet de chercher les données dans ce document (le document peut être un site web, un vidéo youtube, un document notion ,etc...).

```python
from langchain.document_loaders import TextLoader

loader = TextLoader("votre_document", encoding = "utf8")
documents = loader.load()
```


### Document Splitter.
---
Comme on l'a discuté juste avant, on prends notre document en entrée et on le divise en plusieurs morceaux avant de créer des embeddings et les stocker. Pour cela, on utilise un document spltiter de Langchain. Il en existe plusieurs.

On va utiliser un splitter simple qui divisent notre document en se basant sur le nombre de caractères, on définit aussi des overlap pour avoir une cohérence entre les morceaux.

```python
from langchain.text_splitter import CharacterTextSplitter

text_splitter = CharacterTextSplitter(chunk_size=1000, chunk_overlap=50)

texts = text_splitter.split_documents(documents)
```

On va ensuite créer nos embeddings pour nos chunks et les stocker dans notre vectorstore Chromadb. Créant un index qui contient tout l'information.

```python
from langchain.embedding import OpenAIEmbeddings
import os
from langchain.vectorstores import Chroma

os.environ["OPEN_API_KEY"] = ""
embeddings = OpenAIEmbeddings()

db = Chroma.from_documents(texts, embeddings)
```

On peut ensuite créer notre chaînes de Q&A afin de questionner chatGPT sur le document.

```python
from langchains.chains import RetrievalQA
from langchain.llms import OpenAI

retriever = db.as_retriever()
qa = RetrievalQA.from_chain_type(llm=OpenAI(), chain_type="stuff", retriever=retriever)
```

On peut ensuite poser nos questions.
```python
query = ""
qa.run(query)
```
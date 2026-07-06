tags:: #thelaboratory/AI 

Suite du tutorial sur [[Llamaindex]]

Un data connector, dans llamindex, effectue la tâche de prendre les données depuis les différentes sources et les convertis en un format de fichier qui peut être injecté dans llamaindex.

Llamaindex supporte un large type de data connector qui nous permet de lire les données de sites web, PDF, vidéos youtube, document notions, message Slack, etc ...

Entrons dans le vif du sujet :

### Youtube document loader.
---
Voyons comment convertir le transcript d'une vidéo youtube en un format de fichier.
```python
from llama_index import download_loader

YoutubeTranscriptReader = download_loader("YoutubeTranscriptReader")

loader = YoutubeTranscriptReader()
youtube_documents = loader.load_data(ytlinks=['https://www.youtube.com/watch?v=nHcbHdgVUJg&ab_channel=WintWealth'])

```


### PDF Loader.
---
Download le fichier PDF.
```python
!wget https://www.africau.edu/images/default/sample.pdf
```

On le convertit en un fichier lisible.
```python
from pathlib import Path
from llama_index import download_loader

PDFReader = download_loader("PDFReader")

loader = PDFReader()

pdf_document = loader.load_data(file=Path("./sample.pdf"))
```


### Notion loader.
---
```python
from llama_index import download_loader
import os

NotionPageReader = download_loader("NotionPageReader")

integration_token = "notion-token"
database_id = "database-id"
reader= NotionPageReader(integration_token=integration_token)
notion_documents = reader.load_data(database_id=database_id)
```

On fusionne tous nos documents.
```python
all_documents = notion_documents + pdf_document + youtube_documents
```


On créer ensuite notre Q&A sur ces documents.
```python
import os 
from llama_index import VectorStoreIndex
os.environ["OPENAI_API_KEY"] = "key"
index = VectorStoreIndex.from_documents(all_documents)
```

```python
query_engine = index.as_query_engine()
response = query_engine.query("Does IIT help ?")
print(response)
```
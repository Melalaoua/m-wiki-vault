tag:: #thelaboratory/AI 


- Split the knowledge base into text chunks.
- Create a numerical representation ([[Langchain Indexage|Embeddings]]) for each chunk and save them to a vector database.  
    _If your data is static, Steps 1 and 2 are one-time efforts._
- Run a semantic search using the user’s query on this database and fetch relevant text chunks.
- Send these text chunks to the LLM along with the user’s questions and ask them to Answer.
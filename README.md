# Building_document_based_Question_Answering_System

LangChain is a powerful framework designed for developing applications driven by language models, while Pinecone serves as an efficient vector database for building high-performance vector search applications. Our use case focuses on answering questions over specific documents, relying solely on the information within those documents to generate accurate and context-aware answers.

# 1. Loading documents
First, we need to load the documents from a directory using the DirectoryLoader from LangChain. In this example, we assume the documents are stored in a directory called 'data'.

# 2. Splitting documents
Now, we need to split the documents into smaller chunks for processing. We will use the RecursiveCharacterTextSplitter from LangChain, which by default tries to split on the characters ["\n\n", "\n", " ", ""].

# 3. Embedding documents with OpenAI
Once the documents are split, we need to embed them using OpenAI's language model. First, we need to install the tiktoken library.

# 4. Vector search with Pinecone
Next, we will use Pinecone to create an index for our documents.
We are creating a new Pinecone vector index using the Pinecone.from_documents() method. This method takes three arguments:

docs: A list of documents that have been split into smaller chunks using the RecursiveCharacterTextSplitter. These smaller chunks will be indexed in Pinecone to make it easier to search and retrieve relevant documents later on.

embeddings: An instance of the OpenAIEmbeddings class, which is responsible for converting text data into embeddings (i.e., numerical representations) using OpenAI's language model. These embeddings will be stored in the Pinecone index and used for similarity search.

index_name: A string representing the name of the Pinecone index. This name is used to identify the index in Pinecone's database, and it should be unique to avoid conflicts with other indexes.

# 5. Finding similar documents
Now, we can define a function to find similar documents based on a given query.

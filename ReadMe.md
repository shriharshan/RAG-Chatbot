# Conversational Chatbot Using LangChain and Cassandra

This code demonstrates the process of building a conversational chatbot using LangChain, Cassandra, and the OLLAMA language model.

## Dependencies

1. **LangChain**: A framework for building applications with large language models (LLMs).
2. **HuggingFace Embeddings**: Embeddings from the Hugging Face Transformers library.
3. **Cassandra**: A distributed database for storing and querying vector embeddings.
4. **LangChain Community Modules**: Additional modules from the LangChain community, including the DirectoryLoader and OLLAMA LLM.
5. **NLTK (Natural Language Toolkit)**: For text preprocessing (stopword removal and lemmatization).
6. **PyPDF2**: For processing PDF documents.

## Preprocessing

1. The `remove_figures_tables_citations` function removes figures, tables, and citations from the text.
2. The `preprocess_text` function performs text preprocessing, including:
  - Converting the text to lowercase
  - Removing non-alphanumeric characters
  - Removing stop words
  - Lemmatizing the words
3. The `process_pdfs` function processes PDF files in the `Data` folder, extracts the text, preprocesses it, and saves the preprocessed text in the `pre-processed` folder.

## Loading and Chunking Data

1. The `read_doc` function loads the preprocessed text files from the `pre-processed` folder using the `DirectoryLoader`.
2. The `chunk_data` function splits the documents into smaller chunks using the `RecursiveCharacterTextSplitter` from LangChain.

## Embeddings and Vector Store

1. The `HuggingFaceEmbeddings` is used to create embeddings for the text chunks.
2. The `Cassandra` class from LangChain is used to create a vector store in Cassandra to store the embeddings.
3. The `VectorStoreIndexWrapper` is used to create a searchable index for the vector store.

## Querying and Summarization

1. The `astra_vector_index.query` function is used to perform a similarity search on the vector store using the provided query.
2. The `summarize_text` function uses the OLLAMA language model to summarize the text chunks.
3. The `generate_response` function combines the summarized text chunks and uses the OLLAMA language model to generate the final response to the user's query.

## Usage

1. Set up the Cassandra database connection by providing the necessary credentials (ASTRA_DB_APPLICATION_TOKEN, ASTRA_DB_ID).
2. Download the OLLAMA language model "Llama2" by running the following command in your command line:
You can download the OLLAMA language model from [this link](https://ollama.com/download) and run this command to download llama 2 model
```
ollama run llama2
```
3. Run the code to preprocess the PDF files, create the vector store, and set up the chatbot.
4. The chatbot can be queried using the `astra_vector_index.query` function, which will return the relevant research findings and a generated response.

This code provides a foundation for building a conversational chatbot using LangChain, Cassandra, and the OLLAMA language model. It demonstrates how to preprocess text, create a vector store, and generate responses based on the user's query.
---
title: LangChain Chat with Your Data
notetype: feed
date: 2023-11-25
---


## Summary:
[The LangChain Chat with Your Data course](https://learn.deeplearning.ai/langchain-chat-with-your-data) provides a step-by-step exploration of [[RAG Essentials]], guiding users through fundamental processes. The course covers loading various document types using methods like website loaders, directory loaders, and YouTube audio loaders,


### 1. Document Loaders
- Introduction of how to **loading different type of document**, through website loader, directory loader, pdf loader, Youtube Audio loader - [Document Loaders - Github](https://github.com/langchain-ai/langchain/tree/master/libs/langchain/langchain/document_loaders)

### 2. Text Splitters
- Introduction of how to **split the document** e.g., CharacterSplitter, Sentence Transformer, NLTK ,etc. - [Document of text splitters - Github](https://github.com/langchain-ai/langchain/blob/master/libs/langchain/langchain/text_splitter.py)

### 3. Vector Stores and Embeddings
- **Vector stores and Embedding** - They shows that we first embed the document into embedding using OpenAI embedding, however there are various embedding in the LangChain ([Embedding](https://github.com/langchain-ai/langchain/tree/master/libs/langchain/langchain/embeddings)), also the course introduce how to create a persist vector store using ChromaDB, again several vector store supported by the LangChain ([Vector Stores](https://github.com/langchain-ai/langchain/tree/master/libs/langchain/langchain/vectorstores))

### 4. Retrieval Strategies
- **Retrieve the relevant document** with different type of retrievals such as similarity search, maximal marginal relevance, using self-query to specified the metadata filtering, compression the response from LLM (through `ContextualCompressionRetriever`)  - See more ([Retrievers](https://github.com/langchain-ai/langchain/tree/master/libs/langchain/langchain/retrievers)). Finally, they also demonstrate the traditional retriever such as `SVMRetriever` and `TFIDFRetriever`

### 5. Creating Q and A
- Demonstrate how to **create Question Answering** by using `RetrievalQA chain` ([RetrievalQA](https://github.com/langchain-ai/langchain/blob/master/libs/langchain/langchain/chains/retrieval_qa/prompt.py))

### 6. Enhancing them with Memory to create a Q/A Chat Bots.
- Finally, **creating a Chat** need `Memory` component, so the course demonstrate [`ConversationalRetrievalChain`](https://github.com/langchain-ai/langchain/blob/master/libs/langchain/langchain/chains/conversational_retrieval/prompts.py) with [`ConversationBufferMemory`](https://github.com/langchain-ai/langchain/blob/master/libs/langchain/langchain/memory/buffer.py#L10) and finally show how to create the UI wrapping the QA chatbot

#llm #chatgpt #langchain #deeplearning-ai
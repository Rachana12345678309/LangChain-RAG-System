# Retrieval-Augmented Generation (RAG) with LangChain

This project implements a **RAG system**, a technique used to give a Large Language Model (LLM) access to specific, external data without needing to retrain the model. This allows for accurate, context-aware answers based on a provided document.

## Overview

Large Language Models (like GPT or Llama) are limited by their training cutoff dates. **RAG** solves this by:
1. **Retrieving** relevant snippets from a document.
2. **Augmenting** the user prompt with that context.
3. **Generating** an answer based *only* on the provided facts.



## How it Works

The pipeline follows these distinct phases:

### 1. Document Ingestion & Splitting
The raw document (PDF) is loaded and broken down into smaller "chunks." This is necessary because LLMs have a limit on how much text they can process at once (context window).

### 2. Text Embeddings
Each chunk is converted into a numerical vector using an **Embedding Model**. These vectors represent the semantic meaning of the text.

### 3. Vector Storage
The embeddings are stored in a **Vector Database** (ChromaDB/FAISS). This allows us to perform a mathematical search to find chunks that are most similar to a user's question.



### 4. Retrieval & Generation
When a user asks a question:
- The question is converted into a vector.
- The system finds the most similar text chunks.
- These chunks + the question are sent to the LLM (e.g., GPT-3.5/4) to generate a final, grounded answer.

## Key Features

- **Framework:** Built using **LangChain**, the industry standard for LLM orchestration.
- **Custom Knowledge:** Uses a specific PDF as the "Source of Truth."
- **Efficiency:** Implements Recursive Character Text Splitting for better context retention.
- **Semantic Search:** Uses cosine similarity to find the most relevant information.

## Tech Stack

- **Python 3**
- **LangChain:** Core orchestration.
- **PyPDF:** For document parsing.
- **ChromaDB:** As the vector store.
- **HuggingFace / OpenAI:** For embeddings and text generation.

## How to Run

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/](https://github.com/)<your-username>/langchain-rag-basic.git
   cd langchain-rag-basic

2. **Provide your PDF:**
   Place your document in the project folder and update the path in the notebook.

3. **Install dependencies:**
   pip install langchain pypdf chromadb sentence-transformers

4. **Run the Notebook:**
   Execute 40_RAG_project_langchain_basic.ipynb to start querying your data.

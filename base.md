# Retrieval-Augmented Generation (RAG)

## Overview
Retrieval-Augmented Generation (RAG) is a technique used to improve Large Language Model (LLM) responses by **retrieving relevant information from an external knowledge base** and supplying it to the model at query time.  
Instead of relying only on training data, the LLM generates answers grounded in **real, authoritative sources**.

---

## Why RAG Is Needed

### Hallucination Problem
LLMs can produce incorrect or fabricated information when:
- The data is missing from training
- The topic is recent
- The query is domain-specific  

RAG reduces hallucination by **injecting retrieved factual context** into the prompt before generation.

### Fine-Tuning Limitations
Fine-tuning LLMs:
- Is expensive
- Takes time
- Must be repeated for every data update  

RAG avoids retraining by keeping data external and searchable.

---

## RAG Architecture

RAG works through two pipelines:
1. Data Injection Pipeline
2. Retrieval Pipeline

---

## Data Injection Pipeline (Offline)

This pipeline prepares external data for retrieval.

### Data Sources
Documents can come from:
- PDF, HTML, Word, Excel
- SQL databases
- Logs and unstructured text

### Processing Steps
**Parsing and Chunking**  
Documents are read and split into smaller chunks to fit model context limits and improve retrieval accuracy.

**Embeddings**  
Each chunk is converted into a numerical vector using an embedding model.  
Semantically similar text produces similar vectors.

**Vector Store**  
Embeddings are stored in a vector database for fast similarity search.

---

## Retrieval Pipeline (Online)

This pipeline runs when a user submits a query.

### Query Flow
- User query is converted into an embedding
- Similarity search retrieves relevant chunks from the vector database
- Retrieved context is added to the prompt
- LLM generates a response based on both query and context

---

## Key Benefits of RAG
- Reduces hallucination
- No model retraining required
- Works with private and frequently updated data
- Cost-effective and scalable

---

## Summary
RAG combines **retrieval + generation** to produce accurate, reliable, and up-to-date LLM responses by grounding answers in external knowledge sources.

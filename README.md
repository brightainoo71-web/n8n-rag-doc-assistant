# n8n Document RAG & Q&A Assistant

An automated Retrieval-Augmented Generation (RAG) system built in **n8n**. The workflow ingests documents directly from Google Drive, generates vector embeddings using Google Gemini, indexes them into Pinecone, and allows users to query document knowledge in real time through an interactive Q&A chat chain.

---

## Features

- **Automated Document Ingestion**: Fetches documents (PDFs, docs) straight from Google Drive.
- **Smart Chunking**: Splits text into manageable segments using Recursive Character Text Splitting.
- **Vector Storage**: Indexes and stores 3072-dimensional embeddings in a Pinecone serverless vector database.
- **Contextual Q&A Chat**: Uses Gemini models and vector retrieval to deliver grounded, source-accurate answers.

---

## Architecture

1. **Ingestion Flow**:
   - `Trigger` ➔ `Download file (Google Drive)` ➔ `Pinecone Vector Store` (Document insertion)
   - Sub-nodes: `Embeddings Google Gemini` (3072-dim) + `Default Data Loader` + `Recursive Character Text Splitter`

2. **Query & Chat Flow**:
   - `When chat message received` ➔ `Question and Answer Chain`
   - Connected via `Google Gemini Chat Model` and `Vector Store Retriever` linked to the Pinecone index.

---

## Prerequisites

- **n8n** (Cloud or self-hosted)
- **Google Cloud Platform** (Enabled Google Drive API & Google Gemini/PaLM API credentials)
- **Pinecone Account** (Index created with `3072` dimensions and `cosine` metric)

---

## Setup & Deployment

1. **Clone the Repository**:
   ```bash
   git clone [https://github.com/your-username/n8n-rag-doc-assistant.git](https://github.com/your-username/n8n-rag-doc-assistant.git)
   cd n8n-rag-doc-assistant

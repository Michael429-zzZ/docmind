# DocMind

**DocMind** is an open‑source, production‑oriented **multimodal document intelligence platform**.

It enables you to ingest complex PDF documents, extract **text, images, and tables**, store them in a **vector database**, and interact with the content through a **multimodal RAG (Retrieval‑Augmented Generation) chat interface**.

DocMind is designed with **real deployment and extensibility** in mind rather than as a toy demo or one‑off experiment.

---

## Why DocMind

Most existing “Chat with PDF” projects focus on quick demos:

* Text‑only RAG
* Single‑file scripts
* Tight coupling to one LLM provider
* Limited extensibility

**DocMind is different.**

It focuses on:

* 🧠 **Multimodal understanding** (text + figures + tables)
* 🏗️ **Clean system architecture** suitable for production
* 🔌 **Pluggable LLM / embedding backends**
* 📦 **End‑to‑end pipeline** from document ingestion to chat UI

---

## Core Features

* **Document Ingestion Pipeline**

  * PDF parsing with Docling
  * Text chunking for vector storage
  * Image extraction with metadata
  * Table extraction (structured data + rendered images)

* **Vector‑based Retrieval**

  * PostgreSQL + pgvector
  * Metadata‑aware similarity search
  * Image / table references preserved in retrieval

* **Multimodal RAG Chat**

  * Text answers grounded in document context
  * Related images and tables returned with answers
  * Multi‑turn conversation support

* **Production‑Ready Architecture**

  * Clear service boundaries
  * Async backend (FastAPI)
  * Dockerized infrastructure

---

## System Architecture

```
Frontend (Next.js)
   │
   ▼
Backend API (FastAPI)
   │
   ├── Document Ingestion Pipeline
   │     ├── PDF Parsing (Docling)
   │     ├── Text Chunking
   │     ├── Image / Table Extraction
   │
   ├── Retrieval Layer
   │     └── PostgreSQL + pgvector
   │
   └── RAG Engine
         ├── Context Retrieval
         ├── Multimodal Prompting
         └── LLM Response Generation
```

---

## Tech Stack

### Backend

* **Framework**: FastAPI
* **PDF Processing**: Docling
* **Vector Store**: PostgreSQL + pgvector
* **Embeddings**: OpenAI / HuggingFace (pluggable)
* **LLM Providers**: OpenAI, Ollama (pluggable)
* **Cache / Queue**: Redis (optional)

### Frontend

* **Framework**: Next.js (App Router)
* **Styling**: TailwindCSS
* **UI Components**: shadcn/ui

### Infrastructure

* Docker & Docker Compose
* PostgreSQL 15
* Redis

---

## Getting Started

### Prerequisites

* Docker & Docker Compose
* Node.js 18+
* Python 3.11+

(Optional)

* OpenAI API Key **or** Ollama (local LLM)

---

### Quick Start

```bash
# Clone repository
git clone https://github.com/yourname/docmind.git
cd docmind

# Environment setup
cp .env.example .env

# Start services
docker-compose up -d
```

Access:

* Frontend: [http://localhost:3000](http://localhost:3000)
* Backend API: [http://localhost:8000](http://localhost:8000)
* API Docs: [http://localhost:8000/docs](http://localhost:8000/docs)

---

## Example Use Case

DocMind is well‑suited for:

* Technical papers and research PDFs
* Product documentation
* Educational materials
* Reports with figures and tables

For demonstration, you can use the paper **“Attention Is All You Need”** to verify:

* Text‑based Q&A
* Architecture diagram retrieval
* Table‑based performance comparison
* Multi‑turn contextual conversations

---

## Project Structure (Simplified)

```
backend/
  app/
    pipelines/        # Document ingestion pipeline
    retrieval/        # Vector search & storage
    rag/              # RAG & chat logic
    llm/              # LLM adapters
    embeddings/       # Embedding adapters
frontend/
  app/                # Next.js App Router
```

---

## Design Principles

* **Production first**: engineering clarity over quick demos
* **Extensible by design**: swap LLMs, embeddings, or storage
* **Multimodal by default**: images and tables are first‑class citizens
* **Transparent retrieval**: sources are traceable

---

## Roadmap

* [ ] OCR support for scanned PDFs
* [ ] Multi‑document cross‑search
* [ ] Streaming / real‑time chat
* [ ] Plugin system for custom processors
* [ ] Role‑based access & permissions

---

## License

MIT License

---

## Author

Maintained by a single engineer with a focus on **production-grade AI systems**, multimodal RAG, and scalable architecture.

Contributions and discussions are welcome.

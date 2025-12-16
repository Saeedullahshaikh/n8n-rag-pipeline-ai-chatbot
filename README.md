# 📚 RAG Pipeline & AI Chatbot Agent using n8n

A **production‑ready Retrieval‑Augmented Generation (RAG) pipeline** and **AI chatbot agent** built using **n8n**, **LangChain nodes**, **Google Drive**, **Pinecone**, and **LLMs (Anthropic + OpenAI embeddings)**.

This project automatically ingests documents from Google Drive, converts them into embeddings, stores them in Pinecone, and enables an AI agent to answer user queries using retrieved context.

---


---

## 🧠 What This Project Does (High-Level)

1. Watches a **specific Google Drive folder** for new files
2. Automatically **downloads documents**
3. **Splits text intelligently** into chunks
4. **Generates embeddings** using OpenAI
5. **Stores vectors in Pinecone**
6. Exposes a **chat interface**
7. An **AI Agent retrieves relevant context** from Pinecone and answers questions using an LLM

This creates a **self-updating AI knowledge base**.

---

## ✨ Features

### 📂 Document Ingestion

* Google Drive trigger (polls every minute)
* Supports PDFs, Docs, text-based files
* Fully automated ingestion pipeline

### ✂️ Smart Text Processing

* Recursive Character Text Splitter
* Custom chunking strategy for better retrieval
* Optimized for long documents

### 🧬 Vector Embeddings

* OpenAI Embeddings
* High‑quality semantic search
* Stored in Pinecone index

### 🧠 Vector Database (Pinecone)

* Insert mode for document indexing
* Retrieve‑as‑tool mode for AI Agent
* Scalable, production‑grade vector store

### 🤖 AI Agent (Chatbot)

* LangChain Agent inside n8n
* Uses Pinecone as a retrieval tool
* LLM powered by **Anthropic Claude Sonnet 4.5**
* Context‑aware answers

### 💬 Chat Interface

* n8n Chat Trigger
* Real‑time conversational querying
* Perfect for internal tools or SaaS products

---

## 🏗️ Architecture Overview

```
Google Drive
     ↓
Google Drive Trigger
     ↓
Download File
     ↓
Text Splitter
     ↓
Document Loader
     ↓
OpenAI Embeddings
     ↓
Pinecone Vector Store (Insert)

User Chat
     ↓
Chat Trigger
     ↓
AI Agent
     ↓
Pinecone Vector Store (Retrieve as Tool)
     ↓
LLM Response
```

---

## 🧰 Tech Stack

| Layer               | Technology                  |
| ------------------- | --------------------------- |
| Workflow Automation | n8n                         |
| LLM                 | Anthropic Claude Sonnet 4.5 |
| Embeddings          | OpenAI                      |
| Vector DB           | Pinecone                    |
| Storage             | Google Drive                |
| Framework           | LangChain                   |

---

## ⚙️ Setup Instructions

### 1️⃣ Prerequisites

* n8n (self-hosted or cloud)
* Google Cloud project + Drive API enabled
* Pinecone account & index
* OpenAI API key
* Anthropic API key

---

### 2️⃣ Environment Variables

Set the following in n8n:

```bash
OPENAI_API_KEY=your_key
ANTHROPIC_API_KEY=your_key
PINECONE_API_KEY=your_key
PINECONE_ENVIRONMENT=your_env
```

---

### 3️⃣ Google Drive Setup

* Create a folder in Google Drive
* Grant access to n8n Google credentials
* Paste the **Folder ID** into the Google Drive Trigger node

---

### 4️⃣ Pinecone Setup

* Create a Pinecone index
* Dimension must match OpenAI embedding model
* Select the index in both Pinecone nodes:

  * Insert mode
  * Retrieve-as-tool mode

---

### 5️⃣ Import Workflow

1. Copy the workflow JSON
2. In n8n → Import Workflow
3. Paste JSON → Save
4. Configure credentials
5. Activate workflow

---

## 🔐 Security & Production Best Practices 

* Store secrets using n8n credentials (never hardcode)
* Use namespace separation in Pinecone
* Enable rate limiting on chat endpoint
* Add document deduplication logic
* Add logging & error workflows
* Use RBAC for Google Drive access

---

## 📈 Scalability Considerations

* Pinecone scales horizontally
* Async ingestion possible via queues
* Can add:

  * Multiple data sources
  * Metadata filtering
  * Multi-tenant namespaces

---

## 💡 Use Cases

* Internal company knowledge base
* Customer support chatbot
* SOP & policy assistant
* DevOps / Platform documentation bot
* SaaS AI search engine

---

## Author

**Saeedullah Shaikh**
- GitHub: [@Saeedullahshaikh](https://github.com/Saeedullahshaikh)

## License

MIT License



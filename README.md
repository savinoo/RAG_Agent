# Agentic RAG with LangGraph & ChromaDB 🦜🕸️

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![LangChain](https://img.shields.io/badge/LangChain-v0.3-green)](https://github.com/langchain-ai/langchain)
[![LangGraph](https://img.shields.io/badge/LangGraph-Stateful_Agents-orange)](https://github.com/langchain-ai/langgraph)
[![VectorDB](https://img.shields.io/badge/ChromaDB-Vector_Store-lightgrey)](https://www.trychroma.com/)

A sophisticated, stateful **Agentic RAG (Retrieval-Augmented Generation)** system designed for intelligent document interaction. This agent doesn't just retrieve; it reasons about the necessity of retrieval and maintains a coherent conversation state across multiple turns.

## 🌟 Key Features

- **🧠 Agentic Reasoning**: Powered by **LangGraph**, the system employs a cyclic graph-based workflow where the LLM autonomously decides whether to query the knowledge base or respond directly.
- **🔄 Stateful Persistence**: Implements `MemorySaver` to preserve chat history, ensuring contextually aware responses within a single user session.
- **⚡ High-Performance Retrieval**: Utilizes **ChromaDB** for local vector storage and **OpenAI's** `text-embedding-3-small` for precision-grade semantic search.
- **📄 Seamless Ingestion**: Automated PDF processing, chunking, and indexing for immediate "chat-with-your-data" capabilities.

## 🛠️ Tech Stack

- **Orchestration**: [LangGraph](https://github.com/langchain-ai/langgraph) (StateGraph, Nodes, Edges)
- **Framework**: [LangChain](https://github.com/langchain-ai/langchain)
- **Vector Database**: [ChromaDB](https://www.trychroma.com/)
- **LLM**: OpenAI GPT models (Optimized for GPT-4o / GPT-5)
- **Embeddings**: OpenAI `text-embedding-3-small`

## 📂 Architecture

```text
.
├── chroma_db/                  # Local Vector Store persistence
├── your_document.pdf           # Target knowledge source
├── RAG_Agent.py                # Core Agentic logic & Graph definition
├── .env                        # Environment configuration
└── requirements.txt            # Project dependencies
```

## 🚀 Getting Started

### 1. Installation
```bash
git clone https://github.com/savinoo/RAG_Agent.git
cd RAG_Agent
python -m venv venv
source venv/bin/activate # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 2. Configuration
Create a `.env` file:
```env
OPENAI_API_KEY=your_key_here
```

### 3. Execution
Place your PDF in the root directory and run:
```bash
python RAG_Agent.py
```

## 🤖 How it Works
1. **Ingestion**: The script checks for an existing ChromaDB instance. If absent, it parses the PDF into semantic chunks and generates embeddings.
2. **Decision Loop**: When a query is received, the agent enters a LangGraph node.
3. **Tool Call**: If the agent determines retrieval is needed, it calls the ChromaDB tool.
4. **Final Response**: The agent synthesizes the retrieved context and conversation history into a final answer.

---
Developed by [Lucas Lorenzo Savino](https://github.com/savinoo)

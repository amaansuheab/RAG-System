📚 Production-Grade RAG System

A Retrieval-Augmented Generation (RAG) system built for scalable, modular, and production-like document question answering.
This project enables users to query custom knowledge bases using LLMs combined with vector search.

🚀 Features
📄 Document ingestion pipeline (PDFs / text files)
✂️ Intelligent text chunking
🧠 Embedding generation for semantic search
📦 Vector database storage (FAISS / Chroma / Pinecone compatible)
🔍 Semantic retrieval system
🤖 LLM-based response generation
🌐 FastAPI backend for serving queries
⚙️ Modular and production-oriented architecture
🧪 Extensible for evaluation and monitoring
🧠 System Architecture
User Query
   │
   ▼
Query Embedding
   │
   ▼
Vector Search (Similarity Retrieval)
   │
   ▼
Top-K Relevant Chunks
   │
   ▼
Prompt Construction
   │
   ▼
LLM Generation
   │
   ▼
Final Answer
📁 Project Structure
Production-grade-RAG-main/
│
├── data/                  # Raw & processed documents
├── ingestion/            # Data ingestion pipeline
├── embeddings/           # Embedding generation logic
├── vectorstore/          # Stored vector database
├── retrieval/            # Search & retrieval logic
├── generation/           # LLM response generation
├── api/                  # FastAPI backend
├── config/               # Configuration files
├── evaluation/           # (Optional) evaluation scripts
├── logs/                 # System logs
├── tests/                # Unit tests
│
├── requirements.txt
├── .env
└── README.md
⚙️ Tech Stack
Python 3.10+
LLMs: OpenAI / Llama / Ollama (configurable)
Embeddings: OpenAI Embeddings / SentenceTransformers
Vector DB: FAISS / ChromaDB / Pinecone
Backend: FastAPI
Data Processing: PyPDF, LangChain (optional)
📦 Installation
1. Clone the repository
git clone https://github.com/amaansuheab/RAG-System.git
cd RAG-System/Production-grade-RAG-main
2. Create virtual environment
python -m venv venv
source venv/bin/activate   # Mac/Linux
venv\Scripts\activate      # Windows
3. Install dependencies
pip install -r requirements.txt
🔐 Environment Variables

Create a .env file in the root directory:

OPENAI_API_KEY=your_api_key
MODEL_NAME=gpt-4
EMBEDDING_MODEL=text-embedding-3-large

VECTOR_DB_PATH=./vectorstore
CHUNK_SIZE=500
CHUNK_OVERLAP=50
📥 Data Ingestion

Place your documents inside:

data/raw/

Run ingestion pipeline:

python ingestion/ingest.py

This will:

Load documents
Clean text
Split into chunks
Generate embeddings
Store vectors in DB

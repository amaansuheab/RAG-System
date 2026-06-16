********Production-Grade RAG System**********

Overview

This project implements a Retrieval-Augmented Generation (RAG) system for building question-answering applications over custom documents. It retrieves relevant context from a vector database and uses a large language model to generate grounded responses.

The system is modular, extensible, and designed with production-level architecture in mind.

Features

Document ingestion pipeline for PDFs and text files
Text cleaning and chunking with configurable overlap
Embedding generation using LLM-compatible models
Vector database storage for semantic search
Top-k similarity-based retrieval system
Prompt construction with retrieved context
LLM-based response generation
FastAPI backend for serving queries
Config-driven architecture for flexibility
System Architecture
User Query
    |
    v
Query Embedding
    |
    v
Vector Similarity Search
    |
    v
Top-K Relevant Chunks
    |
    v
Context Assembly
    |
    v
Prompt Construction
    |
    v
LLM Generation
    |
    v
Final Response
Project Structure
Production-grade-RAG-main/
│
├── data/
│   ├── raw/                  # Input documents
│   └── processed/           # Cleaned and chunked data
│
├── ingestion/               # Document ingestion pipeline
│
├── embeddings/              # Embedding generation logic
│
├── vectorstore/             # Vector DB storage and indexing
│
├── retrieval/               # Retrieval and search logic
│
├── generation/              # Prompting and LLM response logic
│
├── api/                     # FastAPI application
│
├── config/                  # Configuration files
│
├── evaluation/              # Evaluation scripts (optional)
│
├── logs/                    # Logs and debugging outputs
│
├── tests/                   # Unit and integration tests
│
├── requirements.txt
├── .env
└── README.md
Tech Stack
Python 3.10+
FastAPI
OpenAI API / LLM providers (configurable)
SentenceTransformers / OpenAI Embeddings
FAISS / ChromaDB / Pinecone
PyPDF and text processing libraries
Installation
1. Clone the repository
git clone https://github.com/amaansuheab/RAG-System.git
cd RAG-System/Production-grade-RAG-main
2. Create virtual environment
python -m venv venv
source venv/bin/activate

Windows:

venv\Scripts\activate
3. Install dependencies
pip install -r requirements.txt
Environment Variables

Create a .env file in the root directory:

OPENAI_API_KEY=your_api_key
MODEL_NAME=gpt-4
EMBEDDING_MODEL=text-embedding-3-large

VECTOR_DB_PATH=./vectorstore
CHUNK_SIZE=500
CHUNK_OVERLAP=50
Data Ingestion

Place documents inside:

data/raw/

Run ingestion pipeline:

python ingestion/ingest.py
Pipeline Steps
Load documents
Clean text
Split into chunks
Generate embeddings
Store in vector database
Running the API

Start FastAPI server:

uvicorn api.main:app --reload

Server runs at:

http://127.0.0.1:8000

API documentation:

http://127.0.0.1:8000/docs
API Usage
Endpoint
POST /query
Request
{
  "query": "What is retrieval augmented generation?"
}
Response
{
  "answer": "RAG is a framework that combines retrieval of relevant documents with LLM generation to produce grounded responses.",
  "sources": [
    "document1.pdf",
    "document2.pdf"
  ]
}
Evaluation (Optional)

Run evaluation scripts:

python evaluation/evaluate.py

Metrics may include:

Context relevance
Answer faithfulness
Retrieval accuracy
Response quality
Production Considerations
Scalability
Distributed vector database support
Async ingestion pipeline
Horizontal scaling of API
Performance
Caching layer (Redis)
Hybrid retrieval (BM25 + vector search)
Reranking models
Reliability
Structured logging
Error handling and retries
Monitoring and tracing
Security
API authentication
Rate limiting
Input validation
Future Improvements
Hybrid retrieval (keyword + semantic search)
Cross-encoder reranking
Streaming responses from LLM
Multi-document reasoning
Conversation memory
Evaluation dashboard
Testing

Run tests:

pytest tests/
Author

Amaan Suheab
GitHub: https://github.com/amaansuheab

License

This project is licensed under the MIT License.

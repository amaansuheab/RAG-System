A Retrieval-Augmented Generation (RAG) system designed for document-based question answering using large language models and vector search. The system is structured to reflect production-level design with modular components for ingestion, embedding generation, retrieval, and response generation.

Overview

This project implements a full RAG pipeline that allows users to query custom documents. It retrieves relevant context from a vector database and uses a language model to generate grounded responses based on the retrieved information.

Features

Document ingestion pipeline for raw text and PDFs
Text chunking with configurable overlap
Embedding generation using configurable models
Vector database storage for semantic search
Retrieval system for top-k relevant chunks
LLM-based response generation using retrieved context
FastAPI-based service layer for query handling
Modular architecture separating ingestion, retrieval, and generation
Configurable environment settings for models and storage
Architecture

User Query
→ Query Embedding
→ Vector Similarity Search
→ Top-K Document Chunks Retrieved
→ Prompt Construction with Context
→ LLM Response Generation
→ Final Answer Returned

Project Structure
Production-grade-RAG-main/
│
├── data/              Raw and processed documents
├── ingestion/         Document loading and preprocessing pipeline
├── embeddings/        Embedding generation logic
├── vectorstore/       Vector database storage
├── retrieval/         Similarity search and retrieval logic
├── generation/        LLM prompt and response generation
├── api/               FastAPI application
├── config/            Configuration files
├── evaluation/        Evaluation scripts (optional)
├── logs/              Logging outputs
├── tests/             Unit tests
│
├── requirements.txt
├── .env
└── README.md
Technology Stack
Python 3.10 or higher
OpenAI API or compatible LLM providers
SentenceTransformers or OpenAI embeddings
FAISS, ChromaDB, or Pinecone for vector storage
FastAPI for backend service
Installation
Clone the repository
git clone https://github.com/amaansuheab/RAG-System.git
cd RAG-System/Production-grade-RAG-main
Create a virtual environment
python -m venv venv
source venv/bin/activate

On Windows:

venv\Scripts\activate
Install dependencies
pip install -r requirements.txt
Environment Variables

Create a .env file in the root directory with the following:

OPENAI_API_KEY=your_api_key
MODEL_NAME=gpt-4
EMBEDDING_MODEL=text-embedding-3-large
VECTOR_DB_PATH=./vectorstore
CHUNK_SIZE=500
CHUNK_OVERLAP=50
Data Ingestion

Place documents inside the following directory:

data/raw/

Run the ingestion pipeline:

python ingestion/ingest.py

This process performs:

Document loading
Text cleaning
Chunking
Embedding generation
Storage in vector database
Running the API

Start the FastAPI server:

uvicorn api.main:app --reload

The service will be available at:

http://127.0.0.1:8000

API documentation:

http://127.0.0.1:8000/docs
Example Request
POST /query

Request body:

{
  "query": "What is retrieval augmented generation?"
}

Response:

{
  "answer": "RAG combines retrieval of relevant documents with language model generation to produce grounded responses.",
  "sources": [
    "document1.pdf",
    "document2.pdf"
  ]
}
Evaluation

If evaluation is enabled, run:

python evaluation/evaluate.py

Typical metrics include:

Context relevance
Answer faithfulness
Retrieval accuracy
Production Considerations

To improve readiness for production environments:

Add caching layer (Redis or equivalent)
Implement logging and monitoring
Use hybrid retrieval (BM25 + vector search)
Add reranking model for better relevance
Containerize using Docker
Add authentication for API endpoints
Introduce rate limiting and request validation
Future Improvements
Hybrid retrieval combining keyword and semantic search
Cross-encoder reranking
Multi-query retrieval strategies
Streaming responses from LLM
Conversation memory support
Evaluation dashboard for system performance
Author

Amaan Suheab
GitHub: https://github.com/amaansuheab

License

This project is licensed under the MIT License.

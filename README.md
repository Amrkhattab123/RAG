# Retrieval-Augmented Generation (RAG) System

This repository contains an implementation of a Retrieval-Augmented Generation (RAG) system designed for querying large collections of documents. It is built using **LangChain** and leverages a **vector store** for document retrieval, followed by **answer generation** using a language model.

---

## 1. Setup Instructions

### Prerequisites

- Python 3.9 or later
- All dependencies listed in `requirements.txt`

### Installation Steps

#### Clone the Repository

```bash
git clone https://github.com/your-username/rag-system.git
cd rag-system
Create and Activate a Virtual Environment
# For Linux/macOS
python3 -m venv .venv
source .venv/bin/activate

# For Windows
python -m venv .venv
.venv\Scripts\activate
Install the Dependencies
pip install -r requirements.txt
Set Up Environment Variables
Create a .env file in the root directory with the following content:
VECTOR_DB_PATH=vector_store
EMBEDDING_MODEL=all-MiniLM-L6-v2
CHUNK_SIZE=500
CHUNK_OVERLAP=50
GROQ_API_KEY=your_api_key
BASE_URL=https://api.groq.com/openai/v1
LLM_MODEL=llama3-8b-8192
MAX_RETRIEVALS=5
Prepare Your Documents
Place your .pdf, .txt, or .docx files in the documents/ folder. Ensure that the formatting is clean for optimal performance.
Running the System
Start the interactive RAG interface:
python main.py
To run the evaluation mode instead:
python main.py --evaluate
2. System Architecture

Overview
The system follows the RAG (Retrieval-Augmented Generation) approach, combining:
Retrieval: Relevant documents are fetched using semantic search with vector embeddings.
Generation: A language model generates responses using the retrieved context.
Main Components
Document Loader: Reads and splits documents into chunks.
Vector Store: Stores vector embeddings for efficient retrieval.
Retrieval Pipeline: Matches query embeddings with document vectors.
Language Model: Generates answers based on retrieved content.
3. Experiment Results: Retrieval Strategies

Strategy 1: Basic Similarity Search
Description: Retrieves top-k results using cosine similarity.
Performance: Fast, but less accurate for diverse queries.
Strategy 2: Vector Search with Advanced Filtering
Description: Retrieves top-k documents and applies additional filters (e.g., removing duplicates, metadata filters).
Performance: More accurate, especially when metadata is available.
Strategy 3: Hybrid Search
Description: Combines vector-based and keyword-based retrieval.
Performance: Highest accuracy, but slower due to extra computation.
4. Evaluation Metrics

Retrieval Performance
Precision: Ratio of relevant documents among the retrieved.
Recall: Ratio of retrieved relevant documents out of all relevant ones.
F1-Score: Harmonic mean of precision and recall.
Answer Quality
Exact Match Accuracy: Percentage of generated answers that exactly match the ground truth.
Evaluation Table
Configuration	Precision	Recall	F1-Score
Basic Similarity	0.85	0.75	0.80
Advanced Filter	0.90	0.80	0.85
Hybrid Search	0.92	0.83	0.87
5. Strengths and Weaknesses

Strengths
Flexibility: Easily configurable with various embedding models and retrieval strategies.
Accuracy: Retrieves contextually relevant documents to boost response quality.
Weaknesses
Speed: More complex retrieval methods (e.g., hybrid search) are slower.
Data Dependency: Performance relies heavily on document quality.
6. Challenges and Solutions

Challenge 1: Retrieval Speed
Solution: Tested different vector databases and chunking strategies to improve efficiency.
Challenge 2: Noisy or Incomplete Data
Solution: Implemented filtering techniques to discard irrelevant or duplicated content.
7. Document Corpus

All source documents are stored in the documents/ directory. Supported file types:
.pdf
.txt
.docx
Ensure the documents are clean and well-formatted. Example contents might include:
sample1.pdf: Attention Is All You Need
sample2.pdf: GPT-3: Language Models Are Few-Shot Learners
sample3.pdf: Large Language Models Struggle With Logical Consistency
8. Future Enhancements

Model Upgrades: Integrate newer, more powerful LLMs.
Real-Time Retrieval: Enable live updates to the knowledge base.
Improved Evaluation: Incorporate metrics like BLEU, ROUGE, and fuzzy matching for better quality assessment.

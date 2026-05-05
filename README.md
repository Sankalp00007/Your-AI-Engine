VectorDB — Build a Vector Database from Scratch in C++
A fully working Vector Database built from scratch in C++ with a web UI.
Implements HNSW, KD-Tree, and Brute Force search algorithms side-by-side, plus a RAG pipeline powered by a local LLM via Ollama.

Built as an educational project to show how production vector databases like Pinecone, Weaviate, and Chroma actually work under the hood.

What This Project Does
Feature	Description
3 Search Algorithms	HNSW (production-grade), KD-Tree, Brute Force — run all three and compare speed
3 Distance Metrics	Cosine similarity, Euclidean distance, Manhattan distance
16D Demo Vectors	20 pre-loaded semantic vectors across 4 categories (CS, Math, Food, Sports)
2D PCA Scatter Plot	Live visualization of semantic space — watch clusters form
Real Document Embedding	Paste any text → Ollama embeds it with nomic-embed-text (768D)
RAG Pipeline	Ask questions about your documents → HNSW retrieves context → local LLM answers
Full REST API	CRUD endpoints: insert, delete, search, benchmark, hnsw-info

How It Works

Your Text
    │
    ▼
    
Ollama (nomic-embed-text)          ← converts text to a 768-dimensional vector
    │
    ▼
    
HNSW Index (C++)                   ← indexes the vector in a multilayer graph
    │
    ▼
    
Semantic Search                    ← finds nearest neighbors in vector space
    │
    ▼
    
Ollama (llama3.2)                  ← reads retrieved chunks, generates an answer
    │
    ▼
    
Answer
HNSW (Hierarchical Navigable Small World) is the same algorithm used by Pinecone, Weaviate, Chroma, and Milvus. It builds a multilayer graph where each layer is progressively sparser — searches start at the top layer and zoom in, achieving O(log N) complexity instead of O(N) for brute force.


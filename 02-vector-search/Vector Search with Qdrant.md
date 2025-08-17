# Vector Search with Qdrant

### Vector Search Basics

- Goes beyond keyword matching by comparing semantic meaning.

- Works across data types: text, images, audio.

- Uses embeddings (vector representations) and similarity metrics like **cosine similarity**.

### Why Qdrant

- Open-source, Rust-based, scalable vector search engine.

- Handles millions/billions of vectors efficiently.

- Supports Docker, Kubernetes, and cloud deployment.

- Python libraries: `qdrant-client` (for connection) and `fastembed` (for embedding vectors, lightweight, CPU-friendly, ONNX-based).

### Embedding Models

- Choice depends on data modality, domain, and resource constraints.

- FastEmbed supports dense, sparse, multi-vector, and rerankers.

- Vector dimension affects performance and semantic accuracy.

- Cosine similarity measures semantic closeness.

### Qdrant Structure

- **Point:** A single data item with ID, embedding(s), and optional metadata (Payload: used for filtering).

- **Collection:** Container for points; used to solve a specific problem.

- **Upsert/Batch Insert:** Efficiently embeds and uploads data to collections.

- Visualization (2D projections) & Graphs to help understand vector relationships.

### Hybrid Search

- Combines dense (semantic) and sparse (keyword/BM25) vectors.
  
  - Sparse vectors: mostly zeros, good for exact keyword matching.
    
    - BM25: statistical keyword relevance (TF + IDF).

- **Multi-stage retrieval pipelines:** fast initial search → rerank with another model.

- **Fusion** (e.g., Reciprocal Rank Fusion) combines rankings from multiple methods.

# High-Performance Sparse Recommendation Engine

## Overview
This project implements a scalable **content-based recommendation and similarity search engine** designed to handle high-dimensional, sparse datasets.

Using **Latent Semantic Analysis (LSA)** and **Matrix Factorization**, the system processes over **1.1 million entities** with **6,000+ sparse features** (based on the CMS Medicare Public Use File). It demonstrates efficient memory management and dimensionality reduction techniques to perform near real-time similarity lookups on single-node infrastructure.

## Key Engineering Features
* **Sparse Data Handling:** Utilizes `scipy.sparse` (CSR format) to efficiently store and manipulate a $1.1M \times 6k$ matrix, overcoming standard RAM limitations.
* **Dimensionality Reduction:** Implements **Truncated SVD** (Singular Value Decomposition) to project high-dimensional sparse vectors into a dense latent space (20-30 components).
* **Vectorized Inference:** Optimization of cosine similarity calculations to achieve millisecond-latency for K-Nearest Neighbor (KNN) queries.
* **Scalable Pipeline:** Modular design separating data ingestion, transformation, and inference, applicable to any high-cardinality interaction dataset (e.g., User-Item, Document-Term).

## Architecture

```mermaid
graph LR
    A[Raw Data Ingestion] --> B[Pivot & Sparse Matrix Construction]
    B --> C[L2 Normalization]
    C --> D[Truncated SVD <br> Dimensionality Reduction]
    D --> E[Vectorized Cosine Similarity]
    E --> F[Top-K Neighbor Retrieval]
```

**Dataset:** [Medicare Physician and Other Practitioners](https://data.cms.gov/provider-summary-by-type-of-service/medicare-physician-other-practitioners/medicare-physician-other-practitioners-by-provider-and-service/data)

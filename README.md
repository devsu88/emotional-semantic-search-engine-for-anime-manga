# Gen AI Intensive Course Capstone 2025Q1: Advanced Emotional Semantic Search Engine for Anime/Manga (RAG + ChromaDB + Re-ranking)  

## The Challenge  
Discovering new anime or manga often goes beyond simple genre tags or keyword searches. Users frequently look for titles based on a specific feeling, atmosphere, vibe, or inspiration derived from past experiences (e.g., "something melancholic and beautiful like Your Name", "an epic adventure that gets you hyped like Gurren Lagann"). Traditional search methods struggle to capture these nuanced, emotional queries.

## Our Enhanced Solution:   
A Sophisticated RAG Pipeline: This project tackles the challenge by implementing an advanced Retrieval-Augmented Generation (RAG) system specifically designed for vibe-based anime/manga discovery. The pipeline involves several key stages:
- Data Loading & Filtering: We start with datasets containing anime information (synopses, genres, scores, popularity, etc.) and user reviews. Crucially, we apply genre filtering upfront to exclude categories that might skew recommendations, ensuring a more relevant starting pool.
- Preprocessing: Text data (synopses, reviews) is cleaned and prepared for processing.
Semantic Embedding: We leverage Google's powerful text-embedding-004 model via the google-genai library to generate rich semantic embeddings for the anime synopses, capturing their underlying meaning.
- Vector Storage & Indexing: Instead of in-memory arrays, we utilize ChromaDB, a persistent vector database, to efficiently store and index the anime embeddings along with relevant metadata (title, genre, score, popularity). This allows for persistence across sessions and faster retrieval.
- Hybrid Retrieval & Re-ranking: When a user query is received:
  - A vector search is performed in ChromaDB to retrieve an initial set of k_initial candidates based on semantic similarity between the query and anime synopses.
  - A crucial re-ranking step is applied to these candidates. We calculate a combined score based on weighted factors: semantic similarity, user score (quality), and popularity rank (inverse rank, lower is better). This allows high-quality or popular relevant items to surface even if they aren't the absolute closest semantically.
- Context Augmentation: The top k re-ranked anime are then augmented with additional context: their detailed synopses and relevant user review snippets, providing qualitative insights into the perceived vibe and emotional impact.
- Motivated Generation: Finally, Google's Gemini LLM is prompted with the original user query and the rich, augmented context (re-ranked results, synopses, metadata, reviews). The LLM synthesizes this information to generate a personalized, motivated recommendation, explaining why the suggested titles might match the user's desired feeling.
- Notebook Objective: This notebook provides a comprehensive, step-by-step implementation of this advanced RAG pipeline. It covers data loading, filtering, preprocessing, embedding generation, ChromaDB integration, the hybrid retrieval/re-ranking mechanism, review augmentation, LLM-based generation, and includes a section on evaluating the system's performance.

## Key Technologies & Gen AI Capabilities Demonstrated:

- Retrieval-Augmented Generation (RAG): The core architecture.
- Semantic Embeddings: Using google-genai's text-embedding-004.
- Vector Database / Vector Search: Implementation with chromadb.
- LLM Integration: Using google-genai's gemini-2.0-flash for response generation.
- Re-ranking Algorithms: Combining semantic similarity with metadata features.
- Data Preprocessing & Filtering: Essential steps for quality results.
- Context Augmentation: Using reviews and metadata to enrich LLM input.
- Libraries: pandas, numpy, google-genai, chromadb, scikit-learn.

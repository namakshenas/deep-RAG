# Cached based Retrieval-Augmented Generation (RAG) Pipeline Diagram

1. **Step 1 - User submits query**: The user’s query initiates the RAG pipeline.
2. **Step 2 - Cache Check**: Checks for an existing response in the cache.
3. **Step 3 - Embedding Generation**: If not cached, generates and augments embeddings.
4. **Step 4 - Retrieval Process**: Multi-stage retrieval and re-ranking of relevant documents.
5. **Step 5 - Relevance Scoring**: Scores the retrieved documents for contextual relevance.
6. **Step 6 - Response Generation**: Llama generates the response using contextual documents.
7. **Step 7 - Caching**: Stores the response in the cache for future similar queries.
8. **Step 8 - Feedback Integration**: Collects user feedback to iteratively improve the pipeline.

```mermaid
zenuml
    title Annotators
    @Actor Alice
    @Database Bob
    Alice->Bob: Hi Bob
    Bob->Alice: Hi Alice



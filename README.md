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
sequenceDiagram
    participant User
    participant Preprocessor
    participant Cache
    participant EmbeddingService
    participant RetrievalPipeline
    participant KnowledgeBase
    participant ContentStore
    participant Scoring
    participant LLM
    participant CachingSystem
    participant FeedbackSystem

    Note over User, Preprocessor: Step 1 - User submits query

    User ->> Preprocessor: Send Query
    Preprocessor ->> Cache: Check Cache & Similarity

    Note over Cache: Step 2 - Check if similar response is cached

    alt Cache Hit
        Cache ->> User: Return Cached Response
        Note over Cache, User: Cache hit - return response to user
    else Cache Miss
        Cache ->> EmbeddingService: Proceed to Embedding Generation

        Note over EmbeddingService: Step 3 - Generate and augment embeddings

        EmbeddingService ->> EmbeddingService: Generate Query Embedding
        EmbeddingService ->> EmbeddingService: Embedding Augmentation (Semantic Expansion)
        EmbeddingService ->> RetrievalPipeline: Pass Augmented Embedding

        Note over RetrievalPipeline: Step 4 - Multi-stage retrieval process

        RetrievalPipeline ->> RetrievalPipeline: Initial Vector Store Search
        RetrievalPipeline ->> RetrievalPipeline: Dynamic Re-ranking
        RetrievalPipeline ->> KnowledgeBase: Retrieve Additional Relevant Data
        KnowledgeBase ->> RetrievalPipeline: Return Top-M Matches
        RetrievalPipeline ->> RetrievalPipeline: Re-ranking and Filtering
        RetrievalPipeline ->> ContentStore: Retrieve Documents Based on Embeddings

        Note over Scoring: Step 5 - Advanced relevance and contextual scoring

        ContentStore ->> Scoring: Pass Retrieved Documents
        Scoring ->> Scoring: Advanced Relevance Scoring
        Scoring ->> Scoring: Contextual Scoring and Relevance Filtering

        Note over LLM: Step 6 - Response generation with context

        Scoring ->> LLM: Send Top-k Documents as Context
        LLM ->> LLM: Generate Response with Contextual Documents
        LLM ->> LLM: Track Multi-Turn Dialogue Context

        Note over CachingSystem: Step 7 - Store generated response in cache

        LLM ->> CachingSystem: Store Response in Cache
        CachingSystem ->> FeedbackSystem: Update Cache and Prepare Feedback System
        LLM ->> User: Return Generated Response

        Note over FeedbackSystem: Step 8 - Collect feedback and improve system

        User ->> FeedbackSystem: Provide Feedback on Response
        FeedbackSystem ->> EmbeddingService: Adaptive Feedback Integration
        FeedbackSystem ->> RetrievalPipeline: Model and Embedding Updates
    end



```mermaid
zenuml
    User -> Static_RAG: Trigger Weekly Task
    Static_RAG -> Publishers: Search for DEA Papers
    Publishers --> Static_RAG: Return Relevant Papers
    Static_RAG -> Knowledge_Base: Store Processed Papers
    
    User -> Dynamic_RAG: Submit DEA Model Inputs
    Dynamic_RAG -> Knowledge_Base: Query Relevant Information
    Dynamic_RAG -> Report_Generator: Generate Reports
    Report_Generator --> User: Deliver Performance Report
    
    Static_RAG -> Knowledge_Base: Update with New Papers
    Dynamic_RAG -> Knowledge_Base: Retrieve Data
end

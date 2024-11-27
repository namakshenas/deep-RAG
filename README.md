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
flowchart TD
  A[AI Agent] --> B[Static RAG]
  A --> C[Dynamic RAG]

  %% Static RAG Workflow
  B --> B1[Web Scraper]
  B1 --> B2[Publisher Websites]
  B2 --> B3[Interesting Papers about DEA]
  B3 --> B4[Indexed Data Repository]
  B4 --> B5[Weekly Activation]

  %% Dynamic RAG Workflow
  C --> C1[Input Handler]
  C1 --> C2[Mathematical Models of DEA]
  C2 --> C3[Dynamic Information Retrieval]
  C3 --> C4[Performance Analysis]
  C4 --> C5[Report Generator]
  C5 --> C6[Performance Management Reports]

  %% Shared Components
  B4 --> D[Knowledge Base]
  C4 --> D
  D --> C3

  %% Labels
  classDef static fill:#bbf,stroke:#000,stroke-width:2px;
  classDef dynamic fill:#bfb,stroke:#000,stroke-width:2px;
  class B,B1,B2,B3,B4,B5 static;
  class C,C1,C2,C3,C4,C5,C6 dynamic;



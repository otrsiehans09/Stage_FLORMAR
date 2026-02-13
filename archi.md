```mermaid




graph TB
    %% FRONTEND
    subgraph "FRONTEND (Hostinger / WordPress)"
        UI[Chat Interface<br/>JS / CSS]
        WP_DB[(WP Database)]
    end

    %% BACKEND API
    subgraph "BACKEND API (FastAPI)"
        API_GATE[API Gateway<br/>/ask]
        AUTH[Auth & Access Control]
        FILTER[Input / Output Filtering]
    end

    %% CORE ENGINE
    subgraph "CORE ENGINE (Python / VS Code)"
        ROUTER{Request Router}
        RAG[RAG Engine]
        PROMPT[Prompt Manager]
    end

    %% DATA LAYER
    subgraph "DATA LAYER"
        VDB[(Vector DB<br/>ChromaDB)]
        SQL[(Product DB<br/>Stock / Availability)]
        FILE[Source Files<br/>JSON / PDF]
    end

    %% AI
    subgraph "AI SERVICES"
        LLM[LLM<br/>Ollama / OpenAI / Claude]
    end

    %% OBSERVABILITY
    subgraph "OBSERVABILITY"
        LOGS[(Logs / Metrics)]
    end
    

    %% FUTURE ML
    subgraph "ANALYTICS / ML (Future)"
        ML[Query Analysis<br/>Classification / Ranking]
    end

    %% FLOWS
    UI <--> API_GATE
    API_GATE --> AUTH
    AUTH --> FILTER
    FILTER --> ROUTER

    ROUTER --> |Availability| SQL
    ROUTER --> |Knowledge Search| RAG
    RAG --> VDB

    FILE --> |Ingestion| VDB

    ROUTER --> PROMPT
    PROMPT <--> LLM
    PROMPT --> API_GATE

    %% LOGGING
    ROUTER --> LOGS
    PROMPT --> LOGS

    %% FUTURE ML
    LOGS -.-> ML
    ML -.-> ROUTER


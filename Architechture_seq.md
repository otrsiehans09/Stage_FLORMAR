```mermaid

sequenceDiagram
    autonumber
    actor Client as Client (Site Web)
    participant WP as WordPress / JS Interface
    participant API as FastAPI (Backend)
    participant RAG as RAG Engine
    participant VDB as Vector DB (ChromaDB)
    participant SQL as Product DB (Stock)
    participant LLM as LLM (Ollama / OpenAI)
    participant Logs as Logs / Monitoring

    Client->>WP: Question produit

    WP->>API: POST /ask

    API->>RAG: Classification & Routage
    RAG->>Logs: Log question

    alt Question Stock
        RAG->>SQL: Requête disponibilité
        SQL-->>RAG: Donnée réelle
    else Question Usage / Doc
        RAG->>VDB: Similarité sémantique
        VDB-->>RAG: Context
    end

    RAG->>RAG: Construction prompt sécurisé
    RAG->>LLM: Prompt
    LLM-->>RAG: Réponse

    RAG->>RAG: Validation + Formatage
    RAG->>Logs: Log réponse

    RAG-->>API: Réponse finale
    API-->>WP: JSON
    WP-->>Client: Affichage chat



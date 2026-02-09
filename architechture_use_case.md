```mermaid
%%{init: {'theme': 'default'}}%%
usecaseDiagram
    actor "Client (Visiteur)" as User
    actor "Administrateur (Société)" as Admin

    package "Système Chatbot Sales Pro" {
        usecase "Dialoguer avec le chatbot" as UC0
        usecase "Exprimer un besoin produi:t" as UC1
        usecase "Comparer deux produits" as UC2
        usecase "Vérifier la disponibilité (Stock réel)" as UC3
        usecase "Obtenir des conseils d'usage" as UC4
        usecase "Générer une réponse fiable\n(RAG + LLM)" as UC7
        
        usecase "Mettre à jour le catalogue\n(Ingestion documents & données)" as UC5
        usecase "Consulter les logs & analytics" as UC6
    }

    %% Interactions Client
    User --> UC0
    UC0 --> UC1
    UC0 --> UC2
    UC0 --> UC3
    UC0 --> UC4

    %% Interactions Admin
    Admin --> UC5
    Admin --> UC6

    %% Relations internes
    UC2 ..> UC1 : <<include>>
    UC3 ..> UC1 : <<extend>>

    UC1 ..> UC7 : <<include>>
    UC2 ..> UC7 : <<include>>
    UC3 ..> UC7 : <<include>>
    UC4 ..> UC7 : <<include>>
```

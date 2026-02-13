```mermaid



%%{init: {'theme':'neutral'}}%%
graph TB
    title["Diagramme de Cas d'Utilisation - Chatbot Commercial"]
    
    subgraph "Système Chatbot Commercial"
        UC1["Consulter les prix"]
        UC2["Comparer des produits"]
        UC3["Vérifier la disponibilité"]
        UC4["Obtenir des conseils généraux"]
        UC5["Se connecter / S'authentifier"]
        UC6["Obtenir des recommandations personnalisées"]
        UC7["Accéder à l'historique des commandes"]
        UC8["Suivre une commande en cours"]
        UC9["Gérer sa liste de souhaits"]
        UC10["Recevoir des alertes de prix"]
    end

    acteur1(("Visiteur<br/>(non connecté)"))
    acteur2(("Client<br/>(connecté)"))

    acteur1 --> UC1
    acteur1 --> UC2
    acteur1 --> UC3
    acteur1 --> UC4
    acteur1 --> UC5

    acteur2 --> UC1
    acteur2 --> UC2
    acteur2 --> UC3
    acteur2 --> UC6
    acteur2 --> UC7
    acteur2 --> UC8
    acteur2 --> UC9
    acteur2 --> UC10
    
    note_right_of UC6: "Basées sur l'historique d'achat<br/>et les préférences"
    note_right_of UC10: "Notifications personnalisées<br/>sur les produits suivis"
    
    style title fill:#transparent,stroke:#transparent
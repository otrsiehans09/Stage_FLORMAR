```mermaid



classDiagram

%% =====================
%% CLASSES PRINCIPALES
%% =====================

class Utilisateur {
  +String userId
  +String type
  +envoyerMessage(message)
  +consulterReponse(reponse)
}

class Administrateur {
  +mettreAJourCatalogue()
  +consulterAnalytics()
}

class Chatbot {
  +String chatbotId
  +String language
  +Boolean status
  +recevoirMessage(message)
  +detecterIntention(message)
  +genererReponse(besoin)
}

class Besoin {
  +String besoinId
  +String categorie
  +Float budget
  +String contraintes
  +validerBesoin()
}

class Produit {
  +String produitId
  +String nom
  +String categorie
  +Float prix
  +Integer stock
  +String description
  +estDisponible()
  +comparerAvec(produit)
}

class Catalogue {
  +String catalogueId
  +List~Produit~ produits
  +rechercherProduits(besoin)
  +ajouterProduit(produit)
  +mettreAJourProduit(produit)
}

class MoteurRAG {
  +String sourceDonnees
  +String indexVectoriel
  +indexerDocuments()
  +recupererContexte(besoin)
  +genererReponse(contexte)
}

class Reponse {
  +String reponseId
  +String contenu
  +Date date
  +formatter()
}

class IngestionService {
  +String source
  +String format
  +importerDonnees()
  +nettoyerDonnees()
  +mettreAJourCatalogue()
}

class Log {
  +String logId
  +String type
  +Date timestamp
  +String details
  +enregistrer()
}

%% =====================
%% HERITAGE
%% =====================

Administrateur --|> Utilisateur

%% =====================
%% RELATIONS
%% =====================

Utilisateur --> Chatbot : utilise
Chatbot --> Besoin : crée
Chatbot --> Catalogue : consulte
Catalogue "1" --> "*" Produit : contient
Chatbot --> MoteurRAG : interroge
MoteurRAG --> Reponse : génère
Chatbot --> Log : enregistre
Administrateur --> IngestionService : utilise
IngestionService --> Catalogue : met à jour

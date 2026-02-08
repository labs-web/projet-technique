# Analyse Fonctionnelle Globale

## 1. Acteurs
*   **Visiteur** : Utilisateur non connecté, navigue sur la partie publique du site.
*   **Utilisateur Authentifié (Auteur)** : Utilisateur connecté, peut gérer ses propres contenus (articles).
*   **Administrateur** : Utilisateur disposant de droits étendus pour gérer l'ensemble du contenu et la configuration du site.
*   **Système Tiers** : Application externe consommant l'API (ex: application mobile).

## 2. Fonctionnalités
### Consultation (Front-Office)
*   Affichage de la page d'accueil avec les derniers articles.
*   Consultation de la liste paginée des articles.
*   Consultation du détail d'un article complet.
*   Filtrage des articles par catégorie.
*   Recherche textuelle d'articles (titre/contenu).

### Administration (Back-Office)
*   Authentification sécurisée (Login/Logout).
*   Gestion des Articles (CRUD) :
    *   Créer un nouvel article.
    *   Modifier un article existant.
    *   Supprimer un article.
    *   Lister les articles administrables.
*   Gestion des Catégories (CRUD) :
    *   Créer une nouvelle catégorie.
    *   Modifier une catégorie existante.
    *   Supprimer une catégorie.
    *   Lister les catégories.

### Logique Métier & Sécurité
*   Contrôle d'accès (Autorisation) : Restreindre la modification/suppression d'un article à son créateur (ou admin).
*   Gestion des Rôles : Distinction des droits entre Admin, Éditeur et Lecteur.

### Interface & Expérience Utilisateur
*   Interactivité sans rechargement de page (AJAX) pour la recherche et le filtrage.
*   Utilisation de composants dynamiques (Modales, Dropdowns).

### API REST
*   Exposition des ressources (Articles, Catégories) via une API JSON.
*   Authentification API via jetons (Sanctum).

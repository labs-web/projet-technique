# Analyse Globale des Besoins : Projet Technique (Blog)

Ce document recense l'ensemble des fonctionnalités attendues pour le projet, indépendamment de leur planification dans le temps.

## 1. Acteurs
*   **Visiteur (Public)** : Utilisateur non authentifié accédant au contenu public.
*   **Utilisateur (Authentifié)** : Utilisateur connecté ayant un compte (Auteur).
*   **Administrateur** : Utilisateur disposant de droits étendus (gestion globale).
*   **Système (API Client)** : Consommateur externe des données via l'API.

## 2. Fonctionnalités par Domaine

### 2.1. Consultation (Front-Office)
*   **Consulter la page d'accueil** : Visualiser les derniers articles mis en avant.
*   **Lister les articles** : Parcourir l'ensemble des articles publiés.
*   **Lire un article** : Afficher le contenu complet d'un article spécifique.
*   **Filtrer par catégorie** : Afficher uniquement les articles liés à une catégorie sélectionnée.
*   **Rechercher un article** : Trouver un article via des mots-clés (Titre, Contenu).

### 2.2. Gestion de Contenu (Back-Office)
*   **Se connecter** : S'authentifier pour accéder à l'espace d'administration.
*   **Gérer les Articles (CRUD)** :
    *   Créer un nouvel article (Titre, Contenu, Image, Catégories).
    *   Modifier un article existant.
    *   Supprimer un article.
    *   Lister ses propres articles (ou tous selon rôles).
*   **Gérer les Catégories (CRUD)** :
    *   Créer une catégorie.
    *   Modifier une catégorie.
    *   Supprimer une catégorie.
    *   Lister toutes les catégories.

### 2.3. Sécurité & Droits
*   **Protéger l'accès** : Restreindre l'accès au Back-Office aux utilisateurs authentifiés.
*   **Autoriser la modification** : Un utilisateur ne peut modifier/supprimer que ses propres articles (sauf Admin).
*   **Gérer les Rôles** : Attribuer des rôles (Admin, Éditeur, Lecteur) aux utilisateurs.

### 2.4. Interface & Expérience (UX)
*   **Interaction dynamique** : Rechercher et filtrer sans rechargement de page (AJAX/Interactivité).

### 2.5. API & Interopérabilité
*   **S'authentifier via Token** : Obtenir un accès sécurisé pour les clients API.
*   **Consommer les données** : Récupérer la liste et le détail des articles au format JSON.

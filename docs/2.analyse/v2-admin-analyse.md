# Analyse Fonctionnelle - V2 : Back-Office Admin

## Description
Création d'un espace sécurisé permettant aux administrateurs et auteurs de gérer le contenu du blog. L'accès est restreint aux utilisateurs authentifiés.

## Fonctionnalités Attendues

### 1. Authentification
**En tant que** : Utilisateur
**Je veux** : Me connecter avec email et mot de passe.
**Afin de** : Accéder à l'interface de gestion.

- Formulaire de connexion sécurisé.
- Protection de toutes les pages d'administration.

### 2. Gestion des Catégories
**En tant que** : Administrateur
**Je veux** : Créer, modifier et supprimer des catégories.
**Afin de** : Organiser les articles.

- **Liste** : Tableau des catégories existantes.
- **Création** : Formulaire simple (Nom). Le "Slug" doit être généré automatiquement ou saisi.
- **Édition** : Modification du nom.
- **Suppression** : Possible uniquement si cela ne "casse" pas des articles (ou gestion propre du détachement).

### 3. Gestion des Articles (CRUD)
**En tant que** : Auteur
**Je veux** : Rédiger et publier des articles.
**Afin de** : Alimenter le blog.

- **Liste** : Tableau de bord de mes articles (Titre, Date, Statut).
- **Création / Édition** :
  - Saisie du Titre.
  - Saisie du Contenu (zone de texte large).
  - Choix des Catégories (multi-sélection).
  - *Règle* : L'auteur est automatiquement l'utilisateur connecté.
- **Suppression** : Retirer un article.

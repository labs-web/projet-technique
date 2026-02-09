# Analyse Fonctionnelle Globale : Le Laboratoire (Blog)

## Introduction
Ce document recense l'ensemble des fonctionnalités du projet "Le Laboratoire", une plateforme de blog destinée à l'apprentissage technique progressif.

## Acteurs
- **Visiteur** : Utilisateur non connecté accédant au contenu public.
- **Utilisateur Connecté (Auteur/Éditeur)** : Utilisateur authentifié pouvant gérer ses propres contenus.
- **Administrateur** : Utilisateur disposant de droits étendus pour la gestion système et modération.
- **Client API** : Application tierce consommant les données via l'interface programmatique.

## Règles de Gestion (Business Rules)

### Contraintes et Relations
- **Multi-Catégories** : Un article peut être associé à plusieurs catégories (Relation N-N).
- **Auteur Unique** : Un article est rédigé par un seul auteur (Relation 1-N).
- **Terminologie** : Utilisation stricte du terme "Category" (et non Tag ou Label).

### Permissions et Sécurité
- **Accès Public** : La lecture des articles (Liste et Détail) est accessible sans authentification.
- **Authentification Requise** : Toute opération d'écriture (Création, Modification, Suppression) nécessite une connexion.
- **Propriété (Policy)** : Seul l'auteur d'un article peut le modifier ou le supprimer (sauf autorisation Admin).
- **Rôles Hérarchiques** : Distinction des droits selon les rôles (Admin > Éditeur > Lecteur).
- **Protection API** : Les accès API sont sécurisés par tokens (Sanctum).

## Fonctionnalités par Acteur

### 👤 Visiteur
- **Consulter les articles** : Afficher la liste des articles publiés sur la page d'accueil.
- **Lire un article** : Accéder au détail complet d'un article (Titre, Contenu, Auteur, Date, Catégories).
- **Filtrer les articles** : Trier ou restreindre la liste des articles par catégorie.
- **Rechercher un article** : Effectuer une recherche textuelle instantanée sur les titres ou contenus.

### ✍️ Utilisateur Connecté (Auteur)
- **S'authentifier** : Se connecter à l'application (Login/Logout).
- **Gérer son profil** : Modifier ses informations personnelles.
- **Créer un article** : Rédiger et publier un nouvel article associé à son compte.
- **Modifier ses articles** : Éditer le contenu d'un article dont il est l'auteur (selon règle de propriété).
- **Supprimer ses articles** : Retirer un article dont il est l'auteur.

### 🛡️ Administrateur
- **Gérer les catégories** : Créer, modifier et supprimer les catégories.
- **Gérer tous les articles** : Modération et édition de n'importe quel article, quel que soit l'auteur.
- **Gérer les utilisateurs** : Créer, modifier, supprimer des utilisateurs et gérer leurs rôles.
- **Visualiser le Tableau de Bord** : Afficher la page d'accueil d'administration contenant les statistiques globales (Nombre total d'articles, Nombre total d'inscrits) et le menu de navigation principal.

### 🤖 Client API
- **Consommer les données publiques** : Récupérer la liste et le détail des articles au format JSON.
- **S'authentifier via Token** : Obtenir un jeton d'accès sécurisé pour les requêtes protégées.

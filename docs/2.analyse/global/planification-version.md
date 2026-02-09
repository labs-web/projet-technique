# Planification des Versions (Roadmap)

## Version 1 : Lecture Publique (MVP)
- **Slug** : `v1-public`
- **Objectif** : Mettre en place la structure de base et l'affichage public du contenu (Consultation).
- **Description** : Première version axée sur le Front-Office pour les visiteurs non authentifiés.
- **Fonctionnalités Clés** :
  - Visiteur : Consulter la liste des articles (Pagination, Tri).
  - Visiteur : Consulter le détail d'un article (Contenu, Auteur, Catégorie).

## Version 2 : Administration (CRUD)
- **Slug** : `v2-admin`
- **Objectif** : Permettre aux administrateurs de gérer le contenu via un Back-Office sécurisé.
- **Description** : Implémentation de l'authentification et des opérations CRUD de base.
- **Fonctionnalités Clés** :
  - Administrateur : Authentification sécurisée (Login/Logout).
  - Administrateur : Gérer les Catégories (Création, Lecture, Modification, Suppression).
  - Administrateur : Gérer les Articles (Création, Lecture, Modification, Suppression).

## Version 3 : Autorisation Native (Policies)
- **Slug** : `v3-auth`
- **Objectif** : Affiner les droits d'accès pour les auteurs via les mécanismes natifs de Laravel.
- **Description** : Introduction des règles métier de propriété (un auteur ne gère que ses articles).
- **Fonctionnalités Clés** :
  - Auteur : Gérer ses propres articles uniquement.
  - Système : Application des Policies et Gates pour sécuriser les actions.

## Version 4 : Interactivité AJAX (Native)
- **Slug** : `v4-sap-ajax`
- **Objectif** : Améliorer l'expérience utilisateur (UX) sans rechargement de page.
- **Description** : Utilisation de Fetch API / AJAX natif pour dynamiser la consultation.
- **Fonctionnalités Clés** :
  - Visiteur : Rechercher des articles instantanément.
  - Visiteur : Filtrer les articles par catégorie sans rechargement.

## Version 5 : Interactivité Alpine.js
- **Slug** : `v5-spa-alpine`
- **Objectif** : Moderniser la couche interface avec une librairie légère.
- **Description** : Remplacement/Amélioration des scripts natifs par Alpine.js pour une meilleure maintenabilité.
- **Fonctionnalités Clés** :
  - Visiteur : Interface réactive (Modales, Dropdowns, Transitions).
  - Système : Intégration propre d'Alpine.js dans la stack Blade.

## Version 6 : Permissions Avancées (Spatie)
- **Slug** : `v6-spatie`
- **Objectif** : Gérer des rôles complexes et dynamiques.
- **Description** : Intégration du package `spatie/laravel-permission` pour un RBAC complet.
- **Fonctionnalités Clés** :
  - Administrateur : Gérer les Rôles et Permissions dynamiquement.
  - Système : Middleware de vérification des permissions en base de données.

## Version 7 : API REST
- **Slug** : `v7-api`
- **Objectif** : Exposer les données pour des systèmes tiers (Mobile, SPA).
- **Description** : Création d'une API RESTful sécurisée.
- **Fonctionnalités Clés** :
  - Système Externe : Authentification via Token (Sanctum).
  - Système Externe : Consommation des articles via endpoints JSON standardisés.

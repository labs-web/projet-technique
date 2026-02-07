---
trigger: always_on
---

# Standards de Qualité : Code, Sécurité et Documentation

## Objectif

Garantir un niveau de qualité professionnel du code en imposant les standards PSR-12, les bonnes pratiques Laravel, les règles de sécurité essentielles, et un format de documentation Markdown lisible et maintenable.

## Instructions

### 1. Standards de Code

- **Respecter** les standards PSR-12 pour le code PHP.
- **Utiliser** le typage strict (`declare(strict_types=1);`) autant que possible.
- **Nommer** :
  - Le code en **Anglais** (Variables, Fonctions, Classes).
  - La base de données en **Anglais** (Snake case : `user_id`, `created_at`).
  - Les commits Git en **Français** (cohérence projet).
- **Commenter** en français uniquement pour expliquer une logique complexe :
  - Expliquer le **"Pourquoi"**, pas le **"Comment"**.
  - Éviter les commentaires redondants avec le code.

### 2. Sécurité

- **Utiliser** l'ORM Eloquent ou les bindings PDO pour toutes les requêtes SQL.
- **Utiliser** l'échappement par défaut de Blade `{{ }}` pour prévenir les failles XSS.
- **Utiliser** les façades `Hash` pour hacher les mots de passe (jamais de stockage en clair).
- **Protéger** tous les endpoints sensibles avec le middleware `auth:sanctum` pour les API.
- **Valider** toutes les entrées utilisateur via les FormRequests Laravel.

### 3. Bonnes Pratiques Laravel

- **Appliquer** le principe "Fat Model, Skinny Controller" ou utiliser le Service Pattern pour la logique complexe.
- **Utiliser** les Resource Controllers pour le CRUD standard.
- **Utiliser** les Migrations pour toute modification de la base de données.
- **Éviter** de mettre de la logique métier dans les Vues (Blade).

### 4. Documentation Markdown

- **Rédiger** toute documentation en **Français**.
- **Privilégier** un format clair, concis et aéré.
- **Structurer** le contenu avec des titres hiérarchiques (`##`, `###`).
- **Utiliser** des listes à puces (`-`) ou des listes imbriquées pour organiser l'information.
- **Convertir immédiatement** toute tentation de tableau en liste à puces ou liste de définitions.

## Interdictions

### Code et Sécurité

- **INTERDICTION** d'utiliser des requêtes SQL concaténées (risque d'injection SQL).
- **INTERDICTION** de stocker des mots de passe en clair dans la base de données.
- **INTERDICTION** d'utiliser `{!! $variable !!}` sans validation préalable (risque XSS).
- **INTERDICTION** de créer des endpoints API sans protection `auth:sanctum` pour les opérations sensibles.
- **INTERDICTION** d'accepter des données utilisateur sans validation via FormRequest.
- **INTERDICTION** de mettre de la logique métier dans les contrôleurs ou les vues.

### Documentation Markdown

- **INTERDICTION ABSOLUE** d'utiliser des tableaux Markdown (`| col | col |`).
  - **Raison** : Difficulté de lecture, d'édition et problèmes de rendu.
  - **Action obligatoire** : Transformer immédiatement en liste à puces ou liste de définitions.



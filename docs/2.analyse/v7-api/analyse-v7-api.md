# Analyse Fonctionnelle - V7 : API REST

## 1. Introduction
Ouverture des données de l'application via une API RESTful standardisée et sécurisée, destinée à être consommée par des clients externes (ex: Application Mobile).

## 2. Acteurs
- **Système Externe** : Client API (Postman, App Mobile, SPA externe).

## 3. Règles de Gestion (Business Rules)
### Standardisation
- **Format** : Toutes les réponses doivent être au format JSON standard (`data`, `meta`).
- **Codes HTTP** : Utilisation stricte des codes de statut HTTP appropriés (200, 201, 401, 403, 404).

### Sécurité
- **Token** : Authentification requise via Bearer Token (Laravel Sanctum).

## 4. Fonctionnalités
### Système Externe
- **Authentification API** (Obtention du Token)
- **Consulter la liste des articles (API)**
- **Consulter le détail d'un article (API)**

# Analyse Fonctionnelle - V6 : Permissions Avancées (Spatie)

## 1. Introduction
Implémentation d'un système complet de gestion des rôles et des permissions (RBAC) via le package `spatie/laravel-permission`, permettant une gestion dynamique des droits depuis le Back-Office.

## 2. Acteurs
- **Administrateur** : Gestionnaire des droits.
- **Système** : Middleware de vérification.

## 3. Règles de Gestion (Business Rules)
### RBAC (Role-Based Access Control)
- **Persistance** : Rôles et Permissions stockés en base de données.
- **Dynamisme** : Possibilité d'ajouter/retirer une permission à un rôle sans redéployer le code.

## 4. Fonctionnalités
### Administrateur
- **Gérer les Rôles** (Créer, Editer, Assigner des permissions)
- **Gérer les Permissions** (Créer, Lister)
- **Assigner un rôle à un utilisateur**

### Système
- **Middleware de vérification des permissions en base de données**

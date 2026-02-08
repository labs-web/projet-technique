# Analyse Fonctionnelle - V7 : API REST

## Description
Ouverture des données du blog vers l'extérieur. Création d'une interface de programmation (API) permettant à des applications tierces (Mobile, SPA, Partenaires) de consommer et gérer le contenu.

## Fonctionnalités API

### 1. Accès Public (Lecture)
**En tant que** : Développeur tiers / App cliente
**Je veux** : Récupérer la liste des articles et leur détail au format JSON.
**Afin de** : Les afficher dans mon application.

- Endpoints standardisés, documentés.
- Pagination des résultats pour la performance.

### 2. Accès Privé (Écriture)
**En tant que** : Application authentifiée
**Je veux** : Publier ou modifier des articles via l'API.
**Afin de** : Gérer le blog depuis une application mobile Admin.

- Authentification par Token sécurisé.
- Respect strict des mêmes règles métier que le Web (Rôles, Permissions).

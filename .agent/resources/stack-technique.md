# Stack Technique de Référence

## Back-end (Laravel)
- **Langage** : PHP 8.2+
- **Framework** : Laravel 10/11
- **Architecture** : MVC, Service Pattern
- **API** : Laravel API Resources (RESTful)
- **Auth Web** : Laravel UI (Tailwind Scaffolding)
- **Auth API** : Laravel Sanctum (Tokens Mobile)
- **Permissions** : Laravel Gates/Policies (Native) + Spatie Permissions (ACL)

## Front-end (Web)
- **Templating** : Laravel Blade (Components, Layouts)
- **CSS** : Tailwind CSS (v3+)
- **JS** : Alpine.js + AJAX Vanilla (Fetch API)
  - **Approche** : SPA-like experiences dans une architecture MPA (Multi-Page Application)
  - **Principe** : Réactivité et fluidité avec Alpine.js, tout en gardant le templating côté serveur (Blade)
- **Components** : Preline UI

## Base de Données
- **SGBD** : MySQL 8.0
- **ORM** : Eloquent (Relations, Scopes, Accessors)

## DevOps & Outils
- **Serveur** : Nginx
- **Git** : GitHub Flow
- **API Test** : Postman / Insomnia
- **Design** : Maquettes HTML/CSS avec Preline UI

## Interdictions Techniques

- ❌ Pas d'autre framework PHP que Laravel
- ❌ Pas d'autre framework CSS que Tailwind (sauf demande explicite)
- ❌ Pas de frameworks SPA purs (React, Vue.js, Angular)
  - **Raison** : Ces frameworks remplacent le templating serveur et créent une véritable SPA
  - **Alternative** : Utiliser Alpine.js pour créer des expériences SPA-like dans une architecture MPA
- ❌ Pas d'autre ORM qu'Eloquent
- ❌ Pas de PostgreSQL ou MongoDB sans validation préalable

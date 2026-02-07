# Action Mapping : Projet Technique (Blog Architecture)

**Date** : 2026-02-07
**Objectif** : Identifier toutes les micro-actions techniques nécessaires pour réaliser le "Projet Technique" (Blog Laravel), en respectant les phases d'itération et les contraintes d'architecture.

---

## Liste Brute des Actions

### Fonctionnalité 1 : Initialisation & Architecture
- Initialiser le projet Laravel (v10/11) via Composer/Installer.
- Configurer l'environnement (`.env`, Base de données MySQL).
- Installer et configurer Tailwind CSS (v3+).
- Installer et configurer Preline UI (pour le Dashboard).
- Mettre en place la structure du Service Layer (`app/Services`).
- Configurer `lang/` pour l'internationalisation (FR).
- Initialiser le repository Git (si non fait).

### Fonctionnalité 2 : Design System & UI-Kit (Pré-requis Obligatoire)
- Créer l'arborescence `ui-kit/` à la racine.
- Créer le fichier `ui-kit/index.html` (Catalogue).
- Intégrer Tailwind dans le UI-Kit (mode CDN ou build séparé).
- **Atomes** :
  - Concevoir et coder les Boutons (Primary, Secondary, Danger).
  - Concevoir et coder les Inputs (Text, Password, Textarea).
  - Concevoir et coder les Labels et Badges.
  - Concevoir et coder les Alertes/Toasts.
- **Molécules** :
  - Concevoir et coder la Card Article (Vue Liste).
  - Concevoir et coder la Card Article (Vue Détail - Header).
  - Concevoir et coder la Navbar (Public & Admin).
  - Concevoir et coder le Sidebar Admin.
  - Concevoir et coder les Tableaux de données (DataTables).
  - Concevoir et coder les Formulaires (Login, Create/Edit).
- **Maquettes (Pages)** :
  - Maquetter la Page d'Accueil Public (Liste Articles + Sidebar Recherche).
  - Maquetter la Page Article Détail.
  - Maquetter le Dashboard Admin (Vue globale).
  - Maquetter la Page Login.

### Fonctionnalité 3 : Modélisation de Données (Backend Core)
- Créer la Migration `users` (id, name, email, password, role).
- Créer la Migration `categories` (id, label, slug).
- Créer la Migration `articles` (id, title, slug, content, user_id, category_id, is_published, published_at).
- Créer le Modèle `User` avec relation `hasMany(Article)`.
- Créer le Modèle `Category` avec relation `hasMany(Article)`.
- Créer le Modèle `Article` avec relations `belongsTo(User)` et `belongsTo(Category)`.
- Créer le Seeder `DatabaseSeeder` avec Factory pour jeux de données de test.

### Fonctionnalité 4 : Back-Office (Gestion de Contenu)
- **Authentification** : 
  - Créer `AuthController` (Login, Logout).
  - Créer les Vues Blade `auth.login` (basé sur UI-Kit).
- **Gestion des Catégories** :
  - Créer `CategoryService` (Logique métier: CRUD).
  - Créer `CategoryController` (Resource).
  - Créer `StoreCategoryRequest` et `UpdateCategoryRequest` (Validation).
  - Implémenter la Vue `admin.categories.index` (Tableau).
  - Implémenter la Vue `admin.categories.create` et `edit` (Formulaire).
- **Gestion des Articles** :
  - Créer `ArticleService` (Logique métier: CRUD, Publication).
  - Créer `ArticleController` (Resource).
  - Créer `StoreArticleRequest` et `UpdateArticleRequest`.
  - Implémenter la Vue `admin.articles.index`.
  - Implémenter la Vue `admin.articles.create` et `edit`.
- **Sécurisation (Itération 1)** :
  - Définir `ArticlePolicy` et `CategoryPolicy`.
  - Appliquer les Gates/Middleware pour restreindre l'accès `/admin`.

### Fonctionnalité 5 : Front-Office (Expérience Utilisateur)
- Créer `PublicController` (ou `HomeController` + `ArticleController` public).
- Implémenter la méthode `index` (Liste paginée des articles publiés).
- Implémenter la méthode `show` (Affichage détail article).
- Intégrer la maquette UI-Kit `public.home` dans Blade layout.
- Intégrer la maquette UI-Kit `public.article` dans Blade layout.
- **Recherche Dynamique (Itération 1 - Vanilla JS)** :
  - Créer un endpoint interne ou utiliser l'API pour la recherche.
  - Écrire le script JS `search.js` (Fetch API) pour filtrer sans rechargement.
- **Recherche Dynamique (Itération 2 - Alpine.js)** :
  - Refactoriser la recherche avec un composant Alpine `x-data`.

### Fonctionnalité 6 : API REST (Exposition)
- Configurer Laravel Sanctum (Tokens).
- Créer `ArticleResource` et `CategoryResource` (Transformation JSON).
- Créer `Api\ArticleController`.
- Implémenter `index` (Liste avec filtres).
- Implémenter `show` (Détail).
- Sécuriser les routes API (si modification requise plus tard).
- Tester les endpoints via Postman/Insomnia.

---

## Actions Transverses

Actions qui s'appliquent à toutes les fonctionnalités :

- **Qualité de Code** : Exécuter un linter (Pint/PHPCS) pour respecter PSR-12.
- **Documentation** : Mettre à jour le `README.md` avec les instructions d'installation.
- **Tests Manuels** : Vérifier chaque fonctionnalité sur Chrome/Firefox.
- **Gestion de Version** : Commiter atomiquement (feat/fix/chore).
- **Revue** : Validation par le Mentor Technique à chaque fin d'itération majeure.

---

## Notes

- **Point critique UI** : Ne jamais coder en Blade sans avoir validé le composant dans `ui-kit/` HTML pur auparavant.
- **Sécurité** : Attention particulière aux injections SQL (utiliser Eloquent) et XSS (Blade escape).
- **Scalabilité** : Le Service Pattern est obligatoire pour ne pas surcharger les contrôleurs.

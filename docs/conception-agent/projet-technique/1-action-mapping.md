# Action Mapping : Projet Technique (Blog)

> **Source** : `0-besoins.md`
> **Objectif** : Lister toutes les micro-actions techniques nécessaires sans ordre.

## 1. Initialisation & Environnement
- [ ] Initialiser nouveau projet Laravel 10/11
- [ ] Configurer environnement (.env, MySQL)
- [ ] Initialiser dépôt Git
- [ ] Installer Tailwind CSS (npm) et configurer `tailwind.config.js`
- [ ] Installer Preline UI (plugin Tailwind)
- [ ] Configurer le dossier `ui-kit/` (Hors Laravel pure) pour le prototypage statique

## 2. Base de Données (Model Layer)
- [ ] Créer Migration `categories` (label, slug)
- [ ] Créer Migration `articles` (title, slug, content, user_id, category_id, is_published, published_at)
- [ ] Modifier Migration `users` (ajout role/admin flag ou table séparée selon choix archi)
- [ ] Créer Modèle `Category` (Relations hasMany Articles, Fillable)
- [ ] Créer Modèle `Article` (Relations belongsTo User/Category, Fillable, Scopes)
- [ ] Créer Modèle `User` (Relations hasMany Articles)
- [ ] Créer Factory `CategoryFactory`
- [ ] Créer Factory `ArticleFactory`
- [ ] Créer Seeder `DatabaseSeeder` (Jeux de données complets pour tests)

## 3. UI-Kit (Static Design First)
- [ ] Créer `ui-kit/index.html` (Index des composants)
- [ ] Designer Composant `Atom/Button` (Primary, Secondary, Danger, Ghost)
- [ ] Designer Composant `Atom/Input` (Text, Email, Password, Textarea)
- [ ] Designer Composant `Molecule/Navbar` (Public & Admin, Responsive)
- [ ] Designer Composant `Molecule/CardArticle` (Image, Titre, Extrait, Meta)
- [ ] Designer Composant `Molecule/Sidebar` (Admin Dashboard)
- [ ] Maquetter Page `Maquettes/Public/Home` (Grille articles, Hero section)
- [ ] Maquetter Page `Maquettes/Public/ArticleDetail` (Contenu, Sidebar catégories)
- [ ] Maquetter Page `Maquettes/Admin/Dashboard` (Vue d'ensemble)
- [ ] Maquetter Page `Maquettes/Admin/Article/List` (Tableau CRUD avec actions)
- [ ] Maquetter Page `Maquettes/Admin/Article/Form` (Création/Édition avec WYSIWYG simple ou Textarea)
- [ ] Maquetter Page `Maquettes/Auth/Login` et `Maquettes/Auth/Register`

## 4. Backend Logique (Controllers & Services) - Admin
- [ ] Implémenter/Scaffolder `AuthController` (Login/Logout/Register) avec Fortify ou Manuellement
- [ ] Implémenter `Admin/DashboardController`
- [ ] Créer FormRequest `StoreArticleRequest` (Validation règles métier)
- [ ] Créer FormRequest `UpdateArticleRequest`
- [ ] Créer Service `ArticleService` (Logique de création/update, gestion transactions si besoin)
- [ ] Implémenter `Admin/ArticleController` (Utilise Service + Requests, retourne Vues Admin)
- [ ] Implémenter `Admin/CategoryController` (CRUD complet)
- [ ] Intégrer les vues Blade Admin avec Layout Admin (x-layouts props)

## 5. Frontend & Public (Controllers & Views)
- [ ] Implémenter `Public/HomeController` (Liste paginée, Tri)
- [ ] Implémenter `Public/ArticleController` (show avec resolution de slug)
- [ ] Intégrer les vues Blade Public avec Layout Public
- [ ] Implémenter la pagination des articles (Tailwind styled)

## 6. Interactivité JS (Progressive Enhancement)
- [ ] Créer endpoint API interne ou Route dédiée pour Recherche (Search) JSON
- [ ] Implémenter Search Bar en Vanilla JS (Fetch API, DOM Manipulation) - Itération 1
- [ ] Refactoriser Search Bar avec Alpine.js (x-data, x-model, x-for) - Itération 2
- [ ] Implémenter Filtres par Catégorie dynamiques (AJAX update liste)

## 7. API REST & Sécurité
- [ ] Installer & Configurer Laravel Sanctum (Stateful pour SPA si besoin, ou Token pour externe)
- [ ] Créer `ArticleResource` (JsonResource pour formatage sortie)
- [ ] Créer `CategoryResource` (JsonResource)
- [ ] Créer `UserResource`
- [ ] Implémenter `Api/AuthController` (Login/Token Issue)
- [ ] Implémenter `Api/ArticleController` (index, show, store - sécurisé)
- [ ] Définir les routes API sécurisées (`routes/api.php`) avec middleware `auth:sanctum`

## 8. Sécurité & Qualité code
- [ ] Configurer Middleware `IsAdmin` pour routes Back-Office
- [ ] Définir Policies `ArticlePolicy` (viewAny, view, create, update, delete)
- [ ] Définir Policies `CategoryPolicy`
- [ ] Enregistrer Policies dans `AuthServiceProvider` (ou auto-discovery Laravel 11)
- [ ] Validation des entrées (XSS protection par défaut Blade, validation form requests)
- [ ] Auditer le code avec PHP CodeSniffer / Pint (PSR-12)

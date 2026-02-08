# Conception Technique - V2 : Back-Office Admin

## Objectif Technique
Implémentation de l'authentification et des contrôleurs de ressources pour le CRUD.

## 1. Sécurité & Authentification

### Kit de Démarrage
-   Utiliser **Laravel Breeze** (version Blade) ou implémentation manuelle simple si but pédagogique.
-   Middleware : `auth` appliqué sur le groupe de routes `/admin`.

## 2. Architecture Backend

### Routes (`web.php`)
Groupe préfixé `admin` + middleware `auth` :
-   `Resource /categories` -> `Admin\CategoryController`
-   `Resource /articles` -> `Admin\ArticleController`

### Controllers

#### `Admin\CategoryController` (Resource)
-   `store(CategoryRequest $request)` : Validation (nom unique), génération Slug (`Str::slug`), sauvegarde.
-   `destroy(Category $category)` : `detach()` d'abord les articles liés ? Ou laisser la contrainte FK gérer (si cascade ou restrict). *Choix : Detach dans la méthode destroy.*

#### `Admin\ArticleController` (Resource)
-   `index()` : `$articles = Article::where('user_id', Auth::id())->get();` (Scope initial simple).
-   `create()` : Charger toutes les catégories pour le select : `Category::all()`.
-   `store(ArticleRequest $request)` :
    -   Création Article avec `user_id = Auth::id()`.
    -   Sync des catégories : `$article->categories()->sync($request->categories)`.
-   `update(...)` : Idem store + `sync` pour mise à jour relations.

### Validation (`FormRequests`)

-   **CategoryRequest** :
    -   `name`: `required|string|max:255|unique:categories,name`.
-   **ArticleRequest** :
    -   `title`: `required|string|max:255`.
    -   `content`: `required|string`.
    -   `categories`: `array`.
    -   `categories.*`: `exists:categories,id`.

## 3. Frontend (Blade Admin)

### Layout
-   `layouts/admin.blade.php` : Sidebar navigation, Header avec info User + Logout.

### Vues CRUD
-   Utiliser des composants Blade réutilisables pour les formulaires (`<x-input>`, `<x-label>`) si disponibles (via Breeze ou UI Kit).
-   **Flash Messages** : Afficher les succès/erreurs en haut de page (`session('success')`).

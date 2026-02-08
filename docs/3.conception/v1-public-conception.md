# Conception Technique - V1 : Partie Publique

## Objectif Technique
Mise en place de l'architecture Laravel, du schéma de base de données, et de l'intégration Front-End avec Blade et Tailwind CSS.

## 1. Base de Données (Schema)

### Tables
1.  **users** (Standard Laravel)
    -   `id`, `name`, `email`, `password`, `created_at`...
2.  **categories**
    -   `id` (PK)
    -   `name` (string, unique)
    -   `slug` (string, unique)
    -   `created_at`, `updated_at`
3.  **articles**
    -   `id` (PK)
    -   `user_id` (FK -> users)
    -   `title` (string)
    -   `slug` (string, unique, index)
    -   `excerpt` (text, nullable)
    -   `content` (longText)
    -   `published_at` (datetime, nullable)
    -   `created_at`, `updated_at`
4.  **article_category** (Pivot)
    -   `article_id` (FK -> articles)
    -   `category_id` (FK -> categories)

### Seeding (Fake Data)
-   Utiliser `Faker` pour générer :
    -   1 Admin spécifique (email connu pour tests).
    -   5 Auteurs random.
    -   10 Catégories (mots simples).
    -   20 Articles (avec associations aléatoires auteurs/catégories).

## 2. Architecture Backend

### Routes (`web.php`)
-   `GET /` -> `PublicArticleController@index` (name: `home`)
-   `GET /articles/{slug}` -> `PublicArticleController@show` (name: `articles.show`)

### Controllers
-   **PublicArticleController**
    -   `index()` : Récupère les articles paginés (`Article::with('author', 'categories')->latest()->paginate(10)`).
    -   `show(Article $article)` : Utilise le Route Model Binding (sur le slug).

### Models
-   **Article**
    -   Relations : `belongsTo(User::class)`, `belongsToMany(Category::class)`.
    -   Casts : `published_at` => `datetime`.
-   **Category**
    -   Relations : `belongsToMany(Article::class)`.

## 3. Frontend (Blade & Tailwind)

### Layouts
-   `layouts/app.blade.php` : Structure globale (HTML5, Meta, chargement CSS/JS via Vite).
-   Inclusion de la Navbar (`partials/navbar.blade.php`) et du Footer (`partials/footer.blade.php`).

### Vues
-   `articles/index.blade.php` : Boucle `@foreach` sur les articles. Utilisation d'un composant/partial pour la "Card Article". Pagination avec `$articles->links()`.
-   `articles/show.blade.php` : Affichage du détail. Rendu du contenu via `{!! Str::markdown($article->content) !!}` (si Markdown) ou brut.

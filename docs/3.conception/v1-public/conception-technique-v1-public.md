# Conception Technique - V1 : Lecture Publique (MVP)











## Objectif
Implémenter la couche visuelle publique permettant aux visiteurs de consulter les articles et leur détail. Cette version pose les bases de l'architecture MVC.



## 1. Présentation (Front-End & IHM)



### Vues (Blade Components)
- `resources/views/layouts/app.blade.php`: Layout principal (Header, Footer, Slot).



- `resources/views/components/navbar.blade.php`: Barre de navigation publique.


- `resources/views/posts/index.blade.php`: Liste paginée des articles (Grille de cartes).
- `resources/views/posts/show.blade.php`: Page de détail d'un article.

- `resources/views/components/post-card.blade.php`: Composant réutilisable pour afficher un résumé d'article.

### Interactions
- Navigation fluide entre l'index et le détail via des liens standards (`<a>`).
- Pagination statique via les liens générés par Laravel (`{{ $posts->links() }}`).

## 2. Couche Présentation (Contrôleurs & HTTP)

### Routes (`routes/web.php`)
- `GET /` -> `PostController@index` (Nom: `posts.index`)
- `GET /posts/{slug}` -> `PostController@show` (Nom: `posts.show`)

### Contrôleurs (`App\Http\Controllers\Public\PostController`)
- **Action `index()`** :
  - Récupère les articles publiés avec pagination (10 par page).
  - Tri par date de création décroissante.
  - Retourne la vue `posts.index`.
- **Action `show(string $slug)`** :
  - Recherche l'article par son `slug`.
  - Vérifie qu'il est publié (`is_published`).
  - Charge les relations nécessaires (Auteur, Catégorie).
  - Retourne la vue `posts.show` ou une 404.

## 3. Couche Métier (Logique & Services)

### Règles de Gestion (Implémentation)
- **Scope de Publication** (`PublishedScope`) : 
  - Créer un Scope local `scopePublished($query)` sur le modèle `Article` pour filtrer automatiquement `where('is_published', true)`.
- **Formatage** :
  - Utiliser des *Accessors* pour formater la date (`created_at`) en format lisible (ex: "Il y a 2 jours" ou "10/02/2026").
  - Tronquer le contenu pour l'affichage en liste (Excerpt).

## 4. Couche Data (Persistance)

### Modèles (Eloquent)
- **User** (`App\Models\User`) : Auteur des articles.
- **Category** (`App\Models\Category`) : Classification.
- **Article** (`App\Models\Article`) : Entité principale.
  - Relations :
    - `user()`: `BelongsTo` (User).
    - `categories()`: `BelongsToMany` (Category).
  - Casts :
    - `is_published` => `boolean`.
    - `created_at` => `datetime`.

### Migrations
- `create_users_table` (Standard Laravel).
- `create_categories_table` : `id`, `name`, `slug` (unique), `timestamps`.
- `create_articles_table` : 
  - `id`, `user_id` (FK), `title`, `slug` (unique), `content` (text), `image` (nullable), `is_published` (default false), `timestamps`.
- `create_article_category_table` (Pivot) : `article_id`, `category_id`.

### Seeders (`DatabaseSeeder`)
- `UserSeeder` : Créer un admin et quelques auteurs.
- `CategorySeeder` : Créer 5-10 catégories (ex: Tech, Laravel, Design...).
- `ArticleSeeder` : Créer 20-50 articles factices associés aléatoirement à des auteurs et catégories.

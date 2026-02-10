# Conception Technique - V1 : Lecture Publique


## 1. Couche Front-end (Vues & Layouts)

### Architecture des Vues
L'interface publique sera structurée autour d'un layout principal et de vues dédiées à la consultation des articles.

#### Layout Global
- **Fichier** : `resources/views/layouts/public.blade.php`
- **Responsabilité** : Structure HTML de base, en-tête (Logo, Navigation), pied de page.
- **Slots** : 
  - `$slot` : Contenu principal.
  - `$header` : Titre de la page (optionnel).

#### Pages (Vues Principales)
1.  **Liste des Articles (Accueil)**
    - **Fichier** : `resources/views/public/articles/index.blade.php`
    - **Route** : `/`
    - **Données** : Collection paginée d'articles (`$articles`).
    - **Composants** : Boucle sur les articles utilisant le partial `article-card`.

2.  **Détail d'un Article**
    - **Fichier** : `resources/views/public/articles/show.blade.php`
    - **Route** : `/articles/{slug}`
    - **Données** : Instance unique d'article (`$article`).
    - **Affichage** : Titre, Image de couverture, Méta-données (Auteur, Date, Catégorie), Contenu complet.

#### Partials (Composants Réutilisables)
- **Carte Article** : `resources/views/partials/article-card.blade.php`
  - Affichage résumé d'un article dans une liste (Image, Titre, Extrait, Lien "Lire la suite").
- **Navbar Public** : `resources/views/partials/public-navbar.blade.php`
- **Footer Public** : `resources/views/partials/public-footer.blade.php`

---

## 2. Couche HTTP (Contrôleurs, Routes)

### Routes (`routes/web.php`)
Définition des routes publiques sans authentification requise.

| Verbe | URI                | Nom de la route         | Action Contrôleur                |
| :---- | :----------------- | :---------------------- | :------------------------------- |
| GET   | `/`                | `public.articles.index` | `Public\ArticleController@index` |
| GET   | `/articles/{slug}` | `public.articles.show`  | `Public\ArticleController@show`  |

### Contrôleurs

#### `App\Http\Controllers\Public\ArticleController`
Contrôleur invokable ou resource (only index, show) dédié à l'affichage public.

- **Méthode `index()`** :
  - **rôle** : Récupérer les articles publiés, paginés, triés par date décroissante.
  - **Retour** : `return view('public.articles.index', compact('articles'));`

- **Méthode `show(Article $article)`** :
  - **rôle** : Afficher un article spécifique.
  - **Binding** : Utilisation du Route Model Binding implicite sur le champ `slug`.
  - **Retour** : `return view('public.articles.show', compact('article'));`

### Validation
Pas de validation de formulaire complexe pour cette version (lecture seule). Le Route Model Binding gère la validation d'existence (404 si non trouvé).

---

## 3. Couche Métier (Logique & Scopes)

La logique métier pour cette version se concentre sur la récupération et le filtrage des données.

### Modèle `Article`
- **Scopes Locaux** :
  - `scopePublished($query)` : Filtre `where('is_published', true)`.
  - `scopeRecent($query)` : Tri `orderBy('created_at', 'desc')`.
- **Relations** :
  - `author()` : BelongsTo `User`.
  - `category()` : BelongsTo `Category`.
- **Accesseurs** :
  - `getExcerptAttribute()` : Génération dynamique d'un extrait du contenu.

### Modèle `User`
- **Relations** :
  - `articles()` : HasMany `Article`.

### Modèle `Category`
- **Relations** :
  - `articles()` : HasMany `Article`.

---

## 4. Couche Data (Persistance)

Implémentation physique du schéma de données défini dans le diagramme de classes global.

### Migrations

1.  **Table `users`** (Standard Laravel + modifications si nécessaire)
    - `id`, `name`, `email`, `password`, `role` (enum/string), `timestamps`.

2.  **Table `categories`**
    - `id` (PK)
    - `name` (String)
    - `slug` (String, Unique)
    - `created_at`, `updated_at`

3.  **Table `articles`**
    - `id` (PK)
    - `user_id` (FK -> users.id, nullable ou cascade)
    - `category_id` (FK -> categories.id, nullable)
    - `title` (String)
    - `slug` (String, Unique)
    - `content` (Text/LongText)
    - `image` (String, path vers l'image)
    - `is_published` (Boolean, default false)
    - `created_at`, `updated_at`

### Seeders & Factories
Stratégie de peuplement pour le développement et la démo.

- **`UserSeeder`** : Création d'un admin et de quelques auteurs de test.
- **`CategorySeeder`** : Création de catégories thématiques (ex: Tech, News, Tutorial).
- **`ArticleSeeder`** : Génération de 20-50 articles factices liés à des auteurs et catégories aléatoires via Factory.

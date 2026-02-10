# Conception Technique - V1 : Lecture Publique  


## 0. Contexte
Cette première version (MVP) implémente la consultation publique des articles pour les visiteurs non authentifiés. Elle pose les fondations de l'architecture Front (Layouts, Composants) et Back (Modèles, Contrôleurs).

---

## 1. Couche Front-end (Présentation & UI)

### 1.1 Architecture & Design System (Analyse UI)
Cette section intègre le **Gap Analysis** issu de l'étape de conception UI (`designer-ui`).

**Layout Global**
- **PublicLayout** (`layouts/public.blade.php`) :
  - **Header** : Logo, Navigation (Home, Login).
  - **Main Content** : Slot principal.
  - **Footer** : Copyright, Liens légaux.

**Inventaire des Composants (Atomic Design)**
| Type         | Nom           | Description                                        | Statut  |
| :----------- | :------------ | :------------------------------------------------- | :------ |
| **Atom**     | `Button`      | Bouton principal / secondaire (Tailwind).          | À créer |
| **Atom**     | `Badge`       | Étiquette pour la catégorie (Pill shape).          | À créer |
| **Atom**     | `Avatar`      | Image de l'auteur (Cercle).                        | À créer |
| **Atom**     | `Container`   | Conteneur centré responsive (`max-w-7xl mx-auto`). | À créer |
| **Molecule** | `Navbar`      | Barre de navigation responsive.                    | À créer |
| **Molecule** | `Footer`      | Pied de page simple.                               | À créer |
| **Molecule** | `ArticleCard` | Carte article (Image, Titre, Extrait, Meta).       | À créer |
| **Molecule** | `Pagination`  | Contrôles de pagination (Tailwind).                | À créer |

### 1.2 Vues & Organisation Blade
L'organisation des fichiers suit la séparation stricte **Public/Admin**.

- `resources/views/layouts/public.blade.php` : Squelette HTML principal.
- `resources/views/public/articles/index.blade.php` : Liste des articles (Grille responsive).
- `resources/views/public/articles/show.blade.php` : Détail d'un article.
- `resources/views/partials/article-card.blade.php` : Composant réutilisable pour la liste.

### 1.3 Interactivité (JS / Alpine)
- **Menu Mobile** : Géré par Alpine.js (`x-data="{ open: false }"`) dans la `Navbar`.
- **Images** : Lazy loading natif (`loading="lazy"`).

---

## 2. Couche HTTP (Contrôleurs, Routes)

### 2.1 Routes (`routes/web.php`)
Définition des accès publics.

```php
use App\Http\Controllers\Public\ArticleController;

Route::name('public.')->group(function () {
    // Liste des articles (Page d'accueil par défaut pour le MVP)
    Route::get('/', [ArticleController::class, 'index'])->name('articles.index');
    
    // Détail d'un article
    Route::get('/articles/{slug}', [ArticleController::class, 'show'])->name('articles.show');
});
```

### 2.2 Contrôleurs
Namespace : `App\Http\Controllers\Public`

**ArticleController**
- `index(Request $request)` :
  - Récupère les articles paginés (ex: 9 par page).
  - Trie par `created_at` DESC.
  - Retourne la vue `public.articles.index`.
- `show(string $slug)` :
  - Cherche l'article par slug (ou 404).
  - Charge les relations (Auteur, Catégorie).
  - Retourne la vue `public.articles.show`.

### 2.3 Ressources API (Anticipation)
*Non requis pour la V1 (Blade uniquement), mais structure prête pour V7.*

---

## 3. Couche Métier (Logique & Services)

### 3.1 Règles de Gestion
- **Scope de Publication** : Seuls les articles avec `is_published = true` et `published_at <= now()` doivent être visibles.
- **Tri** : Ordre chronologique inverse par défaut.

### 3.2 Modèles & Eloquent
**Article** (`app/Models/Article.php`)
- **Relations** :
  - `belongsTo(User::class, 'user_id')` (Auteur).
  - `belongsTo(Category::class)` (Catégorie).
- **Scopes** :
  - `scopePublished($query)` : Filtre les articles publics.
  - `scopeRecent($query)` : Trie par date récente.
- **Casts** :
  - `is_published` => `boolean`.
  - `published_at` => `datetime`.

---

## 4. Couche Data (Persistance)

### 4.1 Schéma de Base de Données (Migrations)

**Table `users` (Auteurs)**
- Standard Laravel (+ `role` enum: 'admin', 'author', 'user').

**Table `categories`**
- `id` (PK)
- `name` (String, Unique)
- `slug` (String, Unique, Index)
- `created_at`, `updated_at`

**Table `articles`**
- `id` (PK)
- `user_id` (FK -> users.id, cascade)
- `category_id` (FK -> categories.id, set null)
- `title` (String)
- `slug` (String, Unique, Index)
- `excerpt` (Text, Nullable)
- `content` (LongText)
- `image` (String, Path, Nullable)
- `is_published` (Boolean, Default false)
- `published_at` (DateTime, Nullable)
- `created_at`, `updated_at`

### 4.2 Seeders (`database/seeders`)
Stratégie de peuplement pour le développement.
1. **UserSeeder** : Créer 1 Admin, 1 Auteur.
2. **CategorySeeder** : Créer 5 catégories (Tech, Design, Laravel...).
3. **ArticleSeeder** : Créer 50 articles factices (Faker), répartis, avec images (placeholders).

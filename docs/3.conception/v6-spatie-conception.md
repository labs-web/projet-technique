# Conception Technique - V6 : Rôles & Permissions (Spatie)

## Objectif Technique
Implémentation d'un système RBAC (Role-Based Access Control) robuste via le package standard `spatie/laravel-permission`.

## 1. Installation & Setup

### Package
`composer require spatie/laravel-permission`
Publication config & migration + `php artisan migrate`.

### Seeding (`RoleSeeder`)
Créer les rôles et permissions au démarrage :
1.  Créer Role `admin` et `editor`.
2.  Créer Permissions atomiques : `edit articles`, `delete articles`, `manage categories`.
3.  Assigner :
    -   `admin` -> givePermissionTo(`manage categories`, `edit articles`, `delete articles`...).
    -   `editor` -> (Aucune permission globale, logique gérée par Policy + ownership).

## 2. Adaptation Code existant

### User Model
Ajouter le trait `HasRoles`.

### Policies (`ArticlePolicy`)
La logique de la V3 doit évoluer.

```php
public function update(User $user, Article $article) {
    if ($user->hasRole('admin')) {
        return true; // Admin passe partout
    }
    return $user->id === $article->user_id; // Editor limité à ses articles
}
```

### Middleware
Dans `routes/web.php`, protéger les routes Admin Categories :
`Route::middleware(['auth', 'role:admin'])->group(...)`.

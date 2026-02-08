# Conception Technique - V3 : Autorisation Native

## Objectif Technique
Utilisation des **Policies** et **Gates** de Laravel pour centraliser la logique d'autorisation.

## 1. Classes Policy

### `ArticlePolicy`
Générer via `php artisan make:policy ArticlePolicy --model=Article`.

#### Méthodes à implémenter :
-   `update(User $user, Article $article)` :
    ```php
    return $user->id === $article->user_id;
    ```
-   `delete(User $user, Article $article)` :
    ```php
    return $user->id === $article->user_id;
    ```
-   (Optionnel) `viewAny`: `true` (tout le monde peut voir la liste).

## 2. Intégration Backend

### Controller (`Admin\ArticleController`)
Utiliser la méthode `authorize` du contrôleur (ou `Gate::authorize`) au début des actions sensibles.

```php
public function edit(Article $article) {
    $this->authorize('update', $article); // Renvoie 403 auto si faux
    // ...
}

public function update(Request $request, Article $article) {
    $this->authorize('update', $article);
    // ...
}

public function destroy(Article $article) {
    $this->authorize('delete', $article);
    // ...
}
```

## 3. Intégration Frontend (Blade)

Utiliser la directive `@can`.

```blade
@foreach($articles as $article)
    <tr>
        <td>{{ $article->title }}</td>
        <td>
            @can('update', $article)
                <a href="...">Modifier</a>
            @endcan
            
            @can('delete', $article)
                <button>Supprimer</button>
            @endcan
        </td>
    </tr>
@endforeach
```

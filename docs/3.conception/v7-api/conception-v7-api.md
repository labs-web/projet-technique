# Conception Technique - V7 : API REST & Sanctum

## Objectif Technique
Mise en place d'une API RESTful conforme aux standards JSON, sécurisée par Laravel Sanctum (Tokens).

## 1. Sécurité (Sanctum)

### Setup
-   Vérifier `HasApiTokens` sur le modèle User.
-   Utiliser le guard `sanctum` dans `config/auth.php` (déjà standard).

### Auth Flow
-   Route `POST /api/v1/login` : Prend (email, pwd) -> Retourne `CreateToken()->plainTextToken`.

## 2. API Resources (Transformation)

Créer `ArticleResource` pour formatter la sortie JSON :
```php
public function toArray($request) {
    return [
        'id' => $this->id,
        'title' => $this->title,
        'content' => $this->content, // Ou excerpt
        'author' => new UserResource($this->whenLoaded('author')),
        'links' => [
            'self' => route('api.articles.show', $this->id),
        ],
    ];
}
```

## 3. Controllers API (`Api/V1/ArticleController`)

Séparer les contrôleurs Web et API.
-   `index()` : Retourne `ArticleResource::collection($articles)`.
-   `store(ArticleRequest $request)` : Réutiliser les FormRequests existants si possible, ou en créer des spécifiques API si la validation diffère (retour JSON 422 auto).
-   **Gestion des erreurs** : S'assurer que Laravel renvoie du JSON pour toutes les erreurs (Header `Accept: application/json`).

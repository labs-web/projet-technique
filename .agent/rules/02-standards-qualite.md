---
trigger: always_on
---

# Standards de Qualité : Code, Sécurité et Documentation

## Objectif

Garantir un niveau de qualité professionnel du code en imposant les standards PSR-12, les bonnes pratiques Laravel, les règles de sécurité essentielles, et un format de documentation Markdown lisible et maintenable.

## Instructions

### 1. Standards de Code

- **Respecter** les standards PSR-12 pour le code PHP.
- **Utiliser** le typage strict (`declare(strict_types=1);`) autant que possible.
- **Nommer** :
  - Le code en **Anglais** (Variables, Fonctions, Classes).
  - La base de données en **Anglais** (Snake case : `user_id`, `created_at`).
  - Les commits Git en **Français** (cohérence projet).
- **Commenter** en français uniquement pour expliquer une logique complexe :
  - Expliquer le **"Pourquoi"**, pas le **"Comment"**.
  - Éviter les commentaires redondants avec le code.

### 2. Sécurité

- **Utiliser** l'ORM Eloquent ou les bindings PDO pour toutes les requêtes SQL.
- **Utiliser** l'échappement par défaut de Blade `{{ }}` pour prévenir les failles XSS.
- **Utiliser** les façades `Hash` pour hacher les mots de passe (jamais de stockage en clair).
- **Protéger** tous les endpoints sensibles avec le middleware `auth:sanctum` pour les API.
- **Valider** toutes les entrées utilisateur via les FormRequests Laravel.

### 3. Bonnes Pratiques Laravel

- **Appliquer** le principe "Fat Model, Skinny Controller" ou utiliser le Service Pattern pour la logique complexe.
- **Utiliser** les Resource Controllers pour le CRUD standard.
- **Utiliser** les Migrations pour toute modification de la base de données.
- **Éviter** de mettre de la logique métier dans les Vues (Blade).

### 4. Documentation Markdown

- **Rédiger** toute documentation en **Français**.
- **Privilégier** un format clair, concis et aéré.
- **Structurer** le contenu avec des titres hiérarchiques (`##`, `###`).
- **Utiliser** des listes à puces (`-`) ou des listes imbriquées pour organiser l'information.
- **Convertir immédiatement** toute tentation de tableau en liste à puces ou liste de définitions.

## Interdictions

### Code et Sécurité

- **INTERDICTION** d'utiliser des requêtes SQL concaténées (risque d'injection SQL).
- **INTERDICTION** de stocker des mots de passe en clair dans la base de données.
- **INTERDICTION** d'utiliser `{!! $variable !!}` sans validation préalable (risque XSS).
- **INTERDICTION** de créer des endpoints API sans protection `auth:sanctum` pour les opérations sensibles.
- **INTERDICTION** d'accepter des données utilisateur sans validation via FormRequest.
- **INTERDICTION** de mettre de la logique métier dans les contrôleurs ou les vues.

### Documentation Markdown

- **INTERDICTION ABSOLUE** d'utiliser des tableaux Markdown (`| col | col |`).
  - **Raison** : Difficulté de lecture, d'édition et problèmes de rendu.
  - **Action obligatoire** : Transformer immédiatement en liste à puces ou liste de définitions.

## Exemples

### Exemple 1 : Injection SQL

```php
// ❌ NON-CONFORME : Requête concaténée (vulnérable)
$users = DB::select("SELECT * FROM users WHERE email = '" . $email . "'");

// ✅ CONFORME : Utilisation de l'ORM Eloquent
$users = User::where('email', $email)->get();

// ✅ CONFORME : Utilisation des bindings PDO
$users = DB::select("SELECT * FROM users WHERE email = ?", [$email]);
```

### Exemple 2 : XSS

```blade
{{-- ❌ NON-CONFORME : Pas d'échappement --}}
{!! $userInput !!}

{{-- ✅ CONFORME : Échappement automatique --}}
{{ $userInput }}
```

### Exemple 3 : Hash de Mot de Passe

```php
// ❌ NON-CONFORME : Stockage en clair
$user->password = $request->password;

// ✅ CONFORME : Utilisation de Hash
$user->password = Hash::make($request->password);
```

### Exemple 4 : Validation

```php
// ❌ NON-CONFORME : Pas de validation
public function store(Request $request) {
    User::create($request->all());
}

// ✅ CONFORME : Utilisation de FormRequest
public function store(StoreUserRequest $request) {
    User::create($request->validated());
}
```

### Exemple 5 : Documentation - Pas de Tableaux

```markdown
❌ NON-CONFORME : Tableau Markdown
| Nom   | Type   | Description   |
| ----- | ------ | ------------- |
| id    | int    | Identifiant   |
| email | string | Adresse email |

✅ CONFORME : Liste à Puces
**Champs de la table users :**
- **id** (int) : Identifiant unique de l'utilisateur
- **email** (string) : Adresse email de l'utilisateur
- **name** (string) : Nom complet de l'utilisateur
```

### Exemple 6 : Logique Métier (Service Pattern)

```php
// ❌ NON-CONFORME : Logique dans le contrôleur
public function store(Request $request) {
    $user = User::create($request->all());
    $user->sendWelcomeEmail();
    $user->assignRole('user');
    Log::info('User created: ' . $user->id);
    return redirect()->route('users.index');
}

// ✅ CONFORME : Délégation à un Service
public function store(StoreUserRequest $request, UserService $userService) {
    $user = $userService->createUser($request->validated());
    return redirect()->route('users.index');
}
```

# Conception Technique - V4 : Interactivité Vanilla (AJAX)

## Objectif Technique
Mise en place d'une communication Asynchrone (AJAX) entre le client (JS Natif) et le serveur (Laravel), et gestion des réponses partielles (HTML Fragments).

## 1. Backend

### Controller (`PublicArticleController@index`)
Modifier la méthode pour gérer deux modes de réponse :
1.  **Mode Normal** (Accès direct URL) : Renvoie la vue complète `articles.index` (Layout + Contenu).
2.  **Mode AJAX** (Détecté via `$request->ajax()` ou Header spécifique) : Renvoie uniquement le partial `articles._list`.

```php
if ($request->ajax()) {
    return view('articles._list', compact('articles'))->render();
}
return view('articles.index', compact('articles'));
```

### Blade Refactoring
-   Extraire la boucle d'affichage des articles dans un fichier partiel : `resources/views/articles/_list.blade.php`.
-   Inclure ce partiel dans la vue principale.

## 2. Frontend (JavaScript Vanilla)

### Fichier JS
Créer `resources/js/search-vanilla.js` (à charger dans le layout via Vite).

### Algorithme
1.  **Dambounce** : Créer une fonction utilitaire pour attendre X ms après la dernière frappe.
2.  **Listeners** :
    -   `input` sur `#search-input`.
    -   `click` sur `.category-filter-btn` (utiliser `event.preventDefault()`).
3.  **Fetch API** :
    -   Construire l'URL avec les paramètres : `/?search=xxx&category=yyy`.
    -   Appeler `fetch(url, { headers: { 'X-Requested-With': 'XMLHttpRequest' } })`.
4.  **DOM Update** :
    -   Recevoir le HTML (text).
    -   Injecter dans le container `#articles-container` via `innerHTML`.

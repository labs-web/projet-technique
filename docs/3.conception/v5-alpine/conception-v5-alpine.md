# Conception Technique - V5 : Interactivité Moderne (Alpine.js)

## Objectif Technique
Adoption de **Alpine.js** (Framework JS léger) pour remplacer le Vanilla JS et ajouter des interactions UI.

## 1. Installation

### NPM
```bash
npm install alpinejs
```
Initialisation dans `resources/js/app.js` :
```js
import Alpine from 'alpinejs';
window.Alpine = Alpine;
Alpine.start();
```

## 2. Refactoring Recherche (`search-alpine.js`)

### Logique (`x-data`)
Créer un composant Alpine directement dans le HTML ou via `Alpine.data()`.

```html
<div x-data="articleSearch()">
    <input x-model="query" @input.debounce.300ms="fetchArticles">
    <!-- Liste articles -->
</div>
```

### Script
La logique de fetch reste similaire à la V4, mais la mise à jour du DOM se fait via la réactivité d'Alpine (ou remplacement HTML via `x-html` si on garde le retour partiel serveur).
*Stratégie* : Fetch renvoie du HTML -> Alpine injecte via `x-html`.

## 3. Composants UI

### Dropdown (User Menu)
Utiliser les directives : `x-data="{ open: false }"`, `@click="open = !open"`, `x-show="open"`, `@click.outside="open = false"`.

### Toast Notification
Composant global Blade `<x-toast />`.
Logique Alpine :
-   `x-data="{ show: true }"`
-   `x-init="setTimeout(() => show = false, 3000)"`
-   `x-show.transition="show"` pour l'animation de sortie.

# Spécifications : Validation & Update Tailwind CSS + Preline UI

## 🎯 Objectif
Vérifier l'installation existante de Tailwind CSS (souvent inclus avec Laravel 11+) et garantir l'intégration de Preline UI.

---

## 🔍 Étape 1 : Vérification de Tailwind CSS
### 1.1 Dépendances (package.json)
Vérifier la présence de `tailwindcss`, `postcss`, `autoprefixer` dans les `devDependencies`.
*(Laravel 11 inclut déjà ces paquets par défaut)*

### 1.2 Configuration (tailwind.config.js)
Vérifier si le fichier existe et contient une configuration valide (avec `content` ou `@source`).
*Note : Si Laravel utilise la syntaxe v4 (alpha/beta), la config peut être directement dans le CSS via `@theme`.*

### 1.3 CSS (resources/css/app.css)
Vérifier la présence des directives `@tailwind` ou `@import 'tailwindcss'`.

---

## 🚀 Étape 2 : Ajout de Preline UI (Si manquant)
### 2.1 Installation
```bash
npm install preline --save-dev
```

### 2.2 Configuration (tailwind.config.js / app.css)
**Si `tailwind.config.js` existe classic (v3)** :
Ajouter dans `content` : `'node_modules/preline/dist/*.js'`
Ajouter dans `plugins` : `require('preline/plugin')`

**Si syntaxe v4 ou sans config explicite** :
Vérifier comment ajouter le plugin Preline (peut nécessiter une config JS).

### 2.3 Initialisation (resources/js/app.js)
Ajouter l'import pour activer l'interactivité :
```javascript
import 'preline';
```

---

## ✅ Étape 3 : Validation
- [ ] `npm install` exécuté.
- [ ] `npm run dev` compile sans erreur.
- [ ] Les classes Tailwind fonctionnent dans les vues Blade.
- [ ] Les composants Preline (dropdowns, modals) sont interactifs.

# Spécifications : Tailwind CSS

Ce fichier définit les versions, commandes d'installation et configurations pour Tailwind CSS.

---

## Version
- **Tailwind CSS** : `^3.4`

---

## Installation

### Commande
```bash
npm install -D tailwindcss@^3.4 postcss autoprefixer
npx tailwindcss init -p
```

---

## Configuration `tailwind.config.js`

```javascript
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./resources/**/*.blade.php",
    "./resources/**/*.js",
    "./ui-kit/**/*.html",
    "./node_modules/preline/dist/*.js",
  ],
  theme: {
    extend: {},
  },
  plugins: [
    require('preline/plugin'),
  ],
}
```

---

## Fichier CSS Principal

**Chemin** : `app/resources/css/app.css`

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

---

## Preline UI

### Installation
```bash
npm install preline
```

**Note** : Preline est déjà référencé dans la configuration Tailwind ci-dessus.

---

## Build Assets

### Mode Développement
```bash
cd app
npm run dev
```

### Mode Production
```bash
cd app
npm run build
```

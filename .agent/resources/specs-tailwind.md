# Spécifications : Installation Tailwind CSS + Preline UI

## 🎯 Objectif
Installer et configurer Tailwind CSS avec Preline UI dans le projet Laravel.

---

## 📦 Technologies
- **Tailwind CSS** : v3.x (dernière version stable)
- **Preline UI** : Composants UI basés sur Tailwind
- **PostCSS** : Intégré avec Laravel Mix/Vite

---

## 🔧 Commandes d'Installation

### Étape 1 : Installation Tailwind CSS
```bash
cd app
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

### Étape 2 : Installation Preline UI
```bash
npm install preline
```

---

## ⚙️ Configuration

### Fichier : `app/tailwind.config.js`
```javascript
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./resources/**/*.blade.php",
    "./resources/**/*.js",
    "./resources/**/*.vue",
    'node_modules/preline/dist/*.js',
  ],
  theme: {
    extend: {},
  },
  plugins: [
    require('preline/plugin'),
  ],
}
```

### Fichier : `app/resources/css/app.css`
Ajouter les directives Tailwind au début du fichier :
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### Fichier : `app/resources/js/app.js`
Ajouter l'import de Preline :
```javascript
import 'preline';
```

---

## 📝 Configuration Vite

### Fichier : `app/vite.config.js`
Vérifier que la configuration Vite inclut bien les fichiers CSS et JS :
```javascript
import { defineConfig } from 'vite';
import laravel from 'laravel-vite-plugin';

export default defineConfig({
    plugins: [
        laravel({
            input: ['resources/css/app.css', 'resources/js/app.js'],
            refresh: true,
        }),
    ],
});
```

---

## 🎨 Intégration dans le Layout

### Fichier : `app/resources/views/layouts/app.blade.php`
Créer ou modifier le layout principal pour inclure Vite :

```blade
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>@yield('title', 'Application')</title>
    
    @vite(['resources/css/app.css', 'resources/js/app.js'])
</head>
<body>
    @yield('content')
</body>
</html>
```

---

## ✅ Validation

### Test de Compilation
```bash
npm run dev
```

### Vérifications
- [ ] Tailwind CSS installé via npm
- [ ] Preline UI installé via npm
- [ ] `tailwind.config.js` configuré avec le content et le plugin Preline
- [ ] `app.css` contient les directives @tailwind
- [ ] `app.js` importe Preline
- [ ] `vite.config.js` est correctement configuré
- [ ] Le layout Blade utilise @vite
- [ ] `npm run dev` compile sans erreur

---

## 📚 Documentation

- **Tailwind CSS** : https://tailwindcss.com/docs/installation
- **Preline UI** : https://preline.co/docs/index.html
- **Laravel Vite** : https://laravel.com/docs/vite

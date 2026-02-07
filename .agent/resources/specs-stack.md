# Spécifications d'Initialisation Stack

Ce fichier définit les versions exactes, les commandes d'installation et les configurations pour initialiser l'environnement de développement.

---

## 1. Laravel Backend

### Version
- **Laravel** : `^11.0`
- **PHP** : `8.2+`

### Installation
```bash
composer create-project laravel/laravel:^11.0 app
```

**Note** : Cela créera l'application Laravel dans le dossier `app/` au lieu de la racine du projet.

### Configuration `.env`
```env
APP_NAME="Projet Technique"
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_TIMEZONE=UTC
APP_URL=http://localhost

LOG_CHANNEL=stack
LOG_DEPRECATIONS_CHANNEL=null
LOG_LEVEL=debug

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=projet_technique
DB_USERNAME=root
DB_PASSWORD=admin

BROADCAST_CONNECTION=log
CACHE_STORE=file
FILESYSTEM_DISK=local
QUEUE_CONNECTION=database
SESSION_DRIVER=database
SESSION_LIFETIME=120
```

### Dépendances Supplémentaires
```bash
# Laravel UI avec Tailwind
composer require laravel/ui
php artisan ui tailwind --auth

# Sanctum pour API
composer require laravel/sanctum
php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"

# Spatie Permissions
composer require spatie/laravel-permission
php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"
php artisan migrate
```

---

## 2. Tailwind CSS

### Version
- **Tailwind CSS** : `^3.4`

### Installation
```bash
npm install -D tailwindcss@^3.4 postcss autoprefixer
npx tailwindcss init -p
```

### Configuration `tailwind.config.js`
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

### Fichier CSS Principal `resources/css/app.css`
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### Preline UI
```bash
npm install preline
```

---

## 3. Alpine.js

### Version
- **Alpine.js** : `^3.14`

### Installation
```bash
npm install alpinejs@^3.14
```

### Intégration dans `resources/js/app.js`
```javascript
import Alpine from 'alpinejs'

window.Alpine = Alpine

Alpine.start()
```

---

## 4. MySQL

### Version
- **MySQL** : `8.0`

### Configuration
- **Host** : `127.0.0.1`
- **Port** : `3306`
- **Database** : `projet_technique`
- **Charset** : `utf8mb4`
- **Collation** : `utf8mb4_unicode_ci`

### Script de Création de Base
```sql
CREATE DATABASE IF NOT EXISTS projet_technique 
CHARACTER SET utf8mb4 
COLLATE utf8mb4_unicode_ci;
```

---

## 5. Outils de Qualité

### Laravel Pint

#### Installation
```bash
composer require laravel/pint --dev
```

#### Configuration `pint.json`
```json
{
    "preset": "psr12",
    "rules": {
        "simplified_null_return": true,
        "braces": false,
        "new_with_braces": true,
        "method_argument_space": {
            "on_multiline": "ensure_fully_multiline"
        }
    }
}
```

### Laravel IDE Helper (Optionnel)

#### Installation
```bash
composer require --dev barryvdh/laravel-ide-helper
```

#### Commandes de Génération
```bash
php artisan ide-helper:generate
php artisan ide-helper:models
php artisan ide-helper:meta
```

---

## 6. Architecture des Dossiers

### Dossiers à Créer

```
projet-technique/
├── app/                   # Application Laravel (créé par composer)
│   ├── app/
│   │   ├── Services/      # Logique métier (Service Pattern)
│   │   ├── Policies/      # Autorisations
│   │   └── Http/
│   │       └── Requests/  # Form Requests
│   ├── resources/
│   │   ├── views/
│   │   │   ├── components/    # Blade Components
│   │   │   └── layouts/
│   │   ├── css/
│   │   └── js/
│   ├── tests/
│   │   ├── Feature/
│   │   └── Unit/
│   ├── public/
│   ├── routes/
│   ├── database/
│   └── ...
└── ui-kit/                # Composants UI statiques (hors Laravel)
    ├── atoms/
    ├── molecules/
    └── index.html
```

### Commandes de Création
```bash
# Dossiers métier Laravel (à exécuter après installation de Laravel)
cd app
mkdir -p app/Services
mkdir -p app/Policies

# UI Kit (à la racine du projet)
cd ..
mkdir -p ui-kit/atoms
mkdir -p ui-kit/molecules

# Blade Components (déjà dans Laravel)
cd app
mkdir -p resources/views/components
mkdir -p resources/views/layouts
```

---

## 7. Git & Versionning

### Initialisation
```bash
git init
git add .
git commit -m "Initial commit: Laravel 11 + Tailwind + Alpine"
```

### `.gitignore` (Déjà présent dans Laravel)
Vérifier la présence de :
```
/node_modules
/public/hot
/public/storage
/storage/*.key
/vendor
.env
.env.backup
.phpunit.result.cache
Homestead.json
Homestead.yaml
npm-debug.log
yarn-error.log
```

---

## 8. Démarrage Rapide

### Installation Complète
```bash
# Se placer dans le dossier Laravel
cd app

# Dépendances PHP
composer install

# Dépendances JS
npm install

# Clé d'application
php artisan key:generate

# Migration
php artisan migrate

# Build assets
npm run dev
```

### Serveurs de Développement
```bash
# Se placer dans le dossier Laravel
cd app

# Terminal 1 : Laravel
php artisan serve

# Terminal 2 : Vite (Hot Reload)
npm run dev
```

---

## 9. Versions Node & Composer

### Node.js
- **Version** : `20.x LTS`

### Composer
- **Version** : `2.7+`

### Vérification
```bash
node --version   # v20.x
npm --version    # 10.x
composer --version  # 2.7+
php --version    # 8.2+
```

---

## Notes Importantes

- **Environnement** : Toutes les commandes sont testées sur Windows (PowerShell) et Linux (Ubuntu LTS)
- **Nginx** : Configuration Nginx standard Laravel (voir documentation officielle)
- **Permissions** : Vérifier les permissions sur `storage/` et `bootstrap/cache/`
- **Seeding** : Utiliser `php artisan db:seed` après configuration des seeders

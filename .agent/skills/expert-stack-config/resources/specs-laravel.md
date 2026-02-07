# Spécifications : Laravel Backend

Ce fichier définit les versions, commandes d'installation et configurations pour Laravel.

---

## Version
- **Laravel** : `^11.0`
- **PHP** : `8.2+`

---

## Installation

### Commande
```bash
composer create-project laravel/laravel app
```

**Note** : Cela créera l'application Laravel dans le dossier `app/` au lieu de la racine du projet.

---

## Configuration `.env`

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

---

## Dépendances Supplémentaires

### Laravel UI avec Tailwind
```bash
composer require laravel/ui
php artisan ui tailwind --auth
```

### Sanctum pour API
```bash
composer require laravel/sanctum
php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"
```

### Spatie Permissions
```bash
composer require spatie/laravel-permission
php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"
php artisan migrate
```

---

## Post-Installation

### Générer la clé d'application
```bash
cd app
php artisan key:generate
```

### Installer les dépendances
```bash
cd app
composer install
```

### Lancer les migrations
```bash
cd app
php artisan migrate
```

---

## Serveur de Développement

```bash
cd app
php artisan serve
```

**URL par défaut** : `http://localhost:8000`

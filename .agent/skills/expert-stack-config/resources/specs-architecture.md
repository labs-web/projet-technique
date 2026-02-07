# Spécifications : Architecture & Git

Ce fichier définit l'architecture des dossiers et la configuration Git.

---

## Architecture des Dossiers

### Structure Complète

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

#### Dossiers Laravel
```bash
cd app
mkdir -p app/Services
mkdir -p app/Policies
```

#### Dossiers UI Kit
```bash
# À la racine du projet
mkdir -p ui-kit/atoms
mkdir -p ui-kit/molecules
```

#### Blade Components
```bash
cd app
mkdir -p resources/views/components
mkdir -p resources/views/layouts
```

---

## Git & Versionning

### Initialisation
```bash
git init
git add .
git commit -m "Initial commit: Laravel + Tailwind + Alpine"
```

### `.gitignore`

Laravel inclut déjà un `.gitignore` complet. Vérifier la présence de :

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

## Notes Importantes

- **Environnement** : Toutes les commandes sont testées sur Windows (PowerShell) et Linux (Ubuntu LTS)
- **Nginx** : Configuration Nginx standard Laravel (voir documentation officielle)
- **Permissions** : Vérifier les permissions sur `storage/` et `bootstrap/cache/`
- **Seeding** : Utiliser `php artisan db:seed` après configuration des seeders

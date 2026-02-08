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

### Création de l'architecture
L'agent doit créer ces dossiers s'ils n'existent pas.
- `app/app/Services`
- `app/app/Policies`
- `ui-kit/atoms`
- `ui-kit/molecules`
- `app/resources/views/components`
- `app/resources/views/layouts`

---

## Git & Versionning

### Initialisation (MANUEL DÉVELOPPEUR)
L'agent ne doit **JAMAIS** initialiser le dépôt Git.

```bash
git init
git add .
git commit -m "Initial commit: Laravel + Tailwind + Alpine"
```



---

## Notes Importantes

- **Environnement** : Toutes les commandes sont testées sur Windows (PowerShell) et Linux (Ubuntu LTS)
- **Nginx** : Configuration Nginx standard Laravel (voir documentation officielle)
- **Permissions** : Vérifier les permissions sur `storage/` et `bootstrap/cache/`
- **Seeding** : Utiliser `php artisan db:seed` après configuration des seeders

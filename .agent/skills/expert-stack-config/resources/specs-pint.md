# Spécifications : Outils de Qualité

Ce fichier définit les outils de qualité de code (Laravel Pint, IDE Helper).

---

## Laravel Pint

### Version
- Inclus avec Laravel 11

### Installation
```bash
composer require laravel/pint --dev
```

### Configuration `pint.json`

**Chemin** : `app/pint.json`

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

### Utilisation
```bash
cd app
./vendor/bin/pint
```

---

## Laravel IDE Helper (Optionnel)

### Installation
```bash
composer require --dev barryvdh/laravel-ide-helper
```

### Commandes de Génération
```bash
cd app
php artisan ide-helper:generate
php artisan ide-helper:models
php artisan ide-helper:meta
```

**Note** : Ces commandes génèrent des fichiers d'aide pour l'auto-complétion dans les IDE.

---

## Versions

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

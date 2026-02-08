# Spécifications : Installation Manuelle de Laravel

## 🎯 Objectif
Fournir la commande standard pour initialiser un projet Laravel conformément à la stack technique du projet.

---

## 🔧 Commande d'Installation
*(À exécuter manuellement dans le terminal du projet)*

```bash
composer create-project laravel/laravel:^11.0 app
```
- **Version recommandée** : Laravel 11.x
- **Dossier cible** : `app/`

---

## ⚙️ Configuration Initiale (.env)

Une fois l'installation terminée, vérifier les paramètres suivants dans `app/.env` :

### Base de Données (Optionnel / À configurer selon besoin)
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=
```
*(Si vous n'utilisez pas de BDD pour l'instant, ces valeurs peuvent rester ainsi ou pointer vers SQLite)*

---

## 🔒 Post-Installation
1. **Générer la clé d'application** : `php artisan key:generate`
2. **Vérifier les permissions** : `storage/` et `bootstrap/cache/` doivent être accessibles en écriture.
3. **Lancer le serveur de développement** : `php artisan serve`

---

## ✅ Checklist de Validation
- [ ] Dossier `app/` créé
- [ ] Fichier `artisan` présent à la racine de `app/`
- [ ] Commande `php artisan --version` retourne Laravel Framework 11.x

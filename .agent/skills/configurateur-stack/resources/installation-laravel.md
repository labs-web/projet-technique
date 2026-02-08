# Spécifications : Installation Manuelle de Laravel

## 🎯 Objectif
Fournir la commande standard pour initialiser un projet Laravel conformément à la stack technique du projet.

---

## 🔧 Commande d'Installation
*(ACTION MANUELLE DÉVELOPPEUR)*
L'agent ne doit **JAMAIS** exécuter cette commande. Elle est fournie pour information.

```bash
composer create-project laravel/laravel app
```
- **Version** : Dernière version stable (Laravel 11+, 12...)
- **Dossier cible** : `app/`

> **Note - Erreur SSL** : Si `composer` échoue, vérifiez votre antivirus (analyse SSL) et désactivez-le temporairement.

---

## ⚙️ Configuration Initiale (.env)

Une fois l'installation terminée, vérifier les paramètres suivants dans `app/.env` :

### Base de Données (Standard Projet)
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=admin
```
*(Standard imposé : MySQL. Ne pas utiliser SQLite)*

---

## 🔒 Post-Installation
1. **Générer la clé d'application** : `php artisan key:generate`
2. **Vérifier les permissions** : `storage/` et `bootstrap/cache/` doivent être accessibles en écriture.
3. **Lancer le serveur de développement** : `php artisan serve`

---

## ✅ Checklist de Validation
- [ ] Dossier `app/` créé
- [ ] Fichier `artisan` présent à la racine de `app/`
- [ ] Commande `php artisan --version` retourne une version récente du Framework

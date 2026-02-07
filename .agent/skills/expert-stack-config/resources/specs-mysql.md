# Spécifications : MySQL

Ce fichier définit les versions et configurations pour MySQL.

---

## Version
- **MySQL** : `8.0`

---

## Configuration

- **Host** : `127.0.0.1`
- **Port** : `3306`
- **Database** : `projet_technique`
- **Charset** : `utf8mb4`
- **Collation** : `utf8mb4_unicode_ci`

---

## Script de Création de Base

```sql
CREATE DATABASE IF NOT EXISTS projet_technique 
CHARACTER SET utf8mb4 
COLLATE utf8mb4_unicode_ci;
```

---

## Vérification de la Connexion

### Via MySQL CLI
```bash
mysql -u root -p
```

### Via Laravel
```bash
cd app
php artisan migrate
```

Si les migrations s'exécutent sans erreur, la connexion est fonctionnelle.

---

## Notes Importantes

- **Permissions** : Assurez-vous que l'utilisateur MySQL a les droits sur la base `projet_technique`.
- **Configuration Laravel** : Les paramètres de connexion sont dans `app/.env` (voir `specs-laravel.md`).

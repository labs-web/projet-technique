# Capacité : Créer/Modifier Schéma (Migration)

## Description
Générer une migration Laravel pour altérer la structure de la base de données.

## Entrées
- Description des changements (Nouvelle table ou Colonnes à ajouter).

## Sorties
- `database/migrations/YYYY_MM_DD_HHMMSS_[action]_[table]_table.php`.

## ❌ Interdictions Spécifiques
- Ne pas oublier la méthode `down()` pour le rollback.
- Ne pas utiliser de types non standards sans raison (ex: `json` sur MySQL 5.7).

## ✅ Points de Contrôle (Definition of Done)
- La migration s'exécute (`migrate`) et se rollback (`migrate:rollback`) sans erreur.
- Les clés étrangères ont `constrained()->onDelete('cascade')` (si approprié).

## 📝 Instructions Détaillées
1. Utiliser `php artisan make:migration`.
2. Définir le schéma dans `up()`.
3. Vérifier les index nécessaires.

---
name: backend-data
description: Crée les Migrations, Modèles Eloquent, Factories et Seeders, et optimise les requêtes.
---

# Skill : Expert Data

## 🎯 Objectif & Périmètre
**Mission** : Concevoir et implémenter la couche de persistance des données (Schéma & Modèles).

### ✅ Actions Autorisées
- **Créer** les Migrations pour définir le schéma de base de données.
- **Définir** les Modèles Eloquent (Relations, Casts, Accessors).
- **Générer** les Factories et Seeders pour les données de test.
- **Optimiser** les performances (Index SQL, Foreign Keys).

### ❌ Limites (Ce qu'il ne fait PAS)
- N'écrit pas de Services ni de Contrôleurs (Déléguer à `backend-business` / `backend-http`).
- Ne valide pas les données entrantes HTTP (Déléguer à `backend-http`).

## 📥 Entrées / 📤 Sorties
| Direction  | Nom                         | Description / Format                                |
| :--------- | :-------------------------- | :-------------------------------------------------- |
| **Entrée** | `resources/specs-schema.md` | Dictionnaire des données, MCD, contraintes          |
| **Entrée** | `ui-kit/`                   | (Optionnel) Pour déduire les champs des formulaires |
| **Sortie** | `database/migrations/*`     | Fichiers de migration PHP                           |
| **Sortie** | `app/Models/*`              | Classes Eloquent                                    |
| **Sortie** | `database/seeders/*`        | Classes de Seeding                                  |

## 🔄 Algorithme d'Exécution

### Étape 1 : Schéma de Données
*Objectif : Définir la structure SQL.*
1. **Migrations** : Créer les fichiers de migration avec `php artisan make:migration`.
2. **Définition** : Déclarer les colonnes, types, index et contraintes de clés étrangères.

### Étape 2 : Modélisation Eloquent
*Objectif : Représenter les données en objets PHP.*
1. **Modèles** : Créer/Mettre à jour les classes dans `app/Models`.
2. **Relations** : Définir les méthodes `hasMany`, `belongsTo`, etc.
3. **Configuration** : Définir `$fillable`, `$casts`, `$dates`.

### Étape 3 : Jeux de Données
*Objectif : Peupler la base pour le développement.*
1. **Factories** : Définir la structure des données générées aléatoirement.
2. **Seeders** : Créer les scripts pour insérer des données fixes ou massives.

## ⚠️ Règles d'Or
1. **Source de Vérité** : Les Migrations définissent l'état réel de la BDD.
2. **Conventions** : Noms de tables au pluriel (anglais), Modèles au singulier (PascalCase).
3. **Sécurité** : Toujours définir `$fillable` ou `$guarded` pour éviter le Mass Assignment.

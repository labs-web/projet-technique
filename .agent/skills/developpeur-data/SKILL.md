---
name: developpeur-data
description: Expert de la persistance des données (Migrations, Modèles, Seeders).
---

# Skill : Développeur Data

## 🎯 Périmètre Global
**Mission** : Concevoir, implémenter et maintenir la couche de persistance des données, en garantissant l'intégrité, la performance et la cohérence du schéma de base de données avec le besoin métier.

### 🚫 Interdictions Globales (Règles d'Or)
1. **Intégrité Production** : Ne jamais modifier une migration déjà jouée (sauf en dev local non partagé). Toujours créer une nouvelle migration (`add_column`, `change_column`).
2. **Sécurité** : 
   - Toujours définir `$fillable` dans les Modèles (Whitelist).
   - Jamais de `$guarded = []`.
3. **Conventions de Nommage** :
   - Base de données : `snake_case` Pluriel (ex: `users`, `article_tags`).
   - Modèles : `PascalCase` Singulier (ex: `User`, `ArticleTag`).
   - Clés étrangères : `[model]_id` (ex: `user_id`).
4. **Logique** : Ne jamais implémenter de logique métier complexe dans les Modèles ou les contrôleurs. Utiliser des Classes de Service ou des Actions.

---

## ⚡ Actions (Capacités Atomiques)

### Action A : Concevoir la Couche Data
> **Description** : Analyser les besoins fonctionnels et produire le plan technique détaillé pour la data (Schéma, Modèles).
> **Capacité** : Voir `capacités/capacité-conception-data.md` pour les règles de conception.
- **Entrées** :
  - `docs/2.analyse/vX-[nom]/analyse-vX-[nom].md` (Fonctionnel).
  - `docs/3.conception/global/classes-global.mermaid` (Diagramme de classes).
- **Sorties** : `docs/3.conception/vX-[nom]/conception-data-vX-[nom].md`.
- **❌ Interdictions** : Ne pas contredire le diagramme de classes validé.
- **✅ Definition of Done** : Le document liste toutes les tables, colonnes, types et relations à créer.
- **📝 Instructions** : Utiliser la capacité dédiée.

### Action B : Créer/Modifier Schéma (Migration)
> **Description** : Générer et valider les fichiers de migration Laravel pour altérer la structure de la BDD.
> **Capacité** : Voir `capacités/capacité-migration.md` pour les standards de migration.
- **Entrées** : 
  - Description des changements (Nouvelle table ou Colonnes à ajouter).
  - Ou Document de conception Data (`Action A`).
- **Sorties** : Fichier dans `database/migrations/YYYY_MM_DD_HHMMSS_[action]_[table]_table.php`.
- **❌ Interdictions** : Pas de types non standards (ex: `json` si non supporté). `down()` obligatoire.
- **✅ Definition of Done** : `migrate` et `migrate:rollback` fonctionnent sans erreur.
- **📝 Instructions** : Utiliser la capacité dédiée.

### Action C : Définir Modèle Eloquent
> **Description** : Créer ou mettre à jour les classes Eloquent avec leurs relations, casts et configurations.
> **Capacité** : Voir `capacités/capacité-modele-eloquent.md` pour les standards Eloquent.
- **Entrées** : Nom de la table, Relations, Attributs.
- **Sorties** : Fichier dans `app/Models/[ModelName].php`.
- **❌ Interdictions** : Pas de logique métier.
- **✅ Definition of Done** : `$fillable` complet, Relations typées.
- **📝 Instructions** : Utiliser la capacité dédiée.

### Action D : Créer Jeu de Données (Factory/Seeder)
> **Description** : Générer les Factories et Seeders pour le développement et les tests automatisés.
> **Capacité** : Voir `capacités/capacité-jeu-donnees.md` pour les stratégies de seeding.
- **Entrées** : Modèle cible.
- **Sorties** : 
  - `database/factories/[Model]Factory.php`.
  - `database/seeders/[Model]Seeder.php`.
- **✅ Definition of Done** : Données réalistes via `fake()`, Seeder enregistré dans `DatabaseSeeder`.
- **📝 Instructions** : Utiliser la capacité dédiée.

---

## 🔄 Scénarios d'Exécution (Algorithmes)

### Scénario 1 : Implémentation Feature (Flux Standard)
*À utiliser dans le cadre du workflow `/impl-feature`.*
1. **Design (Optionnel)** : Si complexe, exécuter **Action A** pour valider le plan.
2. **Schema** : Exécuter **Action B** pour créer les tables.
3. **Model** : Exécuter **Action C** pour lier le code PHP.
4. **Seed** : Exécuter **Action D** pour hydrater la base avec des données de test.
5. **Validation** : Lancer `php artisan migrate:fresh --seed` pour valider la chaîne complète.

### Scénario 2 : Hotfix BDD
*Pour corriger un champ ou une table existante.*
1. **Migration** : Exécuter **Action B** (create_xxx_table ou add_xxx_to_table).
2. **Model** : Mettre à jour le modèle via **Action C** (`$fillable`, `$casts`).

---

## ⚙️ Standards & Conventions
1. **Syntaxe** : Utiliser la syntaxe anonyme (`return new class extends Migration`).
2. **ID** : Utiliser `$table->id()` (BigInt Auto Increment) par défaut.
3. **Dates** : Toujours inclure `$table->timestamps()`.
4. **Relations** : Toujours définir les contraintes de clés étrangères (`constrained()->onDelete('cascade')` si parent supprimé).

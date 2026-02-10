# Capacité : Créer Jeu de Données (Factory/Seeder)

## Description
Générer des données de test réalistes.

## Entrées
- Modèle cible.

## Sorties
- `database/factories/[Model]Factory.php`, `database/seeders/[Model]Seeder.php`.

## ✅ Points de Contrôle (Definition of Done)
- La Factory utilise `fake()` pour des données variées.
- Le Seeder est appelé dans `DatabaseSeeder.php`.

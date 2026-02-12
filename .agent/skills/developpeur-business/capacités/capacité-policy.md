# Capacité : Définir Policy (Autorisation)

## Description
Créer et implémenter une Policy pour sécuriser l'accès aux ressources.

## Entrées
- Modèle cible (ex: `Article`).

## Sorties
- `app/Policies/[Model]Policy.php`.

## ❌ Interdictions Spécifiques
- Ne pas laisser de méthode vide (retourner `false` par défaut).

## ✅ Points de Contrôle (Definition of Done)
- La Policy est enregistrée (automatique en Laravel 11 ou via AuthServiceProvider).
- Les méthodes standard (`view`, `create`, `update`, `delete`) sont implémentées.

## 📝 Instructions Détaillées
1. Utiliser `php artisan make:policy [Name]Policy --model=[Model]`.
2. Implémenter la logique booléenne dans chaque méthode.

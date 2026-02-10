# Capacité : Définir Modèle Eloquent

## Description
Configurer la classe Eloquent reflétant une table.

## Entrées
- Table associée, Relations, Attributs.

## Sorties
- `app/Models/[ModelName].php`.

## ❌ Interdictions Spécifiques
- Ne pas inclure de logique métier complexe dans le modèle.

## ✅ Points de Contrôle (Definition of Done)
- `$fillable` est défini.
- `$casts` est utilisé pour les types natifs (boolean, date, array).
- Les méthodes de relation (`hasMany`, etc.) sont typées.

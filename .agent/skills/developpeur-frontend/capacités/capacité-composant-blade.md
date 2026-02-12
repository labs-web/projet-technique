# Capacité : Créer/Adapter Composant Blade

## Description
Convertir un composant HTML statique du UI Kit en composant Blade réutilisable.

## Entrées
- `ui-kit/atoms/[name].html`.

## Sorties
- `resources/views/components/[name].blade.php`.

## ❌ Interdictions Spécifiques
- Ne pas coder en dur les textes, utiliser des slots ou des props.

## ✅ Points de Contrôle (Definition of Done)
- Le composant accepte les attributs HTML standards (`$attributes->merge()`).
- Les variables par défaut sont définies (`@props`).

## 📝 Instructions Détaillées
1. Copier le HTML du kit.
2. Remplacer le contenu variable par `{{ $slot }}`.
3. Gérer les classes dynamiques avec `@class([])`.

# Capacité : Intégrer Page (View)

## Description
Assembler les composants pour créer une page complète connectée aux données.

## Entrées
- Maquette de page, Données attendues du contrôleur.

## Sorties
- `resources/views/[page].blade.php`.

## ❌ Interdictions Spécifiques
- Ne pas effectuer de requêtes DB dans une vue.

## ✅ Points de Contrôle (Definition of Done)
- La vue étend un Layout principal (`<x-layouts.app>`).
- Les directives `@auth`, `@guest`, `@error` sont utilisées pour l'UX.
- Le titre de la page est défini.

## 📝 Instructions Détaillées
1. Créer la vue dans le dossier approprié.
2. Étendre le layout.
3. Intégrer les composants et boucler sur les données.

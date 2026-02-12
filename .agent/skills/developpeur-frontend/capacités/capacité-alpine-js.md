# Capacité : Ajouter Interactivité (Alpine.js)

## Description
Dynamiser les éléments d'interface (Modale, Dropdown, Toggle).

## Entrées
- Vue Blade existante.

## Sorties
- Code Alpine ajouté (`x-data`, `x-on:click`).

## ❌ Interdictions Spécifiques
- Ne pas écrire de logique métier JS complexe dans le HTML -> Extraire dans un fichier JS si > 10 lignes.

## ✅ Points de Contrôle (Definition of Done)
- L'état est réactif.
- Pas de "FOUC" (Flash of Unstyled Content) -> utiliser `x-cloak`.

## 📝 Instructions Détaillées
1. Identifier la zone dynamique.
2. Définir l'état avec `x-data`.
3. Ajouter les interactions.

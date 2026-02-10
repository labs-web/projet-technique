# Capacité : Conception Technique Data

## Description
Rédiger le plan technique de la couche Data pour une version (Schéma, Modèles, Sécurité).

## Entrées
- `docs/2.analyse/vX-[nom]/analyse-vX-[nom].md` (Analyse Version)
- `docs/3.conception/global/classes-global.mermaid` (Diagramme Classes Global)
- `docs/3.conception/vX-[nom]/classes-vX-[nom].mermaid` (Diagramme Classes Version)

## Sorties
- `docs/3.conception/vX-[nom]/conception-data-vX-[nom].md`

## ❌ Interdictions Spécifiques
- Ne pas inventer de règles métier qui contredisent l'analyse.

## ✅ Points de Contrôle (Definition of Done)
- Liste exhaustive des migrations à créer.
- Liste des modèles Eloquent avec leurs relations et `$fillable`.
- Stratégie de seeding définie.

## 📝 Instructions Détaillées
1. **Analyser** les diagrammes de classes pour identifier les nouvelles tables et relations.
2. **Définir** les migrations nécessaires (création de table, ajout de colonne, index).
3. **Spécifier** les modèles Eloquent correspondants (nom, table, relations `hasOne`/`hasMany`/`belongsTo`).
4. **Planifier** les factories et seeders pour peupler la base avec des données de test pertinentes.
5. **Rédiger** le document de conception technique Data en suivant le template standard (si disponible) ou une structure claire.

---
name: modelisation-uml
description: Expert en modélisation et schématisation technique (Analyse/Use Case & Conception/Class Diagram).
---

# Skill : modelisation-uml

## 🎯 Objectif
Produire des diagrammes visuels standards pour illustrer l'analyse fonctionnelle et la conception technique.

## 🛠️ Outils & Standards
- **Analyse (Use Case)** : Utilise **PlantUML** (`.puml`).
- **Conception (Classes)** : Utilise **Mermaid** (Code block `mermaid` dans MD).

## 📥 Entrées / 📤 Sorties
- **Entrée** : Description textuelle d'un besoin ou d'un schéma de données.
- **Sortie** : Code source du diagramme (Fichier `.puml` ou bloc Markdown).

## 🔄 Algorithme d'Exécution

### Action 1 : Modéliser Analyse (Use Case)
**Outil** : PlantUML
1. **Lecture** : Charger `resources/spec-plantuml.md`.
2. **Instruction** : Générer un diagramme de Cas d'Utilisation.
   - Identifier les **Acteurs** (Primaires à gauche, Secondaires à droite).
   - Identifier les **Use Cases** (Verbe à l'infinitif).
   - Définir les relations (`include`, `extend`, `generalization`).
3. **Sortie** : Créer un fichier `.puml` dans le dossier courant ou `docs/2.analyse/`.

### Action 2 : Modéliser Conception (Classes / DB)
**Outil** : Mermaid
1. **Lecture** : Charger `resources/spec-mermaid.md`.
2. **Instruction** : Générer un diagramme de Classes représentant les Entités/Models.
   - Définir les **Attributs** (Types précis si possible).
   - Définir les **Relations** (Cardinalités 1-n, n-n).
3. **Sortie** : Intégrer le bloc `mermaid` directement dans le fichier Markdown de conception.

---

## ✅ Critères de Qualité
- **PlantUML** : `left to right direction` utilisé pour la lisibilité.
- **Mermaid** : Syntaxe `classDiagram` valide.
- **Contenu** : Fidèle aux spécifications textuelles fournies en entrée.

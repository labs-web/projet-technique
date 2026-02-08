---
description: Workflow de création de diagrammes d'analyse (Use Cases).
---

# Workflow : Analyse UML

## 1. Contexte & Flux Global
**Objectif** : Formaliser les besoins fonctionnels sous forme de diagrammes de Cas d'Utilisation (Use Cases).
**Flux Type** : `[Besoin Textuel]` → `[Génération Diagramme]` → `[Validation]`

## 2. Exécution

### Étape 1 : Génération Diagramme (Analyse)

**1. Préparation des Données (Orchestration)**
- Localiser le fichier de besoin (ex: `docs/1.besoin/0-besoins.md` ou autre).
- Identifier le dossier cible pour l'analyse (ex: `docs/2.analyse/`).

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `analyste-uml`
- **Action** : `Générer Use Case (Par Version)` (ou `Analyser le Besoin Global` selon le cas)
- **Inputs Fournis** :
  - `Fichier Besoin` : Chemin du fichier source.
  - `Version` : Nom de la version à modéliser.

**3. Validation Humaine**
- **STOP** : Vérifier que le diagramme `.puml` généré reflète fidèlement le besoin (Acteurs, Cas, Relations).

## 3. Critères de Qualité
- [ ] **Clarté** : Le diagramme est lisible (pas trop d'éléments croisés).
- [ ] **Standard** : Utilise la syntaxe PlantUML valide.
- [ ] **Complétude** : Tous les acteurs et cas principaux sont présents.

---
description: Workflow de création de diagrammes d'analyse (Use Cases).
---

# Workflow : Analyse UML

## 1. Contexte & Flux Global
**Objectif** : Formaliser les besoins fonctionnels sous forme de diagrammes de Cas d'Utilisation (Use Cases).
**Flux Type** : `[Besoin Textuel]` → `[Génération Diagramme]` → `[Validation]`

## 2. Exécution

### Étape 1 : Génération Diagramme (Analyse)
> **Skill responsable** : `analyste-uml`
> **Flux Data** : 📥 `[Besoin Fonctionnel]` → 📤 `[Fichier .puml]`

**Instructions** :
1. Lire la description du besoin (ex: `0-besoins.md` ou autre document d'analyse).
2. Utiliser le skill `analyste-uml` pour traduire ce besoin en diagramme PlantUML.
   - Identifier les Acteurs et Cas d'Utilisation.
   - Définir les relations (`include`, `extend`, `generalization`).
3. Sauvegarder le diagramme dans `docs/2.analyse/` (ou dossier spécifié).
4. **STOP** : Demander la validation du diagramme visuel.

**Validation** : Le diagramme `.puml` reflète fidèlement le besoin fonctionnel.

---

## 3. Critères de Qualité
- [ ] **Clarté** : Le diagramme est lisible (pas trop d'éléments croisés).
- [ ] **Standard** : Utilise la syntaxe PlantUML valide.
- [ ] **Complétude** : Tous les acteurs et cas principaux sont présents.

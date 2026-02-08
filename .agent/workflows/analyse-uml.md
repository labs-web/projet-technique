---
description: Workflow unifié pour l'analyse fonctionnelle et la modélisation UML (Use Cases).
---

# Workflow : Analyse Fonctionnelle & UML (`/analyse-uml`)

## 1. Contexte & Flux Global
**Objectif** : Formaliser le besoin métier, structurer les lots (versions), et produire les diagrammes associés.
**Flux Type** : `[Analyse]` → `[Planification]` → `[Initialisation]` → `[Modélisation]`

## 2. Exécution

### Étape 1 : Diagnostic & Routage
**1. Analyse de la demande**
- Déterminer le périmètre (Scope) : Global, Version ou Diagramme.

**2. Décision**
- **Scope Global** : Exécuter **Action A**. À la fin, proposer **Action B**.
- **Scope Version** : Exécuter **Action B** (Ciblé) ou **Action D**.
- **Scope Diagramme** : Exécuter **Action D** directement.

---

### Étape 2 : Exécution Composite

#### Étape Action A : Analyse du Besoin Global
*Pour initier le projet à partir de l'expression de besoin.*

**1. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `analyste-uml`
- **Action** : `Action A : Analyser le Besoin Global`
- **Inputs Fournis** : `docs/1.besoin/besoin.md`

**2. Validation & Transition**
- **STOP** : Valider le contenu de `analyse-global.md`.
- **Proposition** : "Souhaitez-vous passer à l'**Action B : Planifier les Versions** ?"

#### Étape Action B : Planification des Versions (Stratégie)
*Pour définir la roadmap sans créer de fichiers.*

**1. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `analyste-uml`
- **Action** : `Action B : Planifier les Versions (Stratégie)`
- **Inputs Fournis** : `docs/2.analyse/global/analyse-global.md`

**2. Validation & Transition**
- **STOP** : Valider la création et le contenu de `docs/2.analyse/global/planification-version.md`.
- **Proposition** : "Souhaitez-vous passer à l'**Action C : Initialiser une Version** ?"

#### Étape Action C : Initialiser une Version
*Pour créer l'arborescence et les fichiers d'analyse.*

**1. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `analyste-uml`
- **Action** : `Action C : Initialiser une Version`
- **Inputs Fournis** : 
    - `docs/2.analyse/global/analyse-global.md`
    - `docs/2.analyse/global/planification-version.md`
    - Choix utilisateur ("Toutes" ou version spécifique).

**2. Validation & Transition**
- **STOP** : Vérifier la présence des dossiers `vX` et fichiers `analyse-vX.md`.
- **Proposition** : "Souhaitez-vous passer à l'**Action D : Générer Use Case** ?"

#### Étape Action D : Générer Use Case
*Pour visualiser les fonctionnalités via PlantUML.*

**1. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `analyste-uml`
- **Action** : `Action D : Générer Use Case (Par Version)`
- **Inputs Fournis** : Les fichiers `analyse-vX.md` générés.

**2. Validation Finale**
- **STOP** : Vérifier la cohérence Texte/Diagramme et la syntaxe PlantUML.

---

## 3. Critères de Qualité
- [ ] **Cohérence** : Le diagramme reflète exactement l'analyse textuelle.
- **Standard** : Respect de la syntaxe PlantUML (`left to right direction`).
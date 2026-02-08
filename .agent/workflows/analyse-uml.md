---
description: Workflow unifié pour l'analyse fonctionnelle et la modélisation UML (Use Cases).
---

# Workflow : Analyse Fonctionnelle & UML (`/analyse-uml`)

## 1. Contexte & Flux Global
**Objectif** : Formaliser le besoin métier, structurer les lots (versions), et produire les diagrammes de Cas d'Utilisation. Ce workflow adapte son exécution selon la demande (analyse complète ou mise à jour ciblée).
**Flux Type** : `[Demande]` → `[Diagnostic Stratégie]` → `[Exécution Composite]` → `[Validation]`

## 2. Exécution

### Étape 1 : Diagnostic & Stratégie

**1. Préparation des Données (Orchestration)**
- Analyser la demande utilisateur pour déterminer le **scope** :
  - **Scope Global** : "Analyse tout le projet", "Initialise l'analyse".
  - **Scope Version** : "Mets à jour la V2", "Ajoute une feature à la V1".
  - **Scope Diagramme** : "Régénère le diagramme V3", "Corrige le PlantUML".

**2. Décision (Routage)**
- Si **Scope Global** ➔ Exécuter Étape 2a, puis 2b, puis 2c.
- Si **Scope Version** ➔ Exécuter Étape 2b (ciblé), puis 2c.
- Si **Scope Diagramme** ➔ Exécuter directement Étape 2c.

---

### Étape 2 : Exécution Composite

#### 2a. Analyse du Besoin Global (Si requis)
*Uniquement pour initier le projet ou refondre la vision.*

**1. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `analyste-uml`
- **Action** : `Analyser le Besoin Global`
- **Inputs Fournis** :
  - `Source` : `docs/1.besoin/1.besoin.md` (ou autre source fournie).

**2. Validation Humaine**
- **STOP** : Valider la liste des fonctionnalités dans `docs/2.analyse/global-features.md`.

#### 2b. Planification des Versions (Si requis)
*Pour structurer ou restructurer les lots.*

**1. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `analyste-uml`
- **Action** : `Planifier les Versions (Lotissement)`
- **Inputs Fournis** :
  - `Source` : `docs/2.analyse/global-features.md`.

**2. Validation Humaine**
- **STOP** : Vérifier la cohérence du découpage en versions (Dossiers `vX`).

#### 2c. Génération des Diagrammes (Toujours)
*Pour visualiser le résultat final.*

**1. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `analyste-uml`
- **Action** : `Générer Use Case (Par Version)`
- **Inputs Fournis** :
  - `Version Cible` : "Toutes" ou nom spécifique (ex: "v2-social").
  - `Source` : Fichiers `analyse-vX.md`.

**2. Validation Humaine**
- **STOP** : Vérifier que le diagramme `.puml` est complet et syntaxiquement correct.

---

### Étape 3 : Synthèse & Clôture

**1. Préparation des Données (Orchestration)**
- Lister les fichiers créés ou modifiés.
- Fournir les liens vers les diagrammes générés.

**2. Validation Finale**
- Confirmer que l'analyse textuelle (`.md`) e le diagramme (`.puml`) sont synchronisés.

## 3. Critères de Qualité
- [ ] **Traçabilité** : Chaque diagramme correspond exactement à son fichier d'analyse Markdown.
- [ ] **Standard** : Respect de PlantUML (Direction `left to right`).
- [ ] **Portée** : Pas de détails techniques (BDD, Classes) dans l'analyse fonctionnelle.

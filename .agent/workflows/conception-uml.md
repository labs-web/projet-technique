---
description: Workflow de création de diagrammes de conception (Classes/DB).
---



<!-- ia : Refactoring de la structure du fichier de worflow suivre le template en utiisant le skill : expert-agent -->


# Workflow : Conception UML

## 1. Contexte & Flux Global
**Objectif** : Formaliser l'architecture technique et le modèle de données (Classes/DB).
**Flux Type** : `[Analyse/Entités]` → `[Génération Diagramme]` → `[Validation]`

## 2. Exécution

### Étape 1 : Génération Diagramme (Conception)

**1. Préparation des Données (Orchestration)**
- Rassembler la liste des entités ou le modèle de données validé (depuis l'analyse).
- Identifier le fichier de destination (ex: `implementation_plan.md` ou `docs/3.conception/`).

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `concepteur-uml`
- **Action** : `Modéliser le Domaine (Class Diagram)` et/ou `Modéliser la BDD (ER Diagram)`
- **Inputs Fournis** :
  - `Entités` : Liste des entités à modéliser.
  - `Type Diagramme` : Class ou ERD.

**3. Validation Humaine**
- **STOP** : Vérifier que les types de données sont explicites et les cardinalités correctes.

## 3. Critères de Qualité
- [ ] **Précision** : Les types de données sont explicites (int, string, etc.).
- [ ] **Relations** : Les cardinalités sont correctes et logiques.
- [ ] **Standard** : Syntaxe Mermaid `classDiagram` ou `erDiagram` valide.
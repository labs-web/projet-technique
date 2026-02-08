---
description: Workflow unifié pour la maintenance, l'évolution et l'amélioration continue de l'agent.
---

# Workflow : Maintenance Agent (`/maintenance-agent`)

## 1. Contexte & Flux Global
**Objectif** : Garantir l'intégrité et l'évolution contrôlée de la structure de l'agent (Skills, Rules, Workflows).
**Flux Type** : `[Demande]` → `[Diagnostic]` → `[Exécution Agent]` → `[Validation]`

## 2. Exécution

### Étape 1 : Diagnostic & Routage

**1. Préparation des Données (Orchestration)**
- Analyser la demande pour identifier le type d'objet (Skill, Rule, Workflow) et l'action (Create, Update).
- Identifier le nom de l'élément cible.

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `expert-agent`
- **Action** : `(Implied Analysis Step)` (ou directement passer à l'étape suivante)
- **Inputs Fournis** :
  - `Demande` : Texte de la demande utilisateur.

**3. Validation Humaine**
- **STOP** : Valider le triptyque Type/Action/Cible avant toute modification.

---

### Étape 2 : Exécution de la Maintenance

**1. Préparation des Données (Orchestration)**
- Sélectionner l'action appropriée dans `expert-agent`.

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `expert-agent`
- **Action** : 
  - `Manage Skill (Gérer Compétence)` (si Skill)
  - `Manage Rule (Gérer Règle)` (si Rule)
  - `Manage Workflow (Gérer Processus)` (si Workflow)
- **Inputs Fournis** :
  - `Name` : Nom de l'élément.
  - `Mode` : Create ou Update.
  - `Content` : Contenu ou spécifications.

**3. Validation Humaine**
- **STOP** : Vérifier que l'artefact créé/modifié respecte les standards (`specs/`).

---

### Étape 3 : Checkpoint & Documentation

**1. Préparation des Données (Orchestration)**
- Résumer les changements effectués.

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : (Interaction Directe)
- **Action** : `Report`
- **Inputs Fournis** :
  - `Changes` : Diff ou résumé des fichiers touchés.

**3. Validation Humaine**
- **STOP** : Confirmer que les modifications sont bien isolées dans `.agent/`.

## 3. Critères de Qualité
- [ ] **Unicité** : Pas de doublons fonctionnels.
- [ ] **Conformité** : Respect strict des templates et standards (`specs/`).
- [ ] **Isolation** : Seuls les fichiers de configuration de l'agent sont touchés.
---
description: Workflow unifié pour la maintenance, l'évolution et l'amélioration continue de l'agent.
---

# Workflow : Maintenance Agent (`/maintenance-agent`)

## 1. Contexte & Déclencheurs
Ce workflow centralise la modification de la structure de l'agent (Skills, Rules, Workflows).
- **Déclencheur** : Demande explicite du développeur ou appel d'un autre workflow.
- **Objectif** : Garantir l'intégrité du "cerveau" de l'agent lors des évolutions.

---

## 2. Exécution

### Étape 1 : Diagnostic & Routage
> **Skill responsable** : `expert-agent`
> **Action** : Analyse de la demande

**Instructions** :
1. **Identifier** l'objet de la demande :
   - **Type** : Skill, Rule, ou Workflow ?
   - **Action** : Création (`create`) ou Mise à jour/Correction (`update`) ?
   - **Cible** : Nom de l'élément concerné.
2. **Vérifier** l'existence de la cible (si mise à jour).

**Validation** : Le triptyque Type/Action/Cible est défini.

---

### Étape 2 : Exécution de la Maintenance
> **Skill responsable** : `expert-agent`
> **Action** : Exécution des Actions A, B ou C

**Instructions** :
Confier l'exécution au skill `expert-agent` qui détient la logique, les templates et les spécifications.

1. **Invoquer** l'action correspondante au type identifié :
   - **Skill** → Action A (`Manage Skill`).
   - **Rule** → Action B (`Manage Rule`).
   - **Workflow** → Action C (`Manage Workflow`).

2. **Paramètres** : Fournir explicitement le mode (`Create` ou `Update`) et le nom de la cible.

**Validation** : L'artefact (.md) est conforme aux standards du skill expert.

---

### Étape 3 : Checkpoint & Documentation
> **Skill responsable** : (Interaction Directe)

**Instructions** :
1. **Présenter** les changements à l'utilisateur (Diff ou résumé).
2. **STOP** : Demander une validation explicite avant d'appliquer définitivement (si destructif ou critique).
3. **Confirmer** que les modifications sont bien isolées dans le dossier `.agent/`.

**Validation** : Feu vert utilisateur.

---

## 3. Critères de Qualité
- [ ] **Unicité** : Pas de doublons fonctionnels.
- [ ] **Conformité** : Respect strict des templates et standards (`specs/`).
- [ ] **Isolation** : Seuls les fichiers de configuration de l'agent sont touchés.
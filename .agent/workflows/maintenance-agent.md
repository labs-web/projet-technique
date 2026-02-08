---
description: Workflow unifié pour la maintenance, l'évolution et l'amélioration continue de l'agent.
---

# Workflow : Maintenance Agent (`/maintenance-agent`)

## 1. Contexte & Flux Global
**Objectif** : Garantir l'intégrité et l'évolution contrôlée de la structure de l'agent (Skills, Rules, Workflows).
**Flux Type** : `[Analyse Optionnelle]` → `[Menu Interactif]` → `[Exécution]`

## 2. Exécution

### Étape 1 : Analyse de la Demande (Optionnelle)
**Si l'utilisateur fournit un message avec la commande**, analyser les mots-clés pour suggérer l'action appropriée.

**Logique de Détection** :
- Mots-clés **"skill"**, **"compétence"**, **"expert"**, **"créer skill"** → Suggérer **Action A**
- Mots-clés **"rule"**, **"règle"**, **"mémoire"**, **"contrainte"** → Suggérer **Action B**
- Mots-clés **"workflow"**, **"processus"**, **"slash"**, **"commande"** → Suggérer **Action C**

---

### Étape 2 : Affichage du Menu Interactif

**Présenter au développeur le menu suivant** :

> **Actions disponibles (Skill : expert-agent)** :
>
> **A.** Gérer un Skill (Compétence)  
> → Créer ou mettre à jour un skill dans `.agent/skills/`
>
> **B.** Gérer une Rule (Règle/Mémoire)  
> → Créer ou mettre à jour une règle dans `.agent/rules/`
>
> **C.** Gérer un Workflow (Processus)  
> → Créer ou mettre à jour un workflow dans `.agent/workflows/`
>
> [Si suggestion détectée] **→ Action suggérée : [X]** ← [MARQUÉE]
>
> **Quelle action souhaitez-vous exécuter ?** (Tapez A, B ou C)

**STOP** : Attendre la sélection du développeur.

---

### Étape 3 : Exécution de l'Action Choisie

Selon le choix du développeur, exécuter l'action correspondante du skill `expert-agent`.

#### Si Action A sélectionnée (Gérer Skill)
- **Skill Cible** : `expert-agent`
- **Action** : `Action A : Manage Skill (Gérer Compétence)`
- **Inputs Fournis** :
  - Demander au développeur : "Nom du skill ?"
  - Demander au développeur : "Mode ? (Create/Update)"
  - Demander au développeur : "Besoin/Description ?"
- **STOP** : Vérifier que le fichier `SKILL.md` respecte `specs/specs-skill.md`

#### Si Action B sélectionnée (Gérer Rule)
- **Skill Cible** : `expert-agent`
- **Action** : `Action B : Manage Rule (Gérer Règle)`
- **Inputs Fournis** :
  - Demander au développeur : "Nom de la règle ?"
  - Demander au développeur : "Mode ? (Create/Update)"
  - Demander au développeur : "Contenu de la règle ?"
- **STOP** : Vérifier que le fichier respecte `specs/specs-rule.md`

#### Si Action C sélectionnée (Gérer Workflow)
- **Skill Cible** : `expert-agent`
- **Action** : `Action C : Manage Workflow (Gérer Processus)`
- **Inputs Fournis** :
  - Demander au développeur : "Nom du workflow ?"
  - Demander au développeur : "Mode ? (Create/Update)"
  - Demander au développeur : "Étapes du processus ?"
- **STOP** : Vérifier que le fichier respecte `specs/specs-workflow.md`

---

## 3. Critères de Qualité
- **Découvrabilité** : Le développeur voit toutes les capacités de maintenance
- **Unicité** : Pas de doublons fonctionnels
- **Conformité** : Respect strict des templates et standards (`specs/`)
- **Isolation** : Seuls les fichiers de configuration de l'agent sont touchés

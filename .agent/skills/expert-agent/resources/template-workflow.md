---
description: [Description courte du workflow]
---

# Workflow : [Nom du Workflow] (`/[slug]`)

## 1. Contexte & Flux Global
**Objectif** : [Objectif global du workflow]
**Flux Type** : `[Étape 1]` → `[Étape 2]` → `[Étape 3]`

## 2. Exécution

### Étape 1 : Diagnostic & Routage
**1. Analyse de la demande**
- Analyser le périmètre (Scope).
- Identifier les actions requises.

**2. Décision**
- **Cas A** : Exécuter **Action A**.
- **Cas B** : Exécuter **Action B**.

---

### Étape 2 : Exécution Composite

#### Étape Action A : [Nom de l'Action A]
*[Description du but de cette action]*

**1. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `[Nom du Skill]`
- **Action** : `[Nom de l'Action dans le Skill]`
- **Inputs Fournis** : [Données nécessaires]

**2. Validation & Transition**
- **STOP** : [Critère de validation du résultat]
- **Proposition** : "Souhaitez-vous passer à l'**Action B** ?"

#### Étape Action B : [Nom de l'Action B]
*[Description du but de cette action]*

**1. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `[Nom du Skill]`
- **Action** : `[Nom de l'Action dans le Skill]`
- **Inputs Fournis** : [Données nécessaires]

**2. Validation & Transition**
- **STOP** : [Critère de validation du résultat]
- **Proposition** : "Souhaitez-vous terminer ou passer à l'**Action C** ?"

---

## 3. Critères de Qualité
- [ ] **Pertinence** : Le workflow répond au besoin identifié.
- [ ] **Conformité** : Les actions respectent les règles du Skill.

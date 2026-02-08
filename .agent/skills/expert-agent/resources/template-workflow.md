---
description: [Description courte du workflow]
---

# Workflow: [Nom du Workflow]

## 1. Contexte & Flux Global
**Objectif** : [Objectif global du workflow]
**Flux Type** : `[Demande]` → `[Diagnostic Stratégie]` → `[Exécution Composite]` → `[Validation]`

## 2. Exécution

### Étape 1 : Diagnostic & Stratégie

**1. Préparation des Données (Orchestration)**
- Analyser la demande utilisateur pour identifier le périmètre (Scope).
- Identifier les actions spécifiques du Skill à activer.

**2. Décision (Routage)**
- Établir le plan d'action (Quelles étapes sont nécessaires ?).
- *Exemple : Si demande "X" ➔ Activer Étape 2a.*

---

### Étape 2 : Exécution Composite
*Sélectionner les sous-étapes pertinentes ci-dessous selon le diagnostic.*

#### 2a. [Sous-Étape Optionnelle ou Séquentielle 1]

**1. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `[nom-du-skill]`
- **Action** : `[Nom exact de l'action dans le Skill]`
- **Inputs Fournis** :
  - `[Input 1]` : [Description/Valeur]

**2. Validation Humaine**
- **STOP** : [Critère de validation]

#### 2b. [Sous-Étape Optionnelle ou Séquentielle 2]

**1. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `[nom-du-skill]`
- **Action** : `[Nom exact de l'action dans le Skill]`
- **Inputs Fournis** :
  - `[Input 1]`

**2. Validation Humaine**
- **STOP** : [Critère de validation]

---

### Étape 3 : Synthèse & Clôture

**1. Préparation des Données (Orchestration)**
- Résumer les actions effectuées.
- Lister les artefacts produits.

**2. Validation Finale**
- **STOP** : Confirmer que l'ensemble répond à la demande initiale.

## 3. Critères de Qualité
- [ ] **Pertinence** : Le workflow s'adapte à la demande (pas d'étapes inutiles).
- [ ] **Complétion** : Le résultat final attendu est produit.
- [ ] **Tracabilité** : Les actions du Skill sont clairement identifiées.

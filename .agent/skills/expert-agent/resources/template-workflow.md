---
description: [Description courte du workflow]
---

# Workflow: [Nom du Workflow]

## 1. Contexte & Flux Global
**Objectif** : [Objectif global du workflow]
**Flux Type** : `[Entrée Initiale]` → `[Étape 1]` → `[Étape 2]` → `[Sortie Finale]`

## 2. Exécution
 
### Étape 1 : [Titre de l'étape - Quoi faire]

**1. Préparation des Données (Orchestration)**
- [Instruction pour rassembler/préparer les inputs nécessaires]
- [Instruction pour vérifier les pré-requis]

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `[nom-du-skill]`
- **Action** : `[Nom exact de l'action dans le Skill]`
- **Inputs Fournis** :
  - `[Input 1]` : [Description/Valeur]
  - `[Input 2]` : [Description/Valeur]

**3. Validation Humaine**
- **STOP** : [Critère de validation explicite - ex: Vérifier le fichier X]

---

### Étape 2 : [Titre de l'étape - Quoi faire]

**1. Préparation des Données (Orchestration)**
- [Préparer les inputs basés sur la sortie de l'étape précédente]

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `[nom-du-skill]`
- **Action** : `[Nom exact de l'action dans le Skill]`
- **Inputs Fournis** :
  - `[Input 1]`

**3. Validation Humaine**
- **STOP** : [Critère de validation explicite]

## 3. Critères de Qualité
- [ ] **Linéarité** : Le flux avance sans boucle.
- [ ] **Complétion** : Le résultat final attendu est produit.
- [ ] **Atomicité** : Chaque étape est gérée par un seul Skill principal.

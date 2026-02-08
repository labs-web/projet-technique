---
description: [Description courte du workflow]
---

# Workflow: [Nom du Workflow]

## 1. Contexte & Flux Global
**Objectif** : [Objectif global du workflow]
**Flux Type** : `[Entrée Initiale]` → `[Étape 1]` → `[Étape 2]` → `[Sortie Finale]`

## 2. Exécution
 
### Étape 1 : [Titre de l'action]
> **Skill responsable** : `[nom-du-skill]`
> **Flux Data** : 📥 `[Entrée]` → 📤 `[Sortie]`
   
   
**Instructions** :
1. Exécuter l'action **[Nom de l'action]** (via le Skill).
2. Produire le résultat attendu (Fichier, Analyse, Modification).
3. **STOP** : Demander la validation du développeur (Lecture du fichier ou Confirmation de l'action).

**Validation** : [Livrable] validé par le développeur.

---

### Étape 2 : [Titre de l'action]
> **Skill responsable** : `[nom-du-skill]`
> **Flux Data** : 📥 `[Sortie Étape 1]` → 📤 `[Livrable Final]`

**Instructions** :
1. Exécuter l'action **[Nom de l'action]** (via le Skill).
2. Produire le résultat attendu.
3. **STOP** : Demander la validation du développeur.

**Validation** : [Livrable] validé par le développeur.

---

## 3. Critères de Qualité
- [ ] **Linéarité** : Le flux avance sans boucle.
- [ ] **Complétion** : Le résultat final attendu est produit.
- [ ] **Atomicité** : Chaque étape est gérée par un seul Skill principal.

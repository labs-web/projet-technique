---
description: [Description courte du workflow]
---

# Workflow : [Nom du Workflow] (`/[slug]`)

## 1. Contexte & Flux Global
**Objectif** : [Objectif global du workflow]
**Flux Type** : `[Analyse Optionnelle]` → `[Menu Interactif]` → `[Exécution]`

## 2. Exécution

### Étape 1 : Analyse de la Demande (Optionnelle)
**Si l'utilisateur fournit un message avec la commande**, analyser les mots-clés pour suggérer l'action appropriée.

**Logique de Détection** :
- Mots-clés **"[mot1]"**, **"[mot2]"** → Suggérer **Action A**
- Mots-clés **"[mot3]"**, **"[mot4]"** → Suggérer **Action B**
- Mots-clés **"[mot5]"**, **"[mot6]"** → Suggérer **Action C**

---

### Étape 2 : Affichage du Menu Interactif

**Présenter au développeur le menu suivant** :

> **Actions disponibles (Skill : [nom-du-skill])** :
>
> **A.** [Nom de l'Action A]  
> → [Description courte de l'action A]
>
> **B.** [Nom de l'Action B]  
> → [Description courte de l'action B]
>
> **C.** [Nom de l'Action C]  
> → [Description courte de l'action C]
>
> [Si suggestion détectée] **→ Action suggérée : [X]** ← [MARQUÉE]
>
> **Quelle action souhaitez-vous exécuter ?** (Tapez A, B, C...)

**STOP** : Attendre la sélection du développeur.

---

### Étape 3 : Exécution de l'Action Choisie

Selon le choix du développeur, exécuter l'action correspondante du skill `[nom-du-skill]`.

#### Si Action A sélectionnée
- **Skill Cible** : `[nom-du-skill]`
- **Action** : `[Nom de l'Action A dans le Skill]`
- **Inputs Fournis** : [Données nécessaires]
- **STOP** : [Critère de validation]

#### Si Action B sélectionnée
- **Skill Cible** : `[nom-du-skill]`
- **Action** : `[Nom de l'Action B dans le Skill]`
- **Inputs Fournis** : [Données nécessaires]
- **STOP** : [Critère de validation]

#### Si Action C sélectionnée
- **Skill Cible** : `[nom-du-skill]`
- **Action** : `[Nom de l'Action C dans le Skill]`
- **Inputs Fournis** : [Données nécessaires]
- **STOP** : [Critère de validation]

---

## 3. Critères de Qualité
- **Découvrabilité** : Le développeur voit toutes les actions disponibles
- **Pertinence** : Les suggestions correspondent à l'intention
- **Conformité** : Les actions respectent les règles du Skill

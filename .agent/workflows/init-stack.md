---
description: Workflow d'initialisation de la stack technique. Exécuté une seule fois au début du projet.
---

# Workflow : Initialisation (`/init-stack`)

## 1. Contexte & Flux Global
**Objectif** : Installer et configurer le socle technique Laravel + Tailwind.
**Flux Type** : `[Rien]` → `[Stack Configurée]`

## 2. Exécution

⚠️ **RÈGLE CRITIQUE** : Toutes les commandes doivent être proposées au développeur et validées avant exécution (voir Skill pour détails).

---

### Étape 1 : Initialisation de l'Environnement Laravel
> **Skill responsable** : `expert-stack-config`  
> **Flux Data** : 📥 `[Rien]` → 📤 `[Laravel installé dans app/]`

**Instructions** :
1. Exécuter l'action **Installation Laravel** (via le Skill).
2. Configurer le fichier `.env` selon les specifications.
3. Initialiser le dépôt Git.
4. **STOP** : Demander la validation du développeur (Laravel opérationnel).

**Validation** : Laravel installé et configuré, validé par le développeur.

---

### Étape 2 : Configuration de la Stack Front-end
> **Skill responsable** : `expert-stack-config`  
> **Flux Data** : 📥 `[Laravel installé]` → 📤 `[Tailwind + Alpine + Preline configurés]`

**Instructions** :
1. Exécuter l'action **Configuration Tailwind CSS** (via le Skill).
2. Exécuter l'action **Installation Preline UI & Alpine.js** (via le Skill).
3. **STOP** : Demander la validation du développeur (npm install réussi).

**Validation** : Front-end configuré, validé par le développeur.

---

### Étape 3 : Configuration Qualité & Architecture
> **Skill responsable** : `expert-stack-config`  
> **Flux Data** : 📥 `[Stack configurée]` → 📤 `[Architecture complète]`

**Instructions** :
1. Exécuter l'action **Configuration Laravel Pint** (via le Skill).
2. Exécuter l'action **Création Architecture Dossiers** (via le Skill).
3. **STOP** : Demander la validation du développeur (Arborescence créée).

**Validation** : Architecture prête, validée par le développeur.

---

### Étape 4 : Validation Finale
> **Skill responsable** : `expert-stack-config`  
> **Flux Data** : 📥 `[Architecture complète]` → 📤 `[Environnement opérationnel]`

**Instructions** :
1. Présenter un résumé de l'environnement installé.
2. Demander au développeur de tester les serveurs (via commandes du Skill).
3. **STOP** : Demander la validation finale du développeur.

**Validation** : Environnement opérationnel et testé, validé par le développeur.

---

## 3. Critères de Qualité
- [ ] **Propreté** : Pas de fichiers inutiles par défaut.
- [ ] **Conformité** : Respect des versions demandées.

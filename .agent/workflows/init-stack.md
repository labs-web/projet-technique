---
description: Workflow d'initialisation de la stack technique. Exécuté une seule fois au début du projet.
---

# Workflow : Initialisation (`/init-stack`)

## 1. Contexte & Flux Global
**Objectif** : Installer et configurer le socle technique Laravel + Tailwind.
**Flux Type** : `[Rien]` → `[Stack Configurée]`

## 2. Exécution

### Étape 1 : Configuration Stack
> **Skill responsable** : `expert-stack-config`
> **Flux Data** : 📥 `[Specs]` → 📤 `[Projet Laravel]`

**Instructions** :
1. Installer Laravel et les dépendances.
2. Initialiser Git.
3. Configurer Tailwind et le Linter.
4. Créer l'arborescence des dossiers.
5. **STOP** : Demander la validation du développeur (Projet prêt à démarrer).

**Validation** : Environnement opérationnel validé par le développeur.

---

## 3. Critères de Qualité
- [ ] **Propreté** : Pas de fichiers inutiles par défaut.
- [ ] **Conformité** : Respect des versions demandées.

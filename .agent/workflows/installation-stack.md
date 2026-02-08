---
description: Assistant d'initialisation et de vérification du stack technique.
---

# Workflow : Installation & Configuration Stack (`/installation-stack`)

## 1. Contexte & Flux Global
**Objectif** : Guider l'initialisation du projet ou vérifier la conformité du stack technique existant conformément aux standards.
**Flux Type** : `[Analyse Demande]` → `[Planification Actions]` → `[Exécution Validée]`

### Mode d'Utilisation
Ce workflow est interactif.
- `@[/installation-stack] laravel`: Check/Install Laravel.
- `@[/installation-stack] preline`: Check/Install Tailwind+Preline.
- `@[/installation-stack] all`: Complete verification.

## 2. Exécution

### Étape 1 : Analyse de la Demande

**1. Préparation des Données (Orchestration)**
- Analyser les technologies mentionnées dans la demande.
- Définir l'ordre des opérations (Laravel -> Architecture -> Preline -> Alpine -> Lucide).

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `configurateur-stack`
- **Action** : `Audit` (Action interne, ou implied part of Installation Actions check)
- **Inputs Fournis** :
  - `Scope` : Liste des technos à vérifier.

**3. Validation Humaine**
- **STOP** : Valider la liste des actions à entreprendre.

---

### Étape 2 : Exécution Séquentielle Guide & Verify

**1. Préparation des Données (Orchestration)**
- Pour chaque technologie identifiée à l'étape 1.

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `configurateur-stack`
- **Action** :
  - `Installer Socle Laravel` (si Laravel)
  - `Configurer Frontend (Tailwind + Alpine + Preline)` (si Preline/Tailwind/Alpine)
  - `Initialiser Architecture Dossiers` (si Architecture)
  - `Installer Outils Complémentaires (Lucide)` (si Lucide)
- **Inputs Fournis** :
  - `Technology` : Nom de la techno.
  - `Mode` : Install or Verify.

**3. Validation Humaine**
- **STOP** : Attendre la fin de l'installation/vérification de chaque brique avant de passer à la suivante.

---

### Étape 3 : Récapitulatif

**1. Préparation des Données (Orchestration)**
- Synthétiser l'état final du stack.

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : (Interaction Directe)
- **Action** : `Report`
- **Inputs Fournis** :
  - `Status` : État installé/configuré.

**3. Validation Humaine**
- **STOP** : Vérifier que les commandes de développement (`npm run dev`, `php artisan serve`) fonctionnent.

---

### Étape 4 : Post-Mortem & Amélioration Continue

**1. Préparation des Données (Orchestration)**
- Analyser le déroulement pour détecter des frictions.

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : (Interaction Directe)
- **Action** : `Feedback`

**3. Validation Humaine**
- **STOP** : Lancer `/refine-skill` si nécessaire.

## 3. Critères de Qualité
- [ ] **Sécurité** : Aucune commande destructive sans validation explicite.
- [ ] **Intelligence** : Ne réinstalle pas ce qui est déjà là.
- [ ] **Douceur** : Complète la config (ex: Preline) sans écraser l'existant sans backup.

---
description: Workflow de mise à jour de l'interface utilisateur.
---

# Workflow : Mise à jour Interface (`/update-ui`)

## 1. Contexte & Flux Global
**Objectif** : Modifier le design (CSS), le texte ou l'ergonomie d'une page existante et propager le changement.
**Flux Type** : `[Demande UI]` → `[UI Kit Modifié]` → `[Blade Modifié]`

## 2. Exécution

### Étape 1 : Modification Design System

**1. Préparation des Données (Orchestration)**
- Identifier les changements à apporter (Design Token ou Composant).
- Localiser les fichiers concernés dans `ui-kit/`.

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `designer-ui`
- **Action** : `Créer Styleguide (Tokens)` / `Développer Composant Atomique` / `Assembler Molécule / Organisme`
- **Inputs Fournis** :
  - `Change` : Nouvelle règle ou composant.
  - `Context` : Fichiers statiques concernés.

**3. Validation Humaine**
- **STOP** : Vérifier le rendu visuel dans `ui-kit/` avant toute propagation.

---

### Étape 2 : Propagation Frontend

**1. Préparation des Données (Orchestration)**
- Récupérer les fichiers HTML/CSS modifiés.

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `developpeur-frontend`
- **Action** : `Créer/Adapter Composant Blade` / `Intégrer Page (View)`
- **Inputs Fournis** :
  - `HTML` : Fichier(s) UI Kit modifiés.
  - `Blade` : Fichier(s) View concernés.

**3. Validation Humaine**
- **STOP** : Vérifier que l'intégration Blade correspond aux maquettes HTML validées sans régression JS.

---

### Étape 3 : Post-Mortem & Amélioration Continue

**1. Préparation des Données (Orchestration)**
- Analyser le déroulement pour détecter des erreurs de communication.

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : (Interaction Directe)
- **Action** : `Feedback`

**3. Validation Humaine**
- **STOP** : Appeler `/refine-skill` si nécessaire.

## 3. Critères de Qualité
- [ ] **Cohérence** : Le UI Kit et Blade doivent être synchronisés.
- [ ] **Régression** : La modification n'a pas cassé le JS existant.

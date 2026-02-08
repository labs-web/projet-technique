---
description: Workflow d'ajustement API/HTTP. Change un code de retour ou une validation.
---

# Workflow : Ajustement API/HTTP (`/update-http`)

## 1. Contexte & Flux Global
**Objectif** : Modifier la couche d'exposition (Routes, Validation, Réponse).
**Flux Type** : `[Demande API]` → `[HTTP Layer Modifié]`

## 2. Exécution

### Étape 1 : Modification HTTP

**1. Préparation des Données (Orchestration)**
- Analyser la demande de modification (ex: règle de validation, code de retour, structure de réponse JSON).

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `developpeur-http`
- **Action** : `Créer FormRequest (Validation)` / `Implémenter Contrôleur` / `Créer API Resource`
- **Inputs Fournis** :
  - `Changes` : Détails de la modification attendue.

**3. Validation Humaine**
- **STOP** : Vérifier que la logique métier n'a pas fuité dans le contrôleur.

---

### Étape 2 : Post-Mortem & Amélioration Continue

**1. Préparation des Données (Orchestration)**
- Analyser le déroulement pour détecter des frictions.

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : (Interaction Directe)
- **Action** : `Feedback`

**3. Validation Humaine**
- **STOP** : Si nécessaire, lancer `/refine-skill`.

## 3. Critères de Qualité
- [ ] **Standard** : Respect des codes HTTP (200, 201, 422...).
- [ ] **Validation** : Aucune donnée ne rentre sans validation (FormRequest).
- [ ] **Cohérence** : Les modifs sont cohérentes avec les resources JSON existantes.

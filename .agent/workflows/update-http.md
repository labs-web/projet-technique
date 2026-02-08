---
description: Workflow d'ajustement API/HTTP. Change un code de retour ou une validation.
---

# Workflow : Ajustement API/HTTP (`/update-http`)

## 1. Contexte & Flux Global
**Objectif** : Modifier la couche d'exposition (Routes, Validation, Réponse).
**Flux Type** : `[Demande API]` → `[HTTP Layer Modifié]`

## 2. Exécution

### Étape 1 : Modification HTTP
> **Skill responsable** : `developpeur-http`
> **Flux Data** : 📥 `[Demande]` → 📤 `[Code Modifié]`

**Instructions** :
1. Modifier le FormRequest (Validation) OU le Controller (Orchestration) OU la Resource (Sortie).
2. Vérifier que la logique métier n'a pas été déplacée dans le contrôleur.
3. **STOP** : Demander la validation du développeur.

**Validation** : Endpoint modifié validé par le développeur.

---

### Étape 2 : Post-Mortem & Amélioration Continue
> **Flux Data** : 📥 `[Bilan Exécution]` → 📤 `[Proposition Amélioration]`

**Instructions** :
1. Analyser le déroulement du workflow (points de friction, erreurs, règles manquantes).
2. Demander au développeur : *"Avez-vous noté des améliorations à apporter aux Skills utilisés ?"*
3. **SI OUI** : Proposer de lancer le workflow `/refine-skill`.
4. **Validation** : Fin du workflow (et démarrage éventuel de l'amélioration).

---

## 3. Critères de Qualité
- [ ] **Standard** : Respect des codes HTTP (200, 201, 422...).
- [ ] **Validation** : Aucune donnée ne rentre sans validation.

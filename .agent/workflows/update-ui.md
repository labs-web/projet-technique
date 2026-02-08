---
description: Workflow de mise à jour de l'interface utilisateur.
---

# Workflow : Mise à jour Interface (`/update-ui`)

## 1. Contexte & Flux Global
**Objectif** : Modifier le design (CSS), le texte ou l'ergonomie d'une page existante et propager le changement.
**Flux Type** : `[Demande UI]` → `[UI Kit Modifié]` → `[Blade Modifié]`

## 2. Exécution

### Étape 1 : Modification Design System
> **Skill responsable** : `designer-ui`
> **Flux Data** : 📥 `[Demande]` → 📤 `[HTML/CSS Modifié]`

**Instructions** :
1. Modifier les fichiers HTML statiques dans `ui-kit/`.
2. Vérifier le rendu visuel.
3. **STOP** : Demander la validation du développeur (Le UI Kit est la source de vérité).

**Validation** : Design validé dans le UI Kit par le développeur.

---

### Étape 2 : Propagation Frontend
> **Skill responsable** : `developpeur-frontend`
> **Flux Data** : 📥 `[HTML Modifié]` → 📤 `[Blade Modifié]`

**Instructions** :
1. Répercuter les changements HTML/CSS sur les fichiers Blade correspondants.
2. Vérifier que la dynamique (JS/Variables) n'est pas cassée.
3. **STOP** : Demander la validation du développeur.

**Validation** : Interface finale validée par le développeur.

---

### Étape 3 : Post-Mortem & Amélioration Continue
> **Flux Data** : 📥 `[Bilan Exécution]` → 📤 `[Proposition Amélioration]`

**Instructions** :
1. Analyser le déroulement du workflow (points de friction, erreurs, règles manquantes).
2. Demander au développeur : *"Avez-vous noté des améliorations à apporter aux Skills utilisés ?"*
3. **SI OUI** : Proposer de lancer le workflow `/refine-skill`.
4. **Validation** : Fin du workflow (et démarrage éventuel de l'amélioration).

---

## 3. Critères de Qualité
- [ ] **Cohérence** : Le UI Kit et Blade doivent être synchronisés.
- [ ] **Régression** : La modification n'a pas cassé le JS existant.

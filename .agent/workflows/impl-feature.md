---
description: Workflow principal d'implémentation de fonctionnalité. Assure une implémentation "Vertical Slice" complète.
---

# Workflow : Implémentation de Fonctionnalité (`/impl-feature`)

## 1. Contexte & Flux Global
**Objectif** : Implémenter une fonctionnalité complète de manière séquentielle (Vertical Slice), du design à l'intégration.
**Flux Type** : `[Specs]` → `[UI Design]` → `[Data Schéma]` → `[Logique Métier]` → `[Exposition HTTP]` → `[Intégration Frontend]`

## 2. Exécution

### Étape 1 : Design UI
> **Skill responsable** : `designer-ui`
> **Flux Data** : 📥 `[Spécifications]` → 📤 `[Maquettes HTML/CSS]`

**Instructions** :
1. Analyser les besoins visuels.
2. Créer ou mettre à jour les fichiers statiques dans `ui-kit/`.
3. Valider le rendu visuel (Responsive, Thème).
4. **STOP** : Demander la validation du développeur (Vérification visuelle `ui-kit/index.html`).

**Validation** : Maquettes HTML validées par le développeur.

---

### Étape 2 : Data Layer
> **Skill responsable** : `developpeur-data`
> **Flux Data** : 📥 `[Maquettes HTML]` → 📤 `[Migrations & Models]`

**Instructions** :
1. Déduire le schéma de données depuis les maquettes (Champs de formulaires, Listes).
2. Créer les migrations et les modèles Eloquent.
3. Exécuter les migrations.
4. **STOP** : Demander la validation du développeur (Schéma BDD correct).

**Validation** : Structure de base de données validée par le développeur.

---

### Étape 3 : Business Logic
> **Skill responsable** : `developpeur-business`
> **Flux Data** : 📥 `[Models]` → 📤 `[Services & Policies]`

**Instructions** :
1. Implémenter les règles de gestion dans des Services dédiés.
2. Définir les Policies d'accès.
3. **STOP** : Demander la validation du développeur (Logique métier implémentée).

**Validation** : Services testables et validés par le développeur.

---

### Étape 4 : HTTP Layer
> **Skill responsable** : `developpeur-http`
> **Flux Data** : 📥 `[Services]` → 📤 `[Controllers & Routes]`

**Instructions** :
1. Créer les FormRequests pour valider les entrées.
2. Créer les Contrôleurs qui appellent les Services.
3. Définir les Routes Web/API.
4. **STOP** : Demander la validation du développeur (Endpoints testés).

**Validation** : Routes fonctionnelles validées par le développeur.

---

### Étape 5 : Frontend Integration
> **Skill responsable** : `developpeur-frontend`
> **Flux Data** : 📥 `[Controllers & Maquettes]` → 📤 `[Vues Blade Finales]`

**Instructions** :
1. Convertir les fichiers HTML du `ui-kit` en vues Blade.
2. Injecter les données dynamiques.
3. Ajouter l'interactivité JS (Alpine/Fetch).
4. **STOP** : Demander la validation du développeur (Fonctionnalité complète).

**Validation** : Feature complète testée et validée par le développeur.

---

### Étape 6 : Post-Mortem & Amélioration Continue
> **Flux Data** : 📥 `[Bilan Exécution]` → 📤 `[Proposition Amélioration]`

**Instructions** :
1. Analyser le déroulement du workflow (points de friction, erreurs, règles manquantes).
2. Demander au développeur : *"Avez-vous noté des améliorations à apporter aux Skills utilisés ?"*
3. **SI OUI** : Proposer de lancer le workflow `/refine-skill`.
4. **Validation** : Fin du workflow (et démarrage éventuel de l'amélioration).

---

## 3. Critères de Qualité
- [ ] **Linéarité** : Le flux suit strictement l'ordre Design -> Data -> Business -> Http -> Front.
- [ ] **Complétion** : Tous les fichiers nécessaires ont été créés sans "TODO" critiques.
- [ ] **Atomicité** : Chaque étape est réalisée par l'expert compétent uniquement.

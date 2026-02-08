---
description: Workflow principal d'implémentation de fonctionnalité. Assure une implémentation "Vertical Slice" complète.
---

# Workflow : Implémentation de Fonctionnalité (`/impl-feature`)

## 1. Contexte & Flux Global
**Objectif** : Implémenter une fonctionnalité complète de manière séquentielle (Vertical Slice), du design à l'intégration.
**Flux Type** : `[Specs]` → `[UI Design]` → `[Data Schéma]` → `[Logique Métier]` → `[Exposition HTTP]` → `[Intégration Frontend]`

## 2. Exécution

### Étape 1 : Design UI

**1. Préparation des Données (Orchestration)**
- Analyser les besoins visuels depuis les spécifications.
- Identifier les composants manquants dans `ui-kit/`.

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `designer-ui`
- **Action** : `Développer Composant Atomique` / `Assembler Molécule / Organisme`
- **Inputs Fournis** :
  - `Needs` : Liste des composants ou maquettes à créer.
  - `Context` : Thème et contraintes responsives.

**3. Validation Humaine**
- **STOP** : Vérifier le rendu visuel dans `ui-kit/index.html` (Responsive, Thème).

---

### Étape 2 : Data Layer

**1. Préparation des Données (Orchestration)**
- Déduire le schéma de données depuis les maquettes (Champs de formulaires, Listes).

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `developpeur-data`
- **Action** : `Créer/Modifier Schéma (Migration)` et `Définir Modèle Eloquent`
- **Inputs Fournis** :
  - `Schema` : Structure des tables et relations.
  - `Models` : Nom des modèles Eloquent.

**3. Validation Humaine**
- **STOP** : Vérifier que les migrations s'exécutent correctement et que le schéma correspond aux besoins.

---

### Étape 3 : Business Logic

**1. Préparation des Données (Orchestration)**
- Identifier les règles de gestion et les contrôles d'accès nécessaires.

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `developpeur-business`
- **Action** : `Créer Service Métier` / `Implémenter Logique (Méthode)` / `Définir Policy (Autorisation)`
- **Inputs Fournis** :
  - `Rules` : Règles métier à implémenter.
  - `Service` : Nom du Service.

**3. Validation Humaine**
- **STOP** : Vérifier que la logique métier est isolée dans le Service et couverte par des Policies.

---

### Étape 4 : HTTP Layer

**1. Préparation des Données (Orchestration)**
- Définir les endpoints API ou Web requis.
- Préparer les règles de validation des entrées.

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `developpeur-http`
- **Action** : `Créer FormRequest (Validation)` / `Implémenter Contrôleur` / `Déclarer Routes`
- **Inputs Fournis** :
  - `Endpoints` : Méthodes HTTP et URLs.
  - `Validation` : Règles de validation.

**3. Validation Humaine**
- **STOP** : Vérifier que les routes sont protégées et que les données entrantes sont bien validées.

---

### Étape 5 : Frontend Integration

**1. Préparation des Données (Orchestration)**
- Récupérer les maquettes HTML validées et les contrôleurs prêts.

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `developpeur-frontend`
- **Action** : `Créer/Adapter Composant Blade` / `Intégrer Page (View)` / `Ajouter Interactivité (Alpine.js)`
- **Inputs Fournis** :
  - `HTML` : Fichiers statiques du UI Kit.
  - `Data` : Données passées par le contrôleur.

**3. Validation Humaine**
- **STOP** : Vérifier le fonctionnement complet de la fonctionnalité (Interactvité, Données réelles).

---


## 3. Critères de Qualité
- [ ] **Linéarité** : Le flux suit strictement l'ordre Design -> Data -> Business -> Http -> Front.
- [ ] **Complétion** : Tous les fichiers nécessaires ont été créés sans "TODO" critiques.
- [ ] **Atomicité** : Chaque étape est réalisée par l'expert compétent uniquement.
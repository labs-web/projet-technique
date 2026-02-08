---
description: Workflow d'évolution métier. Change une règle de gestion.
---

# Workflow : Évolution Métier (`/update-logic`)

## 1. Contexte & Flux Global
**Objectif** : Modifier une règle métier sans impacter l'interface externe si possible.
**Flux Type** : `[Nouvelle Règle]` → `[Service Modifié]` → `[Validation]`

## 2. Exécution

### Étape 1 : Implémentation Métier

**1. Préparation des Données (Orchestration)**
- Identifier la règle métier à modifier et la méthode de Service concernée.

**2. Exécution Déléguée (Appel Skill)**
- **Skill Cible** : `developpeur-business`
- **Action** : `Implémenter Logique (Méthode)` / `Créer Service Métier`
- **Inputs Fournis** :
  - `New Rule` : Description de la modification.
  - `Service Call` : Nom du service.

**3. Validation Humaine**
- **STOP** : Vérifier que la logique est isolée et couverte par des tests.

---

### Étape 2 : Vérification d'Impact (Conditionnelle)

**1. Préparation des Données (Orchestration)**
- Vérifier si la signature de la méthode publique du Service a changé.

**2. Exécution Déléguée (Appel Skill)** (Si impact API)
- **Skill Cible** : `developpeur-http`
- **Action** : `Check Impact` (Implied check or call update-http)
- **Inputs Fournis** :
  - `Signature` : Nouvelle signature de méthode.

**3. Validation Humaine**
- **STOP** : Si la signature a changé, déclencher `/update-http`.

---

## 3. Critères de Qualité
- [ ] **Isolation** : La logique ne doit pas fuir dans le contrôleur.
- [ ] **Types** : Le typage strict est respecté.
- [ ] **Stabilité** : Aucune régression sur les fonctionnalités existantes.
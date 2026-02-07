---
description: Workflow principal d'implémentation de fonctionnalité. Assure une implémentation "Vertical Slice" complète.
---

# Workflow : Implémentation de Fonctionnalité (`/impl-feature`)

Ce workflow est le cœur du cycle de développement. Il assure une implémentation "Vertical Slice" complète, du design à l'intégration, en respectant la séparation des couches.

### Flux de Données & Responsabilités
Le flux est strictement séquentiel pour garantir que chaque couche s'appuie sur des fondations stables.

**1. Étape : Design UI**
*   **Skill Responsable** : `designer-ui-kit`
*   **Entrée** : Spécifications Fonctionnelles
*   **Sortie** : Maquettes HTML/CSS statiques dans le dossier `ui-kit/`

**2. Étape : Data Layer**
*   **Skill Responsable** : `backend-data`
*   **Entrée** : Maquettes validées (pour déduire les champs)
*   **Sortie** : Migrations, Models Eloquent, Factories, Seeders

**3. Étape : Business Logic**
*   **Skill Responsable** : `backend-business`
*   **Entrée** : Models disponibles
*   **Sortie** : Services (`app/Services`), Policies, Gates

**4. Étape : HTTP Layer**
*   **Skill Responsable** : `backend-http`
*   **Entrée** : Services fonctionnels, définitions des Routes
*   **Sortie** : Controllers, FormRequests, API Resources, Routes

**5. Étape : Frontend Integration**
*   **Skill Responsable** : `dev-frontend-js`
*   **Entrée** : Controllers opérationnels, Maquettes HTML existantes
*   **Sortie** : Vues Blade finales, Scripts Alpine.js/Vanilla JS

### Détail des Transitions

#### Transition 1 -> 2 : Du Visuel à la Donnée
*   **Condition** : Le `ui-kit` contient les fichiers HTML statiques validés.
*   **Action** : L'expert Data analyse les formulaires et listes du `ui-kit` pour déduire les attributs de la BDD.

#### Transition 2 -> 3 : De la Structure à la Logique
*   **Condition** : Les tables existent et les Models sont prêts.
*   **Action** : L'expert Métier implémente les règles de gestion (ex: "Un article doit être validé avant publication") dans les Services.

#### Transition 3 -> 4 : Exposition HTTP
*   **Condition** : Les Services sont testables et fonctionnels.
*   **Action** : L'expert HTTP expose ces services via des routes Web ou API, sécurisées par des FormRequests.

#### Transition 4 -> 5 : Intégration Finale
*   **Condition** : Les endpoints/contrôleurs retournent les données attendues.
*   **Action** : Le développeur Frontend injecte ces données dans les vues Blade (basées sur le `ui-kit`) et ajoute l'interactivité JS.

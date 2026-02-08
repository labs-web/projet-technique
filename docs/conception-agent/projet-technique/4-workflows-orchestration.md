# Orchestration des Workflows : Projet Technique

## 1. Workflow Principal : Implémentation de Fonctionnalité (`/impl-feature`)
Ce workflow est le cœur du cycle de développement. Il assure une implémentation "Vertical Slice" complète, du design à l'intégration, en respectant la séparation des couches.

### Flux de Données & Responsabilités
Le flux est strictement séquentiel pour garantir que chaque couche s'appuie sur des fondations stables.

**1. Étape : Design UI**
*   **Skill Responsable** : `designer-ui`
*   **Entrée** : Spécifications Fonctionnelles
*   **Sortie** : Maquettes HTML/CSS statiques dans le dossier `ui-kit/`

**2. Étape : Data Layer**
*   **Skill Responsable** : `developpeur-data`
*   **Entrée** : Maquettes validées (pour déduire les champs)
*   **Sortie** : Migrations, Models Eloquent, Factories, Seeders

**3. Étape : Business Logic**
*   **Skill Responsable** : `developpeur-business`
*   **Entrée** : Models disponibles
*   **Sortie** : Services (`app/Services`), Policies, Gates

**4. Étape : HTTP Layer**
*   **Skill Responsable** : `developpeur-http`
*   **Entrée** : Services fonctionnels, définitions des Routes
*   **Sortie** : Controllers, FormRequests, API Resources, Routes

**5. Étape : Frontend Integration**
*   **Skill Responsable** : `developpeur-frontend`
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

---

## 2. Workflow d'Initialisation (`/init-stack`)
Exécuté une seule fois au début du projet.

*   **Skill** : `configurateur-stack`
*   **Action** : Installe Laravel, configure Tailwind, initialise Git.
*   **Sortie** : Socle technique prêt pour le premier `/impl-feature`.

---

## 3. Matrice de Communication
Comment les agents s'échangent l'information sans perte de contexte.

**Fichiers Pivot :**
*   `ui-kit/index.html` : Sert de référence visuelle absolue.
*   `database/migrations/` et `app/Models/` : Référence de vérité pour la structuration des données.
*   `app/Services/` : Référence de vérité pour les opérations métier disponibles.

---

## 4. Workflows de Maintenance
Ces workflows "légers" permettent d'intervenir sur une couche spécifique sans relancer le cycle complet `/impl-feature`. Ils sont cruciaux pour les corrections et petites évolutions.

### A. Mise à jour Interface (`/update-ui`)
*   **Objectif** : Modifier le design (CSS), le texte ou l'ergonomie d'une page existante.
*   **Périmètre** : Couche Présentation uniquement.
*   **Flux** :
    1.  **Skill** `designer-ui` : Modifie les fichiers HTML/CSS dans `ui-kit/`. **C'est la source de vérité.**
    2.  **Skill** `developpeur-frontend` : Répercute les modifications HTML/CSS dans les fichiers `.blade.php`.
*   **Interdit** : Modifier la logique PHP ou la base de données.

### B. Évolution Métier (`/update-logic`)
*   **Objectif** : Changer une règle de gestion (ex: limite de publication, calcul de dates).
*   **Périmètre** : Couche Service.
*   **Flux** :
    1.  **Skill** `developpeur-business` : Modifie le code dans `app/Services/`.
    2.  **Validation** : Vérifie que le changement n'impacte pas l'interface publique des méthodes (signature). Si oui -> déclencher `/update-http`.
*   **Interdit** : Modifier les Vues ou les Controllers directement.

### C. Ajustement API/HTTP (`/update-http`)
*   **Objectif** : Changer un code de retour, ajouter un filtre d'URL, modifier une validation d'entrée.
*   **Périmètre** : Couche HTTP (Entrée/Sortie).
*   **Flux** :
    1.  **Skill** `developpeur-http` : Modifie le Controller, le FormRequest ou la Resource API.
*   **Interdit** : Mettre de la logique métier dans le Controller. Tout traitement complexe doit rester dans le Service.

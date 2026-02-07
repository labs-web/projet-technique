# Clustering & Rôles : Projet Technique (Blog Architecture)

**Date** : 2026-02-07

---

## Groupes de Clustering par Casquettes

### 1. [Expert Configuration Stack]
*   **Skill Déduit** : `expert-stack-config`
*   **Critère de Décision** : Intervient en amont (setup global) et contrôle la cohérence (Service Layer, Linter, Git, Docs). Assure l'échafaudage du projet.
*   **Actions Identifiées** :
    *   Initialisation du projet Laravel (v10/11) via Composer/Installer.
    *   Configuration de l'environnement (`.env`, Base de données MySQL).
    *   Installation et config de Tailwind CSS (v3+) et Preline UI.
    *   Mise en place de la structure du Service Layer (`app/Services`).
    *   Configuration `lang/` pour l'internationalisation (FR).
    *   Initialisation du repository Git et commits atomiques.
    *   Exécution du linter PSR-12 et mise à jour de la documentation.

### 2. [Designer UI & Intégrateur HTML/CSS]
*   **Skill Déduit** : `designer-ui-kit`
*   **Critère de Décision** : Produit des composants visuels purs (HTML/CSS) isolés de la logique backend. Respecte la contrainte majeure du UI-Kit avant intégration.
*   **Actions Identifiées** :
    *   Création de l'arborescence `ui-kit/` et `ui-kit/index.html`.
    *   Intégration de Tailwind dans le UI-Kit.
    *   **Conception & Code des Atomes** : Boutons, Inputs, Labels, Alertes.
    *   **Conception & Code des Molécules** : Cards (List/Detail), Navbars, Sidebars, Tables, Formulaires.
    *   **Maquettage des Pages** : Home, Detail, Admin Dashboard, Login.
    *   Validation visuelle (Tests sur navigateur).

### 3. [Expert Base de Données (Tier 3 : Data Access)]
*   **Skill Déduit** : `backend-data`
*   **Critère de Décision** : Responsable de la persistance et de l'intégrité des données. Ne gère PAS la logique métier ni les requêtes HTTP.
*   **Actions Identifiées** :
    *   Conception du Schéma (MCD/MLD implicite).
    *   Création des Migrations (Users, Categories, Articles) avec contraintes (FK, Index).
    *   Création des Modèles Eloquent et définition des relations (`hasMany`, `belongsTo`).
    *   Création des Factories et Seeders pour les jeux de données.

### 4. [Développeur Métier (Tier 2 : Business Logic)]
*   **Skill Déduit** : `backend-business`
*   **Critère de Décision** : Encapsule les règles de gestion et le traitement des données. Indépendant du framework HTTP.
*   **Actions Identifiées** :
    *   Implémentation des Classes de Service (`CategoryService`, `ArticleService`).
    *   Implémentation de la logique de validation métier.
    *   Définition des Policies et Gates d'autorisation (Règles métier de sécurité).
    *   Tests Unitaires des Services (si applicables).

### 5. [Développeur HTTP & API (Tier 1 : Presentation)]
*   **Skill Déduit** : `backend-http`
*   **Critère de Décision** : Reçoit la requête, valide l'entrée, appelle le Service, et formate la réponse (JSON/View).
*   **Actions Identifiées** :
    *   Définition des Routes (Web & API).
    *   Création des Contrôleurs (Web Resource, API, Auth).
    *   Création des FormRequests (Validation des entrées HTTP).
    *   Création des API Resources (Transformation JSON).
    *   Orchestration de la réponse : Appel des Services -> Renvoi de la Vue Blade ou du JSON.

### 6. [Développeur Frontend (Logique Interactive)]
*   **Skill Déduit** : `dev-frontend-js`
*   **Critère de Décision** : Ajoute l'interactivité côté client sur les pages rendues par le serveur. Manipule JS, DOM, Fetch, Alpine.
*   **Actions Identifiées** :
    *   Intégration des maquettes UI-Kit dans les Vues Blade (layout & components).
    *   Implémentation de la recherche dynamique (Vanilla JS + Fetch).
    *   Refactoring de l'interactivité avec Alpine.js (Search, Filters).
    *   Gestion des appels AJAX vers l'API interne.

---

## Règle d'Or Appliquée

> Si deux actions ne peuvent PAS être faites par la même personne sans changer de contexte mental → **Skills différents**.

L'architecture 3-Tiers est ici strictement respectée pour le Backend :
1.  **Data** (Model/DB)
2.  **Business** (Service/Policy)
3.  **Presentation** (Controller/Route/Resource)

---

## Notes

*   Cette séparation force le respect du pattern "Skinny Controller, Fat Service". Le développeur Controller ne fait QUE du "Traffic Cop".
*   Le `dev-frontend-js` reste le garant de l'intégration finale dans Blade, collaborant étroitement avec le `backend-http` qui fournit les variables.

# Cadrage du Besoin Métier


## 1. Contexte du Projet
* **Nom du Projet** : Projet Technique (Laboratoire pour la réalisation de projet Fil Rouge)
* **Description Courte** : Environnement d'auto-formation ("Bac à sable") basé sur une architecture Blog pour valider les compétences techniques Laravel (Blade/Alpine/API).
* **Objectif Principal** : Maîtriser le framework Laravel et son écosystème à travers la réalisation d'un Blog complet.
* **Vision "Grand Projet"** : Bien que démarrant avec 3 tables, l'architecture doit être conçue dès le départ pour supporter une montée en charge vers 20+ tables (Scalabilité, Modularité, Séparation des responsabilités). Ce projet est la fondation technique d'une future application d'envergure.

## 2. Description du Besoin
Le système à concevoir est une **plateforme de Blog complète** servant de support d'apprentissage pour :
1.  Expliquer à l'apprenant l'architecture Laravel (MVC, Services, API).
2.  Valider la stack de développement complète du Lab Solicode.

### Acteurs
*   **Administrateur / Auteur** : Gère le contenu (Articles, Catégories) via un Back-Office sécurisé.
*   **Utilisateur Public** : Consulte les articles, effectue des recherches.
*   **Client API (Mobile/Externe)** : Consomme les données du blog via des endpoints sécurisés.

### Fonctionnalités Clés & Progression
1.  **Gestion de Contenu (Back-Office Web)** :
    *   CRUD complet pour les Entités : **User**, **Article**, **Category**.
    *   Relations : Un User écrit des Articles ; Un Article a plusieurs Categories.
    *   **Authentification & Autorisation** :
        *   *Itération 1* : Gestion native via Laravel Gates & Policies.
        *   *Itération 2* : Gestion avancée via Spatie Laravel Permission.
    *   Interface : Dashboard Admin responsive avec Tailwind CSS (Preline UI).

2.  **Expérience Utilisateur (Front-End Web)** :
    *   Affichage public des articles (Liste & Détail).
    *   **Interactivité dynamique** (Recherche AJAX, Filtrage) :
        *   *Itération 1* : Implémentation en **Vanilla JS** (Fetch API).
        *   *Itération 2* : Refactoring avec **Alpine.js** pour la réactivité.

3.  **Exposition des Données (API REST)** :
    *   Endpoints JSON pour exposer les Articles, Users et Categories.
    *   Sécurisation via **Laravel Sanctum**.
    *   Standardisation via **API Resources**.

## 3. Contraintes Techniques
*   **Backend** : PHP 8.2+, Laravel 10/11.
*   **Architecture "Scalable"** :
    *   Pattern MVC strict + Couche Service (`app/Services`) obligatoire pour isoler la logique métier.
    *   Principes "Skinny Controller" / "Fat Model".
    *   Préparation à la division par Domaines (pas de couplage fort).
*   **Base de Données** : MySQL 8.0, ORM Eloquent. Structure pensée pour l'évolution (Index, Clés étrangères strictes).
*   **Frontend & Design System** (Contrainte Majeure) :
    *   Templating : Laravel Blade.
    *   CSS : Tailwind CSS v3+.
    *   **UI-Kit Personnalisé (Workflow itératif)** :
        *   Dossier `ui-kit/` contenant les atomes, molécules et maquettes de référence.
        *   **Phase d'Analyse & Conception UI** : Pour chaque demande utilisateur, une étape d'analyse préalable est OBLIGATOIRE pour identifier et concevoir les **Atomes**, **Molécules** et **Pages (Maquettes)** nécessaires avant tout développement Backend.
        *   **Règle d'Or (Just-In-Time)** : Si un développeur a besoin d'un composant non existant, il doit **D'ABORD** le créer et le valider dans le `ui-kit/` AVANT de l'implémenter dans le code applicatif. Il est interdit de créer du style "adhoc" directement dans les vues Laravel sans passer par la case UI-Kit.
*   **Internationalisation** :
    *   Utilisation stricte des fichiers de langue Laravel (`lang/`) pour tous les textes statiques.
*   **Sécurité** :
    *   Validation via FormRequests.
*   **Normes** : PSR-12, Naming Conventions (Anglais).

## 4. Livrables Attendus
*   [ ] **UI-Kit** : Espace de travail statique (HTML/CSS) mis à jour itérativement avant l'intégration Laravel.
*   [ ] **Architecture** : Structure applicative initialisée (Modèles, Migrations, Services).
*   [ ] **Back-Office** : CRUDs fonctionnels avec Auth (Itération 1 & 2).
*   [ ] **Front-End** : Interface publique avec recherche dynamique (Itération 1 Vanilla & 2 Alpine).
*   [ ] **API** : Endpoints documentés et sécurisés.

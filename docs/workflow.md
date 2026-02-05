# Worflow de travail 

Développer une application 3-tiers avec Laravel 

- Respecte de l'architecture MVC + Couche service
- organisation de view par partials


## Terminologie
Nous utiliserons le terme **"Feature"** (Vertical Slice) pour désigner un ensemble fonctionnel complet traversant les couches de l'application (Route -> Ctrl -> Service -> Model -> View).

## Liste des Workflows Antigravity

Ces workflows sont conçus pour supporter la méthodologie **UI-First** : on valide l'expérience utilisateur AVANT de coder la logique complexe.

### 1. Initialisation (One-Shot)
Ces workflows configurent l'environnement.
- **/init-agent** : Initialise la configuration de l'assistant (Règles, Mémoire).
- **/init-lab** : Initialise la documentation d'un nouveau projet pédagogique.
- **/init-laravel-arch** : Transforme un Laravel vierge en architecture "Projet Technique" (Services, Layouts, Preline).

### 2. Cycle de Production UI-First (Quotidien)
C'est le cœur du développement. Les workflows s'utilisent dans cet ordre précis :

#### Étape A : Conception
**Commande** : `/conception-ui`
- **Acteur** : Concepteur UI
- **Intrant** : Une idée ou User Story.
- **Sortie** : Wireframe textuel et mise à jour des manifestes YAML (`ui-kit/`).
- **Objectif** : Identifier les composants manquants avant de coder.

#### Étape B : Fabrication des Briques
**Commande** : `/creation-ui`
- **Acteur** : Créateur UI
- **Intrant** : Manifestes YAML mis à jour.
- **Sortie** : Fichiers HTML statiques dans `ui-kit/`.
- **Objectif** : Coder les composants visuels isolés (Pixel Perfect).

#### Étape C : Prototypage (Assemblage)
**Commande** : `/draft-page`
- **Acteur** : Architecte
- **Intrant** : Composants du `ui-kit`.
- **Action** : Crée une Vue Blade + Route + Contrôleur (Données fictives).
- **Objectif** : **Validation Visuelle** par le développeur dans le navigateur.

#### Étape D : Câblage Backend
**Commande** : `/bind-feature`
- **Acteur** : Backend Developer
- **Intrant** : Une page prototype validée.
- **Action** : Génère Migration + Model + Service + Request. Remplace les données fictives par la BDD.
- **Objectif** : Rendre la fonctionnalité réelle et persistante.

### 3. Maintenance & Qualité
- **/refactor-feature** : Nettoie le code existant (Extraction Service, Découpage Vue).
- **/evolution-agent** : Met à jour la configuration de l'agent lui-même.


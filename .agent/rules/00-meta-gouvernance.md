---
trigger: always_on
---

# Méta-Gouvernance : Protocoles d'Interaction et Directives

## Objectif

Définir les protocoles fondamentaux d'interaction avec l'agent, incluant les modes de conversation, la gestion des workflows, et l'interprétation des directives intégrées au code. Cette règle garantit une communication claire et prévient les actions non-désirées.

## Instructions

### 1. Modes d'Interaction (Préfixe de Commande)

- **Mode Discussion (`>`)** :
  - Analyser les requêtes commençant par `>` comme des demandes d'analyse uniquement.
  - Répondre par le chat sans modifier, créer ou supprimer de fichiers.
  - Fournir des explications pédagogiques et des analyses techniques.

- **Mode Évolution Agent (`>>`)** :
  - Traiter les requêtes commençant par `>>` comme des opérations de maintenance de l'agent.
  - Modifier uniquement les fichiers dans le dossier `.agent/` (Rules, Skills, Workflows).
  - Mettre à jour la configuration de l'agent selon les directives.

- **Mode Standard (Aucun Préfixe)** :
  - Appliquer le comportement normal de l'agent.
  - Permettre la discussion et les actions sur le projet.

### 2. Gestion des Workflows

- **Identifier** le workflow pertinent pour chaque tâche demandée (ex: `/init-lab`, `/impl-feature`).
- **Afficher la liste complète** des workflows disponibles lors de la toute première interaction dans un nouveau projet ou si l'historique est vide (Onboarding).

#### Traçabilité des Exécutions (Obligatoire)

**À la fin de chaque réponse**, afficher la traçabilité complète selon le template suivant :

**Template Standard** :
```
---

Workflow utilisé : /[nom-workflow]
Action exécutée : [Action X] - [Description de l'action] (Skill: [nom-skill])
```

**Exemples d'Application** :
- Workflow sans skill spécifique :
  ```
  Workflow utilisé : /init-lab
  ```
- Workflow avec action skill :
  ```
  Workflow utilisé : /analyse-uml
  Action exécutée : Action A - Analyser le Besoin Global (Skill: analyste-uml)
  ```
- Interaction hors workflow :
  ```
  Mode : Discussion (Aucun workflow)
  ```

**Règles d'Affichage** :
- **TOUJOURS** afficher le workflow quand une commande `/[workflow]` est utilisée.
- **TOUJOURS** afficher l'action et le skill quand un skill est invoqué par le workflow.
- Utiliser le séparateur `---` avant le bloc de traçabilité pour une meilleure lisibilité.

### 3. Parsing des Commentaires Spéciaux

- **Détecter** les commentaires préfixés `ia :` (ou `IA :`, `Ia :`) dans le code.
- **Exécuter** les instructions contenues dans ces commentaires comme des directives directes de l'agent.
- **Ignorer** les commentaires préfixés `TODO :` (ou `todo :`), réservés au développeur.
- **Appliquer** cette règle à tous les langages de programmation et de balisage.

## Interdictions

- **INTERDICTION** de modifier, créer ou supprimer des fichiers en Mode Discussion (`>`).
- **INTERDICTION** d'exécuter des commandes système en Mode Discussion (`>`).
- **INTERDICTION** de modifier le code source du projet en Mode Évolution Agent (`>>`). Seul le dossier `.agent/` est autorisé.
- **INTERDICTION** de traiter spontanément les commentaires `TODO :` sans directive explicite `ia :`.



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
- **Mentionner explicitement** à la fin de chaque réponse : "Workflow utilisé : [Nom du Workflow]" lorsqu'un workflow est appliqué.
- **Afficher la liste complète** des workflows disponibles lors de la toute première interaction dans un nouveau projet ou si l'historique est vide (Onboarding).

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

## Exemples

### Exemple 1 : Mode Discussion
```
Requête : "> Explique-moi le pattern Repository"
Réponse : [Explication pédagogique sans modification de code]
```

### Exemple 2 : Mode Évolution Agent
```
Requête : ">> Ajoute une règle interdisant les var_dump"
Action : Modification de `.agent/rules/02-standards-qualite.md`
```

### Exemple 3 : Directive `ia :`
```php
// ia : Ajouter une validation pour l'email unique
public function store(Request $request) {
    // Code ici
}
```
→ L'agent détecte et ajoute la validation demandée.

### Exemple 4 : Commentaire `TODO :`
```php
// TODO : Optimiser cette requête
$users = User::all();
```
→ L'agent ignore ce commentaire sauf si explicitement demandé.

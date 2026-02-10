---
description: Workflow de création de diagrammes de conception (Classes/DB).
---






# Workflow : Conception UML (`/conception-uml`)

**Objectif** : Formaliser l'architecture technique et le modèle de données (Classes/DB).
**Protocole** : Suivre le standard [`.agent/resources/protocoles-workflow.md`](.agent/resources/protocoles-workflow.md).

## Exécution

### 1. Détection & Menu
- **Analyser** la demande via `.agent/skills/concepteur-uml/SKILL.md`.
- **Afficher** le *Template A* (Confirmation) ou *Template B* (Menu) selon le protocole.
- **STOP** : Attendre validation du développeur.

### 2. Exécution Déléguée
- **Source** : Exécuter strictement l'Action choisie depuis le fichier Skill (`concepteur-uml`).
- **Trace** : Ajouter `Action exécutée : [Nom de l'action] (Skill: concepteur-uml)` en fin de réponse.
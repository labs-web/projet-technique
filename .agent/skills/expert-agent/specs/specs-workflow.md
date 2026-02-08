# Spécifications : Gestion des Workflows

## 1. Structure Obligatoire

Un Workflow valide doit respecter la structure suivante :
- **Emplacement** : `.agent/workflows/[nom-du-workflow].md`.
- **Format** : Fichier Markdown avec Frontmatter YAML.

## 2. Validation & Standards

### Contenu du Workflow
- **En-tête YAML** :
  - `description`: Résumé court de l'objectif.
- **Sections** :
  - `Contexte & Flux Global` : Vue d'ensemble.
  - `Exécution` : Étapes détaillées.
  - `Critères de Qualité` : Checklist de fin.
- **Flux** : Linéaire et unidirectionnel (Pas de boucles complexes).
- **Validation Humaine** : Chaque étape critique doit avoir un point de contrôle (STOP).

### Principes d'Interaction Workflow/Skill
- **Rôle du Workflow (Orchestrateur)** :
  - Il **NE DOIT PAS** expliquer "comment" réaliser une tâche (c'est le rôle du Skill).
  - Il **NE DOIT PAS** répéter les instructions techniques du Skill.
  - Il **DOIT** préparer et organiser les **Données d'Entrée (Inputs)** pour l'action.
  - Il **DOIT** ordonner explicitement au Skill d'exécuter l'action.
- **Appel de Skill** :
  - Chaque étape impliquant une action doit préciser :
    1. **Le SKILL Cible** : Quel expert solliciter.
    2. **L'ACTION** : Quelle capacité activer.
    3. **Les INPUTS** : Les données préparées nécessaires à l'action.

### Annotations Spéciales
- `// turbo` : Autorise l'exécution automatique d'une commande spécifique.

### Workflow de Création/Optimisation
1. **Visualiser** le processus de bout en bout.
2. **Utiliser** `template-workflow.md` (situé dans `.agent/skills/expert-agent/resources/`) comme structure de base.
3. **Simplifier** : Supprimer les étapes redondantes.
4. **Annoter** : Ajouter `// turbo` là où c'est sûr.
5. **Vérifier** : S'assurer que le workflow ne "bloque" pas l'agent dans une boucle infinie.

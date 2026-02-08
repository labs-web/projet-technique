# Spécifications : Gestion des Workflows

## 1. Structure Obligatoire

Un Workflow valide doit respecter la structure suivante :
- **Emplacement** : `.agent/workflows/[nom-du-workflow].md`.
- **Format** : Fichier Markdown avec Frontmatter YAML.

## 2. Validation & Standards

### Nommage du Workflow
- **Format** : `kebab-case`.
- **Sémantique** : **DOIT** décrire une **Phase**, une **Tâche** ou une **Action** (ex: `analyse-uml`, `init-projet`, `maintenance-agent`).
- **Interdiction** : Ne pas utiliser de noms de rôles (réservés aux Skills).

### Contenu du Workflow
- **En-tête YAML** :
  - `description`: Résumé court de l'objectif.
- **Sections** :
  - `Contexte & Flux Global` : Vue d'ensemble.
  - `Exécution` : Étapes détaillées.
  - `Critères de Qualité` : Checklist de fin.
- **Flux** : Linéaire et unidirectionnel (Pas de boucles complexes).
- **Validation Humaine** : Chaque étape critique doit avoir un point de contrôle (STOP).

### Architecture Standard : Orchestration Intelligente
L'architecture par défaut pour orchestrer un Skill multi-actions (cas fréquent) suit le modèle :
`[Demande]` → `[Diagnostic Stratégie]` → `[Exécution Composite]` → `[Validation]`

1.  **Diagnostic & Stratégie** : Le Workflow analyse l'intention (Scope) et décide quelles actions activer.
2.  **Exécution Composite** : Le Workflow appelle séquentiellement ou conditionnellement les actions atomiques du Skill.
3.  **Synthèse & Validation** : Le Workflow vérifie la cohérence du résultat global.

*Note : Cette structure doit être utilisée par défaut, sauf demande spécifique d'un workflow linéaire simple.*

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
1. **Visualiser** le processus de bout en bout (Penser "Orchestration" et non "Procédure").
2. **Utiliser** `template-workflow.md` (situé dans `.agent/skills/expert-agent/resources/`) qui implémente le pattern "Diagnostic-Exécution".
3. **Simplifier** : Supprimer les étapes redondantes.
4. **Annoter** : Ajouter `// turbo` là où c'est sûr.
5. **Vérifier** : S'assurer que le workflow ne "bloque" pas l'agent dans une boucle infinie.

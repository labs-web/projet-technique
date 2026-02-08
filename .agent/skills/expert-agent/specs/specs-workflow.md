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

### Architecture Standard : Menu Interactif avec Auto-Suggestion
Pour les workflows pédagogiques et interactifs, l'architecture standard est basée sur un menu utilisateur :
`[Analyse Optionnelle]` → `[Menu Interactif]` → `[Validation Humaine]` → `[Exécution]`

### Fonctionnement Détaillé

1. **Analyse de la Demande (Optionnelle)** : Détecter des mots-clés dans la demande pour suggérer une action.
2. **Affichage du Menu** : Présenter toutes les actions disponibles avec descriptions courtes.
3. **Validation Humaine** : STOP pour attendre le choix du développeur (A/B/C/D...).
4. **Exécution Conditionnelle** : Appeler l'action choisie avec les inputs appropriés.

**Avantages** :
- **Découvrabilité** : Le développeur voit toutes les actions disponibles
- **Pédagogique** : Idéal pour l'apprentissage (contexte Lab)
- **Contrôle** : Validation humaine avant chaque exécution
- **Simplicité** : Workflow facile à maintenir et à comprendre

**Exemple de Menu** :
```
> Actions disponibles (Skill : nom-du-skill) :
>
> A. Nom de l'Action A
> → Description courte de ce que fait l'action
>
> B. Nom de l'Action B
> → Description courte de ce que fait l'action
>
> [Si suggestion] → Action suggérée : [X] ← [MARQUÉE]
>
> Quelle action souhaitez-vous exécuter ? (Tapez A, B, C...)
```

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
1. **Visualiser** le processus de bout en bout (Penser "Orchestration" et non "Procédure").
2. **Suivre le Pattern** : Utiliser le modèle "Menu Interactif" défini dans le template.
3. **Utiliser** `template-workflow.md` (situé dans `.agent/skills/expert-agent/resources/`) comme base.
4. **Simplifier** : Supprimer les étapes redondantes.
5. **Annoter** : Ajouter `// turbo` là où c'est sûr.
6. **Vérifier** : S'assurer que le workflow ne "bloque" pas l'agent dans une boucle infinie.

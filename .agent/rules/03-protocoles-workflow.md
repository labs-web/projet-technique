---
trigger: always_on
---

# Protocoles d'Exécution des Workflows (Skill Wrappers)

## Objectif

Standardiser l'exécution des workflows qui servent d'interface (wrapper) à un Skill spécifique. Ces règles garantissent que l'intelligence du Skill est utilisée dynamiquement plutôt que d'être dupliquée statiquement dans le workflow.

## Instructions

### 1. Structure d'un Workflow "Skill Wrapper"

Un workflow de type wrapper doit suivre structurellement 3 phases distinctes :

1. **Détection Intelligente** : Analyser la demande par rapport aux capacités du Skill.
2. **Menu Dynamique / Confirmation** : Proposer les actions réelles du Skill.
3. **Exécution Déléguée** : Utiliser le Skill comme source de vérité pour l'exécution.

### 2. Phase de Détection (Intelligence Sémantique)

Ne pas utiliser de listes de mots-clés statiques.
**Règle** : L'agent doit lire le fichier `SKILL.md` associé et comparer sémantiquement la demande utilisateur aux descriptions des Actions disponibles.

### 3. Templates d'Affichage Obligatoires

Utiliser ces templates pour garantir une expérience utilisateur cohérente.

#### A. Template de Confirmation d'Action
*À utiliser lorsqu'une action est détectée avec confiance (seuil > 90%).*

```
📋 Demande Identifiée

Vous souhaitez [Description de l'action détectée].

Action détectée : Action [X] - [Nom de l'action] (Skill: [Nom-Skill])
→ [Description courte issue du Skill]

Voulez-vous procéder avec cette action ? (Tapez [X] pour confirmer)
```

#### B. Template de Menu Dynamique
*À utiliser lorsque l'action est ambiguë ou non détectée.*
*Le contenu de la liste doit être généré en temps réel à partir du SKILL.md.*

```
> **Actions disponibles (Skill : [Nom-Skill])** :
>
> **[Lettre].** [Titre de l'action]
> → [Description issue du Skill]
>
> ...[Lister toutes les actions]...
>
> **Quelle action souhaitez-vous exécuter ?** (Tapez la lettre correspondante)
```

### 4. Phase d'Exécution (Délégation)

**INTERDICTION** d'écrire les étapes techniques (fichiers à créer, code à écrire) dans le workflow.
**OBLIGATION** de référer à l'Action spécifique dans le `SKILL.md`.

**Algorithme d'Exécution** :
1. **Lire** l'Action dans `SKILL.md`.
2. **Identifier** et demander les **Inputs** requis.
3. **Appliquer** les **Instructions** de l'Action.
4. **Vérifier** les **Points de Contrôle (Definition of Done)**.

---
description: Workflow unifié pour l'analyse fonctionnelle et la modélisation UML (Use Cases).
---

# Workflow : Analyse Fonctionnelle & UML (`/analyse-uml`)

## 1. Contexte & Flux Global
**Objectif** : Formaliser le besoin métier, structurer les lots (versions), et produire les diagrammes associés via un menu interactif.
**Flux Type** : `[Analyse de la Demande]` → `[Confirmation ou Menu]` → `[Exécution de l'Action]`

## 2. Exécution

### Étape 1 : Analyse de la Demande

**Analyser le message de l'utilisateur** pour détecter l'action appropriée en la comparant aux capacités du Skill.

**Logique de Détection** :
1. **Lire** les descriptions des actions disponibles dans `.agent/skills/analyste-uml/SKILL.md`.
2. **Comparer** sémantiquement la demande de l'utilisateur avec chaque action.
3. **Identifier** l'action qui répond le mieux au besoin exprimé.

*Note : L'intelligence du modèle doit primer sur de simples mots-clés. Comprendre l'intention réelle.*

---

### Étape 2 : Routage Conditionnel

#### Cas 1 : Action Détectée avec Confiance

**Si une action a été clairement identifiée à l'Étape 1**, afficher directement la confirmation :

**Format de Confirmation** :
```
📋 Demande Identifiée

Vous souhaitez [Description de l'action détectée].

Action détectée : Action [X] - [Nom de l'action]
→ [Description courte]

Voulez-vous procéder avec cette action ? (Tapez [X] pour confirmer)
```

**STOP** : Attendre la confirmation du développeur.

#### Cas 2 : Aucune Action Détectée ou Commande Sans Message

**Si aucune action claire n'est détectée** (commande invoquée seule ou message ambigu), construire le menu dynamiquement à partir du Skill :

1. **Lire le fichier Skill** : `.agent/skills/analyste-uml/SKILL.md`.
2. **Extraire les Actions** : Identifier toutes les sections `### Action [Lettre] : [Titre]` et leurs descriptions.
3. **Afficher le Menu** : Présenter la liste des actions disponibles.

> **Actions disponibles (Skill : analyste-uml)** :
>
> *[Générer la liste dynamiquement ici basées sur le SKILL.md]*
>
> **[Lettre].** [Titre de l'action]
> → [Description]
>
> **Quelle action souhaitez-vous exécuter ?** (Tapez la lettre correspondante)

**STOP** : Attendre la sélection du développeur.

---

### Étape 3 : Exécution de l'Action Choisie

Selon le choix du développeur, exécuter l'action correspondante du skill `analyste-uml`.

#### Exécution Dynamique via le Skill

**Pour l'action sélectionnée [X]** :
1. **Consulter** le fichier `.agent/skills/analyste-uml/SKILL.md`.
2. **Localiser** la section `### Action [X] : [Titre]`.
3. **Identifier** les **Entrées** requises et les demander si nécessaire.
4. **Exécuter** les **Instructions Détaillées** de l'action.
5. **Valider** le résultat en utilisant les **Points de Contrôle (Definition of Done)**.

*Le Skill est la source de vérité pour l'exécution technique.*

---

## 3. Critères de Qualité
- **Découvrabilité** : Le développeur voit toutes les actions disponibles
- **Cohérence** : Le diagramme reflète exactement l'analyse textuelle
- **Standard** : Respect de la syntaxe PlantUML (`left to right direction`)
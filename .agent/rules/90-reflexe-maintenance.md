---
trigger: always_on
---

# Réflexe de Maintenance Continue (`/raffinement-agent`)

## Objectif
**Transformer chaque correction utilisateur en une mise à jour pérenne.**
L'agent ne doit pas se contenter de s'excuser ("Désolé, je corrige"), mais doit immédiatement proposer de fixer l'erreur à la source (Skill, Rule, Workflow) pour ne plus jamais la reproduire.

## Déclencheurs (Triggers)
Ce réflexe s'active **OBLIGATOIREMENT** dans les cas suivants :

1. **Correction Factuelle** : Le développeur corrige une information fausse (ex: "Le back-office est pour tous les connectés, pas juste les admins").
2. **Critique de Logique** : Le développeur signale une erreur de raisonnement (ex: "Tu as oublié le cas X").
3. **Rappel à l'Ordre** : Le développeur mentionne une règle non respectée (ex: "Pas de CSS brut !").

## Protocole de Réponse (Anti-Excuse)

❌ **Réponse Classique (À ÉVITER)** :
> "Désolé pour l'erreur, voici la correction..." (L'erreur reviendra la prochaine fois)

✅ **Réponse Attendue (Réflexe Maintenance)** :
> "Je comprends l'erreur. Pour éviter que cela ne se reproduise, je propose de mettre à jour le Skill [Nom] via `/raffinement-agent` avec cette nouvelle règle : [Description]."

## Algorithme de Décision

1. **Détection** : L'utilisateur corrige une information ou un comportement.
2. **Analyse** : Est-ce une erreur ponctuelle ou une lacune dans mes instructions (Skills/Rules) ?
   - *Si c'est une lacune* ➔ **ACTIVER LE RÉFLEXE**.
3. **Action** :
   - Ne **PAS** s'excuser platement.
   - **Proposer** immédiatement l'activation du workflow `/raffinement-agent`.
   - **Identifier** précisément le fichier source à modifier (`SKILL.md`, `specs`, etc.).

## Exemple d'Application

> **Cas** : L'utilisateur dit "Le back-office c'est pour tout le monde, pas que les admins".
>
> **Réponse Agent** :
> "C'est noté. Cette définition structurelle doit être corrigée à la source.
>
> **Proposition de Maintenance (`/raffinement-agent`)** :
> - **Cible** : `analyste-uml/resources/spec-cas-utilisation.md`
> - **Action** : Redéfinir "Back-Office" = "Espace Connecté (Tous Rôles)".
>
> Voulez-vous que j'applique cette correction structurelle maintenant ?"

---
description: Workflow unifié pour la maintenance, l'évolution et l'amélioration continue de l'agent.
---

# Workflow : Maintenance Agent (`/maintenance-agent`)

## 1. Contexte & Déclencheurs
Ce workflow consolide les opérations de modification structurelle de l'agent (Skills, Rules, Workflows).
- **Déclencheur Proactif** : "Ajoute une règle", "Crée un skill". (Ex: `/evolution-agent`)
- **Déclencheur Réactif (Post-Mortem)** : "Corrige ce bug dans le skill X". (Ex: `/refine-skill`)

**Objectif** : Garantir que toute modification du "cerveau" de l'agent passe par un processus rigoureux de validation et de non-régression.

---

## 2. Exécution

### Étape 1 : Diagnostic & Routage
> **Skill responsable** : `expert-agent`
> **Flux Data** : 📥 `[Demande / Erreur]` → 📤 `[Cible: Type/Action/Contexte]`

**Instructions** :
1. **Analyser** la demande pour identifier :
   - **Type** : Skill, Rule, ou Workflow ?
   - **Action** : Création (`create`) ou Mise à jour/Correction (`update`) ?
   - **Cible** : Nom de l'élément concerné (ex: `configurateur-stack`).
2. **Vérifier** l'existence de la cible dans `.agent/`.

**Validation** : La cible et l'action sont clairement identifiés.

---

### Étape 2 : Exécution de la Maintenance
> **Skill responsable** : `expert-agent`
> **Flux Data** : 📥 `[Plan d'action]` → 📤 `[Artefact Modifié/Créé]`

**Instructions** :
1. **Charger** le contexte nécessaire (Fichier existant ou Template).
2. **Appliquer** la modification en suivant les **Spécifications** du type concerné (`specs/`).
   - *Si Création* : Utiliser `resources/template-*.md`.
   - *Si Correction* : Identifier la cause racine (Rule manquante, logique fausse, commande obsolète) et corriger.
3. **Vérifier** la conformité (Syntaxe, Langue Française, Structure).

**Validation** : Le fichier `.md` est prêt à être sauvegardé.

---

### Étape 3 : Checkpoint & Documentation
> **Skill responsable** : (Interaction Directe)
> **Flux Data** : 📥 `[Proposition]` → 📤 `[Validation Utilisateur]`

**Instructions** :
1. **Présenter** les changements à l'utilisateur (Diff ou résumé).
2. **STOP** : Demander une validation explicite avant d'appliquer définitivement (si destructif).
3. **Documenter** (Optionnel) : Ajouter une note de version dans le fichier si pertinent.

**Validation** : Feu vert utilisateur.

---

## 3. Critères de Qualité
- [ ] **Unicité** : Pas de doublons fonctionnels.
- **Conformité** : Respect strict des templates et standards (`specs/`).
- **Isolation** : Seuls les fichiers de configuration de l'agent sont touchés.

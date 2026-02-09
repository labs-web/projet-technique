---
description: Workflow unifié pour l'analyse fonctionnelle et la modélisation UML (Use Cases).
---

# Workflow : Analyse Fonctionnelle & UML (`/analyse-uml`)

## 1. Contexte & Protocoles
**Objectif** : Formaliser le besoin métier, structurer les lots (versions), et produire les diagrammes associés via un menu interactif.
**Skill Associé** : `analyste-uml`
**Protocole** : Ce workflow suit le protocole "Skill Wrapper" défini dans [`.agent/rules/03-protocoles-workflow.md`](.agent/rules/03-protocoles-workflow.md).

## 2. Exécution

### Étape 1 : Analyse Sémantique

Appliquer la **Phase de Détection** décrite dans la règle `03-protocoles-workflow.md` en utilisant le Skill : `.agent/skills/analyste-uml/SKILL.md`.

---

### Étape 2 : Routage & Affichage

Selon le résultat de l'analyse, appliquer le **Template A (Confirmation)** ou le **Template B (Menu Dynamique)** définis dans la règle `00-meta-gouvernance.md`.

**Source pour le Menu** : Utiliser les sections `### Action` du fichier `SKILL.md`.

**STOP** : Attendre la validation ou le choix du développeur.

---

### Étape 3 : Exécution Déléguée

Appliquer l'**Algorithme d'Exécution** décrit dans la règle `03-protocoles-workflow.md`.

1. **Lire** l'Action choisie dans `.agent/skills/analyste-uml/SKILL.md`.
2. **Exécuter** strictement les instructions de cette Action.

*Le Skill est la seule source de vérité pour l'exécution technique.*

---

## 3. Critères de Qualité

- **Conformité** : Respect strict du protocole Wrapper.
- **Trace** : Mentionner l'Action et le Skill dans le footer de réponse.
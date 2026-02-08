---
name: expert-agent
description: Expert unifié de la gestion, création et maintenance des composants de l'agent (Skills, Rules, Workflows).
---

# Skill : Expert Agent

## 🎯 Périmètre Global
**Mission** : Assurer la cohérence, la qualité et l'évolution du "système cognitif" de l'agent en centralisant l'expertise sur ses trois piliers fondamentaux : Skills, Rules, et Workflows.

### 🚫 Interdictions Globales (Règles d'Or)
1. **Isolation** : Ne JAMAIS modifier le code source du projet utilisateur (hors dossier `.agent/`).
2. **Langue** : Tout le contenu généré (Descriptions, Instructions) doit être impérativement en **Français**.
3. **Source de Vérité** : Les fichiers dans `specs/` (Standards) sont la loi absolue.
4. **Templates** : Interdiction de créer un fichier "from scratch" ; toujours instancier le template correspondant dans `resources/`.

---

## ⚡ Actions (Capacités Atomiques)

### Action A : Manage Skill (Gérer Compétence)
> **Description** : Créer ou mettre à jour un fichier Skill en respectant `specs-skill.md`.
- **Entrées** : `Nom`, `Besoin`, `Mode (Create/Update)`
- **Sorties** : Fichier `.md` dans `.agent/skills/[nom]/SKILL.md`
- **❌ Interdictions Spécifiques** :
  - Ne jamais créer de skill sans définir ses "Actions Atomiques" (nouveau format).
- **✅ Points de Contrôle** :
  - **Nommage** : Le nom est un **Rôle Humain** (ex: `analyste-uml`).
  - Le fichier respecte la structure `template-skill.md`.
  - Le dossier du skill est créé en `kebab-case`.
- **📝 Instructions Détaillées** :
  1. **Lire** la spec : `specs/specs-skill.md`.
  2. **Si Création** :
     - Vérifier l'unicité du nom.
     - Copier `resources/template-skill.md`.
     - Remplir les sections avec le contexte métier.
  3. **Si Mise à jour** :
     - Analyser le skill existant.
     - Appliquer les modifs demandées tout en refactorisant vers le standard actuel si nécessaire.
  4. **Validation** : Vérifier que toutes les rubriques obligatoires sont présentes.

### Action B : Manage Rule (Gérer Règle)
> **Description** : Créer ou mettre à jour une règle ou une mémoire en respectant `specs-rule.md`.
- **Entrées** : `Nom`, `Contenu`, `Mode (Create/Update)`
- **Sorties** : Fichier `.md` dans `.agent/rules/`
- **✅ Points de Contrôle** :
  - Le header YAML contient bien `trigger` et `description`.
- **📝 Instructions Détaillées** :
  1. **Lire** la spec : `specs/specs-rule.md`.
  2. **Si Création** :
     - Copier `resources/template-rule.md`.
     - Adapter le déclencheur (trigger) selon le besoin (always_on, sur demande, etc.).
  3. **Si Mise à jour** :
     - Vérifier que la règle ne contredit pas une règle globale (`meta-gouvernance`).

### Action C : Manage Workflow (Gérer Processus)
> **Description** : Créer ou mettre à jour un workflow en respectant `specs-workflow.md`.
- **Entrées** : `Nom`, `Étapes`, `Mode (Create/Update)`
- **Sorties** : Fichier `.md` dans `.agent/workflows/`
- **❌ Interdictions Spécifiques** :
  - Ne pas utiliser de nom de rôle pour un workflow.
  - Ne pas créer de workflow sans étapes de validation explicites.
- **✅ Points de Contrôle** :
  - **Nommage** : Le nom décrit une **Phase/Tâche** (ex: `analyse-uml`).
- **📝 Instructions Détaillées** :
  1. **Lire** la spec : `specs/specs-workflow.md`.
  2. **Si Création** :
     - Copier `resources/template-workflow.md`.
     - Définir les étapes séquentielles claires.
     - Ajouter les annotations `// turbo` là où l'auto-exécution est sûre.

---

## 🔄 Scénarios d'Exécution (Algorithmes)

### Scénario 1 : Intervention Unitaire (Défaut)
*Cas classique : "Crée-moi un skill pour faire du SQL"*
1. **Analyse** : Déterminer le type d'objet (Skill, Rule, Workflow) et l'action (Create, Update) d'après la demande.
2. **Exécution** :
   - Si **Skill** → Exécuter **Action A**.
   - Si **Rule** → Exécuter **Action B**.
   - Si **Workflow** → Exécuter **Action C**.
3. **Rapport** : Confirmer l'action et le chemin du fichier créé/modifié.

### Scénario 2 : Audit & Mise à Conformité
*Cas : "Vérifie que tous les skills sont à jour"*
1. **Lister** tous les objets du type demandé.
2. **Pour chaque** objet :
   - Exécuter l'Action correspondante en mode **Update** (sans changer le comportement, juste la structure).
3. **Synthèse** : Lister les fichiers mis en conformité.

---

## ⚙️ Standards & Conventions
1. **Architecture** : `.agent/` est le seul domaine d'intervention.
2. **Nomenclature** : Tout en `kebab-case` (dossiers et fichiers).

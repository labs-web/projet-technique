# Spécifications : Gestion des Skills

## 1. Structure Obligatoire

Un Skill valide doit respecter la structure suivante :
- **Dossier** : `.agent/skills/[nom-du-skill]/`.
- **Définition** : Fichier `SKILL.md` à la racine du dossier.
- **Ressources** : Dossier `resources/` contenant les templates, scripts, ou documentations spécifiques.

## 2. Validation & Standards

### Nommage du Skill
- **Format** : `kebab-case`.
- **Sémantique** : **DOIT** correspondre à un **Rôle Humain** ou un **Expert Métier** (ex: `analyste-uml`, `architecte-sie` `designer-ui`).
- **Interdiction** : Ne pas utiliser de verbes d'action ou de noms de processus (réservés aux Workflows).

### Contenu du Skill (`SKILL.md`)
- **En-tête YAML** : Doit contenir `name` et `description`.
- **Sections** :
  - `🎯 Objectif & Périmètre`
  - `📥 Entrées / 📤 Sorties` (Format liste ou définition, PAS de tableau Markdown complexe).
  - `🔄 Algorithme d'Exécution` (Étapes claires et séquentielles).
  - `⚠️ Règles d'Or` (Contraintes strictes).
- **Langue** : Français strict.

### Création d'Artefacts
- **RÈGLE CRITIQUE** : Tout artefact généré par l'agent, et en particulier le plan d'implémentation (`implementation_plan.md`), **DOIT ÊTRE RÉDIGÉ EN FRANÇAIS**.
- **Templates** : Utiliser `template-skill.md` (situé dans `.agent/skills/expert-agent/resources/`) comme base.

### Spécifications dans resources/
- **PRINCIPE DE GÉNÉRICITÉ** : Les fichiers de spécification dans le dossier `resources/` d'un skill **DOIVENT être génériques** et **indépendants des livrables spécifiques**.
- **Interdiction de Couplage** : 
  - ❌ **NE PAS** nommer les specs d'après les livrables (ex: `spec-analyse.md`, `spec-use-case-v1.md`)
  - ✅ **UTILISER** des noms qui décrivent le **type de document** ou le **format** (ex: `spec-document-analyse.md`, `spec-diagramme-uml.md`)
- **Réutilisabilité** : Une spec doit pouvoir s'appliquer à **plusieurs livrables** du même type.
- **Structure Recommandée** :
  - `spec-format-[nom].md` : Pour les formats techniques (PlantUML, Mermaid, Markdown structuré)
  - `spec-type-[nom].md` : Pour les types de documents (Document d'analyse, Plan de conception, etc.)
- **Exemple de Bonne Pratique** :
  - Au lieu de : `spec-analyse.md` → Utiliser : `spec-document-analyse.md`
  - Au lieu de : `spec-use-case-v1.md` → Utiliser : `spec-diagramme-use-case.md`

## 3. Algorithme de Refactoring

1. **Analyse** : Lire le `SKILL.md` existant.
2. **Comparaison** : Vérifier l'écart avec `template-skill.md`.
3. **Mise à niveau** :
   - Réorganiser les sections.
   - S'assurer que les modèles mentaux (Algorithme) sont clairs.
   - Vérifier que les ressources sont bien dans le dossier `resources/`.
4. **Validation** : Confirmer que le skill est complet et fonctionnel.

# Spécifications : Gestion des Règles (Rules)

## 1. Structure Obligatoire

Une Règle valide doit respecter la structure suivante :
- **Emplacement** : `.agent/rules/[nom-du-fichier].md` (Projet) ou `~/.gemini/antigravity/global_rules/` (Global).
- **Format** : Fichier Markdown avec Frontmatter YAML.

## 2. Validation & Standards

### Contenu de la Règle
- **En-tête YAML** :
  - `trigger`: Condition d'activation (`always_on` ou glob pattern).
- **Sections** :
  - `Objectif` : Pourquoi cette règle existe.
  - `Instructions` : Directives positives (Ce qu'il faut faire).
  - `Interdictions` : Directives négatives (Ce qu'il ne faut PAS faire).
- **Langue** : Français strict.

### Workflow de Création
1. **Analyser** le besoin (Restriction, Convention, Qualité).
2. **Vérifier** l'existant pour éviter les doublons ou conflits.
3. **Créer** le fichier en utilisant `template-rule.md` (situé dans `.agent/skills/expert-agent/resources/`).
4. **Valider** la syntaxe YAML et la clarté des instructions.

## 3. Bonnes Pratiques
- Regrouper les règles par thème (ex: `conventions-code.md`, `securite.md`).
- Utiliser des impératifs forts ("DOIT", "NE DOIT PAS").

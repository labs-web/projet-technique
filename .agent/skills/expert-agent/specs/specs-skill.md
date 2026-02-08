# Spécifications : Gestion des Skills

## 1. Structure Obligatoire

Un Skill valide doit respecter la structure suivante :
- **Dossier** : `.agent/skills/[nom-du-skill]/`.
- **Définition** : Fichier `SKILL.md` à la racine du dossier.
- **Ressources** : Dossier `resources/` contenant les templates, scripts, ou documentations spécifiques.

## 2. Validation & Standards

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

## 3. Algorithme de Refactoring

1. **Analyse** : Lire le `SKILL.md` existant.
2. **Comparaison** : Vérifier l'écart avec `template-skill.md`.
3. **Mise à niveau** :
   - Réorganiser les sections.
   - S'assurer que les modèles mentaux (Algorithme) sont clairs.
   - Vérifier que les ressources sont bien dans le dossier `resources/`.
4. **Validation** : Confirmer que le skill est complet et fonctionnel.

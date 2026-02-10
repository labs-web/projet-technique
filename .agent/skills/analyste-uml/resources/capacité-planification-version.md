# Spécifications : Planification des Versions

## 🎯 Objectif
Définir la **stratégie de découpage** du projet en versions incrémentales (Vertical Slices) pour garantir une livraison progressive et valide.

## 📤 Nature du Livrable
Un document Markdown (`planification-version.md`) définissant le périmètre fonctionnel précis de chaque version, structuré pour guider l'initialisation technique.

## 📝 Format et Structure

### 1. Principes Directeurs
- **Vertical Slices** : Chaque version doit apporter une valeur fonctionnelle complète (Front + Back + DB) utilisable.
- **Incrémental** : V1 = MVP (Minimum Viable Product), les suivantes ajoutent de la valeur.
- **Logique** : Respecter les dépendances métier (ex: Créer un user avant de créer un article).

### 2. Format du Fichier
Le fichier doit lister les versions de manière chronologique.

#### Structure Type par Version :
```markdown
## Version [N] : [Nom Expressif]
- **Slug** : `v[N]-[slug-court]` (ex: `v1-public`)
- **Objectif** : Phrase résumant la valeur apportée.
- **Description** : Détail du périmètre.
- **Fonctionnalités Clés** :
  - [Acteur] : [Action Principale]
  - [Acteur] : [Action Secondaire]
```

### 3. Conventions de Nommage
- **Slug de Version** : `v[chiffre]-[concept]`
  - ✅ `v1-public`, `v2-admin`, `v3-social`
  - ❌ `v1`, `version-finale`, `sprint-2`

## ⚠️ Règles et Contraintes

### Interdictions Strictes
- **INTERDICTION** de créer les dossiers réels (`v1-public/`) à cette étape (C'est le rôle de l'Action C).
- **INTERDICTION** d'inclure des détails techniques (Choix de librairie, noms de tables).
- **INTERDICTION** de découper par couche technique (ex: V1 = BDD, V2 = API, V3 = Front). **Toujours Full-Stack**.

### Principes de Qualité
- **Clarté** : Le nom de la version doit expliciter son contenu.
- **Faisabilité** : Chaque version doit être "livrable" et "testable" indépendamment.
- **Cohérence** : Les fonctionnalités d'une version doivent couvrir un scénario complet.
- **Exhaustivité** : La somme de toutes les versions doit couvrir l'intégralité du `fonctionnalite-global.md`.

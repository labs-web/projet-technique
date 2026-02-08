---
name: analyste-uml
description: Expert en modélisation de l'analyse fonctionnelle (Analyse des besoins et Diagrammes de Cas d'Utilisation).
---

# Skill : Analyste UML

## 🎯 Périmètre Global
**Mission** : Formaliser le besoin métier global, le découper en versions réalisables, et produire les diagrammes de Cas d'Utilisation standardisés pour chaque version.

### 🚫 Interdictions Globales (Règles d'Or)
1. **Doublons** : Ne pas répéter les mêmes fonctionnalités dans plusieurs versions (sauf évolution explicite).
2. **Technique** : Ne pas inclure de détails d'implémentation (BDD, Classes) dans l'analyse fonctionnelle (Déléguer à `conception-uml` ou `architecte`).
3. **Format** : Utiliser exclusivement la syntaxe PlantUML standard pour les diagrammes.

---

## ⚡ Actions (Capacités Atomiques)
*Liste des fonctions que ce skill sait exécuter. C'est ici que se trouve le détail technique.*

### Action A : Analyser le Besoin Global
> **Description** : Transformer une expression de besoin brute en une liste structurée de fonctionnalités.
- **Entrées** : `docs/1.besoin/1.besoin.md` (Expression de besoins initiale).
- **Sorties** : `docs/2.analyse/global-features.md` (Liste consolidée des fonctionnalités).
- **❌ Interdictions Spécifiques** :
  - Ne pas inventer de besoins non exprimés ou implicites sans validation.
- **✅ Points de Contrôle (Definition of Done)** :
  - La liste des fonctionnalités est exhaustive par rapport au document source.
  - Le fichier de sortie ne contient aucune notion de version.
- **📝 Instructions Détaillées** :
  1. **Lecture** : Lire attentivement `docs/1.besoin/1.besoin.md`.
  2. **Extraction** : Identifier les acteurs et les fonctionnalités (Format : Verbe d'action + Objet métier).
  3. **Consolidation** : Créer ou mettre à jour `docs/2.analyse/global-features.md` en listant toutes les fonctionnalités identifiées.

### Action B : Planifier les Versions (Lotissement)
> **Description** : Organiser les fonctionnalités en versions logiques et incrémentales (Vertical Slices).
- **Entrées** : `docs/2.analyse/global-features.md`.
- **Sorties** :
    - Structure de dossiers : `docs/2.analyse/vX-[nom-version]/`.
    - Fichiers d'analyse : `docs/2.analyse/vX-[nom-version]/analyse-vX-[nom-version].md`.
- **❌ Interdictions Spécifiques** :
  - Ne pas créer de versions "techniques" (ex: "V1: Base de données"). Toujours orienter valeur utilisateur.
- **✅ Points de Contrôle (Definition of Done)** :
  - Chaque version apporte une valeur testable.
  - La structure de dossiers respecte la convention de nommage.
- **📝 Instructions Détaillées** :
  1. **Découpage** : Répartir les fonctionnalités du fichier global en versions (V1, V2, etc.).
  2. **Création Structure** : Pour chaque version, créer le dossier `docs/2.analyse/vX-[nom]/` s'il n'existe pas.
  3. **Rédaction** : Créer le fichier `analyse-vX-[nom].md` dans chaque dossier, détaillant les fonctionnalités de cette version (Format User Story : En tant que... Je veux... Afin de...).

### Action C : Générer Use Case (Par Version)
> **Description** : Traduire l'analyse textuelle d'une version en diagramme visuel PlantUML.
- **Entrées** : `docs/2.analyse/vX-[nom-version]/analyse-vX-[nom-version].md`.
- **Sorties** : `docs/2.analyse/vX-[nom-version]/usecase-vX-[nom-version].puml`.
- **❌ Interdictions Spécifiques** :
  - Ne pas inclure de détails techniques (classes, base de données).
- **✅ Points de Contrôle (Definition of Done)** :
  - Le diagramme utilise `left to right direction`.
  - Toutes les fonctionnalités du fichier `.md` sont représentées.
  - La syntaxe PlantUML est valide.
- **📝 Instructions Détaillées** :
  1. **Lecture** : Lire le fichier d'analyse de la version cible.
  2. **Modélisation** :
     - Identifier les **Acteurs**.
     - Identifier les **Cas d'Utilisation**.
     - Définir les **Relations** (`include`, `extend`).
  3. **Génération** : Créer ou mettre à jour le fichier `.puml` dans le même dossier.

---

## 🔄 Scénarios d'Exécution (Algorithmes)
*Orchestration des Actions définies ci-dessus.*

### Scénario 1 : Analyse Complète (Workflow Standard)
*À utiliser lors de l'initialisation du projet ou d'une refonte majeure.*
1. **Initialisation** : Exécuter l'**Action A** (Analyse du Besoin Global).
2. **Planification** : Exécuter l'**Action B** (Lotissement) sur la base de l'analyse globale.
3. **Modélisation** : Pour chaque version définie :
   - Exécuter l'**Action C** (Générer Use Case).

### Scénario 2 : Mise à jour d'une Version
*À utiliser lorsqu'une spécification change pour une version donnée.*
1. **Ciblage** : Identifier le dossier de la version (ex: `v2-social`).
2. **Mise à jour** :
   - Si le besoin change, mettre à jour `analyse-vX.md`.
   - Exécuter l'**Action C** pour régénérer le diagramme correspondant.

---

## ⚙️ Standards & Conventions
1. **Source de Vérité** : Les fichiers Markdown (`.md`) d'analyse priment sur les diagrammes.
2. **Conventions de Nommage** :
   - Dossiers : `v[N]-[slug]` (ex: `v1-public`).
   - Fichiers : `[type]-v[N]-[slug].[ext]` (ex: `analyse-v1-public.md`, `usecase-v1-public.puml`).
3. **Ressources** : Utiliser les templates situés dans `.agent/resources/` (si applicables).

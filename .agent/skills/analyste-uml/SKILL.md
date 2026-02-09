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
> **Spécification** : Voir `resources/spec-analyse-global.md` pour les règles et le format du livrable.
- **Entrées** : `docs/1.besoin/besoin.md` (Expression de besoins initiale).
- **Sorties** : `docs/2.analyse/global/fonctionnalite-global.md` (Liste consolidée des fonctionnalités).
- **❌ Interdictions Spécifiques** :
  - Ne pas inventer de besoins non exprimés ou implicites sans validation.
  - Ne pas inclure d'éléments de conception (classes, tables, architecture).
- **✅ Points de Contrôle (Definition of Done)** :
  - La liste des fonctionnalités est exhaustive par rapport au document source.
  - Le fichier respecte le format défini dans `spec-analyse-global.md`.
  - Aucun élément de conception n'est présent.
- **📝 Instructions Détaillées** :
  1. **Lecture** : Lire attentivement `docs/1.besoin/besoin.md`.
  2. **Extraction** : 
     - Identifier les **Acteurs** et les **Fonctionnalités** (Format : Verbe d'action + Objet métier).
     - Identifier les **Règles de Gestion** (Permissions, Contraintes, Scopes) associées.
  3. **Validation** : Vérifier la conformité avec les règles définies dans `resources/spec-analyse-global.md`.

### Action B : Planifier les Versions (Stratégie)
> **Description** : Définir la roadmap et le découpage en versions dans un fichier dédié.
- **Entrées** : `docs/2.analyse/global/analyse-global.md` (Contexte).
- **Sorties** : `docs/2.analyse/global/planification-version.md` (Nouveau fichier contenant la Roadmap/Lotissement).
- **❌ Interdictions Spécifiques** :
  - **INTERDICTION** de créer des dossiers ou des fichiers de version (`vX`). Action purement rédactionnelle/stratégique.
- **✅ Points de Contrôle (Definition of Done)** :
  - Le fichier `planification-version.md` existe.
  - Il définit clairement le contenu de chaque version.
- **📝 Instructions Détaillées** :
  1. **Stratégie** : Définir le contenu de chaque version (V1, V2...) en se basant sur `analyse-global.md`.
  2. **Rédaction** : Créer le fichier `docs/2.analyse/global/planification-version.md` et y rédiger la roadmap.

### Action C : Initialiser une Version
> **Description** : Créer concrètement l'arborescence et le fichier d'analyse pour une ou plusieurs versions validées.
- **Entrées** : 
    - `docs/2.analyse/global/analyse-global.md` (Quoi - Fonctionnalités).
    - `docs/2.analyse/global/planification-version.md` (Quand/Où - Roadmap).
- **Paramètres** : `Version Cible` ("Toutes" ou nom spécifique ex: "v1-public").
- **Sorties** :
    - Structure de dossiers : `docs/2.analyse/vX-[nom-version]/`.
    - Fichiers d'analyse : `docs/2.analyse/vX-[nom-version]/analyse-vX-[nom-version].md`.
- **✅ Points de Contrôle (Definition of Done)** :
  - Le dossier et le fichier existent.
  - Le contenu du fichier `analyse-vX.md` correspond à ce qui a été défini dans la roadmap (`planification-version.md`) et les specs (`analyse-global.md`).
- **📝 Instructions Détaillées** :
  1. **Sélection** : Identifier la/les version(s) à traiter selon le paramètre et la roadmap.
  2. **Création Struct** : Pour la version cible, créer le dossier `docs/2.analyse/vX-[nom]/` s'il n'existe pas.
  3. **Génération** : Créer le fichier `analyse-vX-[nom].md` en y transférant les fonctionnalités définies pour cette version.

### Action D : Générer Use Case (Par Version)
> **Description** : Traduire l'analyse textuelle d'une version en diagramme visuel PlantUML.
> **Spécifications** : 
> - Voir `resources/spec-plantuml.md` pour les standards PlantUML et le format des diagrammes.
> - Voir `resources/spec-cas-utilisation.md` pour les règles de simplification CRUD.
- **Entrées** : `docs/2.analyse/vX-[nom-version]/analyse-vX-[nom-version].md`.
- **Sorties** : `docs/2.analyse/vX-[nom-version]/usecase-vX-[nom-version].puml`.
- **❌ Interdictions Spécifiques** :
  - Ne pas inclure de détails techniques (classes, base de données).
- **✅ Points de Contrôle (Definition of Done)** :
  - Le diagramme respecte les standards définis dans `spec-plantuml.md`.
  - Le diagramme utilise `left to right direction`.
  - Toutes les fonctionnalités du fichier `.md` sont représentées.
  - La syntaxe PlantUML est valide.
- **📝 Instructions Détaillées** :
  1. **Lecture** : Lire le fichier d'analyse de la version cible.
  2. **Modélisation** :
     - Identifier les **Acteurs**.
     - Identifier les **Cas d'Utilisation**.
     - Définir les **Relations** (`include`, `extend`).
  3. **Validation** : Vérifier la conformité avec les règles définies dans `resources/spec-plantuml.md`.
  4. **Génération** : Créer ou mettre à jour le fichier `.puml` dans le même dossier.


### Action E : Générer Diagrammes de Cas d'Utilisation par Contexte
> **Description** : Créer les diagrammes PlantUML séparés pour chaque contexte applicatif (Public, Admin, API).
> **Spécifications** : 
> - Voir `resources/spec-plantuml.md` pour les standards PlantUML et le format des diagrammes.
> - Voir `resources/spec-cas-utilisation.md` pour les règles de simplification CRUD et de séparation des contextes.
- **Entrées** : `docs/2.analyse/global/fonctionnalite-global.md` (Liste consolidée des fonctionnalités).
- **Sorties** (selon les contextes détectés) : 
  - `docs/2.analyse/global/usecase-public.puml` *(si contexte application publique/frontend détecté)*
  - `docs/2.analyse/global/usecase-admin.puml` *(si contexte back-office/administration détecté)*
  - `docs/2.analyse/global/usecase-api.puml` *(si API REST détectée)*
  - **Règle** : Créer **uniquement** les fichiers correspondant aux contextes présents dans l'analyse.
- **❌ Interdictions Spécifiques** :
  - **INTERDICTION** de créer un fichier `usecase-global.puml` regroupant tous les contextes.
  - Ne pas inclure de détails techniques (classes, base de données).
  - Ne pas mélanger les contextes dans un même fichier.
- **✅ Points de Contrôle (Definition of Done)** :
  - Chaque diagramme respecte les standards définis dans `spec-plantuml.md`.
  - Chaque diagramme utilise `left to right direction`.
  - Les fonctionnalités sont correctement réparties par contexte.
  - La syntaxe PlantUML est valide pour tous les fichiers.
  - Les relations `extend` sont appliquées pour les variantes de permissions.
  - Chaque contexte est dans un rectangle distinct avec un nom clair.
- **📝 Instructions Détaillées** :
  1. **Lecture** : Lire le fichier `docs/2.analyse/global/fonctionnalite-global.md`.
  2. **Analyse des Contextes** :
     - Détecter les **contextes applicatifs** (Public, Admin, API).
     - Répartir les fonctionnalités par contexte selon les acteurs et la nature des opérations.
  3. **Modélisation par Contexte** :
     - Pour chaque contexte, identifier les **Acteurs** concernés.
     - Pour chaque contexte, identifier les **Cas d'Utilisation**.
     - Appliquer les **relations `extend`** pour les variantes de permissions (même interface, permissions différentes).
     - Appliquer les **relations `include`** pour les dépendances obligatoires.
  4. **Validation** : Vérifier la conformité avec les règles définies dans `resources/spec-plantuml.md` et `resources/spec-cas-utilisation.md`.
  5. **Génération** : Créer ou mettre à jour les fichiers `.puml` dans le dossier `docs/2.analyse/global/`.

---

## 🔄 Scénarios d'Exécution (Algorithmes)
*Orchestration des Actions définies ci-dessus.*

### Scénario 1 : Analyse Complète (Workflow Standard)
*À utiliser lors de l'initialisation du projet ou d'une refonte majeure.*
1. **Initialisation** : Exécuter l'**Action A** (Analyse du Besoin Global).
2. **Arrêt / Proposition** : Proposer de passer à l'**Action B** (Planification).
3. **Planification** : Exécuter l'**Action B** (Stratégie) (Seulement sur validation).
4. **Arrêt / Proposition** : Proposer de passer à l'**Action C** (Initialisation).
5. **Initialisation** : Exécuter l'**Action C** pour créer les fichiers de version.
6. **Modélisation** : Exécuter l'**Action D** (Générer Use Case).

### Scénario 2 : Mise à jour d'une Version
*À utiliser lorsqu'une spécification change pour une version donnée.*
1. **Ciblage** : Identifier le dossier de la version (ex: `v2-social`).
2. **Mise à jour** :
   - Si le besoin change, mettre à jour `analyse-vX.md`.
   - Exécuter l'**Action D** pour régénérer le diagramme correspondant.

---

## ⚙️ Standards & Conventions
1. **Source de Vérité** : Les fichiers Markdown (`.md`) d'analyse priment sur les diagrammes.
2. **Conventions de Nommage** :
   - Dossiers : `v[N]-[slug]` (ex: `v1-public`).
   - Fichiers : `[type]-v[N]-[slug].[ext]` (ex: `analyse-v1-public.md`, `usecase-v1-public.puml`).
3. **Ressources** : Utiliser les templates situés dans `.agent/resources/` (si applicables).

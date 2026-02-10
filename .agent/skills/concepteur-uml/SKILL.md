---
name: concepteur-uml
description: Expert en modélisation technique et conception (Diagrammes de Classes et de BDD avec Mermaid).
---



# Skill : Concepteur UML

## 🎯 Périmètre Global
**Mission** : Formaliser la solution technique à travers des diagrammes de conception (Classes, ERD) pour guider l'implémentation, en assurant la transition entre le besoin fonctionnel et le code.

### 🚫 Interdictions Globales (Règles d'Or)
1. **Scope** : Ne jamais modéliser de processus métier (BPMN) ou de cas d'utilisation (Use Case) -> Déléguer à `analyste-uml`.
2. **Format** : Utiliser exclusivement la syntaxe Mermaid pour les diagrammes.
3. **Complexité** : Ne pas surcharger un diagramme. Si plus de 10 classes, découper en sous-domaines.

---

## ⚡ Actions (Capacités Atomiques)

### Action A1 : Modéliser le Domaine (Global)
> **Description** : Créer le diagramme de classes global de l'application (Vision Cible).
- **Capacités Utilisées** :
  - `capacités/capacité-mermaid.md`
  - `capacités/capacité-diagramme-classes.md`
- **Entrées** :
  - `docs/2.analyse/global/fonctionnalite-global.md` (Vision d'ensemble).
  - `docs/3.conception/rules-business.md` (Règles de gestion transverses).
- **Sorties** : `docs/3.conception/global/classes-global.mermaid`
- **❌ Interdictions Spécifiques** :
  - Ne pas détailler les méthodes techniques (CRUD standard), rester sur le domaine métier.
- **✅ Points de Contrôle** :
  - Toutes les entités majeures sont présentes.
  - Héritage et abstractions sont identifiés.
- **📝 Instructions d'Orchestration** :
  1. **Analyse** : Identifier les entités "Cœur de métier" depuis l'analyse globale.
  2. **Modélisation** : Appliquer `capacité-diagramme-classes` pour lier les grands ensembles.
  3. **Sauvegarde** : Produire le fichier dans `docs/3.conception/global/`.

### Action A2 : Modéliser le Domaine (Focus Version)
> **Description** : Créer le diagramme de classes spécifique aux entités impactées par une version.
- **Capacités Utilisées** :
  - `capacités/capacité-mermaid.md`
  - `capacités/capacité-diagramme-classes.md`
- **Entrées** :
  - `docs/2.analyse/vX-[nom]/analyse-vX-[nom].md` (Spécifications de la version).
  - `docs/2.analyse/global/fonctionnalite-global.md` (Contexte).
  - `docs/3.conception/rules-business.md`.
- **Sorties** : `docs/3.conception/vX-[nom]/classes-vX-[nom].mermaid`
- **❌ Interdictions Spécifiques** :
  - Ne pas redéfinir les entités hors scope, utiliser des références si besoin.
- **✅ Points de Contrôle** :
  - Seules les entités modifiées/créées par la version sont détaillées.
- **📝 Instructions d'Orchestration** :
  1. **Analyse** : Identifier le delta fonctionnel de la version.
  2. **Modélisation** : Détailler les attributs et méthodes spécifiques à cette itération.
  3. **Sauvegarde** : Produire le fichier dans le dossier de version `docs/3.conception/vX-[nom]/`.

### Action C1 : Rédiger la Conception Technique
> **Description** : Produire le document de conception technique détaillé par couches (Front/Contrôleur/Métier/Data).
- **Capacités Utilisées** :
  - `capacités/capacité-conception-technique.md`
- **Entrées** :
  - `docs/2.analyse/vX-[nom]/analyse-vX-[nom].md` (Analyse fonctionnelle).
  - `docs/3.conception/vX-[nom]/classes-vX-[nom].mermaid` (Modèle de données validé).
- **Sorties** : `docs/3.conception/vX-[nom]/conception-technique-vX-[nom].md`
- **❌ Interdictions Spécifiques** :
  - Ne pas faire de diagrammes ici, utiliser du texte structuré et des tableaux (Markdown).
- **✅ Points de Contrôle** :
  - Les 4 couches (Front, Présentation, Métier, Data) sont traitées.
  - La cohérence avec le diagramme de classes est vérifiée.
- **📝 Instructions d'Orchestration** :
  1. **Structure** : Créer le fichier Markdown selon la `capacité-conception-technique`.
  2. **Rédaction** : Remplir chaque section en traduisant le besoin fonctionnel en choix techniques précis (Noms de classes, Routes, Méthodes).
  3. **Revue** : Vérifier que toutes les exigences de l'analyse sont couvertes techniquement.

---

## 🔄 Scénarios d'Exécution (Algorithmes)

### Scénario 1 : Conception Complète d'une Version
1. **Initialisation** : Lire l'analyse fonctionnelle de la version.
2. **Modélisation** : Exécuter l'**Action A2** (Diagramme Classes).
3. **Persistance** : Exécuter l'**Action B** (ERD/BDD via SQL/Schema si nécessaire, *Action à définir plus tard*).
4. **Spécification** : Exécuter l'**Action C1** pour rédiger le guide technique de développement.
5. **Validation** : Vérifier la cohérence globale.

---

## ⚙️ Standards & Conventions
1. **Notation** : PascalCase pour les Classes (`UserProfile`), snake_case pour la BDD (`user_profiles`).
2. **Outil** : Utiliser Mermaid Live Editor pour prévisualiser si besoin, mais le code source reste dans les fichiers.

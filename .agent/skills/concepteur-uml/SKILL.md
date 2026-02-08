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

### Action A : Modéliser le Domaine (Class Diagram)
> **Description** : Créer un diagramme de classes représentant les entités, leurs attributs, méthodes et relations.
- **Entrées** :
  - `docs/2.analyse/vX-[nom]/analyse-vX-[nom].md` (Besoin analysé).
  - `docs/3.conception/rules-business.md` (Règles de gestion, optionnel).
- **Sorties** : `docs/3.conception/vX-[nom]/classes-vX-[nom].mermaid`
- **❌ Interdictions Spécifiques** :
  - Ne pas utiliser de types spécifiques au langage (ex: `List<String>`) mais des standards UML (`String[]` ou `0..*`).
- **✅ Points de Contrôle (Definition of Done)** :
  - Toutes les entités du besoin sont représentées.
  - Les cardinalités sont précises.
  - Les relations (Rea, Aggregation, Composition, Heritage) sont correctes.
- **📝 Instructions Détaillées** :
  1. **Analyse** : Identifier les noms (Classes) et les verbes (Méthodes) dans l'analyse.
  2. **Structure** : Créer le dossier `docs/3.conception/vX-[nom]/` si inexistant.
  3. **Rédaction** :
     - Définir les classes et attributs.
     - Ajouter les types de données génériques.
     - Établir les relations.
     - Sauvegarder dans le fichier `.mermaid`.

### Action B : Modéliser la BDD (ER Diagram)
> **Description** : Traduire le modèle de classes en schéma relationnel de base de données physique.
- **Entrées** : `docs/3.conception/vX-[nom]/classes-vX-[nom].mermaid`.
- **Sorties** : `docs/3.conception/vX-[nom]/bdd-vX-[nom].mermaid`
- **❌ Interdictions Spécifiques** :
  - Ne pas oublier les clés étrangères (FK).
  - Ne pas utiliser de types non supportés par le SGBD cible (MySQL/MariaDB).
- **✅ Points de Contrôle (Definition of Done)** :
  - Les tables sont normalisées (3NF).
  - La convention de nommage Snake Case est respectée (`user_id`, `created_at`).
- **📝 Instructions Détaillées** :
  1. **Transformation** : Convertir Clsases -> Tables, Attributs -> Colonnes.
  2. **Typage** : Assigner les types SQL (INT, VARCHAR, TIMESTAMP...).
  3. **Relations** : Matérialiser les relations par des Clés Étrangères (FK).
  4. **Table Pivot** : Créer les tables de jointure pour les relations Many-to-Many.

---

## 🔄 Scénarios d'Exécution (Algorithmes)

### Scénario 1 : Conception Complète d'une Version
1. **Initialisation** : Lire l'analyse fonctionnelle de la version.
2. **Architecture** : Exécuter l'**Action A** pour valider la structure objet.
3. **Persistance** : Exécuter l'**Action B** pour préparer le schéma de base de données.
4. **Validation** : Vérifier la cohérence entre Classes et BDD.

---

## ⚙️ Standards & Conventions
1. **Notation** : PascalCase pour les Classes (`UserProfile`), snake_case pour la BDD (`user_profiles`).
2. **Outil** : Utiliser Mermaid Live Editor pour prévisualiser si besoin, mais le code source reste dans les fichiers.

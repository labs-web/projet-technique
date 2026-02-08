# Spécifications : Cas d'Utilisation (Use Case)

## 📌 Usage
Utilisé pour définir les règles de modélisation des **Diagrammes de Cas d'Utilisation** lors de la phase d'**Analyse**.

---

## 📝 Règles de Simplification

### Règle CRUD : Regroupement par "Gestion"

**Contexte** : Lorsqu'une entité métier dispose de plusieurs opérations CRUD (Créer, Lire, Modifier, Supprimer), le diagramme peut rapidement devenir surchargé.

**Principe** : Si le nombre total de cas d'utilisation **dépasse 10**, il est recommandé de regrouper les opérations CRUD sous un cas d'utilisation générique **"Gérer [Entité]"**.

**Application** :
- **Au lieu de** :
  - `Créer un article`
  - `Modifier un article`
  - `Supprimer un article`
  
- **Utiliser** :
  - `Gérer les articles` (cas d'utilisation **unique**, pas un package)

**⚠️ Important** :
- **"Gérer [Entité]"** est un **cas d'utilisation simple** (`usecase`), PAS un package.
- **Ne PAS créer** de package "Gestion Catégories" contenant plusieurs cas d'utilisation.
- **Créer directement** le cas d'utilisation : `usecase "Gérer les catégories" as UC_X`

**Limites de la Simplification** :
- **Ne pas appliquer** si les opérations ont des acteurs différents ou des règles de gestion distinctes.
- **Ne pas simplifier** l'opération de **Lecture/Consultation** (elle reste explicite : `Consulter les articles`).

---

## ✅ Quand Simplifier ?

**Décision basée sur la complexité** :

1. **Moins de 10 cas d'utilisation** :
   - Garder les opérations explicites (`Créer`, `Modifier`, `Supprimer`).
   - Favorise la clarté et la compréhension du périmètre fonctionnel.

2. **Plus de 10 cas d'utilisation** :
   - Appliquer la règle de regroupement "Gestion".
   - Réduit la complexité visuelle du diagramme.
   - Documenter les opérations détaillées dans le fichier d'analyse textuelle (`.md`).

---

## 🔗 Règles de Relations : Extension de Comportement

### Relation `extend` : Variantes de Permissions sur une Même Interface

**Contexte** : Lorsque plusieurs acteurs avec des **rôles différents** accèdent à la **même page/interface** mais avec des **permissions différentes**, il faut modéliser un cas d'utilisation de base et ses variantes.

**Principe** : Utiliser la relation `<<extend>>` pour représenter les variantes de comportement d'un cas d'utilisation de base.

**Règle de Détection** :
- ✅ **Appliquer `extend`** si :
  - Plusieurs cas d'utilisation accèdent à la même interface/page
  - Les acteurs ont des **permissions différentes** (Auteur vs Éditeur vs Admin)
  - Le comportement de base est partagé, mais il existe des variantes selon les rôles

- ❌ **Ne PAS appliquer `extend`** si :
  - Les cas d'utilisation concernent des pages/interfaces complètement différentes
  - Il n'y a qu'un seul acteur pour la fonctionnalité

**Structure UML** :
```puml
' Cas d'utilisation de base (comportement générique)
usecase "Gestion des articles" as UC_Base

' Variantes selon les rôles (extensions)
usecase "Gérer ses articles" as UC_Author
usecase "Gérer tous les articles" as UC_Editor

' Relations d'extension
UC_Author <.. UC_Base : <<extend>>
UC_Editor <.. UC_Base : <<extend>>

' Acteurs accèdent aux variantes
Author -- UC_Author
Editor -- UC_Editor
```

**⚠️ Important** :
- Le **cas d'utilisation de base** représente la fonctionnalité générique (ex: "Gestion des articles")
- Les **extensions** représentent les variantes selon les permissions (ex: "Gérer ses articles", "Gérer tous les articles")
- Les **acteurs** sont liés aux **variantes**, pas au cas de base

**Application** :
- **Cas d'utilisation de base** : `Gestion des articles` (interface commune)
- **Extensions** :
  - `Gérer ses articles` (Auteur : permission limitée à ses propres articles)
  - `Gérer tous les articles` (Éditeur : permission sur tous les articles)

### Exemple Complet

```puml
actor "Auteur" as Author
actor "Éditeur" as Editor

rectangle "Blog" {
  ' Cas de base (générique)
  usecase "Gestion des articles" as UC_Base
  usecase "Gestion des catégories" as UC_Cat_Base
  
  ' Extensions (variantes de permissions)
  usecase "Gérer ses articles" as UC_Author
  usecase "Gérer tous les articles" as UC_Editor
  usecase "Gérer les catégories de ses articles" as UC_Author_Cat
  usecase "Gérer toutes les catégories" as UC_Editor_Cat
}

' Relations d'extension
UC_Author <.. UC_Base : <<extend>>
UC_Editor <.. UC_Base : <<extend>>
UC_Author_Cat <.. UC_Cat_Base : <<extend>>
UC_Editor_Cat <.. UC_Cat_Base : <<extend>>

' Associations acteurs-variantes
Author -- UC_Author
Author -- UC_Author_Cat
Editor -- UC_Editor
Editor -- UC_Editor_Cat
```

---

## 💡 Exemples

### Exemple 1 : Sans Simplification (< 10 cas)
```puml
actor "Auteur" as Author
rectangle "Blog" {
  usecase "Créer un article" as UC1
  usecase "Modifier son article" as UC2
  usecase "Supprimer son article" as UC3
  usecase "Consulter les articles" as UC4
}
Author -- UC1
Author -- UC2
Author -- UC3
Author -- UC4
```

### Exemple 2 : Avec Simplification (> 10 cas)
```puml
actor "Auteur" as Author
actor "Éditeur" as Editor
rectangle "Blog" {
  usecase "Gérer ses articles" as UC1
  usecase "Gérer les catégories" as UC2
  usecase "Consulter les articles" as UC3
}
Author -- UC1
Author -- UC3
Editor -- UC2
Editor -- UC3
```

**Note** : Ici, "Gérer ses articles" et "Gérer les catégories" sont des **cas d'utilisation simples**, pas des packages.

---

## 🏗️ Règles d'Organisation : Séparation des Contextes

### Séparation Partie Publique et Partie Administration

**Contexte** : Lorsque l'application possède **deux contextes métier distincts** (Frontend Public et Back-office Administration), le diagramme doit refléter cette séparation architecturale.

**Principe** : Créer **deux rectangles séparés** pour représenter les deux parties de l'application.

**Règle de Détection** :
- ✅ **Créer deux rectangles** si :
  - L'application a une **partie publique** (accessible aux visiteurs/utilisateurs)
  - L'application a une **partie administration** (back-office, tableau de bord admin)
  - Les deux parties ont des **interfaces distinctes** (URLs différentes, menus différents)

- ❌ **Garder un seul rectangle** si :
  - L'application n'a qu'une seule interface
  - Les fonctionnalités admin sont intégrées dans l'interface publique

**Structure UML** :
```puml
' Partie Publique (Frontend)
rectangle "Application Publique - Blog" {
  usecase "Consulter les articles" as UC_Public1
  usecase "S'inscrire" as UC_Public2
  usecase "Gérer ses articles" as UC_Public3
}

' Partie Administration (Back-office)
rectangle "Back-office Administration" {
  usecase "Gérer les utilisateurs" as UC_Admin1
  usecase "Gérer les rôles" as UC_Admin2
  usecase "Tableau de bord" as UC_Admin3
}
```

**⚠️ Important** :
- Les **rectangles** représentent les **contextes d'exécution** (frontend vs back-office)
- Certains cas d'utilisation peuvent être **partagés** entre les deux contextes
- Les **acteurs** peuvent accéder à un ou plusieurs contextes selon leurs permissions

**Application typique** :
- **Rectangle "Application Publique"** :
  - Consultation des contenus
  - Inscription/Connexion
  - Gestion de contenu (Auteur/Éditeur)
  - Profil utilisateur

- **Rectangle "Back-office Administration"** :
  - Gestion des utilisateurs
  - Gestion des rôles et permissions
  - Tableau de bord statistiques
  - Configuration système

### Exemple Complet

```puml
actor "Visiteur" as Guest
actor "Auteur" as Author
actor "Administrateur" as Admin

' Partie Publique
rectangle "Application Publique - Blog" {
  usecase "Consulter les articles" as UC1
  usecase "S'inscrire" as UC2
  usecase "Se connecter" as UC3
  usecase "Gérer ses articles" as UC4
}

' Partie Administration
rectangle "Back-office Administration" {
  usecase "Accéder au dashboard" as UC_A1
  usecase "Gérer les utilisateurs" as UC_A2
  usecase "Gérer les rôles" as UC_A3
}

' Relations
Guest -- UC1
Guest -- UC2
Guest -- UC3
Author -- UC4
Admin -- UC_A1
Admin -- UC_A2
Admin -- UC_A3
```

**⚠️ Principe Important : Un Contexte = Un Fichier**

Lorsque l'application possède plusieurs contextes distincts, **chaque contexte doit avoir son propre fichier de diagramme** :

- **`usecase-public.puml`** : Contient uniquement les cas d'utilisation de l'application publique
- **`usecase-admin.puml`** : Contient uniquement les cas d'utilisation du back-office
- **`usecase-api.puml`** : Contient uniquement les cas d'utilisation de l'API REST (si applicable)

**⚠️ INTERDICTION** : Ne PAS créer de fichier `usecase-global.puml` regroupant tous les contextes.

**Avantages** :
- **Maintenabilité** : Modifications isolées par contexte
- **Lisibilité** : Diagrammes plus petits et focalisés
- **Collaboration** : Plusieurs développeurs peuvent travailler sur des contextes différents
- **Documentation** : Alignement avec l'architecture technique (routes, controllers)

---

## 🎯 Objectif

- **Lisibilité** : Maintenir un diagramme clair et exploitable.
- **Complétude** : Le fichier d'analyse textuelle (`.md`) reste la source de vérité pour les détails.
- **Cohérence** : Appliquer la règle uniformément sur tous les diagrammes du projet.

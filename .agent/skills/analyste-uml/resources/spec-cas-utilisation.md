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

### Séparation Front-Office et Back-Office

**Définition Stricte** :
- **Front-Office (Public)** : Espace accessible aux **Visiteurs non connectés**.
  - *Fonctions* : Consultation (mode lecture), Inscription, Connexion.
- **Back-Office (Privé/Admin)** : Espace accessible uniquement après **Authentification**.
  - *Fonctions* : Dashboard, Gestion de profil, Gestion de contenu (Auteur/Éditeur), Administration système (Admin).

**Principe** : Tout acteur connecté (Utilisateur, Auteur, Admin) exerce ses fonctions de gestion dans le **Back-Office**. Le Front-Office est réservé à l'acquisition d'audience et l'entrée dans le système.

**Règle de Détection** :
- ✅ **Rectangle "Front-Office / Public"** : Contient uniquement les cas d'utilisation accessibles sans login ( + Login/Register).
- ✅ **Rectangle "Back-office / Espace Connecté"** : Contient TOUS les cas d'utilisation nécessitant une session active.

**Structure UML** :
```puml
' Partie Publique (Front-Office)
rectangle "Front-Office (Public)" {
  usecase "Consulter les articles" as UC_Public1
  usecase "S'inscrire (Register)" as UC_Public2
  usecase "Se connecter (Login)" as UC_Public3
}

' Partie Privée (Back-Office)
rectangle "Back-Office (Espace Connecté)" {
  usecase "Gérer son profil" as UC_User
  usecase "Gérer ses articles" as UC_Author
  usecase "Gérer le système" as UC_Admin
}
```

**⚠️ Important** :
- L'action de "Se connecter" est la porte d'entrée : elle est dans le Front-Office mais mène au Back-Office.
- Les fonctionnalités "métier" (créer un article, modifier son profil) sont **toujours** dans le Back-Office.

**Application typique** :
- **Front-Office** :
  - Home, Articles, Catégories (Lecture seule)
  - Login / Register

- **Back-Office** :
  - **Utilisateur Standard** : Mon Profil, Mes Favoris
  - **Auteur/Éditeur** : Mes Articles, Gestion des Médias
  - **Admin** : Gestion Users, Settings, Logs

### Exemple Complet

```puml
actor "Visiteur" as Guest
actor "Auteur" as Author
actor "Administrateur" as Admin

' Partie Publique
rectangle "Front-Office" {
  usecase "Consulter" as UC1
  usecase "Se connecter" as UC2
}

' Partie Privée
rectangle "Back-Office" {
  usecase "Gérer ses articles" as UC3
  usecase "Administrer le site" as UC4
}

' Relations
Guest -- UC1
Guest -- UC2

' Les acteurs connectés interagissent principalement avec le Back-Office
Author -- UC3
Admin -- UC4
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

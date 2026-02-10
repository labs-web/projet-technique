# Spécifications : Cas d'Utilisation (Use Case)

## 📌 Usage
Utilisé pour définir les règles de modélisation des **Diagrammes de Cas d'Utilisation** lors de la phase d'**Analyse**.

---

## 📝 Règles de Simplification & Précision

### 1. Règle CRUD : Regroupement par "Gestion" (Simplification)

**Contexte** : Lorsqu'une entité métier dispose de plusieurs opérations CRUD (Créer, Lire, Modifier, Supprimer), le diagramme peut rapidement devenir surchargé.

**Principe** : Si le nombre total de cas d'utilisation **dépasse 10**, il est recommandé de regrouper les opérations CRUD sous un cas d'utilisation générique **"Gérer [Entité]"**.

**Application** :
- **Au lieu de** : `Créer un article`, `Modifier un article`, `Supprimer un article`
- **Utiliser** : `Gérer les articles`

### 2. Règle de Précision : Interdiction des Termes "Fourre-Tout"

**Principe** : Un cas d'utilisation doit correspondre à une **intention métier explicite**. Les termes vagues qui masquent la complexité ou le besoin réel sont interdits.

- ❌ **INTERDIT (Trop Vague)** :
  - "Gérer le système"
  - "Gérer toutes les entités"
  - "Administration globale"
  
- ✅ **OBLIGATOIRE (Concret)** :
  - "Configurer le site" (Settings)
  - "Consulter les logs techniques"
  - "Modérer les commentaires"
  - "Gérer les utilisateurs"

**Pourquoi ?** : "Gérer le système" n'aide pas à comprendre ce que l'admin doit *pouvoir faire*. On ne peut pas coder "Gérer le système". On code "Une page de settings", "Un viewer de logs".

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

## 🔗 Règles de Gestion des Permissions (UML Classique)

### Principe Fondamental
**NE PAS créer des cas d'utilisation différents uniquement pour refléter des différences de droits d'accès.**

### Approche Recommandée
1. **Un seul cas d'utilisation partagé** : Utiliser un verbe générique (ex: `Gérer les articles`).
2. **Multiples Acteurs** : Relier tous les acteurs concernés (Auteur, Éditeur) à ce même cas d'utilisation.
3. **Documentation Textuelle** : Préciser les périmètres (Scope) et permissions exactes dans la fiche descriptive du cas d'utilisation (fichier `.md`).

### ⚠️ Interdiction "Matrice de Droits"
- **INTERDICTION** d'utiliser `<<extend>>` pour créer des variantes de droits (ex: `Gérer ses articles` vs `Gérer tous les articles`).
- **INTERDICTION** de multiplier les bulles pour chaque nuance de permission.
- **Raison** : Le diagramme de cas d'utilisation doit montrer **ce que** le système fait, pas **la logique interne** de contrôle d'accès.

### Exemple Correct
```puml
actor "Auteur" as Author
actor "Éditeur" as Editor

rectangle "Blog" {
  usecase "Gérer les articles" as UC_Manage_Articles
  usecase "Gérer les catégories" as UC_Manage_Cats
}

' L'auteur peut gérer (ses) articles
Author -- UC_Manage_Articles

' L'éditeur peut gérer (tous) les articles et les catégories
Editor -- UC_Manage_Articles
Editor -- UC_Manage_Cats
```

**Dans la description textuelle (`analyse.md`)** :
- **Gérer les articles** :
  - *Auteur* : Peut créer, modifier et supprimer uniquement **ses propres** articles.
  - *Éditeur* : Peut modifier et supprimer **tous** les articles.

---
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

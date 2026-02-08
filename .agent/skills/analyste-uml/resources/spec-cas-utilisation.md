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

## 🎯 Objectif

- **Lisibilité** : Maintenir un diagramme clair et exploitable.
- **Complétude** : Le fichier d'analyse textuelle (`.md`) reste la source de vérité pour les détails.
- **Cohérence** : Appliquer la règle uniformément sur tous les diagrammes du projet.

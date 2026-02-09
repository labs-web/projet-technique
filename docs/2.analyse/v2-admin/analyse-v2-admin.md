# Analyse Fonctionnelle - V2 : Administration (CRUD)

## 1. Introduction
Cette version ajoute la couche administrative sécurisée. Elle permet aux administrateurs de gérer le contenu (articles et catégories) via une interface Back-Office dédiée.

## 2. Acteurs
- **Administrateur** : Super-utilisateur ayant accès à toutes les fonctionnalités de gestion.

## 3. Règles de Gestion (Business Rules)
### Sécurité
- **Accès** : L'accès au Back-Office (/admin) requiert une authentification préalable.
- **Unicité** : Le nom et le slug d'une catégorie doivent être uniques.

### Données
- **Articles** : Un article doit être lié à une catégorie existante.
- **Catégories** : La suppression d'une catégorie ne doit pas être possible si elle contient des articles (ou doit gérer le détachement).

## 4. Fonctionnalités
### Administrateur
- **Authentification sécurisée (Login/Logout)**
- **Gérer les Catégories**
  - Créer une catégorie
  - Lister les catégories
  - Modifier une catégorie
  - Supprimer une catégorie
- **Gérer les Articles**
  - Créer un article
  - Lister les articles
  - Modifier un article
  - Supprimer un article

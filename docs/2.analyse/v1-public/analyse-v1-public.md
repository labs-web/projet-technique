# Analyse Fonctionnelle - V1 : Lecture Publique (MVP)

## 1. Introduction
Cette première version (MVP) pose les bases de l'application Blog. Elle se concentre sur l'accès public au contenu, permettant aux visiteurs non authentifiés de consulter les articles publiés.

## 2. Acteurs
- **Visiteur** : Utilisateur non authentifié accédant à la partie publique du site.

## 3. Règles de Gestion (Business Rules)
### Affichage
- **Pagination** : La liste des articles doit être paginée pour gérer le volume d'affichage.
- **Tri** : L'affichage par défaut est chronologique inverse (plus récent en premier).
- **Contenu** : Le détail d'un article doit inclure le titre, contenu, image, catégorie et auteur.

## 4. Fonctionnalités
### Visiteur
- **Consulter la liste des articles**
- **Consulter le détail d'un article**

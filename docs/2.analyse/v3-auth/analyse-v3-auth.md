# Analyse Fonctionnelle - V3 : Autorisation Native (Policies)

## 1. Introduction
Mise en place des règles métier et des restrictions d'accès basées sur la propriété des ressources. L'objectif est de garantir que chaque auteur ne puisse agir que sur ses propres contenus.

## 2. Acteurs
- **Auteur** : Utilisateur authentifié pouvant gérer ses propres articles.
- **Système** : Entité logique appliquant les règles.

## 3. Règles de Gestion (Business Rules)
### Propriété (Policies)
- **Modification** : Un auteur ne peut modifier que les articles dont il est le créateur.
- **Suppression** : Un auteur ne peut supprimer que les articles dont il est le créateur.
- **Visibilité** : Un auteur ne voit que ses propres articles dans le Back-Office (sauf Admin qui voit tout).

## 4. Fonctionnalités
### Auteur
- **Gérer ses propres articles uniquement** (Liste filtrée, Actions restreintes)

### Système
- **Application des Policies et Gates pour sécuriser les actions**

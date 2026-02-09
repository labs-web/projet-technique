# Analyse Globale : Projet Technique (Blog)

## Introduction

Le Projet Technique est un environnement d'apprentissage permettant de valider les concepts techniques (frameworks, sécurité, interactivité) à travers un système de blog progressif. L'objectif global est de maîtriser le développement web Full Stack en isolant la complexité technique du métier.

---

## Acteurs

- Visiteur
- Utilisateur Connecté
- Auteur
- Éditeur
- Administrateur
- Client API Externe

---

## Fonctionnalités

### Visiteur
- Consulter la page d'accueil
- Consulter la liste des articles
- Consulter le détail d'un article
- Consulter les articles par catégorie
- Rechercher des articles
- S'inscrire
- Se connecter

### Utilisateur Connecté
- Se déconnecter
- Accéder à son profil

### Auteur
- Créer un article
- Modifier ses propres articles
- Supprimer ses propres articles
- Gérer les catégories de ses articles

### Éditeur
- Créer un article
- Modifier tous les articles
- Supprimer tous les articles
- Créer une catégorie
- Modifier une catégorie
- Supprimer une catégorie

### Administrateur
- Gérer les utilisateurs
- Gérer les rôles et permissions
- Accéder au back-office
- Gérer toutes les entités du système

### Client API Externe
- Consulter les articles via API REST
- Consulter les catégories via API REST
- S'authentifier via token
- Accéder aux ressources sécurisées

---

## Règles de Gestion (Business Rules)

Ces règles définissent les contraintes métiers et les permissions spécifiques à chaque acteur.

### RG-01 : Gestion des Catégories
- **Création/Modification/Suppression** : Réservé exclusivement aux acteurs **Éditeur** et **Administrateur**.
- **Utilisation** : L'acteur **Auteur** peut seulement *sélectionner* une catégorie existante lors de la création/modification d'un article. Il ne peut pas en créer de nouvelles.

### RG-02 : Propriété des Articles (Scope)
- **Auteur** :
  - Droit de modification/suppression **uniquement sur ses propres articles** (`user_id` de l'article = `id` de l'auteur).
  - Interdiction formelle de modifier les articles d'autres auteurs.
- **Éditeur** :
  - Droit de modification/suppression sur **tous les articles**, quel que soit l'auteur.
  - Peut modérer, corriger ou censurer n'importe quel contenu.

### RG-03 : Visibilité et Statuts
- **Brouillon** : Un article en cours de rédaction n'est visible que par son **Auteur** et les **Éditeurs** dans le Back-Office. Il n'apparaît pas sur le Front-Office.
- **Publié** : Un article publié est visible par **tous** (Visiteurs inclus) sur le Front-Office.

### RG-04 : Administration Système
- Seul l'**Administrateur** a le pouvoir de :
  - Créer ou supprimer des comptes utilisateurs.
  - Changer le rôle d'un utilisateur (promouvoir un Auteur en Éditeur).
  - Accéder aux logs techniques.

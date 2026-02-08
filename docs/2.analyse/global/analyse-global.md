# Analyse Globale : Projet Technique (Blog Pédagogique)

## 1. Contexte du Projet

**Nature** : Laboratoire d'apprentissage individuel (Bac à sable technique).

**Objectifs** :
- Isoler la complexité technique du métier
- Valider les concepts techniques (N1/N2) avant application au Fil Rouge
- Fournir un environnement d'autonomie pour l'apprenant

**Schéma de Référence** : **Blog** (Users, Articles, Categories)

---

## 2. Acteurs Identifiés

### Visiteur (Public)
Utilisateur non authentifié qui consulte le contenu public du blog.

### Utilisateur Authentifié
Utilisateur ayant un compte et des droits d'accès au Back-Office.

### Administrateur
Utilisateur avec tous les droits de gestion du contenu et des utilisateurs.

### Éditeur (Version 6+)
Utilisateur avec des droits limités (via système RBAC).

### Client API (Version 7)
Application tierce consommant les données via API REST.

---

## 3. Fonctionnalités Globales

### Gestion du Contenu Public
- Afficher la page d'accueil avec liste d'articles
- Lister tous les articles publics
- Afficher le détail d'un article
- Naviguer entre les articles
- Visualiser les catégories associées aux articles

### Gestion Administrative (CRUD)
- Créer un article
- Modifier un article existant
- Supprimer un article
- Lister les articles en mode administration
- Gérer les catégories (Créer, Modifier, Supprimer)
- Assigner des catégories aux articles

### Authentification & Autorisation
- Se connecter au système
- Se déconnecter du système
- Gérer son profil utilisateur
- Vérifier les droits d'accès aux actions (Gates & Policies)
- Appliquer des règles métier (ex: seul le créateur peut modifier)
- Gérer les rôles et permissions en base de données (RBAC)

### Interactivité Utilisateur
- Rechercher des articles instantanément (recherche live)
- Filtrer les articles par catégorie
- Interagir avec des modales
- Utiliser des dropdowns interactifs
- Bénéficier d'une interface réactive

### Exposition des Données (API)
- Consommer les données via API REST JSON
- Authentifier les requêtes API (Sanctum)
- Fournir des endpoints standardisés pour clients tiers

---

## 4. Versions du Projet

Le projet est structuré en **7 versions incrémentales** pour valider progressivement chaque concept technique.

### V1 - Partie Publique (Lecture)
- **Slug** : `v1-public`
- **Branche** : `v1-public`
- **Focus Technique** : Structure de base, Migrations, Seeding, Affichage public
- **Périmètre Fonctionnel** : Home, Liste articles, Détail article (pas d'authentification)

### V2 - Partie Admin (CRUD)
- **Slug** : `v2-admin`
- **Branche** : `v2-admin`
- **Focus Technique** : Back-Office, CRUD complet, Authentification standard
- **Périmètre Fonctionnel** : Gestion articles et catégories (Créer, Lire, Mettre à jour, Supprimer)

### V3 - Autorisation Native (Gates & Policies)
- **Slug** : `v3-auth-native`
- **Branche** : `v3-auth-native`
- **Focus Technique** : Gates, Policies Laravel
- **Périmètre Fonctionnel** : Sécurisation fine des actions (ex: seul le créateur peut modifier)

### V4 - Interactivité Vanilla (AJAX)
- **Slug** : `v4-ajax-vanilla`
- **Branche** : `v4-ajax-vanilla`
- **Focus Technique** : JavaScript Vanilla, AJAX
- **Périmètre Fonctionnel** : Recherche instantanée, Filtrage par catégorie

### V5 - Interactivité Moderne (Alpine.js)
- **Slug** : `v5-alpine`
- **Branche** : `v5-alpine`
- **Focus Technique** : Alpine.js, Composants réactifs
- **Périmètre Fonctionnel** : Refactoring interactivité (Modales, Dropdowns, Recherche Live)

### V6 - Permissions Avancées (Spatie)
- **Slug** : `v6-spatie`
- **Branche** : `v6-spatie`
- **Focus Technique** : Package spatie/laravel-permission, RBAC
- **Périmètre Fonctionnel** : Gestion des rôles (Admin, Éditeur, Lecteur) en base de données

### V7 - API REST
- **Slug** : `v7-api`
- **Branche** : `v7-api`
- **Focus Technique** : API JSON, Laravel Sanctum
- **Périmètre Fonctionnel** : Exposure des données via API sécurisée pour clients tiers

---

## 5. Modèle de Données (Schéma de Référence)

### Entités Principales

**User**
- Auteur ou Administrateur
- Attributs : Nom, Email, Mot de passe, Rôle

**Article**
- Contenu principal du blog
- Attributs : Titre, Contenu, Date, Image, Auteur (User)

**Category**
- Classement du contenu
- Attributs : Nom, Slug
- Note : Utiliser strictement le terme `Category` (pas Tag, pas Label)

### Relations

- `User` **1 -- N** `Article` : Un utilisateur écrit plusieurs articles
- `Article` **N -- N** `Category` : Un article peut avoir plusieurs catégories

---

## 6. Principes Directeurs

### Approche Pédagogique
- Chaque version valide **un concept technique spécifique**
- La progression est **incrémentale** (chaque version s'appuie sur la précédente)
- Le schéma Blog est **universel** et applicable à tous les apprenants

### Philosophie de Validation
- Ce qui est validé ici servira de fondation pour les **projets futurs** (Fil Rouge)
- Viser l'**excellence technique** même en contexte d'apprentissage
- Respecter les **standards des frameworks** (Laravel, Tailwind)

### Contraintes Techniques
- Code en **Anglais** (variables, fonctions, classes)
- Base de données en **Anglais** (snake_case)
- Commits Git en **Français**
- Respect strict de la **stack technique** définie

# 🧪 Projet Technique : Le Laboratoire

## 1. Vision & Objectifs

Le **Projet Technique** est un environnement d'apprentissage individuel (« Bac à sable ») conçu pour :
1.  **Isoler la complexité technique** : Apprendre le framework sans la charge cognitive du métier complexe.
2.  **Valider les concepts** : Chaque concept technique (N1/N2) doit être validé ici avant d'être appliqué sur le Fil Rouge.

L'apprenant réalise ce projet en **autonomie** en suivant les concepts requis.

## 2. Schéma de Données de Référence : Le Blog

Pour garantir une structure universelle, le Projet Technique s'appuie sur le schéma **Blog**.

### Entités
*   **User** : L'auteur ou l'administrateur.
*   **Article** : Le contenu principal (Titre, Contenu, Date, Image, Auteur).
*   **Category** : Le classement (Nom, Slug).
    *   *Note : Utiliser strictement le terme `Category` (pas Tag, pas Label).*

### Relations
*   `User` **1 -- N** `Article` (Un utilisateur écrit plusieurs articles).
*   `Article` **N -- N** `Category` (Un article a plusieurs catégories).

---

## 3. Roadmap de Développement

Le projet est découpé en 7 versions incrémentales pour valider chaque compétence technique progressivement.

### Version 1 : Partie Publique (Lecture)
**Description** : Mise en place de la structure de base, migration de données (Seeding), et affichage public des articles (Home, Liste, Détail). Pas d'authentification requise pour l'accès public.
- **Slug** : `v1-public`
- **Branche** : `v1-public`

### Version 2 : Partie Admin (CRUD)
**Description** : Création du Back-Office. Gestion complète des articles et catégories (Créer, Lire, Mettre à jour, Supprimer) sécurisée par l'authentification standard.
- **Slug** : `v2-admin`
- **Branche** : `v2-admin`

### Version 3 : Autorisation Native (Gates & Policies)
**Description** : Sécurisation fine des actions. Implémentation des règles d'autorisation natives de Laravel via Gates et Policies (ex: "Seul le créateur d'un article peut le modifier").
- **Slug** : `v3-auth-native`
- **Branche** : `v3-auth-native`

### Version 4 : Interactivité Vanilla (AJAX)
**Description** : Dynamisation de l'interface sans framework JS lourd. Implémentation de la recherche instantanée et filtrage par catégorie en AJAX avec JavaScript natif (Vanilla JS).
- **Slug** : `v4-ajax-vanilla`
- **Branche** : `v4-ajax-vanilla`

### Version 5 : Interactivité Moderne (Alpine.js)
**Description** : Refactoring de l'interactivité précédente en adoptant **Alpine.js**. Introduction de composants réactifs déclaratifs (Modales, Dropdowns, Recherche Live) pour un code plus maintenable.
- **Slug** : `v5-alpine`
- **Branche** : `v5-alpine`

### Version 6 : Permissions Avancées (Spatie)
**Description** : Gestion professionnelle des rôles et permissions (RBAC). Intégration du package `spatie/laravel-permission` pour gérer les rôles (Admin, Éditeur, Lecteur) en base de données.
- **Slug** : `v6-spatie`
- **Branche** : `v6-spatie`

### Version 7 : API REST
**Description** : Exposition des données du blog via une API JSON standardisée. Sécurisation des endpoints via Laravel Sanctum pour consommation par des clients tiers (Mobile, SPA externe).
- **Slug** : `v7-api`
- **Branche** : `v7-api`

# Analyse Fonctionnelle Globale

## 1. Acteurs
- **Visiteur** : Utilisateur non authentifié accédant à la partie publique du site.
- **Administrateur** : Super-utilisateur ayant accès à toutes les fonctionnalités de gestion.
- **Auteur** : Utilisateur authentifié pouvant gérer ses propres articles.
- **Système Externe** : Application tierce consommant l'API (Mobile, SPA).

## 2. Fonctionnalités par Domaine

### 2.1. Gestion Publique (Front-Office)
- **Consulter la liste des articles**
    - *Acteur* : Visiteur
    - *Priorité* : P1 (V1)
    - *Règle* : Affichage paginé, tri par défaut (plus récent).
- **Consulter le détail d'un article**
    - *Acteur* : Visiteur
    - *Priorité* : P1 (V1)
    - *Règle* : Affichage du contenu complet, image, catégorie et auteur.
- **Rechercher des articles**
    - *Acteur* : Visiteur
    - *Priorité* : P2 (V4/V5)
    - *Règle* : Recherche interactive (AJAX) sur le titre et le contenu.
- **Filtrer par catégorie**
    - *Acteur* : Visiteur
    - *Priorité* : P2 (V4/V5)
    - *Règle* : Filtrage interactif (AJAX) sans rechargement de page.

### 2.2. Administration (Back-Office)
- **Gérer les catégories (CRUD)**
    - *Acteur* : Administrateur
    - *Priorité* : P1 (V2)
    - *Règle* : Création, Lecture, Modification, Suppression. Nom et Slug uniques.
- **Gérer les articles (CRUD)**
    - *Acteur* : Administrateur, Auteur
    - *Priorité* : P1 (V2)
    - *Règle* : Création, Lecture, Modification, Suppression.
- **Gérer ses propres articles**
    - *Acteur* : Auteur
    - *Priorité* : P2 (V3)
    - *Règle* : Un auteur ne peut modifier/supprimer que les articles dont il est le créateur (Policy).

### 2.3. Sécurité & Permissions
- **Authentification**
    - *Acteur* : Administrateur, Auteur
    - *Priorité* : P1 (V2)
    - *Règle* : Accès sécurisé au Back-Office.
- **Gestion des Rôles (RBAC)**
    - *Acteur* : Administrateur
    - *Priorité* : P3 (V6)
    - *Règle* : Attribution des rôles (Admin, Éditeur, Lecteur).

### 2.4. API REST
- **Exposer les articles**
    - *Acteur* : Système Externe
    - *Priorité* : P3 (V7)
    - *Règle* : Endpoints sécurisés via Sanctum. Format JSON.

## 3. Règles de Gestion Transverses
- **RG-01 (Architecture)** : Séparation claire entre Front-Office (Lecture) et Back-Office (Gestion).
- **RG-02 (UX)** : L'interactivité (Recherche/Filtre) doit être fluide (instantanée).
- **RG-03 (Sécurité)** : Les données sensibles ou actions destructives nécessitent une authentification forte.

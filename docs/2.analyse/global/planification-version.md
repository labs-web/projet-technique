# Planification des Versions - Roadmap du Projet

## Objectif de la Planification
Cette roadmap définit le découpage fonctionnel du projet en versions incrémentales. Chaque version apporte une valeur utilisateur mesurable et constitue une base stable pour la version suivante.

---

## V1 - Public (Consultation de Base)
**Objectif** : Permettre la consultation publique du contenu sans authentification.

**Fonctionnalités Incluses** :
- Affichage de la page d'accueil avec les derniers articles
- Consultation de la liste paginée des articles
- Consultation du détail d'un article complet
- Filtrage des articles par catégorie

**Valeur Utilisateur** : Un visiteur peut découvrir et lire les articles du blog.

**Critères de Réussite** :
- Un visiteur accède au site et voit la liste des articles
- Les articles sont paginés correctement
- Le détail d'un article s'affiche avec son contenu complet
- Les catégories sont cliquables et filtrent les articles

---

## V2 - Recherche
**Objectif** : Enrichir l'expérience de consultation avec une recherche textuelle.

**Fonctionnalités Incluses** :
- Recherche textuelle d'articles (titre/contenu)
- Interactivité sans rechargement de page (AJAX) pour la recherche

**Valeur Utilisateur** : Un visiteur peut trouver rapidement un article par mot-clé.

**Critères de Réussite** :
- La recherche retourne des résultats pertinents en temps réel
- L'expérience est fluide sans rechargement de page

---

## V3 - Authentification
**Objectif** : Sécuriser l'accès au back-office et distinguer les utilisateurs.

**Fonctionnalités Incluses** :
- Authentification sécurisée (Login/Logout)
- Gestion des Rôles : Distinction des droits entre Admin, Éditeur et Lecteur

**Valeur Utilisateur** : Les utilisateurs peuvent s'authentifier et accéder à des fonctionnalités selon leur rôle.

**Critères de Réussite** :
- Un utilisateur peut se connecter et se déconnecter
- Les rôles sont correctement assignés
- L'accès au back-office est protégé

---

## V4 - Gestion Articles (CRUD Auteur)
**Objectif** : Permettre aux auteurs de créer et gérer leurs propres articles.

**Fonctionnalités Incluses** :
- Gestion des Articles (CRUD) :
  - Créer un nouvel article
  - Modifier un article existant
  - Supprimer un article
  - Lister les articles administrables
- Contrôle d'accès : Restreindre la modification/suppression d'un article à son créateur (ou admin)

**Valeur Utilisateur** : Un auteur authentifié peut publier et gérer ses propres contenus.

**Critères de Réussite** :
- Un auteur peut créer, modifier et supprimer ses articles
- Un auteur ne peut pas modifier les articles d'un autre auteur
- Un administrateur peut modifier tous les articles

---

## V5 - Gestion Catégories (CRUD Admin)
**Objectif** : Permettre aux administrateurs de structurer le contenu via les catégories.

**Fonctionnalités Incluses** :
- Gestion des Catégories (CRUD) :
  - Créer une nouvelle catégorie
  - Modifier une catégorie existante
  - Supprimer une catégorie
  - Lister les catégories

**Valeur Utilisateur** : Un administrateur peut organiser le contenu du blog par catégories.

**Critères de Réussite** :
- Un administrateur peut créer, modifier et supprimer des catégories
- Les catégories sont utilisables lors de la création d'articles
- La suppression d'une catégorie gère les articles associés

---

## V6 - Composants Dynamiques (UX Avancée)
**Objectif** : Améliorer l'expérience utilisateur avec des composants interactifs.

**Fonctionnalités Incluses** :
- Utilisation de composants dynamiques (Modales, Dropdowns)
- Interactivité sans rechargement de page (AJAX) pour le filtrage

**Valeur Utilisateur** : L'interface devient plus moderne et réactive.

**Critères de Réussite** :
- Les modales s'ouvrent et se ferment sans rechargement
- Les dropdowns fonctionnent correctement
- Le filtrage par catégorie est fluide (AJAX)

---

## V7 - API REST (Consommation Externe)
**Objectif** : Exposer les données du blog via une API pour des systèmes tiers.

**Fonctionnalités Incluses** :
- Exposition des ressources (Articles, Catégories) via une API JSON
- Authentification API via jetons (Sanctum)

**Valeur Utilisateur** : Un système tiers (ex: application mobile) peut consommer les données du blog.

**Critères de Réussite** :
- L'API REST retourne les articles et catégories au format JSON
- L'authentification par jeton fonctionne correctement
- Les endpoints sont documentés et testables

---

## Synthèse de la Roadmap

| Version | Nom                   | Acteurs Principaux             | Complexité | Dépendances |
| ------- | --------------------- | ------------------------------ | ---------- | ----------- |
| V1      | Public                | Visiteur                       | Faible     | -           |
| V2      | Recherche             | Visiteur                       | Moyenne    | V1          |
| V3      | Authentification      | Utilisateur Authentifié, Admin | Moyenne    | -           |
| V4      | Gestion Articles      | Auteur, Admin                  | Élevée     | V3          |
| V5      | Gestion Catégories    | Admin                          | Moyenne    | V3, V4      |
| V6      | Composants Dynamiques | Visiteur, Utilisateur          | Moyenne    | V1, V2      |
| V7      | API REST              | Système Tiers                  | Élevée     | V1, V3      |

---

## Notes de Priorisation

**Ordre Recommandé d'Implémentation** :
1. **V1** → Valeur immédiate : Consultation publique
2. **V3** → Fondation sécurisée pour les fonctionnalités suivantes
3. **V4** → Cœur métier : Gestion de contenu
4. **V5** → Organisation du contenu
5. **V2** → Amélioration de l'expérience utilisateur
6. **V6** → Raffinement UX
7. **V7** → Extension vers des clients externes

**Justification** :
- V1 et V3 constituent la fondation technique
- V4 et V5 apportent la valeur métier principale
- V2 et V6 améliorent l'expérience utilisateur
- V7 étend les capacités vers l'écosystème externe

# Analyse Fonctionnelle - V6 : Rôles & Permissions (Spatie)

## Description
Introduction d'une hiérarchie stricte entre les utilisateurs pour professionnaliser la gestion du blog. Nous distinguons désormais clairement les "Administrateurs" des simples "Éditeurs".

## Rôles & Responsabilités

### 1. Administrateur (`Admin`)
**En tant que** : Super-User
**Je veux** : Avoir un contrôle total sur le système.
**Afin de** : Modérer le contenu et gérer l'équipe.

- **Permissions** :
  - Peut gérer TOUS les articles (Créer, Modifier, Supprimer n'importe lequel).
  - Peut gérer les Catégories (Créer, Modifier, Supprimer).
  - Peut voir/gérer les autres utilisateurs (Admin Dashboard).

### 2. Éditeur (`Editor`)
**En tant que** : Contributeur contenu
**Je veux** : Gérer mes propres publications.
**Afin de** : Participer au blog sans risquer de casser le travail des autres.

- **Permissions** :
  - Peut créer des articles.
  - Peut modifier/supprimer UNIQUEMENT SES articles.
  - **Interdit** : Ne peut PAS toucher aux catégories.
  - **Interdit** : Ne peut PAS toucher aux articles des autres.

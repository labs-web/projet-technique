# Analyse Fonctionnelle - V3 : Autorisation Native

## Description
Affinage des droits d'accès. Il ne suffit pas d'être connecté pour tout faire. Nous devons nous assurer que chaque utilisateur ne manipule que ce qui lui appartient.

## Règles de Gestion (Permissions)

### 1. Modification d'Article
**Règle** : Un auteur ne peut modifier **que** les articles qu'il a lui-même créés.
**Scénario d'erreur** : Si l'utilisateur A tente d'accéder à l'édition de l'article de l'utilisateur B, l'accès doit être refusé (Page 403 / Interdit).

### 2. Suppression d'Article
**Règle** : Idem. Seul le propriétaire peut supprimer.

### 3. Visibilité dans le Back-Office
**Règle** :
- Dans la liste des articles, les boutons "Modifier" et "Supprimer" ne doivent apparaître que pour les articles dont je suis propriétaire.
- (Optionnel) Un Administrateur global pourrait avoir le droit de tout modifier (réservé pour V6, mais conceptuellement possible ici).

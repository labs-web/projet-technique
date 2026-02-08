# Analyse Fonctionnelle - V5 : Interactivité Moderne (Alpine.js)

## Description
Transition vers une approche plus déclarative et moderne pour gérer le dynamisme de l'interface. En remplaçant le JS impératif complexe par Alpine.js, nous gagnons en lisibilité tout en ajoutant de nouvelles interactions.

## Fonctionnalités Attendues

### 1. Refonte Recherche & Filtre (Alpine)
**En tant que** : Visiteur
**Je veux** : La même expérience fluide que la V4, mais plus stable.
**Afin de** : Naviguer sans effort.

- Le comportement reste identique (recherche instantanée + filtre catégorie), mais doit être reimplanté proprement.

### 2. Menu Déroulant Utilisateur (Dropdown)
**En tant que** : Utilisateur connecté
**Je veux** : Cliquer sur mon nom/avatar pour voir un petit menu "Profil / Déconnexion".
**Afin de** : Accéder rapidement à mes actions personnelles sans changer de page.

- **Comportement** :
  - Clic -> Ouverture du menu.
  - Clic dehors -> Fermeture automatique.
  - Touche Esc -> Fermeture.

### 3. Notifications Flash (Toast)
**En tant que** : Utilisateur
**Je veux** : Voir un petit message de confirmation qui disparaît tout seul après une action (ex: "Article sauvegardé").
**Afin de** : Être rassuré sur le succès de mon opération sans devoir cliquer pour fermer une alerte.

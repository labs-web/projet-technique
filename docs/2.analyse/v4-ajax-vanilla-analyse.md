# Analyse Fonctionnelle - V4 : Interactivité Vanilla (AJAX)

## Description
Amélioration de l'expérience utilisateur sur la partie publique (Lecture). L'objectif est de rendre la navigation plus fluide en évitant les rechargements complets de page lors de la recherche ou du filtrage.

## Fonctionnalités Attendues

### 1. Recherche Instantanée
**En tant que** : Visiteur
**Je veux** : Voir la liste des articles s'actualiser dès que je tape dans la barre de recherche.
**Afin de** : Trouver rapidement un sujet sans valider un formulaire.

- **Interaction** : Frappe au clavier -> Délai (debounce) -> Mise à jour de la liste.
- **Feedback** : Si aucun résultat, afficher un message "Aucun article trouvé".

### 2. Filtrage par Catégorie sans rechargement
**En tant que** : Visiteur
**Je veux** : Cliquer sur une catégorie pour ne voir que les articles concernés, sans que la page ne clignote/recharge.
**Afin de** : Naviguer fluidement d'un sujet à l'autre.

- **Interaction** : Clic sur un bouton catégorie -> Mise à jour de la liste d'articles seulement.

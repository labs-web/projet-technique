# Analyse Fonctionnelle - V1 : Partie Publique

## Description
Cette première version vise à mettre en place le socle du blog et à offrir une interface de lecture pour les visiteurs. Il s'agit uniquement de consulter du contenu, aucune interaction ou authentification n'est requise pour la partie publique.

## Fonctionnalités Attendues

### 1. Page d'Accueil (Liste des Articles)
**En tant que** : Visiteur
**Je veux** : Voir la liste des derniers articles publiés.
**Afin de** : Découvrir le contenu du blog.

- **Affichage** :
  - Liste antéchronologique (du plus récent au plus ancien).
  - Pagination (ex: 10 articles par page) pour ne pas charger trop de contenu.
  - Pour chaque article : Image de couverture, Titre, Extrait (résumé), Nom de l'auteur, Date de publication, et les Catégories associées.

### 2. Page Détail Article
**En tant que** : Visiteur
**Je veux** : Lire un article complet.
**Afin de** : Approfondir un sujet.

- **Accès** : Au clic sur un article depuis l'accueil.
- **Affichage** :
  - Titre principal, Auteur, Date, Catégories.
  - Contenu complet de l'article (texte riche).
  - Bouton ou lien pour revenir à l'accueil.

### 3. Navigation Globale
**En tant que** : Visiteur
**Je veux** : Une barre de navigation simple.
**Afin de** : Me repérer sur le site.

- **Éléments** :
  - Logo ou Nom du Blog (retour accueil).
  - Lien "Accueil".
  - Lien "Connexion" (accès discret vers le futur back-office).

## 4. Diagramme de Cas d'Utilisation

![Diagramme Use Case V1](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/ton-repo/projet-technique/main/docs/2.analyse/v1-public-usecase.puml)
*(Fichier source : `v1-public-usecase.puml`)*


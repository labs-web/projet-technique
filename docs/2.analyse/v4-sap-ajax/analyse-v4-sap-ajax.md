# Analyse Fonctionnelle - V4 : Interactivité AJAX (Native)

## 1. Introduction
Amélioration de l'expérience utilisateur (UX) sur le Front-Office en introduisant des interactions dynamiques sans rechargement de page, utilisant l'API Fetch et Javascript natif.

## 2. Acteurs
- **Visiteur** : Utilisateur utilisant l'interface publique.

## 3. Règles de Gestion (Business Rules)
### Performance & UX
- **Instantanéité** : Les résultats de recherche et de filtre doivent s'afficher dynamiquement dans la page courante.
- **Dégradation gracieuse** : Le site doit rester fonctionnel même si JS est désactivé (fallback non-AJAX).

## 4. Fonctionnalités
### Visiteur
- **Rechercher des articles instantanément** (Saisie dans input texte)
- **Filtrer les articles par catégorie sans rechargement** (Clic sur filtre)

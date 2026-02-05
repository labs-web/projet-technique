# 🧪 Projet Technique : Le Laboratoire

## Vision & Objectifs

Le **Projet Technique** est un environnement d'apprentissage individuel (« Bac à sable ») conçu pour :
1.  **Isoler la complexité technique** : Apprendre le framework sans la charge cognitive du métier complexe.
2.  **Droit à l'erreur** : Tester, casser, refaire sans impacter le projet de groupe.
3.  **Valider les concepts** : Chaque concept technique (N1/N2) doit être validé ici avant d'être appliqué sur le Fil Rouge.

L'apprenant réalise ce projet en **autonomie** en suivant les concepts requis.


## 📐 Schéma de Données de Référence : Le Blog

Pour garantir une structure universelle, le Projet Technique s'appuie sur le schéma **Blog**.

### Entités

*   **User** : L'auteur ou l'administrateur.
*   **Article** : Le contenu principal (Titre, Contenu, Date).
*   **Category** : Le classement (Nom, Slug).
    *   *Note : Utiliser strictement le terme `Category` (pas Tag, pas Label).*

### Relations

*   `User` **1 -- N** `Article` (Un utilisateur écrit plusieurs articles).
*   `Article` **N -- N** `Category` (Un article a plusieurs catégories, une catégorie a plusieurs articles).

---

## 🎯 Liste des Fonctionnalités à Développer

Ce projet sert de support pour développer les fonctionnalités techniques suivantes (détaillées dans les niveaux N1/N2) :

*   **Back-Office (Web)** : CRUD complet, Authentification, Dashboard Admin.
*   **API (JSON)** : Exposition des données pour le mobile, Sécurisation basique.
*   **Front-End (Interaction)** : Recherche AJAX, Filtrage dynamique.
*   **Mobile (Android)** : Consommation API, Affichage Liste/Détail, Mode hors-ligne (Favoris).

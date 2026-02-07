# Action Mapping : Projet Technique

**Date** : 2026-02-07
**Objectif** : Valider les compétences Laravel via la création d'un Blog complet (Back, Front, API).

---

## Liste Brute des Actions

### Fonctionnalité 1 : Socle Technique & Configuration
- [ ] Initialiser le projet Laravel et configurer l'environnement (.env)
- [ ] Installer et configurer Tailwind CSS & Preline UI
- [ ] Configurer la langue par défaut (FR) et les fichiers de traduction
- [ ] Mettre en place la structure des dossiers `app/Services`
- [ ] Créer l'architecture de base du UI-Kit (`resources/views/components/ui/`)

### Fonctionnalité 2 : Base de Données & Modèles
- [ ] Créer la migration pour la table `users`
- [ ] Créer la migration pour la table `categories` (nom, slug)
- [ ] Créer la migration pour la table `articles` (titre, slug, contenu, user_id, status)
- [ ] Créer la table pivot `article_category`
- [ ] Définir les relations Eloquent dans les modèles (User, Article, Category)
- [ ] Créer les Factories et Seeders pour les données de test

### Fonctionnalité 3 : Gestion de Contenu (Back-Office)
- [ ] Créer le Layout Admin (Sidebar, Navbar, Footer)
- [ ] Créer le Dashboard Controller & Vue
- [ ] Implémenter le CRUD Users (Service, Controller, Request, Vue)
- [ ] Implémenter le CRUD Categories (Service, Controller, Request, Vue)
- [ ] Implémenter le CRUD Articles (Service, Controller, Request, Vue)
- [ ] Intégrer la gestion des permissions (Gates/Policies puis Spatie)

### Fonctionnalité 4 : Expérience Utilisateur (Front-End)
- [ ] Créer le Layout Public
- [ ] Créer la page d'accueil (Liste des articles paginée)
- [ ] Créer la page de détail d'un article
- [ ] Créer la page de liste par catégorie
- [ ] Implémenter la recherche dynamique en Vanilla JS (Fetch API)
- [ ] Refactoriser la recherche dynamique avec Alpine.js

### Fonctionnalité 5 : API REST
- [ ] Configurer Laravel Sanctum
- [ ] Créer les API Resources (User, Article, Category)
- [ ] Créer les contrôleurs API (Endpoints lecture & écriture)
- [ ] Sécuriser les routes API via Sanctum (Middlewares)

---

## Actions Transverses

Actions qui s'appliquent à toutes les fonctionnalités :

- [ ] Créer systématiquement les `FormRequest` pour la validationc
- [ ] Passer par le `ui-kit` pour tout nouveau composant graphique (Atome/Molécule)
- [ ] Utiliser le Service Pattern pour isoler la logique métier
- [ ] Documenter le code (PHP Docblocks) et les endpoints API
- [ ] Assurer le respect des normes PSR-12

---

## Notes

- **Priorité UI-Kit** : Ne pas coder de vues "en dur" sans avoir validé les composants dans le UI-Kit.
- **Itérations** : Auth et Recherche sont prévues en 2 temps (Basique -> Avancé).

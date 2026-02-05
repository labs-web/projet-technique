---
description: Workflow Maître pour la création d'interfaces en mode UI-First (Agile).
---

# Workflow : Processus de Développement (UI-First)

Ce workflow privilégie le développement des interfaces visuelles avant la logique métier, garantissant une UX de qualité dès le départ.

## Phase 1 : Fondations Design System
1.  **Configuration Tailwind** :
    - Vérifier `tailwind.config.js` (Couleurs, Polices, Breakpoints).
    - Mettre à jour `resources/css/app.css` (ou `index.css`).
2.  **Tokens Design** :
    - Définir les variables CSS ou extensions Tailwind pour les couleurs (Primary, Secondary, Surface).

## Phase 2 : Création de Composants (Atomique)
1.  **Identification** : Lister les composants nécessaires pour la fonctionnalité (Boutons, Cards, Inputs).
2.  **Développement** :
    - Créer le composant Blade : `php artisan make:component NomComposant`.
    - Styler avec Tailwind CSS (Focus sur l'esthétique et les micro-interactions).
    - Utiliser `generate_image` si besoin pour des assets graphiques.
3.  **Isolation** : Valider le rendu visuel indépendamment.

## Phase 3 : Assemblage des Pages (Vues)
1.  **Layout** : Créer ou mettre à jour le Layout principal (`resources/views/layouts/app.blade.php`).
2.  **Structure** : Créer la vue cible : `resources/views/pages/ma-page.blade.php`.
3.  **Intégration** : Assembler les composants dans la vue.
4.  **Responsive** : Tester et ajuster les breakpoints (Mobile, Tablette, Desktop).

## Phase 4 : Logique Métier (Back-end)
*Une fois l'UI validée :*
1.  **Routing** : Définir la route dans `web.php`.
2.  **Contrôleur** : Créer le contrôleur et la méthode.
3.  **Données** : Passer les vraies données (Models) à la vue à la place des mocks statiques.

## Critères de Qualité (Definition of Done)
- [ ] Le design est cohérent avec le "Look & Feel" premium attendu.
- [ ] Le responsive est fluide sur tous les écrans.
- [ ] Le code HTML est sémantique.
- [ ] Les composants sont réutilisables.

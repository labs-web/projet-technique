# Skills Définis : Projet Technique (Blog Architecture)

**Date** : 2026-02-07

---

## Skill 1 : Expert Configuration Stack (`configurateur-stack`)
**Fichier** : `.agent/skills/configurateur-stack/SKILL.md`

### Périmètre
✅ **Fait** :
- Initialise la structure du projet (Laravel Installer, Git init).
- Configure les outils transverses (Tailwind, Linter, .env).
- Met en place l'échafaudage des dossiers (`app/Services`, `ui-kit/`).
- Crée la documentation technique initiale.

❌ **Ne fait PAS** :
- N'écrit pas de logique métier (sauf exemples).
- Ne crée pas les composants UI détaillés.

### Contrat I/O
**Entrée** : `resources/specs-stack.md`
**Sortie** : Projet Laravel installé, dépôt Git initialisé, `README.md` à jour, `pint` configuré.

---

## Skill 2 : Designer UI Kit (`designer-ui`)
**Fichier** : `.agent/skills/designer-ui/SKILL.md`

### Périmètre
✅ **Fait** :
- Crée les fichiers HTML/CSS statiques dans le dossier `ui-kit/`.
- Développe les composants atomiques (Boutons, Inputs) et moléculaires (Cards, Navbars).
- Valide le rendu visuel (Tailwind) indépendamment de Laravel.

❌ **Ne fait PAS** :
- Ne touche JAMAIS aux fichiers `.blade.php`.
- N'écrit pas de JS complexe (juste des états visuels).

### Contrat I/O
**Entrée** : `resources/specs-ui-kit.md`
**Sortie** : Fichiers HTML valides dans `ui-kit/`, prêts à être intégrés.

---

## Skill 3 : Expert Data (`developpeur-data`)
**Fichier** : `.agent/skills/developpeur-data/SKILL.md`

### Périmètre
✅ **Fait** :
- Crée les Migrations (Schéma BDD).
- Crée les Modèles Eloquent (Relations, Casts).
- Crée les Factories et Seeders.
- Optimise les requêtes (Index, FK).

❌ **Ne fait PAS** :
- N'écrit pas de Services ni de Contrôleurs.
- Ne valide pas les données entrantes (HTTP).

### Contrat I/O
**Entrée** : `resources/specs-schema.md`
**Sortie** : Fichiers `database/migrations/*`, `app/Models/*`, `database/seeders/*`.

---

## Skill 4 : Expert Métier (`developpeur-business`)
**Fichier** : `.agent/skills/developpeur-business/SKILL.md`

### Périmètre
✅ **Fait** :
- Implémente les Services (`app/Services/*`).
- Contient toute la logique métier (Business Logic).
- Définit les Policies/Gates (Règles d'autorisation métier).
- Utilise les Modèles pour manipuler les données.

❌ **Ne fait PAS** :
- Ne connait pas HTTP (pas de `Request`, pas de `Response`, pas de `View`).
- Ne gère pas la validation de format (c'est le rôle du FormRequest).

### Contrat I/O
**Entrée** : `resources/specs-business.md`
**Sortie** : Fichiers `app/Services/*`, `app/Policies/*`.

---

## Skill 5 : Expert HTTP (`developpeur-http`)
**Fichier** : `.agent/skills/developpeur-http/SKILL.md`

### Périmètre
✅ **Fait** :
- Déclare les Routes (`web.php`, `api.php`).
- Crée les Contrôleurs (Web & API).
- Crée les FormRequests (Validation des entrées).
- Crée les API Resources (Formatage sortie JSON).
- Appelle les Services pour l'exécution.
- Retourne les Vues ou le JSON.

❌ **Ne fait PAS** :
- N'écrit AUCUNE logique métier dans les contrôleurs.
- N'écrit pas de requêtes Eloquent complexes (délégué au Service/Model).

### Contrat I/O
**Entrée** : `resources/specs-http.md`
**Sortie** : Fichiers `app/Http/Controllers/*`, `app/Http/Requests/*`, `routes/*`.

---

## Skill 6 : Développeur Frontend JS (`developpeur-frontend`)
**Fichier** : `.agent/skills/developpeur-frontend/SKILL.md`

### Périmètre
✅ **Fait** :
- Intégre le HTML du `ui-kit` dans les fichiers `.blade.php`.
- Ajoute la couche interactive (Alpine.js, Vanilla JS).
- Gère les appels AJAX (Fetch) vers l'API interne.
- Dynamise les composants (Modales, Dropdowns).

❌ **Ne fait PAS** :
- Ne crée pas le design system (utilise l'existant).
- Ne touche pas au Backend (sauf pour lire les variables injectées).

### Contrat I/O
**Entrée** : `resources/specs-frontend.md`
**Sortie** : Fichiers `resources/views/*` et `resources/js/*` fonctionnels.

---

## Récapitulatif

**Total Skills définis** : 6
**Skills critiques** : Le trio `developpeur-data` / `developpeur-business` / `developpeur-http` assure la séparation des préoccupations (3-Tiers).
**Flux de production** : `Designer` -> `Data` -> `Business` -> `HTTP` -> `Frontend`.

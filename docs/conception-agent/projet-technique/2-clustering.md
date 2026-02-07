# Clustering : Projet Technique

**Date** : 2026-02-07

---

## Tableau de Clustering par Casquettes

| Groupe (Casquette)         | Actions Identifiées                                                                        | Skill Déduit   | Critère de Décision                                                |
| :------------------------- | :----------------------------------------------------------------------------------------- | :------------- | :----------------------------------------------------------------- |
| **Socle Technique**        | Initialisation Laravel, Config .env, Install Tailwind/Preline, Langues, Structure dossiers | `lead-dev`     | Définit les **fondations** et la configuration globale             |
| **Données / Architecture** | Migrations (Users, Cats, Articles), Relations Eloquent, Factories, Seeders                 | `db-architect` | Structure la **persistance** et les relations de données           |
| **UI & Intégration**       | UI-Kit, Layouts (Admin/Public), Vues Blade (Pages & Composants)                            | `ui-designer`  | Produit le **rendu visuel** (HTML/CSS) et l'expérience utilisateur |
| **Logique Backend & API**  | Services, Controllers, FormRequests, Permissions, API Resources, Sanctum                   | `backend-dev`  | Implémente la **logique métier**, la sécurité et les endpoints     |
| **Interactivité Front**    | Recherche AJAX (Vanilla), Filtrage dynamique (Alpine.js)                                   | `frontend-dev` | Gère le **comportement dynamique** côté client                     |

---

## Règle d'Or Appliquée

> Si deux actions ne peuvent PAS être faites par la même personne sans changer de contexte mental → **Skills différents**.

Exemple : 
- Créer une maquette HTML/CSS (`ui-designer`) vs Coder la logique d'un Service PHP (`backend-dev`).
- Définir un schéma de BDD (`db-architect`) vs Coder une interaction JS (`frontend-dev`).

---

## Questions de Validation

Pour chaque groupe identifié :

1. **Quel est le livrable ?**
   - `lead-dev` : Répo git initialisé, Config files.
   - `db-architect` : Migrations, Models.
   - `ui-designer` : Fichiers Blade, UI-Kit.
   - `backend-dev` : Classes PHP (Services, Controllers), Routes.
   - `frontend-dev` : Scripts JS, Composants Alpine.

2. **Quelle expertise requiert cette action ?**
   - `lead-dev` : DevOps, Conf.
   - `db-architect` : SQL, Eloquent.
   - `ui-designer` : CSS, UX/UI.
   - `backend-dev` : PHP, OOP, API REST.
   - `frontend-dev` : JS, DOM.

3. **À quel moment du cycle intervient-elle ?**
   - `lead-dev` : Au début (Setup).
   - `db-architect` : Avant le dev fonctionnel.
   - `ui-designer` : En parallèle ou avant le backend.
   - `backend-dev` : Cœur du développement.
   - `frontend-dev` : En fin de cycle (dynamisation).

---

## Notes

- **Separation of Concerns** : Séparation stricte entre le rendu (`ui-designer`) et la logique (`backend-dev`) pour respecter le MVC.
- **API First** : Le `backend-dev` couvre aussi bien les contrôleurs Web que API, car la logique métier (Service) est partagée.

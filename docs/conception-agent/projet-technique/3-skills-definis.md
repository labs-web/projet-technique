# Skills Définis : Projet Technique

**Date** : 2026-02-07

---

## Skill 1 : lead-dev

**Fichier** : `.agent/skills/lead-dev/SKILL.md`

### Périmètre
✅ **Fait** :
- Initialisation du projet Laravel (nouveau ou existant).
- Configuration de l'environnement (`.env`, `config/`).
- Installation des paquets NPM/Composer (Tailwind, Preline, etc.).
- Mise en place de la structure des dossiers (Services, Traits, etc.).
- Gestion de la localisation (fichiers `lang/`).

❌ **Ne fait PAS** :
- Création de migrations BDD complexes (délégué à `db-architect`).
- Développement de fonctionnalités métier (délégué à `backend-dev`).
- Design UI (délégué à `ui-designer`).

### Contrat I/O
**Entrée** : `resources/instructions.md` (Contexte & Config).
**Sortie** : Projet Laravel fonctionnel, configuré et prêt à être développé.

### Critères de Validation
- [ ] Atomicité : Une seule responsabilité (Infrastructure/Config).
- [ ] Autonomie : Ne dépend pas du code métier.
- [ ] Testabilité : Le projet se lance (`serve`, `npm run dev`).
- [ ] Réutilisabilité : Utilisable pour tout projet Laravel.

---

## Skill 2 : db-architect

**Fichier** : `.agent/skills/db-architect/SKILL.md`

### Périmètre
✅ **Fait** :
- Création des fichiers de Migration.
- Définition des Modèles Eloquent (Relations, Casts, Mutators).
- Création des Factories et Seeders.
- Optimisation du schéma (Index, Foreign Keys).

❌ **Ne fait PAS** :
- Logique métier dans les contrôleurs (délégué à `backend-dev`).
- Validation des données utilisateur (délégué à `backend-dev`).

### Contrat I/O
**Entrée** : `resources/instructions.md` (Schéma & Règles).
**Sortie** : Fichiers Migrations, Models, Factories, Seeders.

### Critères de Validation
- [ ] Atomicité : Focus uniquement sur la structure des données.
- [ ] Autonomie : Peut être exécuté avant le dev Back/Front.
- [ ] Testabilité : Les migrations s'exécutent sans erreur.
- [ ] Réutilisabilité : Adaptable à tout schéma relationnel.

---

## Skill 3 : ui-designer

**Fichier** : `.agent/skills/ui-designer/SKILL.md`

### Périmètre
✅ **Fait** :
- Création et maintenance du `ui-kit`.
- Développement des Composants Blade (Atomes, Molécules).
- Création des Layouts (Admin, Public).
- Intégration HTML/CSS (Tailwind) des pages complètes.

❌ **Ne fait PAS** :
- Logique PHP complexe (délégué à `backend-dev`).
- Javascript interactif (délégué à `frontend-dev`).
- Appels BDD directs depuis les vues.

### Contrat I/O
**Entrée** : `resources/instructions.md` (Maquettes & Specs UI).
**Sortie** : Fichiers Blade (`resources/views`), `ui-kit`, CSS compilé.

### Critères de Validation
- [ ] Atomicité : Focus sur le rendu visuel.
- [ ] Autonomie : Indépendant de la logique métier (données mockées).
- [ ] Testabilité : Rendu visuel conforme et responsive.
- [ ] Réutilisabilité : Composants génériques réutilisables.

---

## Skill 4 : backend-dev

**Fichier** : `.agent/skills/backend-dev/SKILL.md`

### Périmètre
✅ **Fait** :
- Implémentation des Services (Logique Métier).
- Création des Contrôleurs (Web & API).
- Validation des données (`FormRequest`).
- Gestion de la sécurité (Auth, Policies, Gates).
- Exposition des API Resources.

❌ **Ne fait PAS** :
- Modification du schéma BDD (délégué à `db-architect`).
- Création de vues Blade (délégué à `ui-designer`).
- Scripts JS côté client (délégué à `frontend-dev`).

### Contrat I/O
**Entrée** : `resources/instructions.md` (Specs API & Métier), Vues Blade, Modèles.
**Sortie** : Code PHP fonctionnel, Endpoints API testés.

### Critères de Validation
- [ ] Atomicité : Focus sur le comportement serveur.
- [ ] Autonomie : Utilise les contrats d'interface (Models, Vues).
- [ ] Testabilité : Tests unitaires/fonctionnels passants.
- [ ] Réutilisabilité : Architecture MVC/Service standard.

---

## Skill 5 : frontend-dev

**Fichier** : `.agent/skills/frontend-dev/SKILL.md`

### Périmètre
✅ **Fait** :
- Dynamisation des pages (Alpine.js, Vanilla JS).
- Appels AJAX (Fetch API) vers le Backend.
- Gestion des événements DOM.
- Manipulation de l'état local du navigateur.

❌ **Ne fait PAS** :
- Changement du HTML structurel (délégué à `ui-designer`).
- Logique métier critique (délégué à `backend-dev`).

### Contrat I/O
**Entrée** : `resources/instructions.md` (Interactions & Scripts), Pages HTML.
**Sortie** : Fichiers JS, Comportements interactifs.

### Critères de Validation
- [ ] Atomicité : Focus sur l'interactivité client.
- [ ] Autonomie : Se greffe sur le DOM existant.
- [ ] Testabilité : Interactions fonctionnelles sans rechargement.
- [ ] Réutilisabilité : Scripts modulaires.

---

## Récapitulatif

**Total Skills définis** : 5
**Skills réutilisés** : Aucun (Création ad-hoc pour le Lab, potentiellement promus en global plus tard).
**Skills à créer pour ce projet** : `lead-dev`, `db-architect`, `ui-designer`, `backend-dev`, `frontend-dev`.

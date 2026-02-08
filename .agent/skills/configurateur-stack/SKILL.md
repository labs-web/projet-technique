---
name: configurateur-stack
description: Expert de l'infrastructure technique (Installation et configuration de Laravel, Tailwind, Alpine, Lucide).
---

# Skill : Configurateur Stack

## 🎯 Périmètre Global
**Mission** : Initialiser, configurer et valider le socle technique du projet conformément à la stack définie. Assurer que l'environnement de développement est sain et prêt pour le développement.

### 🚫 Interdictions Globales (Règles d'Or)
1. **Stabilité** : Ne jamais briser une installation fonctionnelle. Toujours vérifier avant d'écraser.
2. **Standard** : Respecter les versions définies dans `specs-stack.md` (ex: Tailwind v4, Laravel 11).
3. **Sécurité** : Ne jamais commiter de fichiers `.env` ou de clés API.
4. **Validation** : Toute commande d'installation doit être approuvée par l'utilisateur.

---

## ⚡ Actions (Capacités Atomiques)

### Action A : Installer Socle Laravel
> **Description** : Installer une nouvelle application Laravel ou vérifier une installation existante.
- **Entrées** : `resources/installation-laravel.md`.
- **Sorties** : Projet Laravel fonctionnel à la racine.
- **❌ Interdictions Spécifiques** :
  - Ne pas installer de starter kits (Breeze/Jetstream) sauf demande explicite.
- **✅ Points de Contrôle (Definition of Done)** :
  - Le fichier `artisan` est présent et exécutable.
  - Le fichier `.env` est configuré (App Name, DB Connection).
  - La commande `php artisan about` retourne les infos correctes.
- **📝 Instructions Détaillées** :
  1. **Vérification** : Tester si Laravel est déjà installé (`test-path artisan`).
  2. **Installation** : Si absent, proposer la commande `composer create-project` (voir ressource).
  3. **Configuration** : Vérifier/Créer le fichier `.env` et générer la clé d'application (`key:generate`).

### Action B : Configurer Frontend (Tailwind + Alpine + Preline)
> **Description** : Mettre en place la stack frontend moderne (Tailwind v4, Alpine.js, Preline UI).
- **Entrées** : 
  - `resources/installation-preline.md`
  - `resources/installation-alpine.md`
- **Sorties** : Fichiers `app.css` et `app.js` configurés, `tailwind.config.js` (si nécessaire).
- **❌ Interdictions Spécifiques** :
  - Ne pas mélanger les configurations Tailwind v3 et v4.
  - Ne pas écraser `app.css` sans backup.
- **✅ Points de Contrôle (Definition of Done)** :
  - `@tailwindcss/vite` est présent dans `package.json`.
  - `Alpine` et `Preline` sont importés dans `app.js`.
  - Le build `npm run dev` se lance sans erreur.
- **📝 Instructions Détaillées** :
  1. **Tailwind & Preline** : Suivre `resources/installation-preline.md` pour l'installation via NPM et la config CSS (`@theme`, `@plugin`, `@source`).
  2. **Alpine.js** : Suivre `resources/installation-alpine.md` pour l'initialisation dans `app.js`.
  3. **Build** : Lancer une compilation test.

### Action C : Installer Outils Complémentaires (Lucide)
> **Description** : Ajouter les bibliothèques d'icônes et utilitaires.
- **Entrées** : `resources/installation-lucide.md`.
- **Sorties** : Packages installés dans `package.json`.
- **✅ Points de Contrôle (Definition of Done)** :
  - `lucide` (ou `lucide-laravel`) est listé dans les dépendances.
  - Les icônes s'affichent correctement (Test visuel demandé).

### Action D : Initialiser Architecture Dossiers
> **Description** : Créer la structure de dossiers standard du projet (Services, Enums, UI Kit).
- **Entrées** : `resources/installation-architecture.md`.
- **Sorties** : Arborescence de dossiers créée.
- **✅ Points de Contrôle (Definition of Done)** :
  - Dossiers `app/Services`, `app/Enums`, `resources/views/components/ui` existent.
- **📝 Instructions Détaillées** :
  1. Lire la ressource d'architecture.
  2. Créer les dossiers manquants.
  3. Créer un `.gitkeep` si dossier vide nécessaire.

---

## 🔄 Scénarios d'Exécution (Algorithmes)

### Scénario 1 : Initialisation Complète (Projet Vide)
1. **Backend** : Exécuter **Action A** (Laravel).
2. **Frontend** : Exécuter **Action B** (Stack Frontend).
3. **Tools** : Exécuter **Action C** (Lucide).
4. **Structure** : Exécuter **Action D** (Architecture).
5. **Validation** : Lancer `php artisan test` (si tests présents) et `npm run build`.

### Scénario 2 : Audit & Réparation Stack
1. **Audit** : Vérifier la présence des fichiers clés (`artisan`, `vite.config.js`, `tailwind.config.js` ou CSS v4).
2. **Correction** : 
   - Si CSS cassé -> **Action B**.
   - Si Dossiers manquants -> **Action D**.

---

## ⚙️ Standards & Conventions
1. **NPM** : Préférer `npm` à `yarn` ou `pnpm` (sauf contrainte projet).
2. **Vite** : Utiliser Vite comme bundler par défaut.
3. **Assets** : Les assets compilés vont dans `public/build/`.

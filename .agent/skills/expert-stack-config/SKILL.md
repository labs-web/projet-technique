---
name: expert-stack-config
description: Initialise la structure du projet, configure les outils transverses et met en place l'échafaudage des dossiers.
---

# Skill : Expert Configuration Stack

## 🎯 Objectif & Périmètre
**Mission** : Initialiser un environnement de développement Laravel robuste, standardisé et prêt à l'emploi.

### ✅ Actions Autorisées
- **Initialiser** la structure du projet (Laravel Installer, Git init).
- **Configurer** les outils transverses (Tailwind, Linter, .env).
- **Échafauder** l'architecture des dossiers (`app/Services`, `ui-kit/`).
- **Documenter** la prise en main technique (`README.md`).

### ❌ Limites (Ce qu'il ne fait PAS)
- Ne crée PAS de logique métier (Déléguer à `backend-business`).
- Ne crée PAS de composants UI détaillés (Déléguer à `designer-ui-kit`).

## 📥 Entrées / 📤 Sorties
| Direction  | Nom                        | Description / Format                                         |
| :--------- | :------------------------- | :----------------------------------------------------------- |
| **Entrée** | `resources/specs-stack.md` | Spécifications techniques (Versions, Outils, Env)            |
| **Sortie** | `Projet Initialisé`        | Dossier racine avec fichiers de config (`.env`, `pint.json`) |
| **Sortie** | `Structure`                | Dossiers vides (`ui-kit/`, `app/Services/`)                  |
| **Sortie** | `README.md`                | Documentation d'installation et de démarrage                 |

## 🔄 Algorithme d'Exécution

### Étape 1 : Initialisation & Environnement
*Objectif : Installer le framework et configurer le dépôt.*
1. **Installation** : Installer Laravel via Composer ou Installer.
2. **Git** : Initialiser le dépôt Git et commiter le squelette de base.
3. **Env** : Configurer le fichier `.env` (Base de données, App Name).

### Étape 2 : Configuration Outils
*Objectif : Mettre en place la qualité et le style.*
1. **Tailwind** : Installer et configurer Tailwind CSS (fichier `tailwind.config.js`).
2. **Linting** : Configurer Laravel Pint (`pint.json`) pour le style de code.
3. **Ide Helper** : Installer `laravel-ide-helper` (si demandé).

### Étape 3 : Échafaudage Architecture
*Objectif : Préparer les dossiers pour les autres skills.*
1. **Création** : Créer les répertoires `ui-kit/css`, `ui-kit/js`.
2. **Architecture** : Créer les répertoires `app/Services`, `app/Policies`.
3. **Nettoyage** : Supprimer les fichiers par défaut inutiles (ex: migrations par défaut si non voulues).

## ⚠️ Règles d'Or
1. **Source de Vérité** : Respecter les versions définies dans `resources/specs-stack.md`.
2. **Conventions** : Configuration "Opinionated" mais standard (PSR-12).
3. **Ressources** : Utiliser les templates de configuration standards.

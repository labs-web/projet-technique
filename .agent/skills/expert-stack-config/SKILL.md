---
name: expert-stack-config
description: Initialise la structure du projet, configure les outils transverses et met en place l'échafaudage des dossiers.
---

# Skill : Expert Configuration Stack

## 🎯 Objectif & Périmètre
**Mission** : Installer et configurer de manière granulaire les technologies du stack technique Laravel.

### ✅ Actions Autorisées
- **Installer** Laravel Backend dans le dossier `app/`.
- **Installer** Tailwind CSS et Preline UI.
- **Installer** Alpine.js pour l'interactivité front-end.
- **Configurer** MySQL (création de base de données).
- **Installer** Laravel Pint et IDE Helper (outils de qualité).
- **Créer** l'architecture des dossiers (Services, Policies, ui-kit).
- **Initialiser** Git avec un commit initial.
- **Documenter** la prise en main technique.

### ❌ Limites (Ce qu'il ne fait PAS)
- Ne crée PAS de logique métier (Déléguer à `backend-business`).
- Ne crée PAS de composants UI détaillés (Déléguer à `designer-ui-kit`).

## 📥 Entrées / 📤 Sorties

- **Entrée** : `Action` (Nom de l'action à exécuter : laravel, tailwind, alpine, mysql, pint, architecture, git)
- **Entrée** : Fichier `resources/specs-*.md` correspondant à l'action
- **Sortie** : Technologie installée et configurée
- **Sortie** : Rapport de validation

## 🔄 Algorithme d'Exécution

⚠️ **IMPORTANT** : Chaque action est indépendante. Le développeur choisit quelle(s) technologie(s) installer.

---

### Action 1 : Installer Laravel Backend
*Objectif : Installer Laravel dans le dossier `app/`.*

1. **Lecture** : Charger `resources/specs-laravel.md`.
2. **Présentation** : Afficher au développeur la version Laravel qui sera installée.
3. **Proposition** : Afficher la commande `composer create-project`.
4. **Attendre** : Validation du développeur.
5. **Exécution** : Lancer la commande après approbation (SafeToAutoRun=false).
6. **Configuration .env** : Proposer les modifications du fichier `.env` selon `specs-laravel.md`.
7. **Attendre** : Validation du développeur.
8. **Modification** : Appliquer les valeurs dans `app/.env`.
9. **Post-Installation** : Proposer `php artisan key:generate`.

**Validation** : Laravel installé et configuré.

---

### Action 2 : Installer Tailwind CSS
*Objectif : Installer et configurer Tailwind CSS.*

1. **Lecture** : Charger `resources/specs-tailwind.md`.
2. **Proposition** : Afficher les commandes d'installation npm.
3. **Attendre** : Validation du développeur.
4. **Exécution** : Lancer les commandes.
5. **Configuration** : Appliquer la configuration `tailwind.config.js` selon `specs-tailwind.md`.
6. **CSS** : Modifier `app/resources/css/app.css` avec les directives Tailwind.
7. **Preline UI** : Proposer l'installation de Preline.
8. **Attendre** : Validation du développeur.
9. **Exécution** : Installer Preline.

**Validation** : Tailwind CSS et Preline UI installés.

---

### Action 3 : Installer Alpine.js
*Objectif : Installer Alpine.js pour l'interactivité.*

1. **Lecture** : Charger `resources/specs-alpine.md`.
2. **Proposition** : Afficher la commande `npm install alpinejs`.
3. **Attendre** : Validation du développeur.
4. **Exécution** : Lancer la commande.
5. **Configuration** : Appliquer l'intégration dans `app/resources/js/app.js` selon `specs-alpine.md`.

**Validation** : Alpine.js installé et intégré.

---

### Action 4 : Configurer MySQL
*Objectif : Créer la base de données MySQL.*

1. **Lecture** : Charger `resources/specs-mysql.md`.
2. **Présentation** : Afficher les paramètres de connexion.
3. **Proposition** : Afficher le script SQL de création de base.
4. **Attendre** : Validation du développeur.
5. **Instructions** : Demander au développeur d'exécuter le script SQL manuellement.

**Validation** : Base de données créée.

---

### Action 5 : Installer Laravel Pint
*Objectif : Installer le linter de code.*

1. **Lecture** : Charger `resources/specs-pint.md`.
2. **Proposition** : Afficher la commande `composer require laravel/pint --dev`.
3. **Attendre** : Validation du développeur.
4. **Exécution** : Lancer la commande.
5. **Configuration** : Créer `app/pint.json` avec la configuration spécifiée dans `specs-pint.md`.

**Validation** : Laravel Pint installé et configuré.

---

### Action 6 : Créer Architecture Dossiers
*Objectif : Échafauder l'arborescence.*

1. **Lecture** : Charger `resources/specs-architecture.md`.
2. **Proposition** : Afficher les commandes de création de dossiers.
3. **Attendre** : Validation du développeur.
4. **Exécution** : Créer les dossiers selon les commandes spécifiées.

**Validation** : Architecture créée.

---

### Action 7 : Initialiser Git
*Objectif : Créer le dépôt Git.*

1. **Lecture** : Charger `resources/specs-architecture.md` (section Git).
2. **Proposition** : Afficher les commandes `git init`, `git add .`, `git commit`.
3. **Attendre** : Validation du développeur.
4. **Exécution** : Lancer les commandes.

**Validation** : Dépôt Git initialisé.

---

## ⚠️ Règles d'Or

1. **Source de Vérité** : Les fichiers `resources/specs-*.md` contiennent TOUTES les commandes et configurations.
2. **Granularité** : Chaque action est indépendante et peut être appelée séparément.
3. **Pas de Duplication** : Le SKILL référence les fichiers specs, il ne répète JAMAIS le contenu.
4. **Conventions** : Configuration "Opinionated" mais standard (PSR-12).
5. **⚠️ VALIDATION OBLIGATOIRE** : Ce skill exécute des commandes système destructives. **CHAQUE commande doit être proposée au développeur et nécessite son approbation EXPLICITE avant exécution**. Ne JAMAIS utiliser `SafeToAutoRun=true`.

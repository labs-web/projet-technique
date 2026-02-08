---
name: expert-stack-config
description: Guide et initialise la structure du projet, vérifie et valide les installations techniques (Laravel, Tailwind, Alpine).
---

# Skill : expert-stack-config

## 🎯 Objectif & Périmètre
**Mission** : Guider le développeur dans l'initialisation du stack technique et valider la conformité de l'environnement.
**Philosophie** : Privilégier l'installation manuelle guidée par l'IA et la vérification de l'existant.

### ✅ Actions Autorisées
- **Guider** l'installation de Laravel Backend (Simple affichage de la commande).
- **Vérifier** et **Compléter** l'installation de Tailwind CSS (Si déjà présent, ne rien faire sauf si demandé).
- **Installer** Alpine.js pour l'interactivité front-end (Si absent).
- **Créer** l'architecture des dossiers (Services, Policies, ui-kit).

### ❌ Limites (Ce qu'il ne fait PAS)
- Ne crée PAS de logique métier.
- Ne crée PAS de composants UI détaillés.
- N'installe PAS MySQL (Action obsolète).
- N'installe PAS Pint (Action obsolète).
- N'initialise PAS Git (À faire manuellement).

## 📥 Entrées / 📤 Sorties

- **Entrée** : `Action` (Nom de l'action à exécuter : laravel, tailwind, alpine, architecture)
- **Sortie** : Plan de modification validé ou instructions manuelles.

## 🔄 Algorithme d'Exécution

⚠️ **RÈGLE CRITIQUE** : Avant toute modification de fichier ou exécution de commande, **AFFICHER UN PLAN DE MODIFICATION DÉTAILLÉ** et attendre la **VALIDATION EXPLICITE** du développeur.

---

### Action 1 : Install Laravel (Mode Manuel)
*Objectif : Fournir la commande pour installer Laravel.*

1. **Vérification** : Vérifier si le dossier `app` contient déjà un projet Laravel.
   - *Si présent* : Afficher "Laravel est déjà installé."
   - *Si absent* :
     1. **Lecture** : Charger `resources/specs-laravel.md`.
     2. **Instruction** : Afficher la commande d'installation et attendre la confirmation d'exécution manuelle.

**Validation** : Projet Laravel présent.

---

### Action 2 : Setup Tailwind CSS
*Objectif : Vérifier et finaliser l'installation de Tailwind (ajout Preline UI).*

1. **Vérification** : Analyser `package.json`, `tailwind.config.js` et `app.css`.
2. **Plan de Modification** :
   - Si tout est conforme : Afficher "Configuration validée."
   - Si incomplet (ex: manque Preline) :
     1. **Lister** les actions prévues (ex: `npm install preline`, modif `tailwind.config.js`).
     2. **Lister** les fichiers qui seront modifiés.
     3. **STOP** : Attendre la validation formelle du plan par le développeur.
3. **Exécution** : Appliquer les modifications uniquement après validation.

**Validation** : Pipeline CSS opérationnel.

---

### Action 3 : Install Alpine.js
*Objectif : Ajouter l'interactivité.*

1. **Vérification** : Vérifier `package.json`.
2. **Plan de Modification** :
   - Si manquant :
     1. **Lister** la commande `npm install`.
     2. **Montrer** le code à ajouter dans `app.js`.
     3. **STOP** : Attendre la validation formelle.
3. **Exécution** : Installer et configurer.

**Validation** : Alpine.js intégré.

---

### Action 4 : Architecture Dossiers
*Objectif : Créer l'arborescence complémentaire.*

1. **Lecture** : Charger `resources/specs-architecture.md`.
2. **Plan de Modification** :
   - **Lister** tous les dossiers qui seront créés.
   - **STOP** : Attendre la validation formelle.
3. **Exécution** : Créer les dossiers.

**Validation** : Structure complète.

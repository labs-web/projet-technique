---
name: configurateur-stack
description: Guide et initialise la structure du projet, vérifie et valide les installations techniques (Laravel, Tailwind, Alpine, Lucide).
---

# Skill : configurateur-stack

## 🎯 Objectif & Périmètre
**Mission** : Guider le développeur dans l'initialisation du stack technique et valider la conformité de l'environnement.
**Philosophie** : Privilégier l'installation manuelle guidée par l'IA et la vérification de l'existant.

### ✅ Actions Autorisées
- **Guider** l'installation de Laravel Backend (Simple affichage de la commande).
- **Vérifier** et **Compléter** l'installation de Tailwind CSS (Si déjà présent, ne rien faire sauf si demandé).
- **Installer** Alpine.js pour l'interactivité front-end (Si absent).
- **Installer** Lucide Icons.
- **Créer** l'architecture des dossiers (Services, Policies, ui-kit).

### ❌ Limites (Ce qu'il ne fait PAS)
- Ne crée PAS de logique métier.
- Ne crée PAS de composants UI détaillés.
- N'installe PAS MySQL (Action obsolète).
- N'installe PAS Pint (Action obsolète).
- N'utilise PAS de composants Blade personnalisés (Préférer les Partials `@include`).
- N'initialise PAS Git (À faire manuellement).

## 📥 Entrées / 📤 Sorties

- **Entrée** : `Action` (Nom de l'action à exécuter : laravel, tailwind, alpine, architecture)
- **Sortie** : Plan de modification validé ou instructions manuelles.

## 🔄 Algorithme d'Exécution

⚠️ **RÈGLE CRITIQUE** : Avant toute modification de fichier ou exécution de commande, **AFFICHER UN PLAN DE MODIFICATION DÉTAILLÉ** et attendre la **VALIDATION EXPLICITE** du développeur.

---

### Action 1 : Install Laravel
*Objectif : Fournir la commande pour installer Laravel.*

1. **Lecture** : Charger `resources/installation-laravel.md`.
2. **Vérification** : Effectuer les vérifications indiquées dans le fichier de ressources.
3. **Plan de Modification** :
   - Si manquant, afficher la commande d'installation décrite dans le fichier.
   - **STOP** : Attendre validation formelle.
4. **Validation** : Projet Laravel présent.

---

### Action 2 : Setup Preline UI
*Objectif : Installer Preline UI sur une installation Tailwind existante.*

1. **Lecture** : Charger `resources/installation-preline.md`.
2. **Vérification** : Effectuer les vérifications indiquées dans le fichier de ressources.
3. **Plan de Modification** :
   - Si manquant ou incomplet, proposer les actions d'installation et configuration décrites dans le fichier.
   - **STOP** : Attendre validation formelle.
4. **Exécution** : Appliquer les modifications validées.

**Validation** : Preline UI installé et configuré selon les specs.

---

### Action 3 : Install Alpine.js
*Objectif : Ajouter l'interactivité.*

1. **Lecture** : Charger `resources/installation-alpine.md`.
2. **Vérification** : Effectuer les vérifications indiquées dans le fichier de ressources.
3. **Plan de Modification** :
   - Si manquant ou incomplet, proposer les actions d'installation et configuration décrites dans le fichier.
   - **STOP** : Attendre validation formelle.
4. **Exécution** : Appliquer les modifications validées.

**Validation** : Alpine.js intégré selon les specs.

---

### Action 4 : Architecture Dossiers
*Objectif : Créer l'arborescence complémentaire.*

1. **Lecture** : Charger `resources/installation-architecture.md`.
2. **Plan de Modification** :
   - Identifier les dossiers manquants selon le fichier chargé.
   - **STOP** : Attendre validation formelle.
3. **Exécution** : Créer les dossiers.

**Validation** : Structure complète selon les specs.

---

### Action 5 : Install Lucide Icons
*Objectif : Installer la bibliothèque d'icônes.*

1. **Lecture** : Charger `resources/installation-lucide.md`.
2. **Vérification** : Effectuer les vérifications indiquées dans le fichier de ressources.
3. **Plan de Modification** :
   - Si manquant ou incomplet, proposer les actions d'installation et configuration décrites dans le fichier.
   - **STOP** : Attendre validation formelle.
4. **Exécution** : Appliquer les modifications validées.

**Validation** : Lucide Icons installé et configuré selon les specs.

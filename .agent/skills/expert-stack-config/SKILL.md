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

⚠️ **IMPORTANT** : Cet algorithme détaille le COMMENT. Chaque commande doit être proposée au développeur et validée avant exécution.

### Étape 1 : Préparation & Consultation (Phase 1)
*Objectif : Charger les spécifications et présenter le plan d'installation.*

1. **Lecture** : Charger le fichier `resources/specs-stack.md`.
2. **Présentation** : Afficher au développeur un résumé des versions listées dans la section "Spécifications d'Initialisation Stack".
3. **Confirmation** : Attendre l'approbation du développeur pour procéder.

---

### Étape 2 : Installation Laravel (Phase 2)
*Objectif : Installer le framework Laravel dans le dossier `app/`.*

1. **Lecture Section** : Consulter `specs-stack.md` → Section "1. Laravel Backend" → "Installation".
2. **Proposition** : Afficher la commande au développeur.
3. **Attendre** : Validation du développeur.
4. **Exécution** : Lancer la commande après approbation (`SafeToAutoRun=false`).
5. **Vérification** : Confirmer que le dossier `app/` contient la structure Laravel.

---

### Étape 3 : Configuration .env (Phase 2)
*Objectif : Configurer les variables d'environnement.*

1. **Lecture Section** : Consulter `specs-stack.md` → Section "1. Laravel Backend" → "Configuration `.env`".
2. **Proposition** : Afficher les modifications au développeur.
3. **Attendre** : Validation du développeur.
4. **Modification** : Appliquer les valeurs spécifiées dans le fichier `app/.env`.

---

### Étape 4 : Initialisation Git (Phase 2)
*Objectif : Créer le dépôt Git avec un commit initial.*

1. **Lecture Section** : Consulter `specs-stack.md` → Section "7. Git & Versionning" → "Initialisation".
2. **Proposition** : Afficher les commandes au développeur.
3. **Attendre** : Validation du développeur.
4. **Exécution** : Lancer les commandes après approbation.

---

### Étape 5 : Installation Tailwind CSS (Phase 3)
*Objectif : Installer et configurer Tailwind CSS.*

1. **Lecture Section** : Consulter `specs-stack.md` → Section "2. Tailwind CSS" → "Installation" et "Configuration".
2. **Proposition** : Afficher les commandes d'installation au développeur.
3. **Attendre** : Validation du développeur.
4. **Exécution** : Lancer les commandes.
5. **Configuration** : Appliquer la configuration `tailwind.config.js` spécifiée dans `specs-stack.md`.
6. **CSS** : Modifier `app/resources/css/app.css` selon le template de `specs-stack.md`.

---

### Étape 6 : Installation Preline UI & Alpine.js (Phase 3)
*Objectif : Installer les bibliothèques front-end.*

1. **Lecture Sections** : 
   - Consulter `specs-stack.md` → Section "2. Tailwind CSS" → "Preline UI"
   - Consulter `specs-stack.md` → Section "3. Alpine.js" → "Installation"
2. **Proposition** : Afficher les commandes au développeur.
3. **Attendre** : Validation du développeur.
4. **Exécution** : Lancer les commandes.
5. **Configuration Alpine** : Appliquer l'intégration dans `app/resources/js/app.js` selon `specs-stack.md`.

---

### Étape 7 : Installation Laravel Pint (Phase 3)
*Objectif : Configurer le linter pour la qualité du code.*

1. **Lecture Section** : Consulter `specs-stack.md` → Section "5. Outils de Qualité" → "Laravel Pint".
2. **Proposition** : Afficher la commande d'installation au développeur.
3. **Attendre** : Validation du développeur.
4. **Exécution** : Lancer la commande.
5. **Configuration** : Créer `app/pint.json` avec la configuration spécifiée dans `specs-stack.md`.

---

### Étape 8 : Création Architecture Dossiers (Phase 4)
*Objectif : Échafauder l'arborescence des dossiers.*

1. **Lecture Section** : Consulter `specs-stack.md` → Section "6. Architecture des Dossiers" → "Commandes de Création".
2. **Proposition** : Afficher les commandes de création au développeur.
3. **Attendre** : Validation du développeur.
4. **Exécution** : Créer les dossiers selon les commandes spécifiées.

---

### Étape 9 : Présentation Finale (Phase 5)
*Objectif : Vérifier que l'environnement est opérationnel.*

1. **Résumé** : Présenter la liste des composants installés.
2. **Lecture Section** : Consulter `specs-stack.md` → Section "8. Démarrage Rapide" → "Serveurs de Développement".
3. **Proposition Tests** : Afficher les commandes de test au développeur.
4. **Validation Finale** : Confirmer que l'environnement fonctionne.

---

## ⚠️ Règles d'Or
1. **Source de Vérité** : `resources/specs-stack.md` contient TOUTES les commandes et configurations.
2. **Pas de Duplication** : Le SKILL référence les sections, il ne répète JAMAIS le contenu.
3. **Conventions** : Configuration "Opinionated" mais standard (PSR-12).
4. **⚠️ VALIDATION OBLIGATOIRE** : Ce skill exécute des commandes système destructives. **CHAQUE commande doit être proposée au développeur et nécessite son approbation EXPLICITE avant exécution**. Ne JAMAIS utiliser `SafeToAutoRun=true`.

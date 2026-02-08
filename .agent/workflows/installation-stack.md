---
description: Assistant d'initialisation et de vérification du stack technique.
---

# Workflow : Installation & Configuration Stack (`/installation-stack`)

## 1. Contexte & Flux Global
**Objectif** : Guider l'initialisation du projet ou vérifier la conformité du stack technique existant.
**Philosophie** : **"Guide & Verify"** - Privilégier la vérification et la configuration manuelle assistée.
**Flux Type** : `[Analyse Demande]` → `[Planification Actions]` → `[Exécution Validée]`

---

## 2. Mode d'Utilisation

Ce workflow est **interactif**. Il s'adapte à l'état actuel du projet.

### Exemples d'Utilisation

```
@[/installation-stack] laravel
→ Affiche la commande pour installer Laravel (si absent).

@[/installation-stack] preline
→ Vérifie l'installation Tailwind et propose l'ajout de Preline UI (V4).

@[/installation-stack] lucide
→ Installe le package d'icônes Blade Lucide.

@[/installation-stack] all
→ Vérifie/Configure tout le stack : Laravel, Architecture, Preline, Alpine, Lucide.
```

### Technologies Gérées

- `laravel` : Installation manuelle (commande fournie).
- `architecture` : Création de l'arborescence (Services, Policies...).
- `preline` : Vérification + Installation Preline UI (sur Tailwind V4).
- `alpine` : Installation Alpine.js.
- `lucide` : Installation Blade Lucide Icons.
- `all` : Séquence complète.

---

## 3. Exécution

### Étape 1 : Analyse de la Demande
> **Flux Data** : 📥 `[Commande]` → 📤 `[Liste Technologies]`

**Instructions** :
1. Identifier les technologies demandées.
2. Si `all`, définir l'ordre : `[laravel, architecture, preline, alpine, lucide]`.
3. Afficher la liste des vérifications prévues.
4. **STOP** : Demander confirmation.

---

### Étape 2 : Exécution Séquentielle Guide & Verify
> **Skill responsable** : `configurateur-stack`

**Instructions** :
Pour chaque technologie :

1. **Appel Skill** : Invoquer `configurateur-stack` avec l'action correspondante.
2. **Plan de Modification** : Le skill va proposer un plan (commandes à lancer ou fichiers à modifier).
3. **Validation développeur** :
   - Si c'est une commande manuelle (ex: Laravel) : Attendre confirmation d'exécution.
   - Si c'est une modif automatique (ex: fichiers config) : Valider le plan.
4. **Passer à la suivante** une fois l'étape validée.

---

### Étape 3 : Récapitulatif
> **Flux Data** : 📥 `[État Final]` → 📤 `[Rapport]`

**Instructions** :
1. Lister ce qui est installé/configuré.
2. Rappeler les commandes de lancement (`php artisan serve`, `npm run dev`).

---

### Étape 4 : Post-Mortem & Amélioration Continue
> **Flux Data** : 📥 `[Bilan Exécution]` → 📤 `[Proposition Amélioration]`

**Instructions** :
1. Analyser le déroulement du workflow (points de friction, erreurs, règles manquantes).
2. Demander au développeur : *"Avez-vous noté des améliorations à apporter aux Skills utilisés ?"*
3. **SI OUI** : Proposer de lancer le workflow `/refine-skill`.
4. **Validation** : Fin du workflow (et démarrage éventuel de l'amélioration).

---

## 4. Critères de Qualité

- [ ] **Sécurité** : Aucune commande destructive sans validation explicite.
- [ ] **Intelligence** : Ne réinstalle pas ce qui est déjà là.
- [ ] **Douceur** : Complète la config (ex: Preline) sans écraser l'existant.

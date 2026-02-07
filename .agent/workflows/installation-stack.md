# Workflow : Installation Stack (`/installation-stack`)

## 1. Contexte & Flux Global
**Objectif** : Installer de manière interactive et granulaire les technologies du stack technique.
**Flux Type** : `[Choix Technologies]` → `[Installation Sélective]` → `[Validation]`

---

## 2. Mode d'Utilisation

Ce workflow est **interactif**. Le développeur choisit quelles technologies installer.

### Exemples d'Utilisation

```
@[/installation-stack] laravel
→ Installe uniquement Laravel

@[/installation-stack] laravel tailwind alpine
→ Installe Laravel, Tailwind CSS et Alpine.js

@[/installation-stack] all
→ Installe tout le stack complet
```

### Technologies Disponibles

- `laravel` : Laravel Backend (PHP 8.2+, Laravel 11)
- `tailwind` : Tailwind CSS + Preline UI
- `alpine` : Alpine.js (interactivité front-end)
- `mysql` : Configuration MySQL
- `pint` : Laravel Pint (linter)
- `architecture` : Architecture des dossiers
- `git` : Initialisation Git
- `all` : Installation complète dans l'ordre recommandé

---

## 3. Exécution

⚠️ **RÈGLE IMPORTANTE** : Le développeur DOIT spécifier quelle(s) technologie(s) installer lors de l'appel du workflow.

---

### Étape 1 : Analyse de la Demande
> **Skill responsable** : Aucun (Logique de workflow)  
> **Flux Data** : 📥 `[Commande @[/installation-stack] <technologies>]` → 📤 `[Liste des Actions]`

**Instructions** :
1. Parser la commande du développeur pour extraire les technologies demandées.
2. Si `all` est spécifié, définir la liste complète : `[laravel, tailwind, alpine, mysql, pint, architecture, git]`.
3. Sinon, utiliser la liste fournie par le développeur.
4. Afficher au développeur la liste des technologies qui seront installées.
5. **STOP** : Demander confirmation avant de procéder.

**Validation** : Liste des technologies confirmée par le développeur.

---

### Étape 2 : Installation Séquentielle
> **Skill responsable** : `expert-stack-config`  
> **Flux Data** : 📥 `[Liste Technologies]` → 📤 `[Installations Complètes]`

**Instructions** :
1. Pour chaque technologie dans la liste confirmée :
   - Appeler l'action correspondante du skill `expert-stack-config`.
   - Attendre la validation du développeur après chaque installation.
2. **Ordre recommandé pour `all`** :
   1. `laravel` (base du projet)
   2. `tailwind` (dépend de Laravel pour les chemins)
   3. `alpine` (dépend de npm comme Tailwind)
   4. `mysql` (configuration indépendante)
   5. `pint` (outil de qualité)
   6. `architecture` (après Laravel)
   7. `git` (en dernier, après toute la configuration)

**Validation** : Chaque technologie installée et validée.

---

### Étape 3 : Récapitulatif Final
> **Skill responsable** : Aucun (Workflow)  
> **Flux Data** : 📥 `[Installations]` → 📤 `[Rapport]`

**Instructions** :
1. Présenter un récapitulatif des technologies installées.
2. Afficher les prochaines étapes recommandées (par exemple, lancer les serveurs).
3. **STOP** : Demander la validation finale du développeur.

**Validation** : Environnement validé et opérationnel.

---

## 4. Critères de Qualité

- [ ] **Granularité** : Le développeur peut installer uniquement ce dont il a besoin.
- [ ] **Flexibilité** : L'ordre d'installation peut être personnalisé (sauf pour `all`).
- [ ] **Validation Continue** : Chaque installation nécessite une validation.
- [ ] **Traçabilité** : Le workflow affiche clairement ce qui a été installé.

---

## 5. Notes Importantes

- **Premier Usage** : Utiliser `@[/installation-stack] all` pour une installation complète.
- **Installation Partielle** : Utile pour ajouter une technologie manquante ultérieurement.
- **Ordre** : Respecter les dépendances (Laravel avant Tailwind, par exemple).

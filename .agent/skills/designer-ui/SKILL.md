---
name: designer-ui
description: Crée les fichiers HTML/CSS statiques dans le dossier ui-kit/, développe les composants atomiques et moléculaires.
---

# Skill : Designer UI

## 🎯 Périmètre Global
**Mission** : Concevoir et développer la bibliothèque de composants visuels (UI Kit) en HTML/CSS pur (Tailwind), totalement découplée du backend Laravel.

### 🚫 Interdictions Globales (Règles d'Or)
1. **No Backend** : Ne jamais toucher aux fichiers PHP/Blade.
2. **No Logic** : Pas de JavaScript métier, uniquement des interactions d'interface (Alpine.js léger autorisé pour toggle/modal).
3. **Mobile First** : Toujours concevoir pour mobile d'abord, puis adapter pour desktop (`md:`, `lg:`).

---

## ⚡ Actions (Capacités Atomiques)

### Action A : Créer Styleguide (Tokens)
> **Description** : Définir les fondations visuelles (Couleurs, Typographie, Espacements) dans la configuration Tailwind.
- **Entrées** : Charte graphique (ou instructions utilisateur).
- **Sorties** : `ui-kit/index.html` (Page de présentation des tokens).
- **✅ Points de Contrôle (Definition of Done)** :
  - Les couleurs principales sont affichées.
  - La typographie est visible.
  - Le fichier ouvre sans erreur dans un navigateur.

### Action B : Développer Composant Atomique
> **Description** : Créer un composant de base (Bouton, Input, Badge).
- **Entrées** : Spécification du composant (Nom, États).
- **Sorties** : `ui-kit/atoms/[nom].html`.
- **❌ Interdictions Spécifiques** :
  - Ne pas utiliser de CSS custom (`style="..."`) -> Tout en Tailwind.
- **✅ Points de Contrôle (Definition of Done)** :
  - Le composant gère les états : Hover, Focus, Disabled.
  - Il est responsive.
- **📝 Instructions Détaillées** :
  1. Créer le fichier HTML.
  2. Importer le script Tailwind (CDN ou Build).
  3. Coder le composant avec les classes utilitaires.
  4. Ajouter des variantes (Primary, Secondary, Outline).

### Action C : Assembler Molécule / Organisme
> **Description** : Créer des composants complexes (Navbar, Card, Formulaire) en assemblant des atomes.
- **Entrées** : `ui-kit/atoms/*`.
- **Sorties** : `ui-kit/molecules/[nom].html`.
- **✅ Points de Contrôle (Definition of Done)** :
  - L'alignement et l'espacement sont cohérents.
  - Le rendu est testé sur plusieurs largeurs d'écran.

---

## 🔄 Scénarios d'Exécution (Algorithmes)

### Scénario 1 : Création d'une Page de Maquette
1. **Analyse** : Identifier les composants nécessaires.
2. **Atomes** : Exécuter **Action B** pour les éléments manquants.
3. **Molécules** : Exécuter **Action C** pour les blocs.
4. **Assemblage** : Créer `ui-kit/pages/[nom-page].html` regroupant le tout.

---

## ⚙️ Standards & Conventions
1. **Chemins** : Tout le travail se fait dans le dossier root `ui-kit/`.
2. **Tailwind** : Utiliser la version 4 (ou 3.4 avec CDN script) pour le prototypage rapide.
3. **Accessibilité** : Utiliser les attributs ARIA appropriés.

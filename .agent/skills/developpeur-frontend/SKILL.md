---
name: developpeur-frontend
description: Intègre le HTML du ui-kit dans les fichiers Blade, ajoute l'interactivité JS.
---

# Skill : Développeur Frontend

## 🎯 Périmètre Global
**Mission** : Transformer les maquettes statiques (UI Kit) en vues dynamiques Laravel (Blade) et implémenter l'interactivité client (Alpine.js, JS).

### 🚫 Interdictions Globales (Règles d'Or)
1. **No Logic in Views** : Ne jamais effectuer de requêtes DB dans une vue Blade.
2. **Atomic Design** : Toujours utiliser des composants Blade (`<x-component>`) pour les éléments réutilisables.
3. **Style** : Ne jamais écrire de CSS inline ou dans `<style>`, utiliser exclusivement les classes utilitaires Tailwind définies dans le UI Kit.

---

## ⚡ Actions (Capacités Atomiques)

### Action A : Créer/Adapter Composant Blade
> **Description** : Convertir un composant HTML statique du UI Kit en composant Blade réutilisable.
- **Entrées** : `ui-kit/atoms/[name].html`.
- **Sorties** : `resources/views/components/[name].blade.php`.
- **❌ Interdictions Spécifiques** :
  - Ne pas coder en dur les textes, utiliser des slots ou des props.
- **✅ Points de Contrôle (Definition of Done)** :
  - Le composant accepte les attributs HTML standards (`$attributes->merge()`).
  - Les variables par défaut sont définies (`@props`).
- **📝 Instructions Détaillées** :
  1. Copier le HTML du kit.
  2. Remplacer le contenu variable par `{{ $slot }}`.
  3. Gérer les classes dynamiques avec `@class([])`.

### Action B : Intégrer Page (View)
> **Description** : Assembler les composants pour créer une page complète connectée aux données.
- **Entrées** : Maquette de page, Données attendues du contrôleur.
- **Sorties** : `resources/views/[page].blade.php`.
- **✅ Points de Contrôle (Definition of Done)** :
  - La vue étend un Layout principal (`<x-layouts.app>`).
  - Les directives `@auth`, `@guest`, `@error` sont utilisées pour l'UX.
  - Le titre de la page est défini.

### Action C : Ajouter Interactivité (Alpine.js)
> **Description** : Dynamiser les éléments d'interface (Modale, Dropdown, Toggle).
- **Entrées** : Vue Blade existante.
- **Sorties** : Code Alpine ajouté (`x-data`, `x-on:click`).
- **❌ Interdictions Spécifiques** :
  - Ne pas écrire de logique métier JS complexe dans le HTML -> Extraire dans un fichier JS si > 10 lignes.
- **✅ Points de Contrôle (Definition of Done)** :
  - L'état est réactif.
  - Pas de "FOUC" (Flash of Unstyled Content) -> utiliser `x-cloak`.

---

## 🔄 Scénarios d'Exécution (Algorithmes)

### Scénario 1 : Intégration d'une Feature
1. **Composants** : Exécuter **Action A** pour tous les nouveaux atomes requis.
2. **Assemblage** : Exécuter **Action B** pour créer la vue.
3. **Scripting** : Exécuter **Action C** si de l'interactivité est requise.

---

## ⚙️ Standards & Conventions
1. **Blade** : Utiliser la syntaxe des composants `<x-name>` et non `@include`.
2. **Icons** : Utiliser les composants Lucid ou SVG inlinés optimisés.
3. **Forms** : Toujours inclure `@csrf` et gérer l'affichage des erreurs `@error`.

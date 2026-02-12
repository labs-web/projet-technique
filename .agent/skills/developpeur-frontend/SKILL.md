---
name: developpeur-frontend
description: Intègre le HTML du ui-kit dans les fichiers Blade, ajoute l'interactivité JS.
---

# Skill : Développeur Frontend

## 🎯 Périmètre Global
**Mission** : Transformer les maquettes statiques (UI Kit) en vues dynamiques Laravel (Blade) et implémenter l'interactivité client (Alpine.js, JS), en garantissant une UX fluide et reactive.

### 🚫 Interdictions Globales (Règles d'Or)
1. **No Logic in Views** : Ne jamais effectuer de requêtes DB dans une vue Blade.
2. **Atomic Design** : Toujours utiliser des composants Blade (`<x-component>`) pour les éléments réutilisables.
3. **Style** : Ne jamais écrire de CSS inline ou dans `<style>`, utiliser exclusivement les classes utilitaires Tailwind définies dans le UI Kit.
4. **JavaScript** : Privilégier Alpine.js pour l'interactivité simple. Ne pas utiliser jQuery.

---

## ⚡ Actions (Capacités Atomiques)

### Action A : Concevoir la Couche UI
> **Description** : Analyser les besoins fonctionnels et produire le plan technique détaillé pour le frontend (Vues, Composants).
> **Capacité** : Voir `capacités/capacité-conception-ui.md`.
- **Entrées** :
  - `docs/2.analyse/vX-[nom]/analyse-vX-[nom].md` (Fonctionnel).
  - Maquettes / UI Kit.
- **Sorties** : `docs/3.conception/vX-[nom]/conception-frontend-vX-[nom].md`.
- **❌ Interdictions** : Ne pas réinventer le Design System.
- **✅ Definition of Done** : Arborescence des vues et liste des composants définie.
- **📝 Instructions** : Utiliser la capacité dédiée.

### Action B : Créer/Adapter Composant Blade
> **Description** : Convertir un composant HTML statique du UI Kit en composant Blade réutilisable.
> **Capacité** : Voir `capacités/capacité-composant-blade.md`.
- **Entrées** : `ui-kit/atoms/[name].html`.
- **Sorties** : `resources/views/components/[name].blade.php`.
- **❌ Interdictions** : Pas de texte en dur.
- **✅ Definition of Done** : Composant générique acceptant `$slot` et `$attributes`.
- **📝 Instructions** : Utiliser la capacité dédiée.

### Action C : Intégrer Page (View)
> **Description** : Assembler les composants pour créer une page complète connectée aux données.
> **Capacité** : Voir `capacités/capacité-integration-page.md`.
- **Entrées** : Maquette de page, Données du contrôleur.
- **Sorties** : `resources/views/[page].blade.php`.
- **✅ Definition of Done** : Page fonctionnelle, responsive, utilisant `@auth`/`@guest`.
- **📝 Instructions** : Utiliser la capacité dédiée.

### Action D : Ajouter Interactivité (Alpine.js)
> **Description** : Dynamiser les éléments d'interface (Modale, Dropdown, Toggle).
> **Capacité** : Voir `capacités/capacité-alpine-js.md`.
- **Entrées** : Vue Blade existante.
- **Sorties** : Code Alpine ajouté (`x-data`, `x-on:click`).
- **❌ Interdictions** : Pas de logique complexe inline.
- **✅ Definition of Done** : Pas de FOUC, état réactif.
- **📝 Instructions** : Utiliser la capacité dédiée.

---

## 🔄 Scénarios d'Exécution (Algorithmes)

### Scénario 1 : Intégration d'une Feature
1. **Design** : Exécuter **Action A** pour lister les composants manquants et l'architecture des vues.
2. **Composants** : Exécuter **Action B** pour tous les nouveaux atomes requis.
3. **Assemblage** : Exécuter **Action C** pour créer la vue principale.
4. **Scripting** : Exécuter **Action D** si de l'interactivité est requise.

---

## ⚙️ Standards & Conventions
1. **Blade** : Utiliser la syntaxe des composants `<x-name>` et non `@include`.
2. **Icons** : Utiliser les composants Lucid ou SVG inlinés optimisés.
3. **Forms** : Toujours inclure `@csrf` et gérer l'affichage des erreurs `@error`.

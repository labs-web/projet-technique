---
name: dev-frontend-js
description: Intègre le HTML du ui-kit dans les fichiers Blade, ajoute l'interactivité JS.
---

# Skill : Développeur Frontend JS

## 🎯 Objectif & Périmètre
**Mission** : Rendre l'interface vivante en intégrant le design statique dans Laravel et en ajoutant l'interactivité utilisateur.

### ✅ Actions Autorisées
- **Intégrer** le HTML du `ui-kit` dans les fichiers `.blade.php` (Layouts, Components, Views).
- **Développer** la couche interactive avec Alpine.js ou Vanilla JS.
- **Connecter** le frontend à l'API via des appels AJAX (Fetch).
- **Dynamiser** l'UI selon les données du Backend.

### ❌ Limites (Ce qu'il ne fait PAS)
- Ne crée pas le design system (Déléguer à `designer-ui-kit`).
- Ne touche pas à la logique Backend (sauf pour afficher les variables).

## 📥 Entrées / 📤 Sorties
| Direction  | Nom                           | Description / Format                       |
| :--------- | :---------------------------- | :----------------------------------------- |
| **Entrée** | `ui-kit/`                     | Maquettes HTML/CSS statiques de référence  |
| **Entrée** | `resources/specs-frontend.md` | Comportements attendus, interactions, flux |
| **Sortie** | `resources/views/*`           | Fichiers Blade finaux                      |
| **Sortie** | `resources/js/*`              | Scripts JS compilés (via Vite)             |

## 🔄 Algorithme d'Exécution

### Étape 1 : Intégration Blade
*Objectif : Transformer le statique en dynamique.*
1. **Découpage** : Identifier les parties réutilisables (Header, Footer, Cards).
2. **Components** : Créer des composants Blade (`x-card`, `x-button`) basés sur le HTML du ui-kit.
3. **Views** : Construire les pages finales en assemblant layout et composants.

### Étape 2 : Injection des Données
*Objectif : Afficher le contenu réel.*
1. **Variables** : Utiliser `{{ $variable }}` pour afficher les données passées par le Contrôleur.
2. **Boucles** : Utiliser `@foreach` pour les listes.
3. **Conditions** : Utiliser `@if`, `@auth` pour l'affichage conditionnel.

### Étape 3 : Interactivité (JS)
*Objectif : Gérer les actions utilisateur côté client.*
1. **Alpine.js** : Ajouter des directives `x-data`, `x-show` pour les interactions simples (modales, dropdowns).
2. **AJAX** : Écrire des scripts `fetch` pour les interactions sans rechargement de page.

## ⚠️ Règles d'Or
1. **Source de Vérité** : Ne jamais inventer de CSS, toujours copier les classes du `ui-kit`.
2. **Sécurité** : Toujours échapper les données utilisateurs (Blade le fait par défaut).
3. **Performance** : Minimiser le JS, privilégier Alpine.js pour les besoins simples.

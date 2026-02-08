---
name: designer-ui
description: Crée les fichiers HTML/CSS statiques dans le dossier ui-kit/, développe les composants atomiques et moléculaires.
---

# Skill : Designer UI Kit

## 🎯 Objectif & Périmètre
**Mission** : Produire une bibliothèque de composants visuels statiques (UI Kit) validée et isolée du backend.

### ✅ Actions Autorisées
- **Créer** les fichiers HTML/CSS statiques dans le dossier `ui-kit/`.
- **Développer** les composants atomiques (Boutons, Inputs) et moléculaires (Cards, Navbars).
- **Valider** le rendu visuel (Tailwind) et la réactivité.

### ❌ Limites (Ce qu'il ne fait PAS)
- Ne touche JAMAIS aux fichiers `.blade.php` (Déléguer à `developpeur-frontend`).
- N'écrit pas de JS complexe (juste des états visuels).

## 📥 Entrées / 📤 Sorties
| Direction  | Nom                         | Description / Format                                     |
| :--------- | :-------------------------- | :------------------------------------------------------- |
| **Entrée** | `resources/specs-ui-kit.md` | Charte graphique, liste des composants, wireframes       |
| **Sortie** | `ui-kit/index.html`         | Page de présentation de tous les composants (Styleguide) |
| **Sortie** | `ui-kit/components/*.html`  | Fichiers HTML unitaires des composants                   |

## 🔄 Algorithme d'Exécution

### Étape 1 : Mise en place du Styleguide
*Objectif : Définir les fondations visuelles.*
1. **Tokens** : Définir les couleurs, typographies et espacements dans `tailwind.config.js`.
2. **Base** : Créer une page `index.html` qui liste ces tokens.

### Étape 2 : Développement Atomique
*Objectif : Créer les briques élémentaires.*
1. **Atomes** : Coder les boutons, inputs, labels, badges en HTML/Tailwind.
2. **Validation** : Vérifier le rendu mobile et desktop.

### Étape 3 : Assemblage Moléculaire
*Objectif : Créer les composants complexes.*
1. **Molécules** : Assembler les atomes pour faire des Cards, Formulaires, Navbars.
2. **États** : Simuler les états (hover, focus, disabled) via les classes utilitaires.

## ⚠️ Règles d'Or
1. **Source de Vérité** : `ui-kit/` est la référence visuelle absolue.
2. **Conventions** : Mobile-First, Tailwind CSS strict (pas de CSS custom si possible).
3. **Isolation** : Aucun lien avec Laravel, tout doit fonctionner en ouvrant le fichier HTML dans le navigateur.

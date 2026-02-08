# Spécifications : Installation Preline UI
*(Pré-requis : Tailwind CSS déjà installé via Laravel)*

## 🎯 Objectif
Installer et configurer **Preline UI** sur une installation existante de Laravel + Tailwind.

---

## 🔍 Pré-requis : Validation Tailwind
Avant d'installer Preline, vérifier que Tailwind est opérationnel :
1. **package.json** : Contient `tailwindcss`.
2. **app.css** : Contient `@tailwind` ou `@import "tailwindcss"`.

---

## 🚀 Installation Preline UI

### 1. Installation du paquet
```bash
npm install preline --save-dev
```

### 2. Configuration Tailwind (V4)

Suivre la documentation officielle de Preline pour Tailwind v4.

**Étape A : Installation des dépendances**
Preline utilise `@tailwindcss/forms`.
```bash
npm install -D @tailwindcss/forms
```

**Étape B : Configuration CSS**
Fichier : `resources/css/app.css`

Ajouter les imports, sources et plugins :
```css
@import "tailwindcss";

/* Preline UI */
@source "../node_modules/preline/dist/*.js";

/* Plugins */
@plugin "@tailwindcss/forms";

/* (Optionnel) Styles par défaut pour conserver le comportement v3 */
@layer base {
  button:not(:disabled),
  [role="button"]:not(:disabled) {
    cursor: pointer;
  }
}
@custom-variant hover (&:hover);
```

### 3. Initialisation JS
**Fichier cible** : `resources/js/app.js`

Initialiser le script interactif de Preline :
```javascript
import 'preline';
```

---

## ✅ Étape 3 : Validation
- [ ] `npm install` exécuté.
- [ ] `@tailwindcss/forms` présent dans package.json.
- [ ] `npm run dev` compile sans erreur.
- [ ] Les classes Tailwind fonctionnent dans les vues Blade.
- [ ] Les composants Preline (dropdowns, modals) sont interactifs.

---
name: dev-frontend-js
description: Intègre le HTML du ui-kit dans les fichiers Blade, ajoute l'interactivité JS, et gère les appels AJAX.
---

# Skill : Développeur Frontend JS (`dev-frontend-js`)

### Périmètre
✅ **Fait** :
- Intégre le HTML du `ui-kit` dans les fichiers `.blade.php`.
- Ajoute la couche interactive (Alpine.js, Vanilla JS).
- Gère les appels AJAX (Fetch) vers l'API interne.
- Dynamise les composants (Modales, Dropdowns).

❌ **Ne fait PAS** :
- Ne crée pas le design system (utilise l'existant).
- Ne touche pas au Backend (sauf pour lire les variables injectées).

### Contrat I/O
**Entrée** : `resources/specs-frontend.md`
**Sortie** : Fichiers `resources/views/*` et `resources/js/*` fonctionnels.

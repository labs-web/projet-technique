# Spécifications : Alpine.js

Ce fichier définit les versions, commandes d'installation et configurations pour Alpine.js.

---

## Version
- **Alpine.js** : `Latest Stable`

---

## Critères de Vérification
1. **package.json** : Présence de `alpinejs` dans `dependencies` ou `devDependencies`.
2. **app.js** : Présence de `import Alpine from 'alpinejs'`.

---

## Installation

### Commande
```bash
npm install alpinejs

```

---

## Intégration

**Chemin** : `app/resources/js/app.js`

```javascript
import Alpine from 'alpinejs'

window.Alpine = Alpine

Alpine.start()
```

---



# Spécifications : Alpine.js

Ce fichier définit les versions, commandes d'installation et configurations pour Alpine.js.

---

## Version
- **Alpine.js** : `^3.14`

---

## Installation

### Commande
```bash
npm install alpinejs@^3.14
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

## Utilisation dans Blade

Alpine.js sera automatiquement disponible dans toutes les vues Blade après l'import ci-dessus.

**Exemple** :
```html
<div x-data="{ open: false }">
    <button @click="open = !open">Toggle</button>
    <div x-show="open">
        Contenu visible/invisible
    </div>
</div>
```

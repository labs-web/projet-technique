# Spécifications : Installation Lucide Icons (Blade)
*(Package PHP : mallardduck/blade-lucide-icons)*

## 🎯 Objectif
Installer la bibliothèque **Blade Lucide Icons** pour utiliser les icônes directement comme composants Blade `<x-lucide-... />`.

---

## 🚀 Installation & Configuration

### 1. Installation (Composer)
```bash
composer require mallardduck/blade-lucide-icons
```

### 2. Publication Config (Optionnel)
Permet de définir des classes par défaut (ex: `w-6 h-6`).
```bash
php artisan vendor:publish --tag=blade-lucide-icons-config
```

---

## 💻 Utilisation dans Blade

Les icônes s'utilisent comme des composants Blade auto-fermant.
Le préfixe est `x-lucide-`.

### Exemples
```html
<!-- Icône simple -->
<x-lucide-activity />

<!-- Avec classes Tailwind -->
<x-lucide-user class="w-6 h-6 text-gray-500" />

<!-- Avec style inline -->
<x-lucide-settings style="color: red;" />
```

### Avantages
- Pas de JS nécessaire au runtime pour les icônes.
- Support natif des classes Tailwind via l'attribut `class`.
- Rendu SVG côté serveur (SEO friendly, pas de saut d'affichage).

---

## ✅ Checklist de Validation
- [ ] `composer.json` contient `mallardduck/blade-lucide-icons`.
- [ ] Une icône test `<x-lucide-check />` s'affiche correctement.

---

## ⚠️ Dépannage SSL (Erreur curl 60)
Si vous rencontrez une erreur SSL lors du `composer require` (ex: "SSL certificate problem: unable to get local issuer certificate") :
1. **Cause probable** : L'antivirus (ex: Kaspersky) intercepte le trafic SSL.
2. **Solution** : Désactiver temporairement l'analyse des connexions chiffrées ou l'antivirus le temps de l'installation.

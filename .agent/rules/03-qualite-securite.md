---
trigger: always_on
---

# Qualité et Sécurité

## Standards de Code
- **PHP** : Respect des standards PSR-12. Typage strict (`declare(strict_types=1);`) encouragé.
- **Naming** : 
  - Code en **Anglais** (Variables, Fonctions, Classes).
  - Base de données en **Anglais** (Snake case).
  - Commits en **Français** (cohérent).
- **Commentaires en français** : Uniquement pour expliquer une logique complexe (« Pourquoi » et non « Comment »).

## Sécurité
- **Injection SQL** : Toujours utiliser l'ORM Eloquent ou les bindings PDO. Jamais de requêtes concaténées.
- **XSS** : Utiliser l'échappement par défaut de Blade `{{ }}`.
- **Auth** : Ne jamais stocker de mots de passe en clair. Utiliser les façades `Hash`.
- **API** : Tous les endpoints sensibles doivent être protégés par `auth:sanctum`.
- **Validation** : Toujours valider les entrées utilisateur via FormRequests.

## Bonnes Pratiques Laravel
- **Fat Model, Skinny Controller** (ou Service Pattern pour la logique complexe).
- Utiliser les **Resource Controllers** pour le CRUD standard.
- Utiliser les **Migrations** pour toute, modification de la BDD.
- Ne pas mettre de logique métier dans les Vues (Blade).
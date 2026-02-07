---
name: backend-business
description: Implémente les Services, la logique métier, et définit les Policies/Gates.
---

# Skill : Expert Métier (`backend-business`)

### Périmètre
✅ **Fait** :
- Implémente les Services (`app/Services/*`).
- Contient toute la logique métier (Business Logic).
- Définit les Policies/Gates (Règles d'autorisation métier).
- Utilise les Modèles pour manipuler les données.

❌ **Ne fait PAS** :
- Ne connait pas HTTP (pas de `Request`, pas de `Response`, pas de `View`).
- Ne gère pas la validation de format (c'est le rôle du FormRequest).

### Contrat I/O
**Entrée** : `resources/specs-business.md`
**Sortie** : Fichiers `app/Services/*`, `app/Policies/*`.

---
name: backend-http
description: Déclare les Routes, crée les Contrôleurs, FormRequests et API Resources, appelle les Services, et retourne les Vues ou le JSON.
---

# Skill : Expert HTTP (`backend-http`)

### Périmètre
✅ **Fait** :
- Déclare les Routes (`web.php`, `api.php`).
- Crée les Contrôleurs (Web & API).
- Crée les FormRequests (Validation des entrées).
- Crée les API Resources (Formatage sortie JSON).
- Appelle les Services pour l'exécution.
- Retourne les Vues ou le JSON.

❌ **Ne fait PAS** :
- N'écrit AUCUNE logique métier dans les contrôleurs.
- N'écrit pas de requêtes Eloquent complexes (délégué au Service/Model).

### Contrat I/O
**Entrée** : `resources/specs-http.md`
**Sortie** : Fichiers `app/Http/Controllers/*`, `app/Http/Requests/*`, `routes/*`.

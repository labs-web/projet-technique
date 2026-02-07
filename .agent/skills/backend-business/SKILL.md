---
name: backend-business
description: Implémente les Services, la logique métier, et définit les Policies/Gates.
---

# Skill : Expert Métier

## 🎯 Objectif & Périmètre
**Mission** : Encapsuler la logique métier complexe et les règles d'autorisation dans des classes dédiées (Services).

### ✅ Actions Autorisées
- **Implémenter** les Services (`app/Services/*`) contenant la Business Logic.
- **Définir** les Policies et Gates pour la gestion des droits.
- **Manipuler** les Modèles Eloquent pour effectuer les traitements.
- **Déclencher** des événements métier (Events/Listeners).

### ❌ Limites (Ce qu'il ne fait PAS)
- Ne connait pas HTTP (pas de `Request`, pas de `Response`, pas de `View`).
- Ne gère pas la validation de format des entrées (Déléguer à `backend-http`).

## 📥 Entrées / 📤 Sorties
| Direction  | Nom                           | Description / Format                              |
| :--------- | :---------------------------- | :------------------------------------------------ |
| **Entrée** | `resources/specs-business.md` | Règles de gestion, flux métier, matrice de droits |
| **Entrée** | `app/Models/*`                | Modèles de données disponibles                    |
| **Sortie** | `app/Services/*`              | Classes de Service (ex: `ArticleService`)         |
| **Sortie** | `app/Policies/*`              | Classes de Policy (ex: `ArticlePolicy`)           |

## 🔄 Algorithme d'Exécution

### Étape 1 : Définition de l'Architecture Service
*Objectif : Structurer le point d'entrée métier.*
1. **Création** : Générer la classe Service dans `app/Services`.
2. **Interface** : Définir les méthodes publiques (le contrat métier).

### Étape 2 : Implémentation de la Logique
*Objectif : Coder les règles de gestion.*
1. **Traitement** : Écrire le code qui manipule les données (Calculs, conditions, workflow).
2. **Transaction** : Utiliser `DB::transaction` pour les opérations atomiques.
3. **Events** : Dispatcher des événements si nécessaire.

### Étape 3 : Sécurisation (ACL)
*Objectif : Protéger l'accès aux fonctionnalités.*
1. **Policies** : Créer les Policies associées aux Modèles.
2. **Règles** : Implémenter les méthodes `view`, `create`, `update`, `delete` avec la logique de droits.

## ⚠️ Règles d'Or
1. **Source de Vérité** : Le Service est le seul point d'entrée pour modifier l'état métier.
2. **Indépendance** : Le code ne doit jamais dépendre de la classe `Illuminate\Http\Request`.
3. **Conventions** : Nommage explicite des méthodes (`publishArticle` et non `save`).

---
name: backend-http
description: Déclare les Routes, crée les Contrôleurs, FormRequests et API Resources.
---

# Skill : Expert HTTP

## 🎯 Objectif & Périmètre
**Mission** : Exposer la logique métier via le protocole HTTP (Web & API) en gérant l'entrée (Validation) et la sortie (Réponse).

### ✅ Actions Autorisées
- **Déclarer** les Routes (`web.php`, `api.php`).
- **Créer** les Contrôleurs (Web & API) qui orchestrent l'appel aux Services.
- **Valider** les entrées via des FormRequests.
- **Formater** les sorties JSON via des API Resources.

### ❌ Limites (Ce qu'il ne fait PAS)
- N'écrit AUCUNE logique métier dans les contrôleurs (Déléguer à `backend-business`).
- N'écrit pas de requêtes Eloquent complexes (Déléguer à `backend-business` ou `backend-data`).

## 📥 Entrées / 📤 Sorties
| Direction  | Nom                       | Description / Format                                 |
| :--------- | :------------------------ | :--------------------------------------------------- |
| **Entrée** | `resources/specs-http.md` | Endpoints, Méthodes HTTP, Codes retour, Formats JSON |
| **Entrée** | `app/Services/*`          | Services métier disponibles à appeler                |
| **Sortie** | `app/Http/Controllers/*`  | Classes Contrôleurs                                  |
| **Sortie** | `app/Http/Requests/*`     | Classes de Validation                                |
| **Sortie** | `routes/web.php`          | Définition des URLs                                  |

## 🔄 Algorithme d'Exécution

### Étape 1 : Routing
*Objectif : Définir les points d'entrée.*
1. **Routes** : Ajouter les définitions dans `routes/web.php` ou `api.php`.
2. **Naming** : Nommer les routes (ex: `articles.show`).

### Étape 2 : Contrôle des Entrées
*Objectif : Garantir la validité des données reçues.*
1. **FormRequest** : Créer une classe Request dédiée par action (ex: `StoreArticleRequest`).
2. **Règles** : Définir les règles de validation (`required`, `email`, `max:255`).

### Étape 3 : Orchestration (Controller)
*Objectif : Faire le lien entre HTTP et Métier.*
1. **Controller** : Créer la méthode du contrôleur.
2. **Appel** : Instancier/Injected le Service et appeler la méthode métier.
3. **Réponse** : Retourner une `View` (Web) ou une `JsonResource` (API).

## ⚠️ Règles d'Or
1. **Source de Vérité** : Les FormRequests sont la barrière de sécurité des entrées.
2. **Skinny Controller** : Le contrôleur ne doit faire que : Valider -> Appeler Service -> Retourner Réponse.
3. **Conventions** : Utiliser les Resource Controllers quand c'est possible (`index`, `store`, `show`...).

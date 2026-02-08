---
name: developpeur-http
description: Déclare les Routes, crée les Contrôleurs, FormRequests et API Resources.
---

# Skill : Développeur HTTP

## 🎯 Périmètre Global
**Mission** : Exposer la logique métier via le protocole HTTP (Web & API) en gérant l'entrée (Validation) et la sortie (Réponse/Vue).

### 🚫 Interdictions Globales (Règles d'Or)
1. **Skinny Controllers** : Ne jamais écrire de logique métier dans un contrôleur -> Déléguer au Service.
2. **Validation** : Ne jamais valider `$request->all()` manuellement dans le contrôleur -> Utiliser `FormRequest`.
3. **Responses** : Ne jamais retourner de JSON brut depuis un contrôleur API -> Utiliser `JsonResource`.

---

## ⚡ Actions (Capacités Atomiques)

### Action A : Déclarer Routes
> **Description** : Définir les endpoints HTTP et les lier aux contrôleurs.
- **Entrées** : Spécification des URL et méthodes.
- **Sorties** : `routes/web.php` ou `routes/api.php`.
- **❌ Interdictions Spécifiques** :
  - Ne pas utiliser de Closures pour les routes complexes (plus de 1 ligne).
- **✅ Points de Contrôle (Definition of Done)** :
  - Chaque route a un nom (`->name('...')`).
  - Les middlewares d'authentification sont appliqués (`auth`, `guest`).

### Action B : Créer FormRequest (Validation)
> **Description** : Créer une classe pour valider les données entrantes.
- **Entrées** : Règles de validation.
- **Sorties** : `app/Http/Requests/[Name]Request.php`.
- **✅ Points de Contrôle (Definition of Done)** :
  - La méthode `authorize()` retourne `true` (ou vérifie une Gate).
  - Les règles sont précises (types, max, unique).

### Action C : Implémenter Contrôleur
> **Description** : Orchestrer la requête : Valider -> Appeler Service -> Répondre.
- **Entrées** : Service Métier, FormRequest, Type de réponse (Vue/JSON).
- **Sorties** : `app/Http/Controllers/[Name]Controller.php`.
- **✅ Points de Contrôle (Definition of Done)** :
  - Le constructeur injecte le Service nécessaire.
  - La méthode de contrôleur est courte (< 10 lignes idéalement).
  - Retourne `view()` ou `redirect()` pour le Web.

### Action D : Créer API Resource
> **Description** : Formater la réponse JSON.
- **Entrées** : Modèle de données.
- **Sorties** : `app/Http/Resources/[Name]Resource.php`.
- **✅ Points de Contrôle (Definition of Done)** :
  - La méthode `toArray()` définit explicitement les champs exposés (pas de `$this->resource->toArray()`).

---

## 🔄 Scénarios d'Exécution (Algorithmes)

### Scénario 1 : Endpoint API complet
1. **Input** : Exécuter **Action B** pour valider l'entrée.
2. **Output** : Exécuter **Action D** pour définir la sortie JSON.
3. **Logic** : Exécuter **Action C** pour créer le contrôleur liant le tout.
4. **Wiring** : Exécuter **Action A** pour rendre la route accessible.

### Scénario 2 : Page Web
1. **Controller** : Exécuter **Action C** (retournant une Vue).
2. **Route** : Exécuter **Action A**.

---

## ⚙️ Standards & Conventions
1. **REST** : Suivre les conventions de nommage REST pour les contrôleurs (`index`, `store`, `update`, `destroy`).
2. **Injection** : Utiliser l'injection de dépendances dans les méthodes de contrôleur (ex: `show(Article $article)`).

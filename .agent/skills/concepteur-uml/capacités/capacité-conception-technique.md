# Capacité : Structuration Conception Technique

## Contexte
Rédiger un document de conception technique détaillé pour une version donnée, structuré par couches architecturales. Ce document sert de pont entre l'analyse fonctionnelle et l'implémentation.

## Processus & Orchestration

### 1. Organisation Technique des Vues
Avant d'entamer la couche HTTP, définir l'architecture des fichiers de présentation.
- **Identifier** les Layouts nécessaires (Public, Admin, Auth).
- **Lister** les Vues principales (Pages).
- **Extraire** les Partials évidents (Composants réutilisables).

## Structure du Document (Template)

### 1. Couche Front-end (Vues & Layouts)
> **Objectif** : Structurer l'affichage sans conception graphique détaillée.
- **Arborescence** : Liste des fichiers Blade à créer (ex: `resources/views/public/posts/index.blade.php`).
- **Layouts** : Structure globale (Header, Footer, Slot).
- **Partials** : Blocs réutilisables identifiés (`@include`).
- **Interactivité** : Besoins JS / Alpine simples.

### 2. Couche HTTP (Contrôleurs, Routes, API)
> **Objectif** : Gérer les entrées/sorties et la validation.
- **Routes** : Définition des endpoints (`web.php`, `api.php`), Verbes HTTP, Middleware.
  - **Convention** : Routes nommées impérativement.
- **Contrôleurs** : Séparation stricte **Public** vs **Admin**.
- **Validation** : Utilisation obligatoire des `FormRequests`.
- **Réponses** : Format de retour (Redirection, JSON Resource).

### 3. Couche Métier (Services & Logique)
> **Objectif** : encapsuler la logique business.
- **Services** : Pour la logique complexe (Fat Model / Skinny Controller).
- **Règles de Gestion** : Implémentation explicite des règles identifiées en analyse.
- **Autorisations** : Définition des `Policies` et `Gates`.

### 4. Couche Data (Persistance)
> **Objectif** : structurer et pérenniser les données.
- **Modèles (Eloquent)** : Relations, Scopes, Accessors/Mutators.
- **Base de Données** :
  - **Migrations** : Structure, Index, Clés étrangères.
  - **Seeders/Factories** : Stratégie de peuplement des données.

## 🚫 Interdictions & Règles d'Or
1. **Diagrammes** : Ne **JAMAIS** inclure de diagrammes ici (référencez le fichier `.mermaid` correspondant).
2. **Blade** : **Ne JAMAIS utiliser les composants Blade Laravel** (`<x-component />`). Privilégier exclusivement les **Partials** (`@include 'partials.name'`).
3. **Niveau de Détail** : Ne **PAS** écrire le code complet, rester au niveau de la conception (signatures, algorithmes clés).

## ✅ Critères de Qualité
- [ ] L'architecture des pages (Atoms/Molecules) est définie et cohérente avec le UI Kit.
- [ ] Les routes sont nommées et les contrôleurs organisés par namespace (Admin/Public).
- [ ] La validation des données est systématiquement externalisée dans des FormRequests.
- [ ] Le modèle de données (Migrations/Models) est aligné avec le diagramme de classes global.

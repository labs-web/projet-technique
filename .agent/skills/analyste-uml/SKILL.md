---
name: analyste-uml
description: Expert en modélisation de l'analyse fonctionnelle (Analyse des besoins et Diagrammes de Cas d'Utilisation).
---

# Skill : Analyste UML

## 🎯 Objectif & Périmètre
**Mission** : Formaliser le besoin métier global, le découper en versions réalisables, et produire les diagrammes de Cas d'Utilisation standardisés pour chaque version.

### ✅ Actions Autorisées
1.  **Analyser le Besoin Global** : Lire le besoin initial et produire une liste exhaustive de fonctionnalités.
2.  **Planifier les Versions** : Découper la liste globale en versions incrémentales (Lotissement).
3.  **Générer les Use Cases** : Produire les diagrammes `.puml` pour chaque version à partir de son analyse détaillée.

### ❌ Limites (Ce qu'il ne fait PAS)
- Ne génère PAS de diagrammes de classes ou techniques (Déléguer à `conception-uml`).
- Ne prend PAS de décisions d'architecture technique (Déléguer à `architecte` ou `concepteur`).

## 📥 Entrées / 📤 Sorties

### Action 1 : Analyse Globale
- **Entrée** : `docs/1.besoin/1.besoin.md` (Expression de besoins initiale).
- **Sortie** : `docs/2.analyse/global-features.md` (Liste consolidée des fonctionnalités).

### Action 2 : Planification des Versions
- **Entrée** : `docs/2.analyse/global-features.md`.
- **Sortie** : 
    - Structure de dossiers : `docs/2.analyse/vX-[nom-version]/`.
    - Fichiers d'analyse par version : `docs/2.analyse/vX-[nom-version]/analyse-vX-[nom-version].md`.

### Action 3 : Génération Use Case
- **Entrée** : `docs/2.analyse/vX-[nom-version]/analyse-vX-[nom-version].md`.
- **Sortie** : `docs/2.analyse/vX-[nom-version]/usecase-vX-[nom-version].puml`.

## 🔄 Algorithme d'Exécution

### Étape 1 : Analyser le Besoin Global
*Objectif : Transformer une expression de besoin brute en une liste structurée de fonctionnalités.*
1.  **Lecture** : Lire `docs/1.besoin/1.besoin.md`.
2.  **Extraction** : Identifier les acteurs et les fonctionnalités (Verbe + Objet).
3.  **Consolidation** : Créer `docs/2.analyse/global-features.md` listant toutes les fonctionnalités sans notion de version.

### Étape 2 : Planifier les Versions (Lotissement)
*Objectif : Organiser les fonctionnalités en versions logiques et incrémentales.*
1.  **Découpage** : Répartir les fonctionnalités du fichier global en versions (V1, V2, etc.) en suivant une logique de "Vertical Slice".
2.  **Création Structure** : Pour chaque version, créer le dossier `docs/2.analyse/vX-[nom]/`.
3.  **Rédaction** : Créer le fichier `analyse-vX-[nom].md` dans chaque dossier, détaillant les fonctionnalités de cette version spécifique (En tant que... Je veux... Afin de...).

### Étape 3 : Modéliser Use Case par Version
*Objectif : Traduire l'analyse textuelle d'une version en diagramme visuel.*
1.  **Lecture** : Lire le fichier d'analyse de la version cible (`analyse-vX-[nom].md`).
2.  **Modélisation** : 
    - Identifier les **Acteurs** de cette version.
    - Identifier les **Cas d'Utilisation** de cette version.
    - Définir les **Relations** (`include`, `extend`).
3.  **Génération** : Créer/Mettre à jour `usecase-vX-[nom].puml` dans le même dossier.
    - **Note** : Le diagramme doit impérativement utiliser `left to right direction`.

## ✓ Points de Contrôle
Validations obligatoires avant de considérer le skill terminé :
1.  **Cohérence** : Les fonctionnalités listées dans `analyse-vX.md` sont toutes présentes dans `usecase-vX.puml`.
2.  **Structure** : Les fichiers respectent strictement la convention de nommage avec slug de version.
3.  **Syntaxe PlantUML** : Le code `.puml` est valide et compilable.

## 🚫 Interdictions
1.  **Doublons** : Ne pas répéter les mêmes fonctionnalités dans plusieurs versions (sauf évolution explicite).
2.  **Technique** : Ne pas inclure de détails d'implémentation (BDD, Classes) dans l'analyse fonctionnelle.

## ⚙️ Standards & Conventions
1.  **Format Use Case** : Syntaxe PlantUML standard.
2.  **Conventions de Nommage** :
    - Dossiers : `v[N]-[slug]` (ex: `v1-public`).
    - Fichiers : `[type]-v[N]-[slug].[ext]` (ex: `analyse-v1-public.md`, `usecase-v1-public.puml`).

---
name: analyste-uml
description: Expert en modélisation de l'analyse fonctionnelle (Diagrammes de Cas d'Utilisation avec PlantUML).
---

# Skill : Analyse UML

## 🎯 Objectif & Périmètre
**Mission** : Produire des diagrammes de Cas d'Utilisation (Use Case) standards pour formaliser l'analyse fonctionnelle.

### ✅ Actions Autorisées
- **Générer** un diagramme de Cas d'Utilisation (`.puml`) à partir d'une description textuelle.
- **Mettre à jour** un diagramme existant suite à une évolution du besoin.

### ❌ Limites (Ce qu'il ne fait PAS)
- Ne génère PAS de diagrammes de classes ou techniques (Déléguer à `conception-uml`).
- Ne rédige PAS les spécifications textuelles (Déléguer à l'analyse métier).

## 📥 Entrées / 📤 Sorties
- **Entrée** : Description textuelle d'un besoin fonctionnel ou fichier de contexte (`0-besoins.md`).
- **Sortie** : Fichier source du diagramme (`.puml`).

## 🔄 Algorithme d'Exécution

### Étape 1 : Modéliser Analyse (Use Case)
*Objectif : Traduire le besoin fonctionnel en diagramme visuel.*
1. **Lecture** : Charger le template `resources/spec-plantuml.md` pour connaître la syntaxe.
2. **Identification** :
   - Identifier les **Acteurs** (Primaires à gauche, Secondaires à droite).
   - Identifier les **Cas d'Utilisation** (Verbe à l'infinitif).
   - Définir les **Relations** (`include`, `extend`, `generalization`).
3. **Génération** : Écrire le code PlantUML en respectant `left to right direction`.
4. **Production** : Créer ou mettre à jour un fichier `.puml` dans le dossier cible (ex: `docs/2.analyse/`).

## ✓ Points de Contrôle
Validations obligatoires avant de considérer le skill terminé :
1. **Syntaxe** : Le code PlantUML est valide (commence par `@startuml`, finit par `@enduml`).
2. **Lisibilité** : La directive `left to right direction` est présente.
3. **Approbation Développeur** : Attendre confirmation que le diagramme correspond au besoin.

## 🚫 Interdictions
1. **Complexité** : Ne pas surcharger le diagramme. Si trop complexe, diviser en plusieurs diagrammes par domaine.
2. **Technique** : Ne pas inclure de détails d'implémentation (classes, tables) dans un Use Case.

## ⚙️ Standards & Conventions
1. **Source de Vérité** : `resources/spec-plantuml.md`.
2. **Conventions** :
   - Alias courts pour les acteurs (`User` -> `U`).
   - Verbes à l'infinitif pour les Use Cases.

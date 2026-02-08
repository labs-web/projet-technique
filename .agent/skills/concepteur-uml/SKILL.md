---
name: concepteur-uml
description: Expert en modélisation technique et conception (Diagrammes de Classes avec Mermaid).
---

# Skill : Conception UML

## 🎯 Objectif & Périmètre
**Mission** : Produire des diagrammes de Classes (Class Diagram) pour structurer le modèle de données et les relations techniques.

### ✅ Actions Autorisées
- **Générer** un bloc `mermaid` (Classes, Relations, Types) à partir d'une liste d'entités ou d'un cas d'usage.
- **Intégrer** ce bloc dans la documentation technique (`implementation_plan.md`, `design_doc.md`).

### ❌ Limites (Ce qu'il ne fait PAS)
- Ne génère PAS de Use Cases (Déléguer à `analyse-uml`).
- Ne crée PAS les fichiers de migration Laravel (Déléguer à `developpeur-backend`).

## 📥 Entrées / 📤 Sorties
- **Entrée** : Description textuelle d'un schéma de données ou d'entités.
- **Sortie** : Bloc de code `mermaid`.

## 🔄 Algorithme d'Exécution

### Étape 1 : Modéliser Conception (Classes / DB)
*Objectif : Transformer des entités conceptuelles en diagramme technique.*
1. **Lecture** : Charger le template `resources/spec-mermaid.md` pour la syntaxe précise.
2. **Identification** :
   - Identifier les **Classes** (Entities / Models).
   - Identifier les **Attributs** (Types précis si possible : int, string, datetime).
   - Définir les **Relations** (Cardinalités 1-n, n-n, Composition, Agrégation/Association).
3. **Génération** : Écrire le code Mermaid en respectant l'en-tête `classDiagram`.
4. **Production** : Insérer le bloc dans le fichier Markdown de conception.

## ✓ Points de Contrôle
Validations obligatoires avant de considérer le skill terminé :
1. **Syntaxe** : Le bloc Mermaid est valide (`classDiagram`, relations correctes).
2. **Compréhension** : Le diagramme reflète correctement les contraintes cardinales.
3. **Approbation Développeur** : Confirmer que la conception technique correspond à l'attente.

## 🚫 Interdictions
1. **Types Flous** : Éviter les types génériques si possible (préférer `int`, `string`, `datetime` à `data`).
2. **Cardinalités Incohérentes** : Vérifier que les relations one-to-many ou many-to-many sont explicites.

## ⚙️ Standards & Conventions
1. **Source de Vérité** : `resources/spec-mermaid.md`.
2. **Conventions** :
   - Noms de classes en PascalCase (ex: `UserProfile`).
   - Attributs en camelCase ou snake_case (cohérence projet).

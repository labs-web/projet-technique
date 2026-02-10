# Capacité : Modélisation Diagramme de Classes

## Contexte
Transformation d'une analyse fonctionnelle ou d'entités en structure objet (Classes UML).

## Règles Techniques

### 1. Définition des Classes
- **Format** : `class [NomPascalCase] { ... }`
- **Attributs** : `+[Type] [nomCamelCase]` (Visibilité publique par défaut pour l'analyse).
- **Méthodes** : `+[TypeRetour] [verbeAction]()`.

### 2. Relations (Cardinalités)
- **Héritage** : `Enfant --|> Parent : extends`
- **Composition** : `Tout *-- Partie : contient`
- **Agrégation** : `Conteneur o-- Contenu : possède`
- **Association** : `A --> B : utilise` (ou `1 "rôle" * "rôle"`)

### 3. Typage
- Utiliser des types **génériques UML** (String, Integer, Boolean, DateTime) et non spécifiques au langage cible (pas de `int`, `varchar`...).

### 4. Bonnes Pratiques
- Limiter à **10 classes** par diagramme principal pour la lisibilité.
- Regrouper les classes par domaine fonctionnel (Namespace ou Package si supporté).

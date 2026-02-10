# Capacité : Syntaxe Mermaid

## Contexte
Standardisation de la création de diagrammes via la syntaxe Mermaid.

## Règles Techniques

### 1. Structure de Base
Tout diagramme doit être encapsulé :
```mermaid
[type-diagramme]
    [contenu]
```

### 2. Conventions de Style
- **Orientation** : De haut en bas (`TD` ou `TB`).
- **Nœuds** : Utiliser des IDs simples (`ClassA`) et des labels clairs (`"Label"`).
- **Commentaires** : Utiliser `%% ` pour commenter le code mermaid.

### 3. Interdictions
- Ne **JAMAIS** utiliser de styles CSS inline complexes (privilégier la lisibilité).
- Ne **JAMAIS** inclure des caractères spéciaux non échappés dans les labels.

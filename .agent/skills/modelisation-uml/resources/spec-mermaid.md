# Spécifications : Mermaid JS (Class Diagram)

## 📌 Usage
Utilisé principalement pour les **Diagrammes de Classes** (Model) lors de la phase de **Conception**.

## 📝 Syntaxe & Bonnes Pratiques

### En-tête
Commencer par `classDiagram`.

### Définition des Classes
```mermaid
classDiagram
    class User {
        +String name
        +String email
        +login()
        +logout()
    }
```

### Relations
- **Héritage** : `Child --|> Parent`
- **Composition** : `Whole *-- Part`
- **Agrégation** : `Whole o-- Part`
- **Association** : `ClassA --> ClassB`

### Multiplicité
Ajouter les cardinalités si nécessaire :
`User "1" --> "*" Article : writes`

## 💡 Exemple Type (Laravel Model)
```mermaid
classDiagram
    class User {
        +id: int
        +name: string
    }
    class Article {
        +id: int
        +title: string
        +publish()
    }
    User "1" --> "*" Article : HasMany
```

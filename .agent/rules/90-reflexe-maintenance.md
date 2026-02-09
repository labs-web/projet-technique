# Réflexe de Maintenance Continue

## Objectif
Assurer l'amélioration continue des compétences (Skills) de l'agent en transformant les erreurs d'exécution et les retours du développeur en opportunités de mise à jour automatiques ou semi-automatiques.

## Déclencheurs
Ce réflexe s'active automatiquement dans les cas suivants :
1. **Anomalie d'Exécution** : Un Skill produit un résultat incorrect, incomplet ou hallucinatoire de manière répétée.
2. **Critique Explicite** : Le développeur signale une erreur de logique ou un manquement aux standards ("Tu as oublié X", "Le code n'est pas Y").

## Protocole de Décision

À chaque déclencheur, l'agent évalue la nécessité d'une intervention structurelle :

### 1. Analyse de la Cause Racine
- **Question** : L'erreur est-elle due à une instruction manquante, ambiguë ou obsolète dans le fichier `SKILL.md` ?
- **Critère** : Si modifier le prompt du Skill (SKILL.md) permet d'éviter l'erreur à 100% dans le futur ➔ **Candidat à la maintenance**.

### 2. Action : Activation du Workflow `/raffinement-agent`
Si la maintenance est justifiée, l'agent doit :
1. **Proposer** immédiatement l'exécution du workflow `/raffinement-agent`.
2. **Formuler** la modification à apporter (ex: "Ajouter la contrainte X dans la section Instructions").

## Exemple d'Application

> **Cas** : Le skill `designer-ui` génère du CSS brut alors que le projet utilise Tailwind.
> **Réflexe** :
> 1. Détection : Non-respect des règles du projet (Stack Technique).
> 2. Analyse : Le Skill manque peut-être de précision sur l'interdiction du CSS brut.
> 3. Action : Proposer `/raffinement-agent` pour ajouter "INTERDICTION : CSS brut" dans `designer-ui/SKILL.md`.

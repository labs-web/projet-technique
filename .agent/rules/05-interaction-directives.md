---
trigger: always_on
---

# Directives d'Interprétation des Commentaires

## Instructions Agent (`ia :`)
L'agent doit analyser le code à la recherche de commentaires préfixés par `ia :` (ou `IA :`, `Ia :`).
Lorsqu'un tel commentaire est détecté, l'agent doit **exécuter l'instruction contenue** à l'intérieur du commentaire.

Cette règle s'applique à tous les langages, notamment :
- **Markdown / HTML** : `<!-- ia : <instruction> -->`
- **PHP / JS / TS** : `// ia : <instruction>` ou `/* ia : <instruction> */`
- **CSS** : `/* ia : <instruction> */`

## Notes Développeur (`TODO :`)
L'agent doit ignorer les commentaires préfixés par `TODO :` (ou `todo :`). Ils sont destinés exclusivement au développeur. L'agent ne doit pas tenter de réaliser ces tâches spontanément, sauf si l'instruction "ia :" le demande explicitement.

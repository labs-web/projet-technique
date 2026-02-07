---
description: Workflow d'évolution métier. Change une règle de gestion.
---

# Workflow : Évolution Métier (`/update-logic`)

*   **Objectif** : Changer une règle de gestion (ex: limite de publication, calcul de dates).
*   **Périmètre** : Couche Service.
*   **Flux** :
    1.  **Skill** `backend-business` : Modifie le code dans `app/Services/`.
    2.  **Validation** : Vérifie que le changement n'impacte pas l'interface publique des méthodes (signature). Si oui -> déclencher `/update-http`.
*   **Interdit** : Modifier les Vues ou les Controllers directement.

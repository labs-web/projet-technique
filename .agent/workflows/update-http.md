---
description: Workflow d'ajustement API/HTTP. Change un code de retour ou une validation.
---

# Workflow : Ajustement API/HTTP (`/update-http`)

*   **Objectif** : Changer un code de retour, ajouter un filtre d'URL, modifier une validation d'entrée.
*   **Périmètre** : Couche HTTP (Entrée/Sortie).
*   **Flux** :
    1.  **Skill** `backend-http` : Modifie le Controller, le FormRequest ou la Resource API.
*   **Interdit** : Mettre de la logique métier dans le Controller. Tout traitement complexe doit rester dans le Service.

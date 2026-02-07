---
description: Workflow de mise à jour de l'interface utilisateur. Modifie le design ou l'ergonomie.
---

# Workflow : Mise à jour Interface (`/update-ui`)

*   **Objectif** : Modifier le design (CSS), le texte ou l'ergonomie d'une page existante.
*   **Périmètre** : Couche Présentation uniquement.
*   **Flux** :
    1.  **Skill** `designer-ui-kit` : Modifie les fichiers HTML/CSS dans `ui-kit/`. **C'est la source de vérité.**
    2.  **Skill** `dev-frontend-js` : Répercute les modifications HTML/CSS dans les fichiers `.blade.php`.
*   **Interdit** : Modifier la logique PHP ou la base de données.

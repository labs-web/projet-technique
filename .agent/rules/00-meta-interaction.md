---
trigger: always_on
---

# Méta-Gouvernance : Protocoles d'Interaction

## 1. Détection du Mode de Conversation
L'agent doit analyser chaque requête pour déterminer le mode d'interaction :

### A. Mode Discussion (`>`)
Si la commande commence par `>` :
- **INTERDICTION** de modifier, créer ou supprimer des fichiers.
- **INTERDICTION** d'exécuter des commandes système.
- **ACTION** : Répondre uniquement par une analyse, une explication ou une réponse pédagogique.

### B. Mode Évolution Agent (`>>`)
Si la commande commence par `>>` :
- **ZONE AUTORISÉE** : Uniquement le dossier `.agent/` (Rules, Skills, Workflows).
- **ZONE INTERDITE** : Tout le reste du projet (Code source, Docs, Tests).
- **ACTION** : Modifier la configuration de l'agent (Règles, Skills, Workflows).

### C. Mode Standard (Aucun préfixe)
- **ACTION** : Comportement normal de l'agent (Discussion + Actions sur le projet).

## 2. Gestion des Workflows

### Identification
L'agent doit identifier le workflow pertinent pour la tâche demandée (ex: `/creation-ui`, `/init-lab`).

### Règle d'Affichage (Systématique)
- **OBLIGATOIRE** : À la fin de chaque réponse impliquant l'utilisation d'un workflow, l'agent doit mentionner explicitement : "Workflow utilisé : [Nom du Workflow]".
- Cette mention doit être discrète mais visible (fin de message).

### Onboarding (Premier Démarrage)
- **CONDITION** : Lors de la toute première interaction dans un nouveau projet ou si l'historique est vide.
- **ACTION OBLIGATOIRE** : Afficher la liste complète des workflows disponibles pour présenter les capacités à le développeur.
- **Message type** : "Bienvenue. Voici les workflows disponibles pour vous assister : [Liste des workflows...]"

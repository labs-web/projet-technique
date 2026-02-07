---
description: Workflow d'évolution métier. Change une règle de gestion.
---

# Workflow : Évolution Métier (`/update-logic`)

## 1. Contexte & Flux Global
**Objectif** : Modifier une règle métier sans impacter l'interface externe si possible.
**Flux Type** : `[Nouvelle Règle]` → `[Service Modifié]` → `[Validation]`

## 2. Exécution

### Étape 1 : Implémentation Métier
> **Skill responsable** : `backend-business`
> **Flux Data** : 📥 `[Nouvelle Règle]` → 📤 `[Service Modifié]`

**Instructions** :
1. Modifier le code du Service concerné dans `app/Services/`.
2. Vérifier si la signature de la méthode publique a changé.
3. **STOP** : Demander la validation du développeur.

**Validation** : Logique métier validée par le développeur.

---

### Étape 2 : Vérification d'Impact (Conditionnelle)
> **Skill responsable** : `backend-http`
> **Flux Data** : 📥 `[Service Modifié]` → 📤 `[Controller Vérifié]`

**Instructions** :
1. SI la signature a changé : Déclencher le workflow `/update-http`.
2. SINON : Vérifier que le contrôleur fonctionne toujours avec la nouvelle logique.
3. **STOP** : Demander la validation du développeur.

**Validation** : Non-régression validée par le développeur.

---

## 3. Critères de Qualité
- [ ] **Isolation** : La logique ne doit pas fuir dans le contrôleur.
- [ ] **Types** : Le typage strict est respecté.

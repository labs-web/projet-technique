---
description: Workflow d'amélioration continue des Skills (Post-Mortem).
---

# Workflow : Raffinement de Skill (`/refine-skill`)

## 1. Contexte & Objectif
**Déclencheur** : Lancé par le développeur après une exécution de workflow où des frictions, erreurs ou manques ont été identifiés.
**Objectif** : Mettre à jour le fichier `SKILL.md` et ses ressources pour éviter que le problème ne se reproduise.
**Philosophie** : "Si ça fait mal une fois, c'est une erreur. Si ça fait mal deux fois, c'est un choix." -> On corrige le Skill.

---

## 2. Étapes d'Exécution

### Étape 1 : Analyse du "Post-Mortem"
> **Flux Data** : 📥 `[Nom du Skill utilisé]` + `[Problèmes rencontrés]`

**Instructions** :
1. Demander au développeur quel Skill est concerné (si non évident).
2. Lister les points de friction rencontrés durant la session précédente (ex: Commande qui plante, règle oubliée, préférence utilisateur non respectée).
3. Analyser le fichier `SKILL.md` actuel.

---

### Étape 2 : Proposition d'Amélioration
> **Skill responsable** : `expert-skills` (ou modification directe par l'agent)

**Instructions** :
1. Identifier la section à modifier dans le Skill :
   - **Règles Critiques** : Pour les blocages majeurs (ex: `&&` dans PowerShell).
   - **Ressources** : Pour des commandes ou versions obsolètes.
   - **Algorithme** : Pour une logique défaillante.
2. Rédiger les modifications proposées (Format Diff ou Explicite).
3. **STOP** : Valider avec le développeur.

---

### Étape 3 : Application & Versionning
**Instructions** :
1. Appliquer les modifications au fichier `.agent/skills/.../SKILL.md` (et ressources associées).
2. Ajouter une entrée dans une section "Changelog" ou "Améliorations" du Skill (optionnel mais recommandé).
3. Confirmer que le Skill est "Prêt pour le prochain combat".

---

## 3. Critères de Qualité

- [ ] **Précision** : La règle ajoutée doit être spécifique et actionnable par l'IA.
- [ ] **Non-Régression** : Ne pas casser le fonctionnement nominal du Skill.
- [ ] **Pédagogie** : Expliquer pourquoi on ajoute cette règle (Contexte).
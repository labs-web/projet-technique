---
description: Workflow unifié pour l'analyse fonctionnelle et la modélisation UML (Use Cases).
---

# Workflow : Analyse Fonctionnelle & UML (`/analyse-uml`)

## 1. Contexte & Flux Global
**Objectif** : Formaliser le besoin métier, structurer les lots (versions), et produire les diagrammes associés via un menu interactif.
**Flux Type** : `[Analyse de la Demande]` → `[Confirmation ou Menu]` → `[Exécution de l'Action]`

## 2. Exécution

### Étape 1 : Analyse de la Demande

**Analyser le message de l'utilisateur** pour détecter l'action appropriée.

**Logique de Détection** :
- Mots-clés **"besoin"**, **"analyse globale"**, **"initialiser"**, **"analyser besoin"** → Détecter **Action A**
- Mots-clés **"planif"**, **"roadmap"**, **"versions"**, **"découpage"**, **"stratégie"** → Détecter **Action B**
- Mots-clés **"créer"**, **"version"**, **"v1"**, **"v2"**, **"v3"**, **"initialiser version"** → Détecter **Action C**
- Mots-clés **"diagramme"**, **"usecase"**, **"puml"**, **"modéliser"**, **"générer"** → Détecter **Action D**

---

### Étape 2 : Routage Conditionnel

#### Cas 1 : Action Détectée avec Confiance

**Si une action a été clairement identifiée à l'Étape 1**, afficher directement la confirmation :

**Format de Confirmation** :
```
📋 Demande Identifiée

Vous souhaitez [Description de l'action détectée].

Action détectée : Action [X] - [Nom de l'action]
→ [Description courte]

Voulez-vous procéder avec cette action ? (Tapez [X] pour confirmer, ou choisissez une autre option A/B/C/D)
```

**STOP** : Attendre la confirmation du développeur.

#### Cas 2 : Aucune Action Détectée ou Commande Sans Message

**Si aucune action claire n'est détectée** (commande invoquée seule ou message ambigu), afficher le menu complet :

> **Actions disponibles (Skill : analyste-uml)** :
>
> **A.** Analyser le Besoin Global  
> → Transformer `besoin.md` en liste structurée de fonctionnalités
>
> **B.** Planifier les Versions (Stratégie)  
> → Définir la roadmap et le découpage en versions
>
> **C.** Initialiser une Version  
> → Créer l'arborescence et les fichiers d'analyse pour une version
>
> **D.** Générer Use Case (Par Version)  
> → Traduire l'analyse textuelle en diagramme PlantUML
>
> **Quelle action souhaitez-vous exécuter ?** (Tapez A, B, C ou D)

**STOP** : Attendre la sélection du développeur.

---

### Étape 3 : Exécution de l'Action Choisie

Selon le choix du développeur, exécuter l'action correspondante du skill `analyste-uml`.

#### Si Action A sélectionnée
- **Skill Cible** : `analyste-uml`
- **Action** : `Action A : Analyser le Besoin Global`
- **Inputs Fournis** : `docs/1.besoin/besoin.md`
- **STOP** : Valider le contenu de `docs/2.analyse/global/analyse-global.md`

#### Si Action B sélectionnée
- **Skill Cible** : `analyste-uml`
- **Action** : `Action B : Planifier les Versions (Stratégie)`
- **Inputs Fournis** : `docs/2.analyse/global/analyse-global.md`
- **STOP** : Valider le contenu de `docs/2.analyse/global/planification-version.md`

#### Si Action C sélectionnée
- **Skill Cible** : `analyste-uml`
- **Action** : `Action C : Initialiser une Version`
- **Inputs Fournis** :
  - `docs/2.analyse/global/analyse-global.md`
  - `docs/2.analyse/global/planification-version.md`
  - Demander au développeur : "Quelle(s) version(s) ? (Toutes ou v1, v2, etc.)"
- **STOP** : Vérifier la présence des dossiers `vX-[nom]` et fichiers `analyse-vX-[nom].md`

#### Si Action D sélectionnée
- **Skill Cible** : `analyste-uml`
- **Action** : `Action D : Générer Use Case (Par Version)`
- **Inputs Fournis** : 
  - Demander au développeur : "Quelle(s) version(s) ? (Toutes ou v1, v2, etc.)"
  - Fichiers `analyse-vX-[nom].md` correspondants
- **STOP** : Vérifier la cohérence Texte/Diagramme et la syntaxe PlantUML

---

## 3. Critères de Qualité
- **Découvrabilité** : Le développeur voit toutes les actions disponibles
- **Cohérence** : Le diagramme reflète exactement l'analyse textuelle
- **Standard** : Respect de la syntaxe PlantUML (`left to right direction`)
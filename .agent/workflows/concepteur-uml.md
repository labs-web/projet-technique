---
description: Workflow de création de diagrammes de conception (Classes/DB).
---

# Workflow : Conception UML

## 1. Contexte & Flux Global
**Objectif** : Formaliser l'architecture technique et le modèle de données (Classes/DB).
**Flux Type** : `[Analyse/Entités]` → `[Génération Diagramme]` → `[Validation]`

## 2. Exécution

### Étape 1 : Génération Diagramme (Conception)
> **Skill responsable** : `concepteur-uml`
> **Flux Data** : 📥 `[Liste Entités]` → 📤 `[Bloc Mermaid]`

**Instructions** :
1. Lire la liste des entités ou le modèle de données validé.
2. Utiliser le skill `concepteur-uml` pour traduire ces entités en diagramme Mermaid.
   - Définir les Classes, Attributs (avec types) et Relations.
   - Assurer les bonnes cardinalités.
3. Intégrer le bloc `mermaid` dans le document de conception (ex: `implementation_plan.md` ou `docs/3.conception/`).
4. **STOP** : Demander la validation du diagramme technique.

**Validation** : Le diagramme Mermaid représente correctement la structure de données.

---

## 3. Critères de Qualité
- [ ] **Précision** : Les types de données sont explicites (int, string, etc.).
- [ ] **Relations** : Les cardinalités sont correctes et logiques.
- [ ] **Standard** : Syntaxe Mermaid `classDiagram` valide.

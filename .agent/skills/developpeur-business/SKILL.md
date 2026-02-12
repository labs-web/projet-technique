---
name: developpeur-business
description: Implémente les Services, la logique métier, et définit les Policies/Gates.
---

# Skill : Développeur Business

## 🎯 Périmètre Global
**Mission** : Encapsuler la logique métier complexe et les règles d'autorisation dans des classes dédiées (Services, Actions, Policies), garantissant l'indépendance vis-à-vis du framework HTTP (Contrôleurs).

### 🚫 Interdictions Globales (Règles d'Or)
1. **No HTTP** : Ne jamais importer `Illuminate\Http\Request` ou `Response` dans un Service.
2. **No Controller Logic** : Ne jamais écrire de logique métier dans un Contrôleur -> Déléguer au Service.
3. **Atomicité** : Utiliser des transactions DB (`DB::transaction`) pour toute opération impliquant plusieurs écritures.
4. **Typage Strict** : Toujours utiliser `declare(strict_types=1);` et typer arguments/retours.

---

## ⚡ Actions (Capacités Atomiques)

### Action A : Concevoir la Couche Métier
> **Description** : Analyser les besoins fonctionnels et produire le plan technique détaillé pour le business (Services, Policies).
> **Capacité** : Voir `capacités/capacité-conception-metier.md`.
- **Entrées** :
  - `docs/2.analyse/vX-[nom]/analyse-vX-[nom].md` (Fonctionnel).
  - `docs/3.conception/global/classes-global.mermaid` (Classes).
- **Sorties** : `docs/3.conception/vX-[nom]/conception-business-vX-[nom].md`.
- **❌ Interdictions** : Ne pas contredire le diagramme de classes validé.
- **✅ Definition of Done** : Liste exhaustive des Services/Méthodes et Policies à implémenter.
- **📝 Instructions** : Utiliser la capacité dédiée.

### Action B : Créer Service Métier
> **Description** : Créer la structure d'une classe de Service pour un domaine donné.
> **Capacité** : Voir `capacités/capacité-service-metier.md`.
- **Entrées** : Nom du domaine (ex: `Article`), Méthodes requises.
- **Sorties** : `app/Services/[Nom]Service.php`.
- **❌ Interdictions** : Pas de dépendance HTTP.
- **✅ Definition of Done** : Classe créée, typée, prête à recevoir la logique.
- **📝 Instructions** : Utiliser la capacité dédiée.

### Action C : Implémenter Logique (Méthode)
> **Description** : Coder le corps d'une méthode de service (Algorithme, Transaction, Event).
> **Capacité** : Voir `capacités/capacité-service-metier.md` (Extension).
- **Entrées** : Signature de la méthode, Règles de gestion.
- **Sorties** : Code PHP dans la méthode.
- **✅ Definition of Done** : Logique isolée, testable, transactionnelle si besoin.
- **📝 Instructions** : Implémenter le code métier pur.

### Action D : Définir Policy (Autorisation)
> **Description** : Créer et implémenter une Policy pour sécuriser l'accès aux ressources.
> **Capacité** : Voir `capacités/capacité-policy.md`.
- **Entrées** : Modèle cible (ex: `Article`).
- **Sorties** : `app/Policies/[Model]Policy.php`.
- **✅ Definition of Done** : Méthodes standard implémentées (`view`, `create`, `update`, `delete`).
- **📝 Instructions** : Utiliser la capacité dédiée.

---

## 🔄 Scénarios d'Exécution (Algorithmes)

### Scénario 1 : Implémentation Feature (Flux Standard)
*À utiliser dans le cadre du workflow `/impl-feature`.*
1. **Design** : Exécuter **Action A** pour valider l'architecture des services.
2. **Sécurité** : Exécuter **Action D** pour créer la Policy associée au modèle.
3. **Structure** : Exécuter **Action B** pour créer le Service.
4. **Logique** : Exécuter **Action C** pour implémenter chaque méthode métier.

---

## ⚙️ Standards & Conventions
1. **Injection** : Préférer l'injection de dépendance dans le constructeur.
2. **Typage** : `strict_types=1` obligatoire sur tous les fichiers PHP.
3. **Nommage** : Verbe + Nom pour les méthodes (ex: `publishArticle`, `archiveUser`).

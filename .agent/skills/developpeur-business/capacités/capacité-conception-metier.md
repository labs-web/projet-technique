# Capacité : Conception Technique Métier

## Description
Rédiger le plan technique de la couche Business pour une version (Services, Policies, Règles).

## Entrées
- `docs/2.analyse/vX-[nom]/analyse-vX-[nom].md` (Analyse Version)
- `docs/3.conception/global/classes-global.mermaid` (Diagramme Classes Global)
- `docs/3.conception/vX-[nom]/classes-vX-[nom].mermaid` (Diagramme Classes Version)

## Sorties
- `docs/3.conception/vX-[nom]/conception-business-vX-[nom].md`

## ❌ Interdictions Spécifiques
- Ne pas inventer de règles métier qui contredisent l'analyse.

## ✅ Points de Contrôle (Definition of Done)
- Liste exhaustive des Services à créer ou modifier.
- Liste des méthodes publiques avec leurs signatures (entrées/sorties).
- Liste des Policies nécessaires pour sécuriser les actions.
- Identification des Events/Listeners si nécessaire.

## 📝 Instructions Détaillées
1. **Analyser** les diagrammes de classes et les cas d'utilisation.
2. **Identifier** les Services nécessaires (1 Service = 1 Domaine Métier).
3. **Définir** les méthodes publiques (Actions) pour chaque Service.
4. **Spécifier** les règles de sécurité (Policies) pour chaque action.
5. **Rédiger** le document de conception technique Business.

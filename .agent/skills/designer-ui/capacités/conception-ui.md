# Capacité : Conception UI (Analyste UI)

## Objectif
Définir la structure visuelle et fonctionnelle d'une page ou d'un composant complexe avant son développement. Cette capacité repose sur l'analyse de l'existant (Manifestes) pour éviter la duplication et garantir la cohérence du Design System.

## Processus Général

### 1. Décomposition (Atomic Design)
Découper la demande (Maquette/Description) en éléments hiérarchiques :
- **Layout** : Structure globale (Header, Sidebar, Footer, Content).
- **Organismes** : Sections autonomes (ex: Formulaire de contact, Grille de produits).
- **Molécules** : Groupes fonctionnels (ex: Champ de recherche, Card article).
- **Atomes** : Éléments indivisibles (ex: Bouton, Input, Label, Tag).

### 2. Gap Analysis (Analyse de l'existant)
Consulter systématiquement les manifestes du UI Kit pour identifier ce qui existe déjà.

**Sources de Vérité :**
- `ui-kit/atoms-manifest.yaml`
- `ui-kit/molecules-manifest.yaml`
- `ui-kit/components-manifest.yaml`

**Matrice de Décision :**
- **Existe** -> Utiliser (Noter le chemin et le nom).
- **Existe partiellement** -> Étendre (Action Update).
- **Manquant** -> Créer (Action Create).

### 3. Spécification d'Assemblage
Définir comment les composants s'imbriquent.
- Identifier les propriétés configurables (Props) nécessaires pour le contexte.
- Définir les états (Loading, Empty, Error).
- Vérifier la compatibilité Responsive.

## Format de Sortie (Livrable)
Un plan de conception (Markdown) listant :
1. **Layout cible** (ex: `layouts/app-layout.html`).
2. **Zones de contenu**.
3. **Inventaire des Composants** :
   - [X] `Button` (existant : `atoms/button.html`)
   - [ ] `ProductCard` (à créer : `molecules/product-card.html`)
4. **Instructions d'intégration**.

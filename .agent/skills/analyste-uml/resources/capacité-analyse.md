# Spécifications : Analyse Globale

## 🎯 Objectif
Définir le **format et les règles** pour transformer une expression de besoins brute en une liste structurée de fonctionnalités métier.

## 📤 Nature du Livrable
Un document Markdown listant les acteurs et fonctionnalités de l'application, sans aucun élément de conception technique.

## 📝 Format et Structure

### Sections Obligatoires

1. **Introduction**
   - Contexte du projet (1-2 phrases maximum)
   - Objectif global de l'application

2. **Acteurs**
   - Liste des acteurs identifiés
   - Format : Liste à puces minimaliste
   - Exemple :
     ```markdown
     - Visiteur
     - Utilisateur Connecté
     - Administrateur
     ```

3. **Règles de Gestion (Business Rules)**
   - Contraintes métier, règles de calcul, permissions globales
   - Format : Liste catégorisée ou simple liste à puces
   - Exemple :
     ```markdown
     ### Permissions
     - Un article ne peut être supprimé que par son auteur ou un administrateur.
     
     ### Contraintes
     - Un article doit avoir au moins une catégorie.
     ```

4. **Fonctionnalités**
   - Liste exhaustive des fonctionnalités
   - Format : **Verbe d'action + Objet métier**
   - Regroupement par acteur ou par domaine fonctionnel
   - Exemple :
     ```markdown
     ### Visiteur
     - Consulter la liste des articles
     - Lire un article complet
     - S'inscrire
     
     ### Utilisateur Connecté
     - Se connecter / Se déconnecter
     - Rédiger un article
     - Modifier ses articles
     ```

## ⚠️ Règles et Contraintes

### Interdictions Strictes
- **INTERDICTION** d'inclure des éléments de conception :
  - Classes, Entités, Modèles
  - Tables de base de données
  - Architecture technique
  - Diagrammes de classes
- **INTERDICTION** d'inventer des besoins non exprimés dans le document source
- **INTERDICTION** d'anticiper ou inventer un découpage en versions
- **INTERDICTION** d'utiliser des termes vagues comme "Accéder au Back-Office".
  - **Correction** : Identifier les écrans réels (ex: "Visualiser les statistiques", "Accéder au Menu Principal").

### Principes de Qualité
- **Exhaustivité** : Toutes les fonctionnalités du besoin doivent être extraites
- **Clarté** : Utiliser systématiquement le format "Verbe d'action + Objet métier"
- **Séparation des Préoccupations** : 
  - L'analyse globale = **QUOI** (fonctionnalités)
  - La planification = **QUAND** / **COMMENT** (découpage en versions)
- **Source de Vérité** : Le document source est la seule référence autorisée


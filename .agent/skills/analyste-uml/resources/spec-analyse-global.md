# Spécifications : Analyse Globale

## 📌 Usage
Utilisée lors de l'**Action A : Analyser le Besoin Global** pour transformer l'expression de besoins brute en une liste structurée de fonctionnalités.

## 🎯 Objectif
Déterminer les **fonctionnalités de l'application** afin de construire le **Diagramme de Cas d'Utilisation**.

## 📤 Livrable
**Fichier** : `fonctionnalite-global.md`  
**Emplacement** : `docs/2.analyse/global/fonctionnalite-global.md`

## 📝 Contenu du Livrable

### Structure du Fichier

Le fichier doit contenir **UNIQUEMENT** les fonctionnalités métier, **SANS conception** (classes, tables, architecture).

#### Sections Obligatoires

1. **Introduction**
   - Contexte du projet (1-2 phrases)
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

3. **Fonctionnalités**
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

## ⚠️ Règles d'Or

### Interdictions Strictes
- **INTERDICTION** d'inclure des éléments de conception :
  - Classes, Entités, Modèles
  - Tables de base de données
  - Architecture technique
  - Diagrammes de classes
- **INTERDICTION** d'inventer des besoins non exprimés dans `besoin.md`
- **INTERDICTION** de créer la liste des versions si elle n'est pas présente dans `besoin.md`

### Principes Directeurs
- **Chaque Action lit le besoin directement** : Ne pas dupliquer des informations si elles seront lues à nouveau par une action suivante
- **Séparation des Préoccupations** : 
  - L'analyse globale = **QUOI** (fonctionnalités)
  - La planification (Action B) = **QUAND** / **COMMENT** (découpage en versions)
- **Source de Vérité** : Le fichier `besoin.md` est la seule source d'information


## 🔄 Processus d'Extraction

1. **Lecture** : Analyser `docs/1.besoin/besoin.md`
2. **Identification** :
   - Extraire les acteurs (Qui ?)
   - Extraire les fonctionnalités (Quoi ?)
   - Format : Verbe d'action + Objet métier
3. **Détection Versions** :
   - Rechercher les sections "Roadmap", "Versions", "Lotissement"
   - Si présentes, extraire **uniquement** les métadonnées (Nom + Description courte)
4. **Consolidation** :
   - Créer le fichier `fonctionnalite-global.md`
   - Structurer selon le template ci-dessus
5. **Validation** :
   - Vérifier l'exhaustivité par rapport à `besoin.md`
   - Vérifier l'absence d'éléments de conception

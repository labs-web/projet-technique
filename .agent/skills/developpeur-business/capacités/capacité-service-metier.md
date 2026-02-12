# Capacité : Créer Service Métier

## Description
Créer une classe de Service pour encapsuler un domaine métier.

## Entrées
- Nom du domaine (ex: `Article`), Méthodes requises.

## Sorties
- `app/Services/[Nom]Service.php`.

## ❌ Interdictions Spécifiques
- Ne pas créer de Service "Fourre-tout". Un Service = Un Domaine.
- Ne pas importer `Illuminate\Http\Request` ou `Response`.

## ✅ Points de Contrôle (Definition of Done)
- La classe est dans le namespace `App\Services`.
- Les méthodes sont typées (arguments et retour).
- Aucune dépendance à `Request` ou `Auth::user()` (passer l'user en paramètre).

## 📝 Instructions Détaillées
1. Créer le dossier `app/Services` si inexistant.
2. Créer la classe PHP.
3. Définir les méthodes publiques correspondant aux cas d'utilisation.

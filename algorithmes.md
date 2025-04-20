# Rendu 3 – Deuxième Raffinement

---

## 1. Traduction des associations en attributs


- La classe `Seance` contient :
  - `film : Film` (le film projeté)
  - `salle : Salle` (la salle où a lieu la séance)

- La classe `Reservation` contient :
  - `seance : Seance` 
  - `utilisateur : Utilisateur` 

- La classe `Administrateur` est liée à :
  - `Film`
  - `Seance` 


## 2. Traduction des agrégations / compositions

- Une `Seance` utilise un `Film` et une `Salle`, mais ces derniers peuvent exister sans la séance. C’est donc une agrégation.
- Une `Reservation` est liée à un `Utilisateur`. Si l’utilisateur est supprimé, ses réservations peuvent l’être aussi, mais ce n’est pas automatique. C’est également une agrégation.
- Une `Reservation` est fortement liée à une `Seance`. Si une séance est supprimée, ses réservations doivent l’être aussi. Cela correspond à une composition.

## 3. Traduction des diagrammes en algorithmes

### Algorithme : Réserver une séance
SI utilisateur est connecté ALORS
    Afficher la liste des films disponibles
    Laisser l’utilisateur choisir un film
    Afficher les séances disponibles pour ce film
    Laisser l’utilisateur choisir une séance
    SI places disponibles > 0 ALORS
        Demander le nombre de places souhaitées
        SI nombre demandé ≤ places disponibles ALORS
            Demander les informations de paiement
            SI paiement validé ALORS
                Créer la réservation
                Décrémenter le nombre de places disponibles
                Changer l’état de la réservation → Confirmée
                Afficher "Réservation confirmée"
            SINON
                Afficher "Paiement échoué"
        SINON
            Afficher "Nombre de places insuffisant"
    SINON
        Afficher "Séance complète"
SINON
    Afficher "Veuillez vous connecter pour réserver"

### Algorithme : Connexion utilisateur 


Demander email et mot de passe
Rechercher l’utilisateur dans la base de données
SI utilisateur trouvé ET mot de passe correct ALORS
    Connexion réussie
SINON
    Afficher "Identifiants incorrects"


### Algorithme : Ajout d’un film

SI administrateur est connecté ALORS
    Saisir les informations du film (titre, genre, durée)
    Vérifier que le titre n’existe pas déjà
    SI le titre est unique ALORS
        Enregistrer le film dans la base
        Afficher "Film ajouté avec succès"
    SINON
        Afficher "Titre déjà utilisé"
SINON
    Afficher "Accès non autorisé"

### Algorithme : Diagramme d'état de transition 

Quand l’utilisateur clique sur "Réserver"
    Créer une réservation → état = Créée
    Attendre les informations de paiement → état = EnAttentePaiement
    SI paiement validé → état = Confirmée
    SINON ou annulation → état = Annulée










 

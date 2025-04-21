# Projet : CineBook

**Auteurs :** Ines Hamdoun / Asma Ayari / Kenza Zouaoui 
**Matière :** Atelier de Génie Logiciel  

-----------------------------------

## 1. Sujet du projet

Développement d’une application de billetterie de cinéma en ligne. Elle permet aux utilisateurs de réserver des places, consulter les films à l'affiche et payer en ligne. Deux types d’utilisateurs : client et administrateur.

-------------------------------------
## 2. Introduction au projet
## objectifs : 	
.Offrir une expérience utilisateur fluide et moderne 
•	Réduire les files d’attente au cinéma 
•	Centraliser les statistiques et la gestion interne 

---------------------------------------
## 3. Spécifications générales : 
### Acteurs :
· Client (Utilisateur enregistré) : réserver un billet, consulter les films.
· Administrateur : gérer les films, les séances, les statistiques.

### Fonctionnalités :
Inscription / connexion 
Consulter les films et les séances 
Réserver un billet 
Consulter ses réservations
Ajouter/ modifier/ supprimer un film 
Ajouter/modifier/supprimer une séance
Voir les statistiques de fréquentation 

---------------------------------------

## 4. Cas d’utilisation principaux (haute priorité)
 1 Cas d’utilisation : Réserver un billet 
préconditions
. L'utilisateur est connecté
· Une séance est sélectionnée
. Il reste des places disponibles
. Un mode de paiement valide est choisi
Postconditions :
· La réservation est enregistrée
· Le nombre de places est mis à jour
· Une confirmation est envoyée à l'utilisateur


Condition	            1	2	3	4	5   6
Utilisateur connecté	F	T	T	T   T	T
Séance sélectionnée	    T	F	T	T	T	T
Places disponibles	    T	T	F	T	T	T
Paiement valide	        T	T	T	F	T	T
Réservation enregistrée	F	F	F	F	T	T
Places mise a jour   	F	F	F	F	T	T
Confirmation envoyée	F	F	F	F	T	T

--------

2 Cas d’utilisation : Consulter les films
Préconditions :
•	Aucune (fonction publique)
Postconditions :
•	La liste desfilms est attachée 
•	Les films sont classés par date ou popularité

Condition	                1	2
Films disponibles       	T	F
Liste affichée 	            T	F
Films triés correctement 	T	F


------------------------------------------------

Élément	            Type	           Attributs probables
Film	         Classe métier	      titre, durée, genre
Séance	         Classe métier	      dateHeure, salle, film, placesDisponibles
Salle	         Classe métier	      nom, nombrePlaces
Utilisateur  	 Classe métier	      nom, email, motDePasse, rôle (client/admin)
Réservation	     Classe métier	      utilisateur, séance, nbPlaces, statut
Paiement	     Classe métier	      mode, statut, montant, date

ASSOCIATIONS :

Un Film peut être joué dans plusieurs Séances

Une Séance a lieu dans une Salle

Une Séance concerne 1 Film

Un Utilisateur peut faire plusieurs Réservations

Une Réservation concerne 1 Séance
--------------------------------------------------
# Algorithme "reserver seance "

L’utilisateur est connecté

Il choisit un film

Il choisit une séance

Le système vérifie la disponibilité

L’utilisateur choisit le nombre de places

Le système vérifie les places

L’utilisateur valide et paie

Le système enregistre la réservation

Le système génère un billet

-------------------------
# Diagrammes de séquence

- DSUC1 : Réserver une séance → ![Diagramme DSUC1](Diagrams/DSUC1_reserver_seance.png)
-------------------------------------------------------
# algorithme "se connecter/s'inscrire"

🔁 Si l’utilisateur a déjà un compte :
L’utilisateur ouvre la page de connexion.

Il entre son identifiant (email ou nom d'utilisateur) et son mot de passe.

Le système vérifie les informations :

Si elles sont correctes → il est connecté et redirigé vers la page d’accueil.

Sinon → un message d’erreur s’affiche (“Identifiants incorrects”).

➕ Sinon, s’il n’a pas de compte (inscription) :
L’utilisateur ouvre la page d’inscription.

Il entre ses informations personnelles : nom, prénom, email, mot de passe, etc.

Le système :

Vérifie que l’email n’existe pas déjà.

Si c’est bon → il crée un nouveau compte.

Sinon → il affiche un message d’erreur (“Email déjà utilisé”).

L’utilisateur est connecté automatiquement après l’inscription réussie.
-------------------------------
# Diagrame de séquence 
- DSUC2 : Se connecter / S’inscrire → ![Diagramme DSUC2](Diagrams/DSUC2_connexion_inscription.png)
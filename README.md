# Troc-en-Stock  
Application de ventes aux enchères:
- Architecture microservices
- exécutables natifs avec GraalVM
- API REST + Mariadb (conteneurs séparés) pour chaque microservice
- PhpMyAdmin pour contrôler chaque base de données
- docker-compose de 8 conteneurs au total
- UI avec Angular (HttpClient, Observables, Directives, Services, Router, Guards...)
  
Pour exécuter le projet:  
1. Installer Docker ( https://docs.docker.com/get-docker/ )  
2. Créer un dossier "Troc-en-Stock"  
3. Télécharger les fichiers du dépôt Github (ArticleVendu.sql, Enchere.sql, Utilisateur.sql, docker-compose.yml) et les enregistrer dans le dossier "Troc-en-Stock"  
4. En ligne de commande, se positionner dans "Troc-en-Stock", puis exécuter la commande "docker-compose up -d"  
5. Dans le navigateur, entrer "localhost:8181", pour se connecter à PhpMyAdmin et importer des données:  
-> Utilisateur: root  
-> Mot de passe: mot-magique  
-> Pour chaque base de données, accéder à la table, onglet "importer", puis importer le fichier .sql correspondant  
6. Dans le navigateur, entrer "localhost:8080", pour accéder à la page d'accueil de Troc-en-Stock  
  
Règles d'utilisation:  
  
- Page d'accueil:  
  Affichage de tous les objets dont la date de fin d'enchères n'est pas encore dépassée (à la nanoseconde près)  
  N'affiche pas les objets vendus par l'utilisateur courant si celui-ci est authentifié  
  Possibilité de trier les objets par catégorie  
  Possible d'accéder aux détails d'un objet en vente sans être authentifié, mais authentification obligatoire pour pouvoir enchèrir  
    
- Barre de navigation:  
  Transformation du bouton "S'inscrire/Se connecter" lors de l'authentification de l'utilisateur (Bienvenue + pseudo)  
  Après la connexion/inscription, les onglets "Mes ventes" et "Mes enchères" n'apparaissent que si l'utilisateur courant est vendeur et/ou enchèrisseur  
  L'onglet "Déconnexion" supprime tous les éléments stockés en session utilisateur  
    
- Compte utilisateur:  
  Après la création d'un compte, possibilité de modifier les champs sauf "Pseudo", "Nom", "Prénom" et "Points"  
  Crédit de 100 points attribué automatiquement lors de la création du compte  
  Après la suppression du compte, retour automatique sur la page d'accueil 5 secondes après l'affichage de la suppression  
  Lorsque l'utilisateur consulte ses ventes et/ou ses enchères, possibilité de trier celles "en cours" et "terminées"  
  Si une vente est terminée, le prix de vente correspond à l'enchère la plus elevé + affichage du pseudo de l'acquéreur  
  Si une enchère est terminée, l'affichage est différent si l'utilisateur a remporté la vente ou non  
   
- Ventes:  
  L'utilisateur doit être authentifié pour pouvoir vendre un objet  
  Lors de la création d'une vente, l'utilisateur fixe une date de début des enchères; automatiquement la date de fin des enchères sera fixée 5 jours après  
  Après la création d'une vente, plus possible de la modifier, seulement la supprimer  
  Par défaut, le lieu de retrait de l'objet correspond à l'adresse du vendeur mais modification possible  
   
- Enchères:  
  L'utilisateur doit avoir suffisamment de points pour pouvoir enchérir sur un objet  
  Si pas encore d'enchère sur l'objet, l'enchère minimum sera la mise à prix + 1 points  
  Si déjà des enchères en cours, la nouvelle enchère sera au minimum équivalente à l'enchère la plus élevée + 1 points  

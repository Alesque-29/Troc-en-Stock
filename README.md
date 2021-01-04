# Troc-en-Stock  
Pour exécuter le projet:  
1. Installer Docker CE pour Mac ou Windows ( http://docker.com )  
2. Créer un dossier "Troc-en-Stock"  
3. Télécharger les fichiers du dépôt Github (ArticleVendu.sql, docker-compose.yml, Enchere.sql, Utilisateur.sql) et les enregistrer dans le dossier "Troc-en-Stock"  
4. En ligne de commande, se positionner dans "Troc-en-Stock", puis exécuter la commande "docker-compose up -d"  
5. Dans le navigateur, entrer "localhost:8181", pour se connecter à phpmyadmin et importer des données:  
-> Utilisateur: root  
-> Mot de passe: mot-magique  
-> Pour chaque base de données, accéder à la table, onglet "importer", puis importer le fichier .sql correspondant  
  
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
   
- Ventes:  
   
- Enchères:  
 

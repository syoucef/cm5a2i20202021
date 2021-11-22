# Introduction à Docker


docker run image_name : permet de créer et démarer une nouvelle instance de l'image (conteneur)

si l'image n'existe pas, elle sera téléchargée à partir de docker hub

docker run -d image_name:tag : permet de démarrer conteneur en arrière plan 

la valeur par défaut d'une image est latest

docker ps : permet de lister tous les conteneurs qui sont en cours d'exécution. Chaque conteneur dispose d'un identifiant unique 

docker ps -a : permet de lister tous les onteneur aver leurs statuts (Up, Exited Created) 

Exécuter une image du serveur nginx : ``docker run -d -p 9999:80 nginx``

Pour donner un nom précis à votre conteneur, on utilise --name. Exemple : ``docker run --name moningx -d -p 8989:80 nginx`` Cette commande permet de démarrer un conteneur dont le nom est ``moningnx``. Pour pouvoir y accéder de l'extérieur (du moteur), on utilise la notion de redirection des ports. Ici, on va utiliser le port  ``8989``pour y accéder comme ceci : ``localhost:8989`` 


Pour arrêtre un conteneur ``docker stop identifiant_conteneur``. Pour supprimer un conteneur, on doit d'abord l'arrêter : ``docker rm identifiant_conteneur``. 

Pour lister toutes vos images ``docker images``


Pour forcer la suppression d'une image ou d'un conteneur : ``docker rmi -f nom_image``


La commande ``exec`` permet d'exécuter une commande dans un conteneur démarré

Exemple : notre objectif est de démarrer un conteneur MySQL et d'exécuter le client mysql

Solution : ''docker run --name monserveur -e MYSQL_ROOT_PASSWORD=root -d mysql`` 




 

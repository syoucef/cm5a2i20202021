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

Solution : ``docker run --name monserveur -e MYSQL_ROOT_PASSWORD=root -d mysql``

Pour lancer mysql : ``docker exec -ti monserveur mysql --password``


Exercice : démarer un conteneur à partir de l'image ubuntu et puis installer java et exécuter un programme simple. 
 
 
 ``docker run -it ubuntu bash``  
 
 Une fois à l'intérieur du conteneur, vous pouvez  installer les outils dont vous avez besoin comme vous avez l'habitube de le faire en utilisant ubuntu. 

Si on veut installer par exemple Java, on procède de la façon suivante : on met d'abord à jour ``apt-get update``et puis ``apt-get install java``. Si on veut utiliser vim comme éditeur `` apt-get install vim``.  
  
  
Pour inspecter un contenur et avoir des détails sous forme d'un ficheir json ``docker inspect id_conteneur`` 

Pour avoir les logs d'un contenur : ``docker logs id_conteneur`` 

Pour redémarrer un conteneur : ``docker start id_conteneur`` 

Exercice : démarrer un conteneur nginx et changer le contenu du fichier index.html. 

La page index.html est par défaut dans le répertoire ``/usr/share/nginx/htm ``  

Notion de volume :


``docker volume``

```java 
Commands:
  create      Create a volume
  inspect     Display detailed information on one or more volumes
  ls          List volumes
  prune       Remove all unused local volumes
  rm          Remove one or more volumes
```



Pour faire "mapping volume" 


``docker run -dti -p 8080:80 -v /Users/syoucef/Desktop/dockerexample/mapage/:/usr/share/nginx/html/ --name myserverweeb nginx``

``docker run -tid --name webvolumebis -p 8691:80 --mount source=mesdonnees,target=/usr/share/nginx/html/ nginx`` 


Pour accéder aux volumes (sous mac) : 

`` docker run -it --privileged --pid=host debian nsenter -t 1 -m -u -n -i sh ``

Une fois à l'intéreiur du conteneur, les volumes se trouvent dans le dossier :  ``/var/lib/docker/volumes/``


La soslution ici : https://stackoverflow.com/questions/38532483/where-is-var-lib-docker-on-mac-os-x


Gestion des variables d'environnement : 

``docker run -tid --name variableenvironnement --env MAVARIABLE="samir1234" ubuntu:latest ``

 

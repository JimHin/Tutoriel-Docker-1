# Tutoriel-Docker 1
Conteneurisation d'un projet php mysql

petite précision, ce tutoriel ne vous permettra pas de pérenniser la donnée. En effet,si l'image est arrêtée elle revient à son état initiale.
je prépare donc un autre tutoriel.
Il s'agira de  lier un répertoire ~/mysql et ~/www crée sur le système qui héberge le conteneur.



Pré-requis: avoir installé docker (et lui donner les droits sudoers)

voilà la manip en considérant que docker est sudoer sur votre système 
sinon vous savez ce que vous devez ajouter devant la commande qui va suivre. :

- vous devez vous trouver à la racine de votre serveur local là où se trouve le répertoire de votre projet.
- Attention la commande qui suit doit être éxécuté en dehors du répertoire de votre projet (dans le terminal).
- Le but est de créer un conteneur docker avec une suite lamp toute prête et d'y copier votre projet
- docker run -i -t -p "80:80" -v ${PWD}/nomdevotre repertoirecontenant votre projet:/app mattrayner/lamp:latest
- // vous adaptez les ports si vous le désirez
- //moi j'ai préféré stopper mes serveurs

exemple:
docker run -i -t -p "80:80" -v ${PWD}/projetschool:/app mattrayner/lamp:latest 

- ensuite vous scrutez votre terminal lors de l'installation.
- vous y trouvez vos accés mysql dans un cartouche formé d'étoiles (le serveur mysql de l'image docker)
- Rendez-vous dans votre navigateur
- tapez dans la barre url:  localhost/phpmyadmin  (si vous avez laissé 80:80 sinon il vous faudra préciser le port)
- vous vous connecté avec les logs du terminal (le login c'est admin  et le mot de passe est autogénéré. 
  voir le cartouche dans le terminal)
- une fois dans le phpmyadmin du conteneur, vous importez votre base de données 
  via un dump que vous avez préalablement préparer.
- puis vous créer un nouveau compte utilisateur avec le login et le mot de passe 
  que vous avez utilisé dansle code de votre projet
 -vous lui octroyez tout les droits
 - vous executez et le tour est joué
 - Tapez localhost ou localhost:"port choisi" pour accéder à votre projet conteneurisé
 
 Dans votre terminal:
 
 docker ps -a                     (pour visualiser les conteneurs crées avec leur ID , noms etc...)
 docker start ID du conteneur     (les 3 premiers caractères de l'ID suffisent d'ailleurs)
 docker stop ID du conteneur      (pareil les 3 premiers caractères de l'ID suffisent)

PROCHAINE ETAPE DE MAITRISE DE DOCKER -----------> https://github.com/JimKrow/Redaction-du-DOCKERFILE

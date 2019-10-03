# Tutoriel-Docker
Conteneurisation d'un projet php mysql

petite précision, avec ce tutoriel on a pas encore vu comment mysql va pérenniser la donnée vu que si l'image est arrêtée elle revient à son état initiale
je prépare un autre tuto
pas compliqué on doit lier un répertoire ~/mysql et ~/www crée sur le système qui héberge le conteneur.
C'est lors du build d'un fichier Dockerfile qu'on peut faire ce genre de déclaration

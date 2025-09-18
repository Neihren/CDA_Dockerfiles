# Port par défaut 3306
# Utilise l'image mariadb de version 11
FROM mariadb:11

# Variable environnement pour le compte admin de la DB
ENV MYSQL_ROOT_PASSWORD=azer

# Créer une base de donnée nommée mydatabase
ENV MYSQL_DATABASE=mydatabase

# Créer un utilisateur ayant les droits sur la basse crée précédemment
ENV MYSQL_USER=jessy

# Définir le mdp pour cet utilisateur
ENV MYSQL_PASSWORD=1234

VOLUME [ "/data" ]
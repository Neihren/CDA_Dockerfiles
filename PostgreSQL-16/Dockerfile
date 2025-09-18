## port par défaut 5432
# Utilise l'image postgres
FROM postgres:16


ENV POSTGRES_ROOT_PASSWORD=1234
# Créer une base de donnée nommée mydatabase
ENV POSTGRES_DB=mydatabase

# Créer un utilisateur ayant les droits sur la basse crée précédemment
ENV POSTGRES_USER=jessy

# Variable environnement pour le mdp du compte jessy
ENV POSTGRES_PASSWORD=azer

VOLUME [ "/data" ]
# MariaDB 11 Docker Image

Ce dépôt contient un Dockerfile pour construire une image Docker basée sur MariaDB version 11, une base de données relationnelle open source populaire.

## Description

L'image est basée sur l'image officielle MariaDB 11. Elle permet de rapidement déployer un serveur MariaDB configurable via des variables d'environnement. Des scripts d'initialisation peuvent être ajoutés pour personnaliser la base de données au démarrage.

## Utilisation

### Construction de l'image
```
docker build -t mariadb:11-custom . 
```

### Lancement d'un conteneur

Voici une commande d'exemple pour lancer un conteneur avec un mot de passe root défini :
```
docker run -d --name mariadb11-container -e MARIADB_ROOT_PASSWORD=monmotdepasse -p 3306:3306 mariadb:11-custom
```

### Variables d'environnement disponibles

- `MARIADB_ROOT_PASSWORD` : mot de passe pour l'utilisateur root (obligatoire)
- `MARIADB_DATABASE` : nom d'une base de données à créer au démarrage (optionnel)
- `MARIADB_USER` : nom d'un utilisateur à créer (optionnel)
- `MARIADB_PASSWORD` : mot de passe du nouvel utilisateur (optionnel)

### Initialisation

Pour ajouter des scripts SQL ou shell à exécuter lors du premier démarrage, placez-les dans le dossier `/docker-entrypoint-initdb.d` dans l'image.

## Ports exposés

- `3306` : port par défaut MySQL/MariaDB

## Exemple de Dockerfile

```
FROM mariadb:11

ENV MARIADB_ROOT_PASSWORD=change_me
ENV MARIADB_DATABASE=exampledb
ENV MARIADB_USER=user
ENV MARIADB_PASSWORD=password

EXPOSE 3306

CMD ["mysqld"]
```
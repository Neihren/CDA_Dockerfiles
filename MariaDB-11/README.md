# MariaDB 11 Docker Image

Ce dépôt contient un Dockerfile pour construire une image Docker basée sur `MariaDB version 11`, une base de données relationnelle open source populaire.

## Description

L'image est basée sur l'image officielle MariaDB 11. Elle permet de rapidement déployer un serveur MariaDB configurable via des variables d'environnement.

La persistance des données est assurée via un volume Docker bindé sur le répertoire des données MariaDB.

## Utilisation

### Construction de l'image

Voici une commande d'exemple pour contruire une image :
```
docker build --tag [imagebase-version:tag] . 
```

### Lancement d'un conteneur

Voici une commande d'exemple pour lancer un conteneur :
```
docker run --detach --name [nomimage-version:tag] --publish [port]:3306 -v [nomvolume]:/var/lib/mysql [image:tag]
```

### Exécution du conteneur

```
docker exec -it [conteneur] bash
```

### Volumes par défaut

`/var/lib/mysql`

### Variables d'environnement disponibles

- `MARIADB_ROOT_PASSWORD` : mot de passe pour l'utilisateur root (obligatoire)
- `MARIADB_DATABASE` : nom d'une base de données à créer au démarrage (optionnel)
- `MARIADB_USER` : nom d'un utilisateur à créer (optionnel)
- `MARIADB_PASSWORD` : mot de passe du nouvel utilisateur (optionnel)

### Ports exposés

- `3306` : port par défaut MySQL/MariaDB

### Exemple de Dockerfile

```
FROM mariadb:11

ENV MYSQL_ROOT_PASSWORD=password
ENV MYSQL_DATABASE=dbname
ENV MYSQL_USER=user
ENV MYSQL_PASSWORD=password

VOLUME [ "/data" ]
```

## License

Ce projet est libre, merci de respecter les licences des composants utilisés (MariaDB est sous licence GPL).

---

Pour toute question ou suggestion, merci d'ouvrir une issue sur ce dépôt.
# MySQL 8.4 Docker Image

Ce dépôt contient un Dockerfile pour construire une image Docker basée sur MySQL version 8.4, l'un des systèmes de gestion de base de données relationnelle les plus utilisés.

## Description

L'image est construite à partir de l'image officielle MySQL 8.4. Elle permet de déployer rapidement un serveur MySQL configurable via des variables d'environnement.

La persistance des données est assurée grâce à un volume Docker bindé vers le répertoire des données MySQL.

## Utilisation

### Construction de l'image

```
docker build --tag [imagebase-version:tag] . 
```

### Lancement d'un conteneur

```
docker run --detach --name [nomimage-version:tag] --publish [port]:3306 -v [nomvolume]:/var/lib/mysql [image:tag]
```

### Exécution du conteneur

```
docker exec -it [conteneur] bash
```

### Variables d'environnement disponibles

- `MYSQL_ROOT_PASSWORD` : mot de passe pour l'utilisateur root (obligatoire)
- `MYSQL_DATABASE` : nom de la base de données à créer au démarrage (optionnel)
- `MYSQL_USER` : nom d'un utilisateur à créer (optionnel)
- `MYSQL_PASSWORD` : mot de passe pour l'utilisateur créé (optionnel)

### Ports exposés

- `3306` : port par défaut MySQL

### Volumes par défaut

- `/var/lib/mysql`

## Exemple de Dockerfile

```
FROM mysql:8.4

ENV MYSQL_ROOT_PASSWORD=azer
ENV MYSQL_DATABASE=mydatabase
ENV MYSQL_USER=jessy
ENV MYSQL_PASSWORD=1234
```

## License

Ce projet est libre, merci de respecter les licences des composants utilisés (MySQL est sous licence GPL).

---

Pour toute question ou suggestion, merci d'ouvrir une issue sur ce dépôt.
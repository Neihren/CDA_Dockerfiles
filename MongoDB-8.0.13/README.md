# MongoDB 8.0.13 Docker Image

Ce dépôt contient un Dockerfile pour construire une image Docker basée sur `MongoDB version 8.0.13`, une base de données NoSQL populaire.

## Description

L'image utilise l'image officielle MongoDB 8.0.13. Elle permet de déployer rapidement un serveur MongoDB configurable via des variables d'environnement.

La persistance des données est assurée grâce à un volume Docker bindé vers le répertoire des données MongoDB.

## Utilisation

### Construction de l'image

```
docker build --tag [imagebase-version:tag] . 
```

### Lancement d'un conteneur

```
docker run --detach --name [nomimage-version:tag] --publish [port]:27017 -v [nomvolume]:/data/db -v [nomvolume]:/data/configdb [image:tag]
```

### Exécution du conteneur

```
docker exec -it [conteneur] bash
```

### Variables d'environnement disponibles

- `MONGO_INITDB_ROOT_USERNAME` : nom d'utilisateur administrateur (obligatoire)
- `MONGO_INITDB_ROOT_PASSWORD` : mot de passe administrateur (obligatoire)
- `MONGO_INITDB_DATABASE` : nom de la base créée au premier lancement (optionnel)

### Ports exposés

- 27017 : port par défaut d’écoute MongoDB

### Volumes par défaut

- `/data/db`
- `/data/configdb`

## Exemple de Dockerfile

```
FROM mongo:8.0.13

ENV MONGO_INITDB_ROOT_USERNAME: root
ENV MONGO_INITDB_ROOT_PASSWORD: password
ENV MONGO_INITDB_DATABASE=dbname
```

## License

Ce projet est libre, merci de respecter les licences des composants utilisés (MongoDB est sous licence SSPL).

---

Pour toute question ou suggestion, merci d'ouvrir une issue sur ce dépôt.
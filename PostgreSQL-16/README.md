# PostgreSQL 16 Docker Image

Ce dépôt contient un Dockerfile pour créer une image Docker basée sur `PostgreSQL version 16`, une base de données relationnelle puissante et open source.

## Description

L'image utilise l'image officielle PostgreSQL 16. Elle permet de déployer rapidement un serveur PostgreSQL avec des variables d'environnement pour la configuration initiale.

La persistance des données est assurée par un volume Docker bindé vers le répertoire PostgreSQL.

## Utilisation

### Construction de l'image

```
docker build --tag [imagebase-version:tag] . 
```

### Lancement d'un conteneur

```
docker run --detach --name [nomimage-version:tag] --publish [port]:5432 -v [nomvolume]:/var/lib/postgresql/data [image:tag]
```

### Exécution du conteneur

```
docker exec -it [conteneur] bash
```

### Variables d'environnement disponibles

- `POSTGRES_USER` : nom de l'utilisateur administrateur (obligatoire)
- `POSTGRES_PASSWORD` : mot de passe de l'utilisateur (obligatoire)
- `POSTGRES_DB` : nom de la base de données créée au démarrage (optionnel)

### Ports exposés

- `5432` : port par défaut d'écoute PostgreSQL

### Volumes par défaut

- `/var/lib/postgresql/data`

## Exemple de Dockerfile

```
FROM postgres:16

ENV POSTGRES_DB=mydatabase
ENV POSTGRES_USER=admin
ENV POSTGRES_PASSWORD=password
```

## License

Ce projet est libre, merci de respecter les licences des composants utilisés (PostgreSQL est sous licence PostgreSQL License).

---

Pour toute question ou suggestion, merci d'ouvrir une issue sur ce dépôt.
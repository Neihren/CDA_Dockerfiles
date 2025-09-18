# Commandes de base Docker

## Construction d’une image

- `docker build .`
  - Construit une image Docker à partir du contexte de build courant.
- `-t, --tag [nom:tag]`
  - Attribue un nom et un tag à l’image.
- `-f, --file [dockerfile]`
  - Spécifie le Dockerfile à utiliser.

## Exécution d’un conteneur

- `docker run`
  - Lance un conteneur à partir d’une image Docker.
- `-d, --detach`
  - Lance le conteneur en arrière-plan.
- `-e, --env [VARIABLE=valeur]`
  - Définit une variable d’environnement dans le conteneur.
- `-i, --interactive`
  - Maintient STDIN ouvert même si non attaché.
- `-t, --tty`
  - Alloue un terminal TTY pour l’interaction avec le conteneur.
- `--name [nom]`
  - Donne un nom au conteneur.
- `-p, --publish [hôte:conteneur]`
  - Lie un port local avec un port du conteneur.
- `-v, --volume [volume:chemin]`
  - Monte un volume ou répertoire dans le conteneur.

## Interaction avec un conteneur existant

- `docker exec -it [nom] bash`
  - Accède à un shell Bash dans un conteneur en cours d’exécution.
- `bin/bash` ou `bin/sh`
  - Lancement d’un shell.

# Gestion des volumes

- `docker volume ls`
  - Liste tous les volumes Docker existants.
- `docker volume prune`
  - Supprime tous les volumes inutilisés.
- Emplacements typiques :
  - MySQL/MariaDB : `VOLUME /var/lib/mysql`
  - PostgreSQL : `VOLUME /var/lib/postgresql/data`

# Gestion des images et conteneurs

- `docker images`
  - Liste toutes les images Docker locales.
- `docker ps`
  - Liste les conteneurs en cours d’exécution.
- `docker ps -a`
  - Liste tous les conteneurs, même arrêtés.

# Ports de base de données par défaut

| SGBD                 | Port recommandé |
|----------------------|-----------------|
| MySQL                | 3306            |
| MariaDB              | 3306            |
| PostgreSQL           | 5432            |
| MongoDB              | 27017           |
| Microsoft SQLServer  | 1433            |


# Exemples pratiques

- Construction d'une image PostgreSQL

`docker build . -t postgres-171`
- Lancement d'un conteneur PostgreSQL

`docker run -d --name postgres-1 -p 4002:5432 -v postgres-1pgdata:/var/lib/postgresql/data -v postgres-1data:/data postgres-171`
- Prendre la main dans le conteneur

`docker exec -it postgres-1 bash`
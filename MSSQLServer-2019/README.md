# Microsoft SQL Server 2019 Docker Image

Ce dépôt contient un Dockerfile pour construire une image Docker basée sur `Microsoft SQL Server 2019-latest`. Cette image permet de déployer un serveur SQL Server sur Linux.

## Description

L'image est construite à partir de l'image officielle Microsoft SQL Server Linux.

Elle permet de configurer rapidement un serveur SQL Server avec les variables d'environnement nécessaires.

## Utilisation

### Construction de l'image

```
docker build --tag [imagebase-version:tag] . 
```

### Lancement d'un conteneur

```
docker run --detach --name [nomimage-version:tag] --publish [port]:1433 [image:tag]
```

### Exécution du conteneur

```
docker exec -it [conteneur] bash
```

### Variables d'environnement disponibles

- `ACCEPT_EULA=Y` : accepte le contrat de licence (obligatoire)
- `MSSQL_SA_PASSWORD` : définit le mot de passe(fort : 8 caractère, minuscule, majuscule, chiffre) de l'utilisateur administrateur `sa` (obligatoire) 

### Ports exposés

- `1433` : port TCP par défaut pour SQL Server

### Volumes par défaut

-

## Exemple de Dockerfile

```
FROM mcr.microsoft.com/mssql/server:2019-latest

ENV ACCEPT_EULA=Y
ENV MSSQL_SA_PASSWORD=Password1234
USER root
```

## License

Ce projet est libre, merci de respecter les licences des composants utilisés (Microsoft SQL Server est sous licence propriétaire mais avec image officielle pour usage évaluable).

---

Pour toute question ou suggestion, merci d'ouvrir une issue sur ce dépôt.
# Commandes Docker

Pour télécharger une image depuis un dépôt Docker

```shell
docker pull my-image
```

Pour démarrer un container à partir d'une image en mode deamon

```shell
docker run -d --name my-container my-image
```

Pour se connecter et ouvrir un shell dans un container en mode interactif

```shell
docker exec -it my-container /bin/sh
```

Pour stopper un container

```shell
docker stop my-container
```

Pour supprimer un container

```shell
docker rm my-container
```

Pour supprimer le container et son volume

```shell
docker rm -v my-container
```

Pour supprimer un volume

```bash
docker volume rm my-volume
```

Pour lister les volumes d'un container

```shell
docker inspect my-container | jq -r '.[0].Mounts[]'
```

Pour lister les réseaux d'un container

```shell
docker inspect my-container | jq -r '.[0].NetworkSettings.Networks | keys[]'
```

# Commandes

Télécharger une image depuis un dépôt Docker

```shell
docker pull my-image
```

Démarrer un container à partir d'une image en mode deamon

```shell
docker run -d --name my-container my-image
```

Se connecter et ouvrir un shell dans un container en mode interactif

```shell
docker exec -it my-container /bin/sh
```

Stopper un container

```shell
docker stop my-container
```

Supprimer un container

```shell
docker rm my-container
```

Supprimer le container et son volume

```shell
docker rm -v my-container
```

Supprimer un volume

```bash
docker volume rm my-volume
```

Lister les volumes d'un container

```shell
docker inspect my-container | jq -r '.[0].Mounts[]'
```

Lister les réseaux d'un container

```shell
docker inspect my-container | jq -r '.[0].NetworkSettings.Networks | keys[]'
```

Créer un réseau sur Docker

```shell
docker network create --driver bridge my-network
```

L'argument `--driver bridge` permet de créer un réseau en mode "pont" (ce qui permet à différents conteneurs de communiquer entre eux)

Une fois que le réseau a été créé, vous pouvez l'utiliser comme ceci :

```perl
docker run --network my-network my-image
```

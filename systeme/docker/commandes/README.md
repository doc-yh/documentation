# Commandes

## Télécharger une image depuis un dépôt Docker

```shell
docker pull my-image
```

## Démarrer un container à partir d'une image en mode deamon

```shell
docker run -d --name my-container my-image
```

## Se connecter et ouvrir un shell dans un container en mode interactif

```shell
docker exec -it my-container /bin/sh
```

## Stopper un container

```shell
docker stop my-container
```

## Supprimer un container

```shell
docker rm my-container
```

## Supprimer le container et son volume

```shell
docker rm -v my-container
```




# Container

## Démarrer et se connecter à un container

```shell
docker run -it --name my-container my-image
```

## Démarrer un container en mode deamon

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

## Afficher les logs d'un conteneur

```shell
docker logs -f my_container
```

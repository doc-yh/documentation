# Network

## Lister les réseaux d'un container

```shell
docker inspect my-container | jq -r '.[0].NetworkSettings.Networks | keys[]'
```

Créer un réseau (`--driver bridge` permet de créer un réseau en mode "pont" : ce qui permet à différents conteneurs de communiquer entre eux)

```shell
docker network create --driver bridge my-network
```

## Attacher un réseau à un container

```shell
docker network connect my-network my-container
```

## Détacher un conteneur d'un réseau

```shell
docker network disconnect my-network my-container
```

# Volume

## Créer un volume

```shell
docker volume create --opt type=none --opt device=/mnt/c/docker/ --opt o=bind my_volume
```

Cela créera un volume qui utilise le répertoire /mnt/c/docker/ sur votre hôte comme stockage de données.

Vous pouvez également utiliser la commande `docker run` avec l'option `-v` pour créer un volume et l'attacher à un conteneur en même temps. Par exemple:

```shell
docker run -v my_volume:/container_folder -it my_image
```

L'option `type` de la commande `docker volume create` vous permet de spécifier le type de stockage à utiliser pour le volume que vous créez. Les différents types disponibles sont les suivants:

* `bind`: Ce type vous permet de monter un répertoire du système de fichiers de l'hôte sur un répertoire du conteneur. Cela peut être utile lorsque vous souhaitez utiliser des fichiers ou des répertoires de votre hôte dans un conteneur.
* `volume`: Ce type utilise un volume Docker pour stocker les données du conteneur. Cela peut être utile lorsque vous souhaitez séparer les données d'un conteneur de l'image du conteneur, de sorte que les données ne soient pas perdues lorsque vous mettez à jour ou supprimez l'image du conteneur.
* `tmpfs`: Ce type utilise un système de fichiers en mémoire pour stocker les données du conteneur. Cela peut être utile lorsque vous souhaitez stocker des données de manière temporaire, qui ne doivent pas être persistantes sur le disque.
* `none`: Ce type ne crée pas de volume et n'attache aucun stockage au conteneur. Cela peut être utile lorsque vous souhaitez exécuter un conteneur sans stockage attaché.

Il est important de choisir le type de stockage approprié en fonction de vos besoins. Par exemple, si vous souhaitez que les données d'un conteneur soient persistantes et indépendantes de l'image du conteneur, vous devriez utiliser un type de volume. Si vous avez besoin de stocker des données de manière temporaire, vous pouvez utiliser un système de fichiers en mémoire (tmpfs). Si vous ne souhaitez pas de stockage attaché au conteneur, vous pouvez utiliser le type `none`.

## Supprimer un volume

```bash
docker volume rm my-volume
```

## Lister les volumes d'un container

```shell
docker inspect my-container | jq -r '.[0].Mounts[]'
```

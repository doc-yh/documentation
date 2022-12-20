# Image

## Télécharger une image depuis un dépôt Docker

```shell
docker pull my-image
```

## Exemple de publication d'image sur Docker Hub

Créez un fichier nommé `Dockerfile` avec le contenu suivant :

```css
FROM ubuntu:18.04

CMD ["echo", "Hello, world!"]
```

Exécutez la commande suivante pour créer une image :

```bash
docker build -t my_username/my_image:latest .
```

Cela créera une image Docker nommée `my_image` avec l'étiquette `latest` à partir de votre fichier Dockerfile.

1. Authentifiez-vous sur votre compte Docker Hub avec la commande `docker login`. Spécifiez votre nom d'utilisateur et votre mot de passe Docker Hub.
2. Publiez votre image Docker sur Docker Hub en utilisant la commande `docker push`. Spécifiez le nom de votre image Docker et le nom de votre référentiel Docker Hub. Par exemple:

```bash
docker push my_username/my_image:latest
```

## Lister les images

```shell
docker images
```

## Supprimer une image

```shell
docker rmi my_image
```

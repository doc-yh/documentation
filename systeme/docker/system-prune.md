# System prune

La commande `docker system prune` permet de nettoyer le système Docker en supprimant les éléments inutilisés. L'option `-a` (ou `--all`) indique que tous les éléments doivent être supprimés, y compris les images, les conteneurs, les volumes et les réseaux qui ne sont pas utilisés par au moins un conteneur.

Voici les éléments qui seront supprimés par cette commande :

* Tous les conteneurs qui sont terminés ou en échec
* Toutes les images qui ne sont pas utilisées par au moins un conteneur
* Tous les volumes qui ne sont pas liés à un conteneur
* Tous les réseaux qui ne sont pas utilisés par au moins un conteneur

Il est important de noter que cette commande ne supprime pas les images, les conteneurs, les volumes ou les réseaux qui sont actuellement en cours d'exécution. Pour supprimer ces éléments, vous devez utiliser des commandes spécifiques, comme `docker rm` pour supprimer un conteneur, `docker rmi` pour supprimer une image, etc.

Cette commande peut être utile pour libérer de l'espace disque sur un serveur Docker et pour maintenir le système en bon état de fonctionnement.

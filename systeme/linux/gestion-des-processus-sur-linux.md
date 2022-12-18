# Gestion des processus sur Linux

#### Lister les processus en cours d'execution

Pour lister les processus en cours d'exécution :

* Tapez la commande `ps aux`

Cette commande affichera la liste de tous les processus en cours d'exécution sur votre système, avec les informations suivantes pour chaque processus :

* `USER` : nom de l'utilisateur propriétaire du processus.
* `PID` : numéro de processus unique (PID).
* `%CPU` : pourcentage de temps CPU utilisé par le processus.
* `%MEM` : pourcentage de mémoire physique utilisée par le processus.
* `VSZ` : taille virtuelle du processus en octets.
* `RSS` : taille réelle du processus en octets.
* `TTY` : terminal associé au processus.
* `STAT` : état du processus (par exemple, "S" pour "suspendu" ou "R" pour "en cours d'exécution").
* `START` : date et heure de démarrage du processus.
* `TIME` : temps CPU total utilisé par le processus.
* `COMMAND` : nom du programme exécuté.

#### Arrêter un processus

Pour arrêter un processus sur un système Linux, vous pouvez utiliser la commande `kill`. Voici comment l'utiliser :

1. Ouvrez un terminal.
2. Pour arrêter un processus, vous devez connaître son numéro de processus unique (PID). Vous pouvez utiliser la commande `ps` pour afficher la liste des processus en cours d'exécution sur votre système et trouver le PID du processus que vous souhaitez arrêter.

Par exemple, pour afficher la liste de tous les processus en cours d'exécution et trouver le PID du processus `program`, vous pouvez utiliser la commande suivante :

```perl
ps aux | grep program
```

Cette commande affichera la liste de tous les processus en cours d'exécution et leur PID, et vous pourrez trouver le PID du processus `program` dans la colonne `PID`.

1. Une fois que vous avez trouvé le PID du processus que vous souhaitez arrêter, tapez la commande `kill <PID>` et appuyez sur Entrée.

Par exemple, si le PID du processus `program` est 12345, vous pouvez arrêter ce processus en utilisant la commande suivante :

```bash
kill 12345
```

Cette commande enverra un signal d'arrêt au processus et l'arrêtera. Si le processus ne répond pas à ce signal, vous pouvez essayer d'utiliser le signal `SIGKILL` en utilisant la commande `kill -9 <PID>`. Cependant, ce signal est généralement réservé aux cas où le processus ne répond pas aux autres signaux et peut entraîner la perte de données.

Pour plus d'informations sur les différents signaux disponibles avec la commande `kill` et sur l'utilisation de cette commande, consultez la documentation de la commande ou les ressources en ligne sur Linux.

#### Mettre un processus en pause puis revenir :

* Lancer la commande : sl
* Appuyez sur ctrl + z (le process va se mettre en pause)
* Revenir sur le process grâce à la commande fg

#### Démarrer un processus en arrière plan

* Il faut rajouter un "&" aprés la commande
  * par exemple : sl &

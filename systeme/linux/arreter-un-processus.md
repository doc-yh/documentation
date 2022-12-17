# Arrêter un processus

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

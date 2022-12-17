# Lister les processus en cours d'execution

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

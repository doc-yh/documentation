# Lister les ports utilisés

`netstat -tulpn`

`-t` pour afficher uniquement les ports TCP

`-u` pour afficher uniquement les ports UDP

`-l` pour afficher uniquement les ports en écoute.

`-p` pour afficher les processus associés aux sockets

`-n` pour afficher les adresses IP et les numéros de port sous forme numérique



Voici quelques exemples des différents états d'un port qui peuvent être affichés par la commande `netstat` :

* `LISTEN` : le port est en attente de connexion. Cela signifie que le processus associé au port est en train d'écouter les connexions entrantes.
* `ESTABLISHED` : le port est en cours d'utilisation. Cela signifie qu'il y a une connexion active entre le port local et un port distant.
* `CLOSED` : le port n'est pas en cours d'utilisation et ne peut pas être utilisé pour une nouvelle connexion.
* `SYN_SENT` : le port a envoyé une demande de synchronisation (SYN) pour établir une connexion TCP, mais n'a pas encore reçu une réponse.
* `SYN_RECEIVED` : le port a reçu une demande de synchronisation (SYN) pour établir une connexion TCP, mais n'a pas encore envoyé une réponse.
* `FIN_WAIT_1` : le port est en train de fermer une connexion TCP et attend une confirmation de la fin de la connexion de l'autre côté.
* `FIN_WAIT_2` : le port a reçu une confirmation de la fin de la connexion de l'autre côté et attend la fermeture complète de la connexion.
* `TIME_WAIT` : le port a fermé une connexion TCP et attend un certain temps avant de pouvoir être réutilisé pour une nouvelle connexion.


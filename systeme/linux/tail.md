# Tail

Pour afficher les 10 dernières lignes d'un fichier en temps réel :

* Tapez la commande `tail -f -n 10 <nom-du-fichier>` et appuyez sur Entrée.

`-n` pour spécifier le nombre de lignes à afficher

`-f` pour suivre le fichier en temps réel.



`ccze` est un outil en ligne de commande qui permet de surligner et de colorer la sortie de différentes commandes.

```bash
tail -f -n 10 /var/log/syslog | ccze -p ERROR=red -p INFO=green
```


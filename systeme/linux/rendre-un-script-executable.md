# Rendre un script exécutable

Donner les permissions d'exécution d'un script à tous les utilisateurs du système :

```bash
chmod +x myscript.sh
```

```bash
./myscript.sh
```

Donner les permissions d'exécution uniquement au propriétaire du fichier :

```bash
chmod u+x myscript.sh
```

Pour rendre exécutable le script `myscript.sh` par l'utilisateur `john`, vous pouvez utiliser la commande suivante :

```bash
chmod u+x:john myscript.sh
```

Pour rendre exécutable le script par le groupe `users`, vous pouvez utiliser la commande suivante :

```bash
chmod g+x:users myscript.sh
```

# Droits d'accès

## Chown

Voici quelques exemples de commandes `chown` :

Pour changer le propriétaire d'un fichier nommé `monfichier.txt` en utilisant l'utilisateur `utilisateur1` et le groupe `groupe1` :

```bash
chown utilisateur1:groupe1 monfichier.txt
```

Pour changer le propriétaire d'un répertoire nommé `mondossier` en utilisateur `utilisateur2` :

```bash
chown utilisateur2 mondossier
```

Pour changer le propriétaire de tous les fichiers et répertoires du répertoire courant en utilisateur `utilisateur3` :

```bash
chown -R utilisateur3 .
```

Pour changer le propriétaire de tous les fichiers et répertoires du répertoire `/var/www` en utilisateur `www-data` et en groupe `www-data` :

```kotlin
chown -R www-data:www-data /var/www
```

Note : la commande `chown` est utilisée pour changer le propriétaire d'un fichier ou d'un répertoire. Elle est généralement utilisée par les administrateurs système pour gérer les droits d'accès aux fichiers et répertoires sur un système Unix ou Linux. Cette commande nécessite des privilèges d'administration (généralement en utilisant la commande `sudo`).

## Chmod

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

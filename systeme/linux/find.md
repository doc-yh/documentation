# Find

Voici quelques exemples d'utilisation de la commande `find` :

Rechercher tous les fichiers de type `.txt` dans le répertoire courant et sous-répertoires :

```shell
$ find . -name "*.txt"
```

Rechercher tous les fichiers modifiés il y a moins de deux jours :

```shell
$ find . -mtime -2
```

Rechercher tous les fichiers appartenant à l'utilisateur `john` :

```shell
$ find . -user john
```

Rechercher tous les fichiers ayant les permissions `644` :

```shell
$ find . -perm 644
```

Rechercher tous les fichiers vides :

```shell
$ find . -empty
```

Rechercher tous les fichiers dont le nom commence par `doc` et les copier dans le répertoire `/backup` :

```shell
$ find . -name "doc*" -exec cp {} /backup \;
```

Rechercher tous les fichiers de type `.pdf` dans le répertoire courant et sous-répertoires et les supprimer :

```shell
$ find . -name "*.pdf" -delete
```

Rechercher tous les fichiers de plus de 1 Mo de taille et les déplacer dans le répertoire `/big_files` :

```shell
$ find . -size +1M -exec mv {} /big_files \;
```

Rechercher tous les fichiers modifiés il y a plus de 30 jours et les archiver dans un fichier `old_files.tar` :

```shell
$ find . -mtime +30 -exec tar -rvf old_files.tar {} \;
```

Rechercher tous les fichiers appartenant au groupe `admin` et changer leur propriétaire en `root` :

```shell
$ find . -group admin -exec chown root {} \;
```

Rechercher tous les fichiers cachés (dont le nom commence par un point) et les afficher :

```shell
$ find . -name ".*" -exec ls -l {} \;
```

Rechercher tous les fichiers de type `.docx` dans le répertoire `/documents` et sous-répertoires et les convertir en fichiers `.pdf` :

```shell
$ find /documents -name "*.docx" -exec libreoffice --convert-to pdf {} \;
```

Rechercher tous les fichiers modifiés il y a plus de 60 jours et les compresser avec `gzip` :

```shell
$ find . -mtime +60 -exec gzip {} \;
```

Rechercher tous les fichiers dont le nom contient la chaîne de caractères `report` et les copier dans le répertoire `/reports` :

```shell
$ find . -name "*report*" -exec cp {} /reports \;
```

Rechercher tous les fichiers ayant la permission `700` et les rendre accessibles en lecture et écriture pour tous les utilisateurs :

```shell
$ find . -perm 700 -exec chmod 755 {} \;
```

Rechercher tous les fichiers vides et les supprimer, en demandant confirmation avant chaque suppression :

```shell
$ find . -empty -ok rm {} \;
```

Rechercher tous les fichiers dont le nom commence par une lettre majuscule et se termine par `.txt` :

```shell
$ find . -regex ".*/[A-Z].*\.txt"
```

Rechercher tous les fichiers dont le nom contient un nombre entier compris entre 10 et 99 :

```shell
$ find . -regex ".*/[0-9][0-9]$"
```

Rechercher tous les fichiers dont le nom contient une chaîne de caractères alphanumérique de 8 caractères :

```shell
$ find . -regex ".*/[a-zA-Z0-9]{8}"
```

Rechercher tous les fichiers dont le nom commence par `file_` suivi de 3 chiffres et d'une lettre majuscule :

```shell
$ find . -regex ".*/file_[0-9]{3}[A-Z]"
```

Rechercher tous les fichiers dont le nom contient une chaîne de caractères alphabétique de 3 à 5 caractères, suivie de `.txt` :

```shell
$ find . -regex ".*/[a-zA-Z]{3,5}\.txt"
```

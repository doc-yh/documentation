# Stocker le résultat d'une commande

Il existe plusieurs façons de stocker le résultat d'une commande sur un système Linux. Voici quelques exemples :

1. Redirection de sortie : vous pouvez utiliser les opérateurs de redirection de sortie (`>` et `>>`) pour enregistrer la sortie d'une commande dans un fichier. Par exemple, pour enregistrer la sortie de la commande `ls` dans le fichier `list.txt`, vous pouvez utiliser la commande suivante :

```bash
ls > list.txt
```

Cette commande écrasera le contenu du fichier `list.txt` s'il existe déjà, ou en créera un nouveau s'il n'existe pas. Pour ajouter la sortie de la commande au contenu existant du fichier sans l'écraser, vous pouvez utiliser l'opérateur `>>` à la place de `>` :

```bash
ls >> list.txt
```

1. Capture de sortie : vous pouvez utiliser la commande `echo` pour afficher la sortie d'une commande dans un fichier. Par exemple, pour enregistrer la sortie de la commande `ls` dans le fichier `list.txt`, vous pouvez utiliser la commande suivante :

```bash
echo $(ls) > list.txt
```

Cette commande enregistrera la sortie de la commande `ls` dans le fichier `list.txt`.

1. Variables : vous pouvez utiliser la commande `$()` pour stocker la sortie d'une commande dans une variable. Par exemple, pour stocker la sortie de la commande `ls` dans la variable `files`, vous pouvez utiliser la commande suivante :

```makefile
files=$(ls)
```

Voici quelques autres exemples d'utilisation de la commande `$()` pour stocker la sortie d'une commande dans une variable :

```bash
# Stocke la sortie de la commande "date" dans la variable "current_date"
current_date=$(date)

# Affiche la variable "current_date"
echo $current_date

# Stocke la sortie de la commande "df -h" dans la variable "disk_usage"
disk_usage=$(df -h)

# Affiche la variable "disk_usage"
echo $disk_usage

# Stocke la sortie de la commande "uname -r" dans la variable "kernel_version"
kernel_version=$(uname -r)

# Affiche la variable "kernel_version"
echo $kernel_version
```

Vous pouvez également utiliser la commande `$()` pour stocker la sortie d'une commande dans un fichier. Par exemple, pour enregistrer la sortie de la commande `ls` dans le fichier `list.txt`, vous pouvez utiliser la commande suivante :

```shell
$(ls) > list.txt
```

Cette commande enregistrera la sortie de la commande `ls` dans le fichier `list.txt`.

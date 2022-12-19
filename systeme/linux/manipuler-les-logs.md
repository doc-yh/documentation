# Manipuler les logs

1. `tail` : permet de afficher les dernières lignes d'un fichier de log.
2. `grep` : permet de rechercher des chaînes de caractères dans un fichier de log.
3. `awk` : permet de traiter et formater les données d'un fichier de log.
4. `sed` : permet de remplacer des chaînes de caractères dans un fichier de log.
5. `sort` : permet de trier les lignes d'un fichier de log par ordre alphabétique ou numérique.
6. `uniq` : permet de supprimer les lignes en double d'un fichier de log.
7. `wc` : permet de compter le nombre de lignes, de mots et de caractères d'un fichier de log.
8. `cut` : permet de sélectionner des colonnes spécifiques d'un fichier de log.
9. `tee` : permet de rediriger la sortie d'une commande vers un fichier de log tout en l'affichant à l'écran.
10. `logrotate` : permet de gérer la rotation et l'archivage des fichiers de log.

##

## Tail

Pour afficher les 10 dernières lignes d'un fichier en temps réel :

* Tapez la commande `tail -f -n 10 <nom-du-fichier>` et appuyez sur Entrée.

`-n` pour spécifier le nombre de lignes à afficher

`-f` pour suivre le fichier en temps réel

`ccze` est un outil en ligne de commande qui permet de surligner et de colorer la sortie de différentes commandes.

```bash
tail -f -n 10 /var/log/syslog | ccze -p ERROR=red -p INFO=green
```

##

## Grep

Afficher toutes les lignes d'un fichier qui contiennent un mot spécifique :

```bash
grep 'mot' fichier.txt
```

Afficher toutes les lignes d'un fichier qui ne contiennent pas un mot spécifique :

```bash
grep -v 'mot' fichier.txt
```

Afficher le nombre de lignes qui contiennent un mot spécifique dans un fichier :

```bash
grep -c 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui commencent par un certain mot :

```bash
grep '^mot' fichier.txt
```

Afficher les lignes d'un fichier qui se terminent par un certain mot :

```bash
grep 'mot$' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique en majuscule ou en minuscule :

```bash
grep -i 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique en utilisant une expression régulière :

```bash
grep -E 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et en surligner les occurences du mot :

```bash
grep --color 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher le numéro de ligne de chaque ligne :

```bash
grep -n 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher le nom du fichier avant chaque ligne :

```bash
grep -H 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher les lignes avant et après chaque ligne correspondante :

```bash
grep -A 2 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher seulement le premier résultat de chaque fichier :

```bash
grep -m 1 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher seulement le premier résultat de chaque groupe de lignes consécutives qui correspondent :

```bash
grep -m 1 -o 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et ignorer les différences entre majuscules et minuscules :

```bash
grep -i 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et ignorer les différences entre majuscules et minuscules en utilisant une expression régulière :

```bash
grep -i -E 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher le nombre de lignes qui correspondent :

```bash
grep -c 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher le nombre de lignes qui correspondent, en ignorer les différences entre majuscules et minuscules :

```bash
grep -ic 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher le nombre de lignes qui correspondent, en ignorer les différences entre majuscules et minuscules en utilisant une expression régulière :

```bash
grep -ic -E 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher uniquement le nom du fichier qui contient le mot :

```bash
grep -l 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher uniquement le nom du fichier qui contient le mot, en ignorant les différences entre majuscules et minuscules :

```bash
grep -il 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher uniquement le nom du fichier qui contient le mot, en ignorant les différences entre majuscules et minuscules en utilisant une expression régulière :

```bash
grep -il -E 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher uniquement le nom du fichier qui contient le mot, en utilisant une expression régulière :

```bash
grep -l -E 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher uniquement le nom du fichier qui ne contient pas le mot :

```bash
grep -L 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher uniquement le nom du fichier qui ne contient pas le mot, en ignorant les différences entre majuscules et minuscules :

```bash
grep -Li 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher uniquement le nom du fichier qui ne contient pas le mot, en ignorant les différences entre majuscules et minuscules en utilisant une expression régulière :

```bash
grep -Li -E 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher uniquement le nom du fichier qui ne contient pas le mot, en utilisant une expression régulière :

```bash
grep -L -E 'mot' fichier.txt
```

## Awk

Afficher toutes les lignes d'un fichier qui contiennent un mot spécifique :

```bash
awk '/mot/ {print}' fichier.txt
```

Afficher la première colonne de chaque ligne d'un fichier :

```bash
awk '{print $1}' fichier.txt
```

Afficher la somme de la deuxième colonne de chaque ligne d'un fichier :

```bash
awk '{total+=$2} END {print total}' fichier.txt
```

Afficher le nombre de lignes d'un fichier :

```bash
awk 'END {print NR}' fichier.txt
```

Afficher la moyenne de la troisième colonne de chaque ligne d'un fichier :

```bash
awk '{sum+=$3} END {print sum/NR}' fichier.txt
```

Remplacer un mot par un autre dans chaque ligne d'un fichier :

```bash
awk '{gsub("ancien_mot","nouveau_mot")}; {print}' fichier.txt
```

Afficher les lignes d'un fichier qui ont plus de 10 caractères :

```bash
awk 'length($0)>10' fichier.txt
```

Afficher les lignes d'un fichier qui ont moins de 20 caractères :

```bash
awk 'length($0)<20' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent au moins un chiffre :

```bash
awk '/[0-9]/' fichier.txt
```

Afficher les lignes d'un fichier qui ne contiennent aucun chiffre :

```bash
awk '!/[0-9]/' fichier.txt
```

Afficher la première et la troisième colonne de chaque ligne d'un fichier :

```bash
awk '{print $1, $3}' fichier.txt
```

Afficher les lignes d'un fichier qui commencent par un certain mot :

```bash
awk '/^mot/' fichier.txt
```

Afficher les lignes d'un fichier qui se terminent par un certain mot :

```bash
awk '/mot$/' fichier.txt
```

Afficher le nombre de mots dans chaque ligne d'un fichier :

```bash
awk '{print NF}' fichier.txt
```

Afficher la somme de la troisième colonne de chaque ligne d'un fichier qui contient un certain mot :

```bash
awk '/mot/ {total+=$3} END {print total}' fichier.txt
```

Afficher la moyenne de la quatrième colonne de chaque ligne d'un fichier qui ne contient pas un certain mot :

```bash
awk '!/mot/ {sum+=$4} END {print sum/NR}' fichier.txt
```


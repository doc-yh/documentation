# Exemples d'utilisation de la commande 'grep'

Afficher toutes les lignes d'un fichier qui contiennent un mot spécifique :

```perl
grep 'mot' fichier.txt
```

Afficher toutes les lignes d'un fichier qui ne contiennent pas un mot spécifique :

```perl
grep -v 'mot' fichier.txt
```

Afficher le nombre de lignes qui contiennent un mot spécifique dans un fichier :

```perl
grep -c 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui commencent par un certain mot :

```perl
grep '^mot' fichier.txt
```

Afficher les lignes d'un fichier qui se terminent par un certain mot :

```perl
grep 'mot$' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique en majuscule ou en minuscule :

```perl
grep -i 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique en utilisant une expression régulière :

```perl
grep -E 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et en surligner les occurences du mot :

```perl
grep --color 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher le numéro de ligne de chaque ligne :

```perl
grep -n 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher le nom du fichier avant chaque ligne :

```perl
grep -H 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher les lignes avant et après chaque ligne correspondante :

```perl
grep -A 2 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher seulement le premier résultat de chaque fichier :

```perl
grep -m 1 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher seulement le premier résultat de chaque groupe de lignes consécutives qui correspondent :

```perl
grep -m 1 -o 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et ignorer les différences entre majuscules et minuscules :

```perl
grep -i 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et ignorer les différences entre majuscules et minuscules en utilisant une expression régulière :

```perl
grep -i -E 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher le nombre de lignes qui correspondent :

```perl
grep -c 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher le nombre de lignes qui correspondent, en ignorer les différences entre majuscules et minuscules :

```perl
grep -ic 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher le nombre de lignes qui correspondent, en ignorer les différences entre majuscules et minuscules en utilisant une expression régulière :

```perl
grep -ic -E 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher uniquement le nom du fichier qui contient le mot :

```perl
grep -l 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher uniquement le nom du fichier qui contient le mot, en ignorant les différences entre majuscules et minuscules :

```perl
grep -il 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher uniquement le nom du fichier qui contient le mot, en ignorant les différences entre majuscules et minuscules en utilisant une expression régulière :

```perl
grep -il -E 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher uniquement le nom du fichier qui contient le mot, en utilisant une expression régulière :

```perl
grep -l -E 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher uniquement le nom du fichier qui ne contient pas le mot :

```perl
grep -L 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher uniquement le nom du fichier qui ne contient pas le mot, en ignorant les différences entre majuscules et minuscules :

```perl
grep -Li 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher uniquement le nom du fichier qui ne contient pas le mot, en ignorant les différences entre majuscules et minuscules en utilisant une expression régulière :

```perl
grep -Li -E 'mot' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent un mot spécifique et afficher uniquement le nom du fichier qui ne contient pas le mot, en utilisant une expression régulière :

```
grep -L -E 'mot' fichier.txt
```

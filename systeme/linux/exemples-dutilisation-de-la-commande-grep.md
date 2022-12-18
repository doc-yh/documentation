# Exemples d'utilisation de la commande 'grep'

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

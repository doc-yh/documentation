# Exemples d'utilisation de la commande 'awk'

Afficher toutes les lignes d'un fichier qui contiennent un mot spécifique :

```python
awk '/mot/ {print}' fichier.txt
```

Afficher la première colonne de chaque ligne d'un fichier :

```python
awk '{print $1}' fichier.txt
```

Afficher la somme de la deuxième colonne de chaque ligne d'un fichier :

```python
awk '{total+=$2} END {print total}' fichier.txt
```

Afficher le nombre de lignes d'un fichier :

```python
awk 'END {print NR}' fichier.txt
```

Afficher la moyenne de la troisième colonne de chaque ligne d'un fichier :

```python
awk '{sum+=$3} END {print sum/NR}' fichier.txt
```

Remplacer un mot par un autre dans chaque ligne d'un fichier :

```graphql
awk '{gsub("ancien_mot","nouveau_mot")}; {print}' fichier.txt
```

Afficher les lignes d'un fichier qui ont plus de 10 caractères :

```scss
awk 'length($0)>10' fichier.txt
```

Afficher les lignes d'un fichier qui ont moins de 20 caractères :

```scss
awk 'length($0)<20' fichier.txt
```

Afficher les lignes d'un fichier qui contiennent au moins un chiffre :

```python
awk '/[0-9]/' fichier.txt
```

Afficher les lignes d'un fichier qui ne contiennent aucun chiffre :

```python
awk '!/[0-9]/' fichier.txt
```

Afficher la première et la troisième colonne de chaque ligne d'un fichier :

```swift
awk '{print $1, $3}' fichier.txt
```

Afficher les lignes d'un fichier qui commencent par un certain mot :

```python
awk '/^mot/' fichier.txt
```

Afficher les lignes d'un fichier qui se terminent par un certain mot :

```python
awk '/mot$/' fichier.txt
```

Afficher le nombre de mots dans chaque ligne d'un fichier :

```python
awk '{print NF}' fichier.txt
```

Afficher la somme de la troisième colonne de chaque ligne d'un fichier qui contient un certain mot :

```python
awk '/mot/ {total+=$3} END {print total}' fichier.txt
```

Afficher la moyenne de la quatrième colonne de chaque ligne d'un fichier qui ne contient pas un certain mot :

```python
awk '!/mot/ {sum+=$4} END {print sum/NR}' fichier.txt
```


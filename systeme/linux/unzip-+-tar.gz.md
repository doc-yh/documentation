# Unzip + Tar.gz

## Compression

### Zip

Pour compresser un fichier :&#x20;

```shell
zip nom_du_fichier_compressé.zip nom_du_fichier
```

Pour compresser un dossier :

```shell
zip -r nom_du_fichier_compressé.zip nom_du_dossier
```

### Tar.gz

Pour compresser un fichier :

```shell
tar -czvf nom_du_fichier.tar.gz nom_du_fichier
```

Pour compresser un dossier :

```shell
tar -czvf nom_du_fichier.tar.gz nom_du_dossier
```

## Décompression

### Zip

```shell
unzip nom_du_fichier.zip -d /chemin/vers/le/répertoire/de/destination
```

### Tar.gz

```shell
tar -xzvf nom_du_fichier.tar.gz
```


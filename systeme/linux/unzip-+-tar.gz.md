# Unzip + Tar.gz

## Compression

### Zip

Pour compresser un fichier en zip :&#x20;

```shell
zip nom_du_fichier_compressé.zip nom_du_fichier
```

Pour compresser un dossier en zip :

```shell
zip -r /chemin/vers/le/répertoire/de/destination/nom_du_fichier_compressé.zip nom_du_dossier
```

### Tar.gz

Pour compresser un fichier dans un fichier ".tar.gz" :

```shell
tar -czvf nom_du_fichier.tar.gz nom_du_fichier
```

Pour compresser un dossier dans un fichier ".tar.gz" :

```shell
tar -czvf nom_du_fichier.tar.gz nom_du_dossier
```

## Décompression

### Zip

```shell
unzip /chemin/vers/le/fichier/nom_du_fichier.zip -d /chemin/vers/le/répertoire/de/destination
```

### Tar.gz

```shell
tar -xzvf nom_du_fichier.tar.gz
```


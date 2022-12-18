# Disk usage (du)

Afficher l'espace disque utilisé par un répertoire et tous ses sous-répertoires :

```bash
du -sh répertoire
```

Afficher l'espace disque utilisé par un répertoire et tous ses sous-répertoires, en unités lisibles par l'homme (par exemple, en Mo ou en Go) :

```bash
du -sh --human-readable répertoire
```

Afficher l'espace disque utilisé par un répertoire et tous ses sous-répertoires, en utilisant un autre niveau de répertoire comme référence :

```bash
du -sh --exclude-from=répertoire_de_référence répertoire
```

Afficher l'espace disque utilisé par chaque fichier d'un répertoire :

```bash
du -ah répertoire
```

Afficher l'espace disque utilisé par les fichiers d'un type de fichier spécifique (par exemple, les fichiers PDF) dans un répertoire :

```bash
du -ah --include='*.pdf' répertoire
```

Afficher l'espace disque utilisé par un répertoire et tous ses sous-répertoires, en triant les résultats par ordre décroissant :

```bash
du -sh répertoire | sort -nr
```

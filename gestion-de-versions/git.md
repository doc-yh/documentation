# Git

## Add et commit

Pour ajouter des fichiers à l'index (staging area)

```bash
git add filename.txt
```

Une fois que vous avez ajouté des fichiers à l'index, vous pouvez utiliser la commande suivante pour enregistrer ces changements dans l'historique de votre dépôt Git.

```sql
git commit -m "Ajout de nouveaux fichiers à l'index"
```

L'option `-a` de la commande `git commit` permet d'indiquer à Git de commit tous les changements de fichiers déjà suivis (tracked) dans le dépôt. Cela signifie que Git inclura automatiquement tous les fichiers modifiés et supprimés dans le commit, sans avoir besoin de les ajouter à l'index (staging area) avec la commande `git add`.

Il est important de noter que la option `-a` ne prend en compte que les fichiers qui étaient déjà suivis (tracked) dans le dépôt Git avant d'être modifiés. Si vous avez créé de nouveaux fichiers qui ne sont pas encore suivis par Git, vous devrez utiliser la commande `git add` pour les ajouter à l'index avant de pouvoir les inclure dans le commit avec `git commit -a`.

Il est possible de modifier un commit existant dans Git en utilisant la commande `git commit --amend`. Cette commande vous permet de fusionner les modifications en cours dans votre répertoire de travail avec le dernier commit de votre dépôt.

## Stash

La commande `git stash` permet de "cacher" temporairement les modifications apportées à vos fichiers dans le dépôt Git, afin que vous puissiez basculer sur une autre branche ou exécuter une autre commande sans avoir à commit ou abandonner vos changements en cours.

Pour réappliquer les modifications mises en attente (stashed) plus tard, vous pouvez utiliser la commande `git stash apply`. Cette commande réapplique les dernières modifications mises en attente et les ajoute de nouveau à votre répertoire de travail.

# Git

## Add et commit

Pour ajouter des fichiers à l'index (staging area)

```shell
git add filename.txt
```

Une fois que vous avez ajouté des fichiers à l'index, vous pouvez utiliser la commande suivante pour enregistrer ces changements dans l'historique de votre dépôt Git.

```shell
git commit -m "Ajout de nouveaux fichiers à l'index"
```

L'option `-a` de la commande `git commit` permet d'indiquer à Git de commit tous les changements de fichiers déjà suivis (tracked) dans le dépôt. Cela signifie que Git inclura automatiquement tous les fichiers modifiés et supprimés dans le commit, sans avoir besoin de les ajouter à l'index (staging area) avec la commande `git add`.

Il est important de noter que la option `-a` ne prend en compte que les fichiers qui étaient déjà suivis (tracked) dans le dépôt Git avant d'être modifiés. Si vous avez créé de nouveaux fichiers qui ne sont pas encore suivis par Git, vous devrez utiliser la commande `git add` pour les ajouter à l'index avant de pouvoir les inclure dans le commit avec `git commit -a`.

Il est possible de modifier un commit existant dans Git en utilisant la commande `git commit --amend`. Cette commande vous permet de fusionner les modifications en cours dans votre répertoire de travail avec le dernier commit de votre dépôt.

## Stash

{% tabs %}
{% tab title="Sans nom" %}
La commande `git stash` permet de "cacher" temporairement les modifications apportées à vos fichiers dans le dépôt Git, afin que vous puissiez basculer sur une autre branche ou exécuter une autre commande sans avoir à commit ou abandonner vos changements en cours.

Pour réappliquer les modifications mises en attente (stashed) plus tard, vous pouvez utiliser la commande `git stash apply`. Cette commande réapplique les dernières modifications mises en attente et les ajoute de nouveau à votre répertoire de travail.

Pour visualiser le contenu d'un stash dans Git, vous pouvez utiliser la commande `git stash show`. Cette commande affiche les différences entre l'état actuel de votre dépôt et le stash que vous souhaitez afficher.

Si vous souhaitez afficher les différences pour tous les fichiers, y compris les fichiers ajoutés et supprimés, vous pouvez utiliser l'option `-p` :

```shell
git stash show -p
```
{% endtab %}

{% tab title="Avec un nom" %}
Vous pouvez donner un nom à un stash en utilisant la commande git stash save avec l'option --include-untracked. Cette option inclut également les fichiers non suivis (untracked) dans le stash, ce qui vous permet de les enregistrer dans votre dépôt Git plus tard, Voici un exemple :

```shell
git stash save --include-untracked "Nom du stash"
```

Vous pouvez également utiliser la commande `git stash save` sans l'option `--include-untracked` pour ne mettre en attente (stash) que les modifications apportées aux fichiers suivis (tracked) :

```shell
git stash save "Nom du stash"
```

Pour réappliquer un stash nommé :

```shell
git stash apply stash@{Nom du stash} --index
```

Pour visualiser le contenu d'un stash :&#x20;

```shell
git stash show stash@{Nom du stash}
```
{% endtab %}
{% endtabs %}

## Branch et checkout

Pour créer une nouvelle branche dans Git, vous pouvez utiliser la commande `git branch`. Cette commande vous permet de créer une nouvelle branche à partir de votre position actuelle dans le dépôt.

Voici un exemple de syntaxe de la commande `git branch` pour créer une nouvelle branche appelée "nom-de-la-branche" :

```shell
git branch nom-de-la-branche
```

Cette commande crée une nouvelle branche appelée "nom-de-la-branche", mais ne bascule pas sur cette branche. Pour basculer sur la nouvelle branche, vous devez utiliser la commande `git checkout` :

```shell
git checkout nom-de-la-branche
```

Vous pouvez également créer une nouvelle branche et basculer dessus en une seule commande en utilisant la commande `git checkout -b` :

```shell
git checkout -b nom-de-la-branche
```

## Push

Pour envoyer une nouvelle branche dans un dépôt distant, vous pouvez utiliser la commande `git push`

```shell
git push origin nouvelle_branche
```

Cette commande enverra la nouvelle branche au dépôt distant, où elle pourra être visualisée et fusionnée par d'autres personnes travaillant sur le projet.

Notez que vous devrez peut-être utiliser la commande `git push --set-upstream origin nouvelle_branche` la première fois que vous envoyez la branche, afin de définir le dépôt distant comme destination pour les futurs envois de cette branche.

Pour forcer et remplacer les modifications sur une branche du dépôt distant par les modifications locales :

```shell
git push --force origin ma_branche
```

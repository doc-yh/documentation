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

## Pull avec un Rebase&#x20;

Le "pull" est une opération qui permet de récupérer les modifications du dépôt distant et de les fusionner dans votre branche locale. Le "rebase" est une opération qui consiste à réappliquer vos propres commits sur les dernières modifications de la branche.

Pour faire un "pull" avec un "rebase" :

```shell
git pull --rebase origin ma_branche
```

Cette commande récupèrera les modifications de la branche `ma_branche` sur le dépôt distant, puis les réappliquera sur votre branche locale en utilisant un "rebase". Cela permettra de fusionner les modifications du dépôt distant avec votre branche de manière à ce qu'il n'y ait pas de commits de fusion inutiles dans l'historique.

### Conflits lors d'un rebase

Lorsqu'un "rebase" échoue en raison de conflits, Git arrête le processus et vous indique où se situent les conflits dans les fichiers en question. Vous devrez alors résoudre ces conflits avant de pouvoir continuer le "rebase".

Voici comment procéder :

Ouvrez les fichiers contenant des conflits et cherchez les sections de code entourées de marqueurs de conflit, comme ceci :

```shell
<<<<<<< HEAD
Code sur votre branche
=======
Code sur la branche distante
>>>>>>> nouvelle_branche
```

1. Décidez de la version du code à conserver et supprimez les marqueurs de conflit ainsi que la version du code que vous ne voulez pas garder.
2. Enregistrez et fermez les fichiers une fois que vous avez résolu tous les conflits.
3. Utilisez la commande `git add` pour marquer les fichiers modifiés comme étant prêts à être commités :

```shell
git add fichier1 fichier2
```

Continuez le "rebase" en utilisant la commande `git rebase --continue`.

Git continuera alors le "rebase" et appliquera les commits restants sur les modifications du dépôt distant. Si d'autres conflits surgissent, le processus s'arrêtera de nouveau et vous devrez résoudre ces conflits avant de pouvoir continuer.

Pour afficher la liste des fichiers en conflit lors d'un "rebase", vous pouvez utiliser la commande `git diff` avec l'option `--name-only`. Par exemple :

```shell
git diff --name-only --diff-filter=U
```

Cette commande affichera la liste des fichiers qui ont des conflits non résolus.

Vous pouvez également utiliser la commande `git status` pour afficher la liste des fichiers en conflit. Le résultat inclura une section intitulée "Unmerged paths" qui liste les fichiers en conflit.

### Annuler un rebase

Il est possible d'annuler un "rebase" en cours en utilisant la commande `git rebase --abort`. Cette commande annulera le "rebase" en cours et vous ramènera à l'état de votre branche avant le début du "rebase".

## Squash

Le "squash" est une opération qui permet de fusionner plusieurs commits en un seul. Cela peut être utile lorsque vous avez effectué plusieurs commits de petites modifications et que vous souhaitez les regrouper en un seul commit plus significatif.

Voici comment procéder :

```bash
git log
```

1. Repérez le commit juste avant celui que vous voulez "squasher" et copiez son identifiant (un long nombre hexadécimal).
2. Utilisez la commande `git rebase -i` suivi de l'identifiant du commit copié à l'étape précédente pour lancer l'interface interactive de "rebase" :

```shell
git rebase -i <identifiant_commit>
```

1.  Dans l'interface interactive, remplacez "pick" par "squash" pour chaque commit que vous voulez "squasher". Enregistrez et quittez l'interface.

    a - Vous devriez voir quelque chose comme ceci dans votre éditeur de texte :

    ```
    pick 9caf27b commit_1
    pick 47aeebb commit_2
    ```

    b - Modifiez la liste comme suit :

    ```
    pick 9caf27b commit_1
    squash 47aeebb commit_2
    ```
2. Git vous demandera de modifier le message du commit fusionné. Modifiez le message selon vos besoins, enregistrez et quittez l'interface.

Le "rebase" continuera alors et fusionnera les commits sélectionnés en un seul commit.

## Cherry pick

Voici comment vous pouvez effectuer un cherrypick pour récupérer un commit de la branche `branche_2` et l'appliquer à la branche `master` :

1. Basculez sur la branche `branche_2` en utilisant la commande `git checkout branche_2`.
2. Trouvez le hash du commit que vous souhaitez récupérer en utilisant la commande `git log`. Prenez note du hash du commit.
3. Basculez sur la branche `master` en utilisant la commande `git checkout master`.
4. Utilisez la commande `git cherry-pick <hash du commit>` pour récupérer le commit et l'appliquer à la branche `master`. Si vous rencontrez des conflits, vous devrez les résoudre avant de pouvoir poursuivre.

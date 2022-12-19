# Git

Voici une liste de commandes Git couramment utilisées :

1. `git clone` : utilisée pour cloner un dépôt Git existant sur votre ordinateur.
2. `git status` : vous permet de voir l'état de votre dépôt local, c'est-à-dire les fichiers qui ont été modifiés et qui n'ont pas encore été commités.
3. `git add` : utilisée pour ajouter des fichiers à l'index, c'est-à-dire les préparer pour le prochain commit.
4. `git commit` : utilisée pour enregistrer les modifications que vous avez apportées dans l'index dans votre dépôt local.
5. `git push` : utilisée pour envoyer vos commits vers le dépôt distant (sur un serveur).
6. `git pull` : utilisée pour synchroniser votre dépôt local avec le dépôt distant.
7. `git branch` : utilisée pour gérer les branches dans votre dépôt.
8. `git merge` : utilisée pour fusionner les branches dans votre dépôt.
9. `git log` : utilisée pour afficher l'historique des commits de votre dépôt.
10. `git stash` : utilisée pour mettre de côté des changements temporaires dans votre dépôt.
11. `git config` : utilisée pour configurer les options de Git, comme votre nom d'utilisateur et votre adresse email.
12. `git diff` : utilisée pour afficher les différences entre les fichiers dans votre dépôt.
13. `git reset` : utilisée pour annuler des commits ou des changements dans votre dépôt.
14. `git tag` : utilisée pour ajouter des tags (étiquettes) à des commits dans votre dépôt.
15. `git rebase` : utilisée pour réappliquer les commits d'une branche sur une autre branche.
16. `git cherry-pick` : utilisée pour sélectionner et appliquer individuellement des commits à partir d'une autre branche.
17. `git fetch` : utilisée pour récupérer les derniers commits d'un dépôt distant sans fusionner les changements dans votre branche courante.
18. `git gc` : utilisée pour optimiser et nettoyer votre dépôt local.
19. `git ls-tree` : utilisée pour afficher le contenu d'un commit sous forme d'arborescence de fichiers et de répertoires.
20. `git show` : utilisée pour afficher les détails d'un commit, comme les modifications apportées et l'auteur du commit.
21. `git blame` : utilisée pour afficher les lignes modifiées dans chaque fichier et le commit qui a apporté ces modifications.
22. `git shortlog` : utilisée pour afficher un résumé des commits d'un dépôt, regroupés par auteur.
23. `git grep` : utilisée pour rechercher des chaînes de caractères dans l'historique des commits de votre dépôt.
24. `git remote` : utilisée pour gérer les dépôts distants associés à votre dépôt local.
25. `git submodule` : utilisée pour gérer des sous-modules dans votre dépôt, c'est-à-dire des références à d'autres dépôts Git inclus dans votre projet.
26. `git rev-parse` : utilisée pour extraire des informations sur les objets Git, comme les commits et les branches.
27. `git bisect` : utilisée pour effectuer une recherche binaire dans l'historique des commits de votre dépôt pour trouver un commit spécifique.
28. `git mv` : utilisée pour déplacer ou renommer des fichiers dans votre dépôt.
29. `git filter-branch` : utilisée pour appliquer des filtres sur l'historique des commits de votre dépôt, comme la suppression de fichiers ou la modification de l'auteur d'un commit.
30. `git archive` : utilisée pour créer un archive des fichiers de votre dépôt, dans un format spécifié (par exemple, ZIP ou tar).
31. `git am` : utilisée pour appliquer des patchs envoyés par courrier électronique à votre dépôt.
32. `git cherry` : utilisée pour afficher et appliquer les commits qui ne sont pas encore présents dans une autre branche.
33. `git instaweb` : utilisée pour lancer un serveur web local qui affiche votre dépôt Git en utilisant gitweb.
34. `git subtree` : utilisée pour gérer les sous-arbres (sous-ensembles de répertoires) dans votre dépôt.
35. `git merge-base` : utilisée pour trouver le commit commun le plus récent entre deux branches.
36. `git pack-refs` : utilisée pour empaqueter les références (branches et tags) dans votre dépôt.
37. `git prune` : utilisée pour supprimer les références orphelines (non pointées par aucune branche) dans votre dépôt.
38. `git reflog` : utilisée pour afficher l'historique des références (branches et tags) de votre dépôt.
39. `git request-pull` : utilisée pour générer un message de demande de fusion de changements provenant d'une branche de votre dépôt vers un autre dépôt.
40. `git worktree` : utilisée pour gérer des arbres de travail (copies de votre dépôt) sur votre ordinateur.

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

Pour faire un commit vide sans ajouter de fichiers, vous pouvez utiliser la commande `git commit --allow-empty` avec un message de commit vide.

## Log

Pour lister les commits dans votre référentiel Git local, vous pouvez utiliser la commande `git log`. Cette commande affichera une liste de tous les commits dans votre référentiel, avec leurs hash de commit, auteurs et messages de commit.

Vous pouvez également utiliser des options avec la commande `git log` pour afficher des informations supplémentaires ou filtrer les commits affichés. Par exemple, vous pouvez utiliser l'option `--author` pour afficher uniquement les commits créés par un auteur spécifique, ou l'option `--since` pour afficher uniquement les commits créés après une date spécifique.

Par exemple, si vous souhaitez afficher les commits de l'auteur "Alice" depuis le 1er janvier 2020, vous pouvez utiliser la commande suivante:

```bash
git log --author="Alice" --since="2020-01-01"
```

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

## Rebase d'une branch vers le master

Pour effectuer un rebase d'une feature branch vers le master, vous devez d'abord vous assurer que vous êtes sur la feature branch et que vous avez récupéré les dernières mises à jour du master. Pour ce faire, utilisez les commandes suivantes&#x20;

```shell
$ git checkout feature-branch
$ git pull origin master
```

Une fois que vous êtes sur la feature branch et que vous avez récupéré les dernières mises à jour du master, vous pouvez exécuter la commande de rebase suivante :

```shell
$ git rebase master
```

Cela va appliquer les commits de la feature branch sur le dessus des commits du master, en les "rejouant" l'un après l'autre. Si des conflits surviennent pendant le rebase, vous devrez les résoudre avant de pouvoir continuer.

## Merge d'une branch vers le master

Pour merger une feature branch vers le master, vous devez d'abord vous assurer que vous êtes sur la branche master et que vous avez récupéré les dernières mises à jour du dépôt distant. Pour ce faire, utilisez les commandes suivantes :

```shell
$ git checkout master
$ git pull origin master
```

Une fois que vous êtes sur la branche master et que vous avez récupéré les dernières mises à jour, vous pouvez merger la feature branch en utilisant la commande `git merge`. Par exemple :

```shell
$ git merge feature-branch
```

Cela va fusionner les commits de la feature branch dans le master, en créant un nouveau commit de fusion qui regroupe les modifications apportées dans les deux branches. Si des conflits surviennent pendant le merge, vous devrez les résoudre avant de pouvoir continuer.

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

## Conflits lors d'un rebase

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

## Annuler un rebase

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

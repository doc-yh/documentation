# Gérer les groupes sous Linux

Il existe plusieurs façons de gérer les groupes sous Linux. Voici quelques exemples :

Ajouter un utilisateur à un groupe :

Pour ajouter un utilisateur à un groupe, vous pouvez utiliser la commande "usermod" avec l'option "-a" et "-G", comme ceci :

```bash
usermod -a -G group_name username
```

Cela ajoutera l'utilisateur "username" au groupe "group\_name".

Créer un nouveau groupe :

Pour créer un nouveau groupe, vous pouvez utiliser la commande "groupadd" suivie du nom du groupe que vous souhaitez créer, comme ceci :

```bash
groupadd group_name
```

Supprimer un groupe :

Pour supprimer un groupe, vous pouvez utiliser la commande "groupdel" suivie du nom du groupe que vous souhaitez supprimer, comme ceci :

```bash
groupdel group_name
```

Il est important de noter que cette commande ne supprimera pas les utilisateurs membres du groupe. Si vous souhaitez également supprimer ces utilisateurs, vous devrez les supprimer individuellement en utilisant la commande "userdel".

Lister les utilisateurs d'un groupe :

Pour lister les utilisateurs d'un groupe, vous pouvez utiliser la commande "getent" avec l'option "group", comme ceci :

```bash
getent group group_name
```

Cela affichera la liste des utilisateurs du groupe "group\_name", ainsi que d'autres informations sur le groupe.

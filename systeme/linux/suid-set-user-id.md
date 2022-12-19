# SUID (Set User ID)

Le SUID (Set User ID) est un attribut de fichier utilisé dans les systèmes d'exploitation Unix et Unix-like, tels que Linux et macOS. Il permet de définir l'identité de l'utilisateur propriétaire d'un fichier ou d'un répertoire, ainsi que l'identité du groupe propriétaire.

Le SUID est indiqué par un bit spécial dans les informations du fichier, qui peut être activé ou désactivé en utilisant la commande chmod. Lorsqu'un fichier a le SUID activé, les utilisateurs qui exécutent ce fichier obtiennent les privilèges du propriétaire du fichier, plutôt que leurs propres privilèges. Cela peut être utilisé pour autoriser des utilisateurs à effectuer des actions qui nécessitent des privilèges spéciaux, sans leur donner ces privilèges de manière permanente.

Il est important de noter que le SUID peut être utilisé pour renforcer la sécurité d'un système, mais il peut également être utilisé à des fins malveillantes. Par conséquent, il est recommandé de s'assurer que seuls les fichiers qui en ont vraiment besoin ont le SUID activé, et de s'assurer que ces fichiers sont correctement protégés et gérés.

## Voici un exemple d'utilisation du SUID :

Imaginons qu'un utilisateur a besoin de changer son mot de passe, mais qu'il n'a pas les privilèges nécessaires pour exécuter la commande passwd. Le propriétaire du système peut alors créer un fichier contenant la commande passwd et activer le SUID pour ce fichier. Lorsque l'utilisateur exécute ce fichier, il obtient les privilèges du propriétaire du fichier, ce qui lui permet de changer son mot de passe.

Voici comment cela pourrait être mis en place sur un système Unix ou Unix-like :

Le propriétaire du système crée un fichier nommé "change\_password" contenant la commande passwd :

```bash
#!/bin/bash
passwd
```

Le propriétaire du système active le SUID pour ce fichier en utilisant la commande chmod :

```bash
chmod u+s change_password
```

L'utilisateur peut maintenant exécuter le fichier "change\_password" pour changer son mot de passe, même s'il n'a pas les privilèges nécessaires pour exécuter la commande passwd directement.

Il est important de noter que le SUID peut également être désactivé en utilisant la commande chmod, comme ceci :

```bash
chmod u-s change_password
```

Cela peut être utile si le propriétaire du fichier veut retirer les privilèges spéciaux accordés par le SUID à un fichier donné.

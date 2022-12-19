# sysvinit vs systemd

sysvinit et systemd sont deux gestionnaires de démarrage utilisés sur les systèmes d'exploitation basés sur Unix, tels que Linux. Ils sont responsables de lancer les processus et les services nécessaires au démarrage et au fonctionnement du système.

Voici quelques différences clés entre sysvinit et systemd :

1. Architecture : sysvinit utilise une architecture en cascade, qui consiste en une série de scripts de démarrage exécutés successivement pour démarrer le système. systemd, en revanche, utilise une architecture en arbre, qui permet de démarrer les processus de manière parallèle et de gérer les dépendances entre eux.
2. Gestion des services : sysvinit utilise des scripts de démarrage individuels pour chaque service, tandis que systemd utilise des unités de service, qui sont des fichiers de configuration qui décrivent comment chaque service doit être géré.
3. Gestion des journaux : sysvinit ne gère pas les journaux de manière centralisée, tandis que systemd permet de gérer et de consulter les journaux de tous les services depuis un emplacement unique.
4. Vitesse de démarrage : systemd est généralement considéré comme plus rapide que sysvinit pour démarrer le système, en raison de son architecture en arbre et de sa gestion parallèle des processus.

Il est important de noter que sysvinit est encore largement utilisé sur de nombreux systèmes Linux, mais que systemd est de plus en plus populaire et est devenue la norme de facto sur de nombreuses distributions récentes.

## Exemple de démarrage d'un programme java avec systemd :&#x20;

Voici comment démarrer un programme Java en utilisant systemd sur un système Linux :

Tout d'abord, vous devez créer une unité de service pour votre programme Java. Une unité de service est un fichier de configuration qui décrit comment votre programme doit être géré par systemd. Vous pouvez utiliser l'outil "systemctl" pour créer une unité de service à partir d'un fichier de configuration :

```bash
systemctl create --force --description="My Java program" --user myprogram.service
```

Cela créera une unité de service nommée "myprogram.service" pour votre programme, avec une description "My Java program" et qui sera exécuté en tant qu'utilisateur.

Ensuite, vous devez ajouter le contenu de votre unité de service dans le fichier "myprogram.service" qui vient d'être créé. Voici un exemple de contenu pour une unité de service qui démarre un programme Java nommé "MyProgram" :

```bash
[Unit]
Description=My Java program

[Service]
Type=simple
ExecStart=/usr/bin/java -jar /path/to/MyProgram.jar

[Install]
WantedBy=multi-user.target
```

Notez que vous devez spécifier le chemin complet vers l'exécutable Java et vers votre programme Java dans la ligne "ExecStart".

Enfin, vous pouvez utiliser "systemctl" pour démarrer votre programme Java :

```bash
systemctl start myprogram.service
```

Cela démarrera votre programme Java et le rendra disponible pour être utilisé. Vous pouvez également utiliser "systemctl" pour arrêter, redémarrer ou afficher l'état de votre programme.

Voici quelques exemples de commandes utiles :

#### Pour arrêter le programme :

```bash
systemctl stop myprogram.service
```

#### Pour redémarrer le programme :

```bash
systemctl restart myprogram.service
```

#### Pour afficher l'état du programme :

```bash
systemctl status myprogram.service
```

#### Pour afficher les journaux du service en temps réel :

```bash
journalctl -f myprogram.service
```

Cela affichera les journaux du service Java en temps réel, en ajoutant de nouvelles lignes au fur et à mesure qu'elles sont écrites dans les journaux.

#### Afficher les journaux du service à un moment donné :

```bash
journalctl --since "2022-12-01 00:00:00" --until "2022-12-02 00:00:00" myprogram.service
```

Cela affichera les journaux du service Java pour la période allant du 1er décembre 2022 à minuit jusqu'au 2 décembre 2022 à minuit.

#### Comment configurer un service Java pour qu'il démarre après un service mongo par exemple

```bash
[Unit]
Description=My Java program
After=mongodb.service

[Service]
Type=simple
ExecStart=/usr/bin/java -jar /path/to/MyProgram.jar

[Install]
WantedBy=multi-user.target
```

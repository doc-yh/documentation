# Ajouter un certificat au truststore de Java

Localisez le fichier du truststore par défaut de Java, généralement nommé `cacerts`. Il se trouve généralement dans le répertoire `jre/lib/security` ou `lib/security` de votre installation Java.

Exportez le certificat du serveur distant en utilisant la commande `openssl`. Ouvrez un terminal et exécutez la commande suivante en remplaçant `yourserver.com` par l'adresse du serveur et `mycert.pem` par le nom de fichier souhaité pour le certificat exporté :

```sh
openssl s_client -connect yourserver.com:443 -showcerts </dev/null 2>/dev/null | openssl x509 -outform PEM > mycert.pem
```

Importez le certificat dans le truststore de Java en utilisant la commande `keytool`. Ouvrez un terminal et exécutez la commande suivante en remplaçant `path/to/cacerts` par le chemin d'accès au fichier `cacerts` trouvé à l'étape 1, `mycert.pem` par le nom de fichier du certificat exporté à l'étape 2, et `myalias` par un alias unique pour le certificat :

```sh
keytool -import -trustcacerts -file mycert.pem -alias myalias -keystore /mnt/c/jdk-17.0.2/lib/security/cacerts
```

Vous devrez saisir le mot de passe du truststore pour effectuer cette opération. Le mot de passe par défaut est `changeit`.

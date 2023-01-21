# WSL / Ubuntu

Pour activer systemd, ouvrez votre fichier wsl.conf dans un éditeur de texte en utilisant sudo pour les droits d'administrateur et ajoutez ces lignes au fichier `/etc/wsl.conf` :

```shell
[boot]
systemd=true
```

Vous devrez ensuite fermer votre distribution WSL en utilisant `wsl.exe --shutdown` depuis PowerShell pour redémarrer vos instances WSL. Une fois votre distribution redémarrée, systemd devrait être en cours d'exécution. Vous pouvez le confirmer en utilisant la commande : `systemctl list-unit-files --type=service`, qui affichera le statut de vos services.

**Installer Docker + Compose**

```shell
# Install Docker, you can ignore the warning from Docker about using WSL
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

# Add your user to the Docker group
sudo usermod -aG docker $USER

# Install Docker Compose v2
sudo apt-get update && sudo apt-get install docker-compose-plugin

# Sanity check that both tools were installed successfully
docker --version
docker compose version

# Using Ubuntu 22.04 or Debian 10 / 11? You need to do 1 extra step for iptables
# compatibility, you'll want to choose option (1) from the prompt to use iptables-legacy.
sudo update-alternatives --config iptables
```

Redémarrer ubuntu


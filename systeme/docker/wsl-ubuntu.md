# WSL / Ubuntu

## **Installer Docker + Compose**

```shell
# Install Docker, you can ignore the warning from Docker about using WSL
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

# Add your user to the Docker group
sudo usermod -aG docker $USER

# Install Docker Compose v2
sudo apt-get update && sudo apt-get install docker-compose-plugin

# Using Ubuntu 22.04 or Debian 10 / 11? You need to do 1 extra step for iptables
# compatibility, you'll want to choose option (1) from the prompt to use iptables-legacy.
sudo update-alternatives --config iptables
```

## Docker au démarrage

`nano ~/.bashrc`

Ajouter à la fin du fichier :

```shell
if grep -q "microsoft" /proc/version > /dev/null 2>&1; then
    if service docker status 2>&1 | grep -q "is not running"; then
        wsl.exe --distribution "${WSL_DISTRO_NAME}" --user root \
            --exec /usr/sbin/service docker start > /dev/null 2>&1
    fi
fi
```

Redémarrer le wsl&#x20;

```bash
wsl --shutdown
```

## Pour tout supprimer

En cas de problème : désintaller ubuntu depuis le store + `wsl --unregister Ubuntu` depuis le terminal windows


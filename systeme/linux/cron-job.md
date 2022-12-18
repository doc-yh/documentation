# Exemple de cron job

> Ajouter un cronjob :

```bash
crontab -e
```

> Ajouter la ligne suivante : (tous les jours à 08:00)

```bash
0 8 * * * /dir/start.sh
```

> Puis redémarrer le service :

```bash
sudo service cron restart
```


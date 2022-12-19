# Batch windows

**Variables d'environnement :**

```bash
set CURRENT_DIR=%cd%
set REP_DIR=%CURRENT_DIR%\rep
```

**Vérifier si un dossier existe**

```bash
if exist "%DIR%" (

)
if not exist "%DIR%" (

)
```

**Importer un fichier batch depuis un autre :**

> On crée un fichier "env.bat" Puis on l'appele depuis un autre fichier grâce à la commande call :

```bash
call env.bat
```

**GOTO / CHOICE :**

```bash
@echo off

CHOICE /C yn /M "Y/N ?"
	if errorlevel == 2 goto BUILD --NO--
	if errorlevel == 1 goto START --YES--
	goto END
        
:START  
	echo "start"
	goto END

:BUILD
	echo "build"

:END
	echo "end"
```

**Télécharger des fichiers**

> **Prérequis** : Télécharger la version binary de curl depuis le site : [curl - Download](https://curl.haxx.se/download.html)

```bash
cd "%CURL_DIR%"
curl -o "%DIR%\fichier_local.txt" "http://123.14.01.10:8080/fichier_distant.txt"
```

**Dézipper un fichier**

> **Prérequis** : Télécharger 7zip depuis le site : [Download](https://www.7-zip.org/download.html)

```bash
set ZIP_PATH=C:\Program Files\7-Zip\7z.exe
"%ZIP_PATH%" x "%ZIP_SOURCE%" -o"%DIR_DESTINATION%" -r
```

**Exécuter des commandes sur la même fenêtre**

```bash
cd "%SOURCE%"
call mvn clean install
```

**Exécuter des commandes sur une autre fenêtre**

```bash
set MYSQL_DIR=C:\wamp64\bin\mysql\mysql5.7.14\bin
start cmd /k  "cd %MYSQL_DIR% & call mysqld.exe & call exit"
```

**Exécuter un job tout les 10 secondes**

```bash
@echo off
:loop
	cmd /c "mon_batch.bat"
	timeout /t 10 /NOBREAK
goto loop
```

**Appuyer sur une touche pour continuer...**

```bash
pause
```

**Supprimer un répertoire (Silent)**

```bash
rmdir /s /q %DIR%
```

**Supprimer le contenu d'un répertoire (Silent)**

```bash
DEL /s /q "%DIR%\*"
```

**Supprimer un fichier**

```bash
DEL "%DIR%\1.txt"
```

**Copier le contenu d'un répertoire vers un autre**

```bash
xcopy /s /Y "%SOURCE%\*" "%DESTINATION%\"
```

**Créer un répertoire**

```bash
mkdir "%DIR%"
```

**Passer des arguments**

```bash
set FILE=%1
```

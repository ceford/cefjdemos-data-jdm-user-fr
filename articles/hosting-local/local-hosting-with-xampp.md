<!-- Filename: / Display title: Hébergement local avec XAMPP  -->

## Introduction

XAMPP est un package facile à installer qui regroupe le serveur web Apache, PHP, XDEBUG et la base de données MySQL. Cela vous permet de créer l'environnement dont vous avez besoin pour exécuter Joomla! sur votre machine locale. La dernière version de XAMPP est disponible sur le site web [Apache Friends](https://www.apachefriends.org/index.html). Des téléchargements sont disponibles pour Linux, Windows et Mac OS X. Téléchargez le package pour votre plateforme.

*Note importante concernant XAMPP et Skype :* Apache et Skype utilisent tous deux le port 80 comme alternative pour les connexions entrantes. Si vous utilisez Skype, allez dans le panneau Outils-Options-Avancé-Connexion et désélectionnez l'option *Utiliser les ports 80 et 443 comme alternatives pour les connexions entrantes*. Si Apache démarre en tant que service, il prendra le port 80 avant le démarrage de Skype et vous ne rencontrerez pas de problème. Mais, pour être sûr, désactivez l'option dans Skype.

## Installation

L'installation sur n'importe quelle plateforme est très simple - utilisez l'Installateur. Il n'existe pas de véritable manuel ou guide pour XAMPP. La documentation est sous forme de FAQs liées depuis la page de Téléchargements.

### Installation sur Windows

Pour Windows, il est recommandé d'installer XAMPP dans "c:\xampp" (et non dans "c:\program files"). Si vous faites cela, vos dossiers Joomla! (et tout autre site web local) iront dans le dossier "c:\xampp\htdocs". (Par convention, tout le contenu web va sous le dossier "htdocs".)

Si vous avez plusieurs serveurs http (comme IIS) vous pouvez changer le port d'écoute de xampp. Dans \apache\conf\httpd.conf, modifiez la ligne Listen 80 en Listen \[numéro de port\] (ex : "Listen 8080").

<div class="alert alert-info">
<h4>Tutoriel du Magazine de la Communauté Joomla</h4>
<p>Vous pouvez trouver un tutoriel détaillé sur l'installation de XAMPP sur Windows, ainsi que le Joomla 4 Beta, le Joomla Patch Tester et Git dans cet <a href="https://magazine.joomla.org/all-issues/june-2020/github-installing-git" rel="noreferrer noopener">article du Magazine de la Communauté Joomla</a>.</p></div>

Pour installer XDebug : [XAMPP - Configuration de XDebug pour PHP 8](https://odan.github.io/2020/12/03/xampp-xdebug-setup-php8.html)

### Installation sur Linux

#### Installer XAMPP

La page de téléchargement télécharge un installateur xampp-linux-x64-8.2.12-0-installer.run où 8.2.12 est la dernière version. Exécutez le fichier d'installation pour installer Apache2, MySQL et PHP.

Après l'installation, utilisez les commandes suivantes pour démarrer et arrêter les services :
```sh
    sudo /opt/lampp/lampp start
    sudo /opt/lampp/lampp stop
```

#### Tester votre serveur localhost XAMPP

Ouvrez votre navigateur et pointez-le vers

    http://localhost

Le index.php redirigera vers

    http://localhost/xampp

Là, vous trouverez des instructions sur comment changer les noms d'utilisateur/mots de passe par défaut. Sur un ordinateur qui ne sert pas de fichiers à Internet ou au LAN, changer les paramètres par défaut est une décision personnelle.

#### Obtenir Joomla

* Téléchargez le dernier fichier zip d'installation de Joomla
* Décompressez-le sur votre disque dur
* Connectez-vous à localhost avec un client FTP par défaut
* Créez un dossier pour votre Joomla sur le serveur localhost
* Transférez par FTP les fichiers d'installation décompressés de Joomla dans le dossier Joomla nouvellement créé.

##### Important :

- L'installation de xampp définit la propriété correcte des fichiers et les permissions.
- Utiliser la **commande CHOWN** entraînera **des problèmes de propriété avec xampp**.
- **Utiliser nautilus** pour manipuler des dossiers/fichiers sur localhost **causera des problèmes de propriété avec xampp**.

#### Informations sur la base de données

- Hôte : localhost
- Nom par défaut de la base de données : test
- Utilisateur par défaut de la base de données : root
- Mot de passe par défaut : Il n'y a **pas de mot de passe par défaut**.
- Mot de passe administrateur : votre choix.

Il est recommandé pour l'utilisateur novice d'installer les données d'exemple.

Après installation, supprimez le répertoire d'installation et pointez votre navigateur vers : `http://localhost/votrenouveau\dossierjoomla` ou `http://localhost/votrenouveaudossierjoomla/administrateur`.

#### Créer un lien dans le menu Ubuntu

##### Pour créer une interface graphique pour xamp connectée à votre menu Ubuntu

Ouvrez le Terminal et tapez

    sudo nano /usr/share/applications/xampp-control-panel.desktop

Puis copiez le texte suivant dans l'éditeur nano et enregistrez.

    [Desktop Entry]
    Encoding=UTF-8
    Name=XAMPP Control Panel
    Comment=Start and Stop XAMPP
    Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
    Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg
    Terminal=false
    Type=Application
    Categories=GNOME;Application;Network;
    StartupNotify=true

Si le panneau de contrôle échoue à lancer, essayez de lancer la commande Exec directement dans le terminal :

    gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"

Si vous recevez l'erreur :

    Error importing pygtk2 and pygtk2-libglade

Installez les bibliothèques manquantes :

    sudo apt-get install python-glade2

#### Débogueur PHP XDebug

Le package XAMPP pour Linux n'inclut pas le débogueur PHP XDebug. Pour installer XDebug sur Debian ou Ubuntu :

- Installez le package *build-essential* :

    sudo apt-get update
    sudo apt-get install build-essential
    sudo apt-get install autoconf

- Téléchargez le [package de développement](http://www.apachefriends.org/en/xampp-linux.html)
pour votre version de XAMPP et extrayez-le sur votre installation existante :

    sudo tar xvfz xampp-linux-devel-1.7.7.tar.gz -C /opt

- Construire XDebug :

    wget http://xdebug.org/files/xdebug-2.1.3.tgz
    tar xzf xdebug-2.1.3.tgz
    cd xdebug-2.1.3/
    /opt/lampp/bin/phpize

Après cela, vous aurez la sortie suivante sur votre console…

    Configuring for:
    PHP Api Version:         20090626
    Zend Module Api No:      20090626
    Zend Extension Api No:   20090626

    ./configure --with-php-config=/opt/lampp/bin/php-config
    make
    sudo make install

Ensuite, la sortie sera ceci... veuillez surveiller le répertoire spécifié.

    Installing shared extensions:     /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/

Créez un dossier dans votre dossier temp qui contiendra le fichier de données généré par XDebug :

    sudo mkdir /opt/lampp/tmp/xdebug
    sudo chmod a+rwx -R /opt/lampp/tmp/xdebug

Installations alternatives :

Installez en utilisant la bibliothèque communautaire d'extensions PHP (PECL) fournie avec xampp :

    sudo /opt/lampp/bin/pecl install xdebug

Sur Ubuntu/Debian vous pouvez installer en utilisant :

    apt-get install php5-xdebug

(avertissement : cela installera aussi Apache et PHP depuis les dépôts apt).

##### Avertissement pour les utilisateurs 64bit

Lors de la compilation d'XDebug ou de l'installation via apt-get, vous recevrez une erreur lors du (re)démarrage de xampp :

    /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/xdebug.so: wrong ELF class: ELFCLASS64

C'est parce que xampp fonctionne en 32 bits mais que XDebug est en 64 bits. Pour surmonter ce problème, soit créez xdebug.so sur un ordinateur 32 bits, soit téléchargez-le depuis :

    http://code.activestate.com/komodo/remotedebugging/

Téléchargez le fichier : "PHP Remote Debugging Client" pour "Linux (x86)"
Extrayez le contenu du fichier sur votre ordinateur, ce fichier compressé contient plusieurs dossiers avec des numéros de version ex : 4.4, 5.0, 5.1 ... 5.3 et ainsi de suite, allez dans le dossier avec le numéro de version le plus élevé ou celui qui fonctionne pour vous, puis copiez manuellement le fichier "xdebug.so" à l'emplacement suivant, écrasez si nécessaire

    /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/

N'oubliez pas que cet emplacement pourrait être différent sur votre ordinateur.

### Installation sur Mac OS X

Mac OS X inclut en fait un serveur Apache dès le départ, mais la plupart des développeurs préféreront utiliser les outils intégrés et la configurabilité fournis par XAMPP.

Comme pour la plupart des programmes sur Mac, l'installation est un jeu d'enfant. Visitez le site web [Apache Friends](https://www.apachefriends.org/) et téléchargez l'installateur (xampp-osx-8.2.4-0-installer.dmg). Double-cliquez sur l'installateur téléchargé pour commencer le processus d'installation.

Pour démarrer le serveur, ouvrez "XAMPP Control.app" et appuyez sur le bouton de démarrage à côté d'Apache.

#### Un peu de dépannage

De nombreux utilisateurs de Mac ont une petite difficulté à ce stade lorsqu'ils essaient de configurer une autre instance d'Apache sur leur machine. Si vous ne pouvez pas démarrer l'Apache de XAMPP, vous avez deux options :
**Vous pouvez changer le port d'écoute de XAMPP.** Dans \Applications\XAMPP\xamppfiles\etc\httpd.conf, modifiez la ligne qui dit, "Listen 80" en Listen \[Numéro de port\]. Par exemple :

    Listen 8080

**Vous pouvez changer le port d'écoute du serveur Apache pré-installé.** Dans le finder, allez à "/etc" (CMD+SHIFT+G); à partir de là vous pourrez naviguer à travers les fichiers Apache normalement cachés. Trouvez le dossier appelé Apache2, et éditez le fichier "http.conf". Modifiez la ligne qui dit, "Listen 80" en Listen \[Numéro de port\]. Par exemple :

    Listen 8080

*Note : Si vous choisissez de changer le port du serveur Apache pré-installé, vous pourriez avoir besoin de redémarrer votre ordinateur pour que les changements prennent effet. Vous devrez également vous authentifier en tant qu'administrateur pour changer ces fichiers.*

### Tester l'installation de XAMPP

Une fois que XAMPP est installé et que vous avez démarré le service Apache avec l'outil XAMPP Control Panel, vous pouvez le tester en ouvrant votre navigateur et en vous rendant sur `http://localhost`. Vous devriez voir l'écran d'accueil de XAMPP similaire à celui ci-dessous.

![La page de démarrage de xampp](../../../en/images/hosting/local-hosting-xampp.png)

Sélectionnez le lien appelé `phpinfo()` dans le menu supérieur. Cela affichera un long écran d'information sur la configuration PHP, comme montré ci-dessous.

![La page d'information de la version php de xampp](../../../en/images/hosting/local-hosting-xampp-php.png)

À ce stade, XAMPP est installé avec succès. Notez le *Fichier de Configuration Chargé*. Nous allons éditer ce fichier dans la prochaine section pour configurer XDebug.

*Traduit par openai.com*


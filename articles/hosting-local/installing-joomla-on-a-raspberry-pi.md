<!-- Filename: Installing_Joomla_on_a_Raspberry_Pi / Display title: Installation de Raspberry Pi -->

## Préface

**Remarque : Ce document n'est pas encore complet ni entièrement testé.**

La <a href="https://www.raspberrypi.org/" rel="nofollow noreferrer noopener">Raspberry Pi</a> est un petit ordinateur monocarte initialement développé pour promouvoir l'enseignement des bases de l'informatique dans les écoles et les pays en développement. En raison de sa polyvalence, il est devenu très populaire et est utilisé comme lecteur multimédia, petit serveur autonome, etc. Vous pouvez l'utiliser comme serveur web et y installer Joomla!. Cette page vous montre comment faire fonctionner votre site Joomla! sur le Raspberry Pi.

## Matériel

- **Raspberry Pi version 3 Modèle B** - Il existe différents modèles de Raspberry Pi. Vous pouvez utiliser la plupart des modèles qui possèdent un port Ethernet (les types Modèle B). Cependant, pour des raisons de performance, nous utiliserons la dernière version avec le plus de mémoire RAM.
- **Carte micro SD** - Pour le système d'exploitation + serveur web + Joomla. (Le RPi version 3 modèle B utilise des cartes micro SD, d'autres versions pourraient utiliser des cartes SD normales)
- **Adaptateur de 5 Volts (1 Ampère)** - Pour alimenter le Raspberry Pi, vous devrez convertir l'alimentation secteur (230V ou 110V) en 5 Volts. Le Raspberry Pi a besoin d'environ 1 Ampère, et peut-être plus si vous y connectez des appareils USB.
- Câble **Ethernet standard** - Pour connecter le RPi à votre réseau local / routeur / internet.

## Installation du système d'exploitation

Le système d'exploitation Raspbian est une version de Debian Linux spécialement compilée pour le Raspberry Pi. Il existe deux versions de <a href="https://www.raspberrypi.com/software/" rel="nofollow noreferrer noopener">Raspbian</a> disponibles : **Raspbian Jessie avec Pixel Lite** (version avec bureau PIXEL basé sur Debian Jessie) et **Raspbian Jessie Lite** (version minimale basée sur Debian Jessie). Comme nous utilisons le Raspberry Pi comme serveur web pour Joomla, nous n'aurons pas besoin de l'interface graphique.

**Téléchargez** <a href="https://www.raspberrypi.org/downloads/raspbian/" rel="nofollow noreferrer noopener">Raspbian Jessie Lite</a> et décompressez le fichier téléchargé, par exemple **2016-09-23-raspbian-jessie-lite.zip** (306 MB) en **2016-09-23-raspbian-jessie-lite.img** (1,4 Go).

Nous devons maintenant copier le fichier .img sur la carte SD (micro). Vous pouvez utiliser un outil avec une interface graphique tel que <a href="https://unetbootin.github.io/" rel="nofollow noreferrer noopener">UNetbootin</a> (pour Windows, Mac OS X et Linux) ou le faire en ligne de commande.

**Soyez prudent** lors de l'écriture de l'image disque *.img* sur un autre disque. Si vous spécifiez le mauvais disque de destination, vous le remplacerez par le fichier *.img*, rendant ce disque inutilisable, ce qui entraînera une perte de données.

### Windows

Dans un terminal (CMD), vérifiez quel périphérique correspond à la carte SD et exécutez quelque chose comme :

```
    dd bs=1M if=c:\temp\2016-09-23-raspbian-jessie-lite.img od=[le périphérique de votre carte SD]
```

Voir aussi : <a href="https://www.raspberrypi.org/documentation/installation/installing-images/windows.md" rel="nofollow noreferrer noopener">Installation des images du système d'exploitation en utilisant Windows</a>

### Apple OSX

Vérifiez quel périphérique est utilisé pour votre carte SD. Dans notre cas, il s'agit de *disk1s1* et nous allons exécuter dans le Terminal :

```
    sudo dd bs=1M if=~/Downloads/2016-09-23-raspbian-jessie-lite.img of=/dev/disk1s1
```

Voir aussi : <a href="https://www.raspberrypi.org/documentation/installation/installing-images/mac.md" rel="nofollow noreferrer noopener">Installation des images du système d'exploitation sur MacOS</a>

### Linux

Nous connectons un lecteur de carte SD avec la (micro) carte SD à un ordinateur. Avec *dmesg*, nous pouvons trouver le nom du périphérique de la carte SD. Dans notre cas, dmesg montre quelque chose comme `[xxxxxx.xxxxxxx]  sdd: sdd1 sdd2`, ce qui signifie que nous avons une carte SD avec 2 partitions. Ne pas écrire l'image Raspbian sur une partition mais sur le disque entier **sdd**.

Nous utiliserons *dd* ("Disk Dump") pour écrire un fichier d'entrée (*if*) dans un fichier de sortie (*of*) en utilisant une taille de bloc spécifiée (*bs*).

**Soyez prudent** : *dd* écrira sur un périphérique sans aucun avertissement. Vérifiez deux fois que vous écrivez sur le bon périphérique ! Si vous écrivez sur le mauvais disque, vous vous souviendrez toujours de la commande *dd* comme "Destructeur de Disque".

```bash
    sudo dd if=~/Downloads/2016-09-23-raspbian-jessie-lite.img of=/dev/sdd bs=4M
```

Voir aussi : <a href="https://www.raspberrypi.org/documentation/installation/installing-images/linux.md" rel="nofollow noreferrer noopener">Installation des images du système d'exploitation sur Linux</a>

**AVERTISSEMENT pour la version Raspbian Stretch** : pour avoir un serveur SSH fonctionnant dès le démarrage, vous devez créer un fichier vide *ssh* sur la partition racine.

## Connecter le Raspberry Pi au réseau local (LAN)

Lorsque nous avons installé le système d'exploitation Raspbian sur la carte SD, nous devons :

- Insérer la carte micro SD dans le logement pour carte SD du Raspberry Pi.
- Connecter un câble Ethernet au Raspberry Pi et au réseau local (le connecter à notre routeur).
- Connecter l'alimentation de 5V au Raspberry Pi.

Le démarrage du Raspberry Pi prend environ 30 secondes. Nous devons trouver l'adresse IP pour nous y connecter via SSH. Nous pouvons utiliser différentes approches pour cela :

- se connecter à l'interface web de votre routeur et rechercher les appareils connectés ;
- utiliser un téléphone mobile connecté au routeur Wi-Fi avec une application de scan de réseau appelée **Fing Overlook** ;
- utiliser une commande comme **nmap**. En supposant que notre PC a l'adresse IP **192.168.0**.25, nous pouvons trouver tous les autres appareils dans le même intervalle de réseau en faisant ce qui suit :
```
    sudo nmap -sP 192.168.0/24
```
Ce qui pourrait afficher les détails suivants :

    Starting Nmap 6.47 ( http://nmap.org ) at 2016-10-22 17:42 CEST
    Nmap scan report for 192.168.0.35
    Host is up (0.00042s latency).
    MAC Address: 42:42:42:42:42:42 (Raspberry Pi Foundation)

Pour se connecter à notre Raspberry Pi, nous utiliserons la commande **ssh**.

```
    ssh pi@192.168.0.35
```

La première fois que vous vous connecterez, cela affichera quelque chose comme :

    The authenticity of host '192.168.0.35 (192.168.0.35)' can't be established.
    ECDSA key fingerprint is 42:42:42:42:42:42:42:42:42:42:42:42:42:42:42:42.
    Are you sure you want to continue connecting (yes/no)?

Nous choisirons **Yes**

    Warning: Permanently added 192.168.0.35 (ECDSA) to the list of known hosts.
    pi@192.168.0.35's password:

et utiliser le *mot de passe par défaut* : *raspberry* qui après une connexion réussie affichera :

    The programs included with the Debian GNU/Linux system are free software;
    the exact distribution terms for each program are described in the
    individual files in /usr/share/doc/*/copyright.

    Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
    permitted by applicable law.
    pi@raspberrypi:~ $

Nous pouvons configurer le Raspberry Pi via une interface texte avec :

    sudo raspi-config

### Outil de configuration logicielle du Raspberry Pi (raspi-config)

Avec cet outil de configuration, nous changerons seulement les paramètres suivants.

#### 1 Étendre le système de fichiers

Par défaut, l'espace disque sur la carte SD est de la même taille que le fichier de 1.4 Go .img utilisé pour créer la carte SD pour votre Raspberry Pi. Vous pouvez utiliser cette option pour obtenir le reste de l'espace disque.

#### 2 Changer le mot de passe utilisateur

Pour des raisons de sécurité, il est préférable de **changer le mot de passe par défaut** "raspberry" dès que possible.

#### 3 Options de démarrage

Nous souhaitons que le Raspberry Pi démarre sur la console texte.

##### B2 Console Autologin Console texte, automatiquement connectée en tant qu'utilisateur 'pi'

#### 9 Options avancées

##### A3 Partage de la mémoire

Parce que nous utiliserons le Raspberry Pi en tant que serveur sans écran, sans le connecter à un moniteur, nous pouvons diminuer la mémoire utilisée pour le GPU de 64 à **16**

#### 5 Options de localisation

##### I2 Changer le fuseau horaire

Nous changerons le fuseau horaire pour notre propre fuseau horaire (par exemple, Europe/Amsterdam)

Après avoir effectué tous les changements, nous redémarrerons le Raspberry Pi, et nous nous reconnecterons avec notre nouveau mot de passe.

    ssh pi@192.168.0.35

Il est maintenant temps d'installer tout le reste.

## Mettre à jour le logiciel

Avant d'installer quoi que ce soit d'autre, nous allons :

- **mettre à jour** la liste des versions logicielles de tous les
  dépôts externes
    sudo apt-get update

- **mettre à niveau** tous les logiciels installés
    sudo apt-get upgrade

**Mettre à jour la liste des versions et mettre à niveau tous les logiciels est quelque chose qui doit être fait régulièrement.**

## Serveur Web Nginx

Une alternative rapide et légère au serveur web Apache est le serveur web **Nginx**, qui devient de plus en plus populaire.

### Installation de Nginx

Nous allons installer nginx et toutes ses dépendances (lire : les logiciels dont nginx a besoin pour fonctionner) avec

    sudo apt-get install nginx

Nous recevrons un message comme celui-ci :

    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    The following extra packages will be installed:
     fontconfig-config fonts-dejavu-core libfontconfig1 libgd3 libjbig0 libtiff5 libvpx1 libxpm4 libxslt1.1 nginx-common nginx-full
    Suggested packages:
     libgd-tools fcgiwrap nginx-doc ssl-cert
    The following NEW packages will be installed:
     fontconfig-config fonts-dejavu-core libfontconfig1 libgd3 libjbig0 libtiff5 libvpx1 libxpm4 libxslt1.1 nginx nginx-common nginx-full
    0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
    Need to get 3,550 kB of archives.
    After this operation, 8,666 kB of additional disk space will be used.
    Do you want to continue? [Y/n] y

En choisissant "y", nginx et tous les paquets nécessaires seront installés.

Vous pouvez vérifier l'installation avec un navigateur. Rendez-vous à l'adresse IP de votre Raspberry Pi, dans notre cas
<a href="http://192.168.0.35/"
rel="nofollow noreferrer noopener">http://192.168.0.35/</a> Nous devrions voir un message comme :

    Welcome to nginx on Debian!
    If you see this page, the nginx web server is successfully installed and working on Debian. Further configuration is required.
    For online documentation and support please refer to nginx.org
    Please use the reportbug tool to report bugs in the nginx package with Debian.
    However, check existing bug reports before reporting a  new bug.
    Thank you for using debian and nginx.

#### Démarrage et arrêt de Nginx

Après l'installation, Nginx sera automatiquement démarré. Vous pouvez :

- Arrêter Nginx : sudo service nginx stop
- Démarrer Nginx : sudo service nginx start
- Redémarrer Nginx : sudo service nginx restart

### Configurer Nginx

#### Configuration globale de Nginx

Dans la configuration globale de Nginx, nous pouvons configurer le cache par défaut, etc. Le Raspberry Pi 3 utilise un processeur ARM Cortex-A53 **quad-core** 64 bits de 1,2 GHz. Si vous avez une version antérieure avec moins de cœurs CPU, vous devez utiliser

    sudo nano /etc/nginx/nginx.conf

pour ajuster les "worker_processes" au nombre de CPU de votre appareil. Par défaut, c'est configuré comme

    worker_processes 4;

donc pour le Raspberry Pi 3, vous n'avez pas besoin de le changer.

Après avoir modifié la configuration de Nginx ou la configuration du domaine virtuel, vous devez exécuter un

    sudo nginx reload

pour rendre les modifications effectives.

#### Domaines virtuels

Il est possible d'exécuter plusieurs sites Joomla sur le même serveur en utilisant des domaines virtuels.

Placez chaque site dans un dossier séparé dans le répertoire racine web par défaut /var/www/ par exemple :

- /var/www/example.com/
- /var/www/voorbeeld.nl/
    sudo mkdir /var/www/example.com
    sudo mkdir /var/www/voorbeeld.nl

Pour chaque site, nous créerons un domaine virtuel qui est essentiellement un fichier texte avec des informations spécifiques au domaine :

- /etc/nginx/sites-available/example.com
    server {
    listen 80;
    server_name example.com www.example.com;
    root /var/www/example.com;

    access_log /var/log/nginx/example.com.access_log;
    error_log /var/log/nginx/example.com.error_log info;

    location / {
      index index.php index.html index.htm;
      }
    }

- /etc/nginx/sites-available/voorbeeld.nl
    server {
    listen 80;
    server_name voorbeeld.nl www.voorbeeld.nl;
    root /var/www/voorbeeld.nl;

    access_log /var/log/nginx/voorbeeld.nl.access_log;
    error_log /var/log/nginx/voorbeeld.nl.error_log info;

    location / {
      index index.php index.html index.htm;
      }
    }

Nous devons activer chaque site en créant un lien à partir de /etc/nginx/sites-enabled/ vers le domaine virtuel dans "sites-available". Nous créons un lien symbolique pour chaque domaine virtuel :

    sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/example.com
    sudo ln -s /etc/nginx/sites-available/voorbeeld.nl /etc/nginx/sites-enabled/voorbeeld.nl

Pour rendre cette configuration de domaine virtuel effective, nous exécutons

    sudo nginx reload

et lorsque tout est configuré correctement, il répondra :

    Reloading nginx configuration: nginx.

## Base de données

Nous pouvons installer MariaDB ou MySQL ; Joomla fonctionnera avec les deux. Installons MariaDB avec la commande suivante :

```bash
sudo apt-get install mariadb-server
```

Pendant l'installation, vous devez ajouter un mot de passe pour l'utilisateur **root**. Créons un **mot de passe pour la base de données**, par exemple **correcthorsebatterystaple**.

Enfin, améliorons la sécurité de notre installation de MariaDB en supprimant les comptes root accessibles depuis l'extérieur de l'hôte local, les comptes utilisateurs anonymes et la base de données de test. Nous pouvons le faire avec la commande suivante :

```bash
mysql_secure_installation
```

## PHP

Pour PHP, nous allons installer **php-fpm** (FastCGI Process Manager) qui fonctionne comme un démon et reçoit les requêtes Fast/CGI. De plus, nous allons installer **php5-mysql**, qui est un module pour les connexions à la base de données MySQL directement depuis les scripts PHP.

La version plus récente php7 doit être installée avec

```bash
sudo apt-get install php-fpm php-mysql
```

Nous devons maintenant informer Nginx qu'il doit utiliser php-fpm pour les fichiers .php. Nous ajoutons quelques lignes à nos domaines virtuels :

```bash
sudo nano /etc/nginx/sites-available/example.com
```

ajoutez :

```nginx
location ~ \.php$ {
    fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;
    fastcgi_index index.php;
    include fastcgi_params;
}
```

Testez-le en créant le fichier PHP suivant

```bash
sudo nano /var/www/example.com/test.php
```

Nous utilisons un navigateur pour tester si nous voyons la page de configuration PHP à l'adresse
<a href="http://192.168.0.35/example.com/test.php" rel="nofollow noreferrer noopener">http://192.168.0.35/example.com/test.php</a>

## Joomla!

- à faire
```
    sudo wget https://github.com/joomla/joomla-cms/releases/download/3.6.3/Joomla_3.6.3-Stable-Full_Package.zip
    sudo unzip -x Joomla_3.6.3-Stable-Full_Package.zip
```

## Connexion du Raspberry Pi à Internet

Nous souhaitons que les internautes puissent visiter notre site Joomla sur notre Raspberry Pi. Pour ce faire, nous devons **configurer notre routeur Internet** pour rediriger tout le **trafic entrant** sur le port 80 **vers notre Raspberry Pi**.

Utilisez votre navigateur web pour vous connecter à l’interface Web de votre routeur. Un routeur est généralement situé sur le premier numéro de votre plage d’IP, dans notre cas sur 192.168.0.1. Dans notre routeur, nous configurons le **transfert de port** :

- Adresse IP externe : 0.0.0.0
- Port de départ externe : 80
- Port de fin externe : 80
- Adresse IP interne : 192.168.0.35 ( = notre Raspberry Pi)
- Port de départ interne : 80
- Port de fin interne : 80
- Protocole : TCP

Assurez-vous qu'il est activé.

Si tout fonctionne correctement, vous devriez voir votre propre site Joomla sur le Raspberry Pi en visitant votre adresse IP externe (Trouvez votre adresse IP externe avec un outil comme
<a href="http://www.whatsmyip.org/"
rel="nofollow noreferrer noopener">whatsmyip.org</a>).

### Utilisation d'un nom de domaine

Supposons que notre adresse IP externe soit 42.42.42.42. Supposons également que nous ayons enregistré un nom de domaine appelé example.com. Nous aimerions que notre site Joomla sur notre Raspberry Pi soit accessible aux visiteurs qui visitent example.com. Si notre registraire de nom de domaine nous donne la possibilité de configurer le **système des noms de domaine (DNS)**, alors nous devrons créer un **enregistrement MX** dans le DNS qui pointe notre **nom de domaine vers** notre **adresse IP** 42.42.42.42. Notez que cela peut prendre jusqu'à 24 heures pour que tous les fournisseurs d'accès à Internet redirigent le trafic de leurs clients vers l'enregistrement MX configuré.

### Adresse IP statique

La plupart des routeurs continueront à attribuer la même adresse IP interne à votre Raspberry Pi. Parfois, il est préférable de configurer votre Raspberry Pi pour utiliser une adresse IP statique :

    sudo nano /etc/network/interfaces

modifiez

    iface eth0 inet static

en

    iface eth0 inet static
    address 192.168.0.35
    netmask 255.255.255.0
    gateway 192.168.0.1

La passerelle est l'adresse IP de votre routeur. Vous pouvez également la trouver en utilisant

    route

# Liens externes

- <a href="https://raspberrypi.org"
  rel="nofollow noreferrer noopener">Fondation Raspberry Pi</a> (RPF) -
  site officiel et forums
- <a href="http://elinux.org/RaspberryPiBoard"
rel="nofollow noreferrer noopener">Wiki Raspberry Pi</a>,
  soutenu par la RPF
- Vidéo de la présentation
  <a href="https://youtu.be/u2MFQCoexD0"
  rel="nofollow noreferrer noopener">Joomla sur Raspberry
  Pi (avec Nginx)</a> lors du JoomlaDay Allemagne 2013 à Nuremberg, Allemagne

*Traduit par openai.com*


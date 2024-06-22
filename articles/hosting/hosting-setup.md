<!-- Filename: J4.x:Hosting_Setup / Display title: Configuration de l'hébergement -->

## Introduction

Cette page fournit quelques conseils à toute personne totalement novice
en matière de technologie d'hébergement. Vous pouvez créer un site web
sur votre propre ordinateur portable ou de bureau. C'est ce qu'on
appelle l'hébergement local. C'est un bon moyen d'expérimenter de
nouvelles fonctionnalités et c'est totalement gratuit. Pour mettre le
contenu de votre site Web à la disposition du reste du monde, vous aurez
besoin d'un compte sur un service d'hébergement et vous devrez payer
pour cela.

## Service d'hébergement

Les hébergeurs commerciaux fournissent tout ce dont vous avez besoin
pour gérer un site Web. Certains proposent également l'installation en
un clic d'applications populaires telles que les systèmes de gestion de
contenu, les tableaux d'affichage, les wikis, etc. Mais attention : les
gourous du forum Joomla ne recommandent pas l'installation en un clic.
Chaque service d'hébergement propose différents plans à différents
niveaux de prix. Plus vous payez, plus vous bénéficiez d'espace disque
et de bande passante, ainsi que d'un plus grand nombre d'adresses
électroniques, de bases de données, etc. Certains fournissent également
un nom de domaine gratuit.

Vous pouvez obtenir un plan d'hébergement minimal pour environ 50 € par
an. Ce niveau de plan est souvent appelé hébergement partagé et convient
à tout ce qui n'implique pas de données sensibles. Les entreprises
doivent demander l'avis d'un spécialiste sur les plans d'hébergement
appropriés. Le choix d'un service d'hébergement n'est pas sans poser
problème. Les moins chers peuvent avoir des paramètres php.ini indûment
restrictifs qui n'apparaissent pas dans leur publicité. Certains peuvent
avoir une mauvaise réputation en matière d'assistance.

If you opt for a shared hosting plan check the following:

- Support for PHP applications such as Joomla, WordPress and Mediawiki.
- Disk space: 500Mb is an absolute minimum. 1Gb or more would be better
  if you plan on using lots of images.
- Number of Databases: Joomla uses one but you will soon find you need 5
  or 10 or more. Some plans offer an unlimited number within the total
  disk space allocation.
- Database size: with Smart Search the database can grow very quickly.
  If shared hosting has a restriction on the size of the database, it
  will be important to find out what this is. It can lead to a site not
  working.
- Number of email addresses: plenty!
- Number of HTTP and DB connections to the server, which some shared
  hosts limit
- Backups: how are these done, and is there a Terms of Service (TOS)
  document stating who is responsible for backups.

Vérifiez également le panneau d'administration et la plate-forme
proposés. À en juger par les messages du forum, la plupart utilisent
cPanel sur Linux. Le service d'hébergement doit fournir tous les
logiciels d'assistance de base pour les sites Web :

- Serveur web Apache
- Base de données MySQL
- Support des scripts PHP
- Outil de gestion de la base de données phpMyAdmin.

Avant d'acheter, vérifiez les exigences php minimales suivantes pour
Joomla :

- memory_limit - Minimum : 128M Recommandé : 256M ou mieux
- upload_max_filesize - Minimum : 30M
- post_max_size - Minimum : 30M
- max_execution_time : Recommandé : 30

Si vous avez acheté un nom de domaine, votre service d'hébergement le
configurera pour vous. Il devrait également vous fournir une adresse IP
à utiliser jusqu'à ce que l'enregistrement de votre domaine se propage
aux serveurs de noms de domaine (DNS), généralement quelques heures.

## Hébergement cPanel

Lorsque vous vous connectez au cpanel de votre hébergeur, voici ce que
vous devez vous attendre à voir :

<img
src="https://docs.joomla.org/images/thumb/7/7b/J4.x-hosting-setup-cpanel-en.png/800px-J4.x-hosting-setup-cpanel-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/7/7b/J4.x-hosting-setup-cpanel-en.png 1.5x"
data-file-width="1000" data-file-height="508" width="800" height="406"
alt="J4.x-hosting-setup-cpanel-en.png" />

### Configuration de la base de données

Le panneau d'administration de Bases de données est utilisé pour créer
une base de données et un utilisateur de base de données pour Joomla.

Sélectionnez les bases de données MySQL et entrez un nom de base de
données dans le formulaire. La première partie du formulaire est
prédéfinie. Le reste est à votre discrétion. Il doit être court et
peut-être pas évident - jblog par exemple.

Dans le même formulaire, vous passez ensuite à la section Ajouter un
nouvel utilisateur. Saisissez un nom d'utilisateur. Il peut s'agir de ce
que vous voulez. Il sera utilisé dans votre fichier de configuration de
Joomla, ce n'est donc pas quelque chose dont vous devez vous souvenir.
Utilisez le générateur de mot de passe pour créer un mot de passe non
mémorisable et copiez-le dans un éditeur de texte - vous en aurez besoin
lors de l'installation de Joomla.

Dans le même formulaire, descendez jusqu'à Ajouter un utilisateur à la
base de données. Sélectionnez l'utilisateur que vous avez créé et la
base de données que vous avez créée dans les listes déroulantes, puis
cliquez sur le bouton Ajouter. Un formulaire de gestion des privilèges
s'ouvre. Cochez la case Tous les privilèges, puis cliquez sur le bouton
Modifier.

C'est tout - vous avez maintenant une base de données prête pour une
installation de Joomla.

### Télécharger la source Joomla

À un moment donné, vous aurez téléchargé l'archive zip du code source de
Joomla sur votre ordinateur portable ou de bureau. Vous devez maintenant
décider comment structurer votre site. La racine du document de votre
site est le dossier public_html. Vous pourriez y placer Joomla.
Cependant, cela vous empêche d'utiliser une autre application sur le
même site. Par exemple, vous pourriez avoir deux installations Joomla
entièrement distinctes, l'une pour la production (affichage public) et
l'autre pour les tests (affichage privé). Vous pourriez donc créer un
dossier dans public_html, nommé j4 par exemple, et y télécharger Joomla.
Vous pourriez avoir un autre dossier nommé j4test et y placer une autre
copie de Joomla. L'illustration ci-dessous montre une telle
configuration avec deux sites web Joomla.

<img
src="https://docs.joomla.org/images/thumb/0/01/J4.x-hosting-setup-cpanel-file-manager-en.png/800px-J4.x-hosting-setup-cpanel-file-manager-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/0/01/J4.x-hosting-setup-cpanel-file-manager-en.png 1.5x"
data-file-width="1000" data-file-height="508" width="800" height="406"
alt="J4.x-hosting-setup-cpanel-file-manager-en.png" />

Lorsque vous avez décidé de votre structure, sélectionnez le dossier
Joomla choisi dans le gestionnaire de fichiers et cliquez sur le bouton
Télécharger. Dans le formulaire de téléchargement, sélectionnez
l'archive zip source de Joomla sur votre ordinateur local pour le
télécharger dans le dossier sélectionné. Après le téléchargement,
retournez au gestionnaire de fichiers, sélectionnez le fichier zip et
cliquez sur le bouton Extraire. Après l'extraction, vous pouvez
sélectionner et supprimer le fichier zip.

Voilà, c'est fait ! Vous êtes prêt à installer Joomla.

## Configuration de l'hébergement local avec WAMP

Si vous utilisez un ordinateur Windows, vous pouvez mettre en place un
environnement de développement en utilisant WampServer :

- <a href="https://www.wampserver.com/en/" class="external free"
  target="_blank"
  rel="nofollow noreferrer noopener">https://www.wampserver.com/en/</a>
- <a href="http://forum.wampserver.com/list.php" class="external free"
  target="_blank"
  rel="nofollow noreferrer noopener">http://forum.wampserver.com/list.php</a>
- <a href="https://wampserver.aviatechno.net/" class="external free"
  target="_blank"
  rel="nofollow noreferrer noopener">https://wampserver.aviatechno.net/</a>

## Configuration de l'hébergement local avec XAMPP

Si vous souhaitez installer Joomla sur votre ordinateur personnel, vous
pouvez le faire en utilisant le tutoriel XAMPP ci-dessous.

## Introduction

XAMPP is an easy-to-install package that bundles the Apache web server,
PHP, XDEBUG, and the MySQL database. This allows you to create the
environment you need to run Joomla! on your local machine. The latest
version of XAMPP is available at
<a href="http://www.apachefriends.org/en/index.html"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">the XAMPP web site</a>. Downloads are
available for Linux, Windows, Mac OS X and Solaris. Download the package
for your platform.

*Important Note Regarding XAMPP and Skype:* Apache and Skype both use
port 80 as an alternative for incoming connections. If you use Skype, go
into the Tools-Options-Advanced-Connection panel and deselect the "Use
80 and 443 as alternatives for incoming connections" option. If Apache
starts as a service, it will take 80 before Skype starts and you will
not see a problem. But, to be safe, disable the option in Skype.

### Installation on Windows

Installation for Windows is very simple. You can use the XAMPP installer
executable (for example,
"xampp-windows-x64-7.4.4-0-VC15-installer.exe"). Detailed installation
instructions for Windows are available
<a href="https://www.apachefriends.org/download.html"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">here</a>.

If you are on Windows XP or 2003 they are not supported by the main
package but there are compatible versions of XAMPP for these platforms
listed on the download page (but you will only be able to run PHP 5.4 or
lower - and therefore will only be able to test Joomla 3.x and lower).

For Windows, it is recommended to install XAMPP in "c:\xampp" (not in
"c:\program files"). If you do this, your Joomla! (and any other local
web site folders) will go into the folder "c:\xampp\htdocs". (By
convention, all web content goes under the "htdocs" folder.)

If you have multiple http servers (like IIS) you can change the xampp
listening port. In \apache\conf\httpd.conf, modify the line Listen 80 to
Listen \[portnumber\] (ex: "Listen 8080").

Joomla Community Magazine Tutorial

You can find a detailed tutorial on installing XAMPP on Windows, along
with the Joomla 4 Beta, the Joomla Patch Tester and Git in this <a
href="https://magazine.joomla.org/all-issues/june-2020/github-installing-git"
class="external text" target="_blank" rel="noreferrer noopener">Joomla
Community Magazine article</a>.

### Installation on Linux

#### Install XAMPP

Open Terminal and enter:

    sudo tar xvfz xampp-linux-1.7.7.tar.gz -C /opt

(replace *xampp-linux-1.7.7.tar.gz* with the version of xammp you
downloaded). It has been reported that the MYSQL database of xampp 1.7.4
does not work with Joomla 1.5.22

This installs ... Apache2, mysql and php5 as well as an ftp server.

    sudo /opt/lampp/lampp start

and

    sudo /opt/lampp/lampp stop

starts/stops all the services

#### Test your XAMPP localhost server

Open your Browser and point it to

    http://localhost

The index.php will redirect to

    http://localhost/xampp

There you will find instructions on how to change default
usernames/passwords. On a PC that does not serve files to the Internet
or LAN then changing the defaults is a personal decision.

#### Get Joomla

Download the latest Joomla instalation zip
<a href="https://www.joomla.org/download.html"
class="external autonumber" target="_blank"
rel="noreferrer noopener">[1]</a>

Unzip to your hard drive

Connect to localhost with an FTP client Default

    nobody
    lampp

Create a folder for your Joomla on the localhost server

FTP the unpacked Joomla installation files to the newly created Joomla
folder.

**Important:**

- The xammp installation sets the correct Ownership of the files and
  permissions.
- Using the **CHOWN command** will **cause Ownership problems with
  xampp**.
- **Using nautilus** to manipulate folders/files on localhost will
  **cause Ownership problems with xampp**.

**Database info**

Host

    localhost

Default Database name

    test

Default Database user

    root

There is **no** default Password.

Administrator password is your choice.

Installing Sample Data is recommended for the novice user.

After installation delete the installation directory and point your
Browser to:

    http://localhost/yournewjoomlafolder

or

    http://localhost/yournewjoomlafolder/administrator

#### Creating a link in the Ubuntu menu

**To create a GUI for xammp connected to your Ubuntu menu**

Open up the Terminal and type

    sudo gedit /usr/share/applications/xampp-control-panel.desktop

Then copy the following into the gedit and save.

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

If the control panel fails to launch, try running the Exec command
directly in the terminal:

    gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"

If you receive the error:

    Error importing pygtk2 and pygtk2-libglade

Install the missing libraries:

    sudo apt-get install python-glade2

#### XDebug PHP debugger

The XAMPP package for Linux does not includes the XDebug PHP debugger.
To install XDebug on Debian or Ubuntu:

\- Install the *build-essential* package:

    sudo apt-get update
    sudo apt-get install build-essential
    sudo apt-get install autoconf

\- Download the
<a href="http://www.apachefriends.org/en/xampp-linux.html"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">development package</a> for your
version of XAMPP and extract it over your existing installation:

    sudo tar xvfz xampp-linux-devel-1.7.7.tar.gz -C /opt 

\- Build XDebug:

    wget http://xdebug.org/files/xdebug-2.1.3.tgz
    tar xzf xdebug-2.1.3.tgz
    cd xdebug-2.1.3/
    /opt/lampp/bin/phpize

After this you will have following output on your console…

    Configuring for:
    PHP Api Version:         20090626
    Zend Module Api No:      20090626
    Zend Extension Api No:   20090626 

    ./configure --with-php-config=/opt/lampp/bin/php-config
    make
    sudo make install 

Then the output will be this.. please monitor the directory specified.

    Installing shared extensions:     /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/ 

Create a folder in your temp folder that will holds the data file
generated by XDebug:

    sudo mkdir /opt/lampp/tmp/xdebug
    sudo chmod a+rwx -R /opt/lampp/tmp/xdebug 

Alternative installations:

Install using PHP extensions community library (PECL) bundled with
xampp:

    sudo /opt/lampp/bin/pecl install xdebug

On Ubuntu/Debian you can install using:

    apt-get install php5-xdebug 

(warning: this will also install Apache and PHP from apt repositories).

**Warning for 64bit users**

When compiling XDebug or installing via apt-get, you will receive an
error when (re)starting xampp:

    /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/xdebug.so: wrong ELF class: ELFCLASS64

This is because xampp runs 32bit but XDebug is 64bit. To overcome this
problem, either make xdebug.so on a 32bit machine or download it from:

    http://code.activestate.com/komodo/remotedebugging/

Download the file: "PHP Remote Debugging Client" for "Linux (x86)"
Extract the content of the file on your computer, this compressed file
contains several folders with version numbers ex: 4.4, 5.0, 5.1 ... 5.3
and so forth, get in the folder with the higher version number or the
one that works for you, then manually copy the file "xdebug.so" to the
following location, overwrite if needed

    /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/

Remember this location could be different on your computer

### Installation on Mac OS X

Mac OS X actually includes an Apache server out-of-the-box, but most
developers will prefer to use the integrated tools and configurability
provided by XAMPP.

As with most programs on Mac, installation is a breeze. Visit
<a href="https://www.apachefriends.org/en/download.html"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Apache Friends - Mac OS X</a> for the
universal binary download.

Once the file has finished downloading, just open the disk image, and
drag the XAMPP folder to the "Applications" folder alias.

To start the server, open "XAMPP Control.app" and press the start button
next to Apache.

##### A Little Troubleshooting

Many Mac users have a little difficulty at this stage when trying to set
up another instance of Apache on their machine. If you cannot start
XAMPP's Apache, you have two options:  
**You can change the listening port of XAMPP.** In
\Applications\XAMPP\xamppfiles\etc\httpd.conf, modify the line that
says, "Listen 80" to Listen \[portNumber\]. E.g.:

    Listen 8080

**You can change the listening port of the pre-installed Apache
server.** In finder, go to "/etc" (CMD+SHIFT+G); from here you will be
able to navigate through the normally hidden Apache files. Find the
folder labeled Apache2, and edit the "http.conf" file. Modify the line
that says, "Listen 80" to Listen \[portNumber\]. E.g.:

    Listen 8080

*Note: If you choose to change the port of the pre-installed Apache
server, you may need to restart your computer for changes to take
effect. You will also have to authenticate as an administrator to change
these files.*

### Test XAMPP Installation

Once XAMPP is installed and you have started the Apache service with the
XAMPP Control Panel tool, you can test it by opening your browser and
navigating to
"<a href="http://localhost" class="external free" target="_blank"
rel="nofollow noreferrer noopener">http://localhost</a>". You should see
the XAMPP welcome screen similar to the one below.

<img
src="https://docs.joomla.org/images/thumb/f/fc/Phpinfo_on_xampp.png/800px-Phpinfo_on_xampp.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/f/fc/Phpinfo_on_xampp.png/1200px-Phpinfo_on_xampp.png 1.5x, https://docs.joomla.org/images/f/fc/Phpinfo_on_xampp.png 2x"
data-file-width="1498" data-file-height="883" width="800" height="472"
alt="Phpinfo on xampp.png" />

Select the link called "phpinfo()" in the top menu. This will display a
long screen of information about the PHP configuration, as shown below.

<img
src="https://docs.joomla.org/images/thumb/d/db/Phpinfo.png/800px-Phpinfo.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/d/db/Phpinfo.png/1200px-Phpinfo.png 1.5x, https://docs.joomla.org/images/d/db/Phpinfo.png 2x"
data-file-width="1432" data-file-height="1282" width="800" height="716"
alt="Phpinfo.png" />

At this point, XAMPP is installed successfully. Notice the "Loaded
Configuration File". We will be editing this file in the next section to
configure XDebug.

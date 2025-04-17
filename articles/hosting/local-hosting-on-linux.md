<!-- Filename: No_original_yet / Display title: # Hébergement local sur Linux -->

Cet article traite de l'hébergement de Joomla sur un ordinateur personnel basé sur Linux à des fins de test et de développement. Les versions de Linux abordées font partie de la famille Debian-Ubuntu, et spécifiquement Linux Mint. D'autres distributions sont similaires, mais ont une syntaxe de commande et des emplacements de fichiers différents.

Vous devez installer un ensemble de logiciels souvent appelé le stack LAMP. Les lettres se réfèrent à Linux, Apache, MySQL et PHP. Vous pouvez installer les logiciels en utilisant soit l'interface graphique (GUI), soit la ligne de commande dans une fenêtre Terminal. Ce sont différentes manières d'utiliser le gestionnaire de paquets Synaptic.

## Installer Apache avec l'interface graphique

Depuis le menu système, marqué par le logo LM, sélectionnez Administration / Gestionnaire de paquets Synaptic. Vous serez invité à entrer votre mot de passe. Entrez votre mot de passe de connexion pour ouvrir l'interface graphique. En haut à droite se trouve un bouton `Rechercher`. Sélectionnez-le et entrez **apache**, puis sélectionnez `Rechercher`. Cochez la case `apache2` et, dans le label qui s'affiche, sélectionnez `Marquer pour installation`. Une autre fenêtre s'affichera avec une liste de paquets supplémentaires nécessaires pour prendre en charge apache. Sélectionnez `Marquer` :

![gestionnaire de paquets synaptic](../../../en/images/hosting/synaptic-package-manager-gui.png)

Sélectionnez le bouton `Appliquer` dans la barre d'outils en haut et le bouton `Appliquer` dans la boîte de dialogue Récapitulatif. Apache sera installé et configuré. Le processus se terminera par une **boîte de dialogue Changements appliqués**. Sélectionnez `Fermer`.

Vous pouvez confirmer qu'Apache est installé et fonctionne en ouvrant votre navigateur, Firefox par défaut dans une nouvelle installation de Linux Mint, et en entrant **localhost** dans la barre d'URL. Vous devriez voir la page par défaut d'Ubuntu Apache2 :

![page par défaut d'apache](../../../en/images/hosting/apache-default-page.png)

La page contient des informations utiles sur les emplacements des fichiers qui pourraient ne pas être facilement disponibles plus tard. Vous pourriez donc vouloir imprimer cette page sur papier ou dans un fichier pdf.

## Installer PHP avec le CLI

Il est probablement préférable d'installer PHP en utilisant la ligne de commande. Une raison à cela est qu'au moment de l'écriture, le Gestionnaire de paquets Synaptic n'offre que PHP8.1, bien que PHP8.2 soit disponible depuis un certain temps et puisse être installé à partir d'un dépôt tiers. Il y a une bonne description de la procédure dans ce tutoriel avec des sections de démarrage rapide et détaillée.

Tout d'abord, fermez votre interface graphique du Gestionnaire de paquets Synaptic, puis ouvrez une fenêtre de Terminal et saisissez les commandes suivantes une par une :

```bash
sudo add-apt-repository ppa:ondrej/php
sudo apt update
sudo apt install php8.2 php8.2-cli php8.2-{bz2,curl,mbstring,intl}
sudo apt install php8.2-fpm
sudo a2enconf php8.2-fpm
sudo systemctl reload apache2
```

Dans votre navigateur, vérifiez que la page par défaut de localhost fonctionne toujours.

## Installer MySQL ou MariaDB

Vous pouvez chercher sur le web des informations sur chacun de ces paquets de bases de données. MySQL est le choix traditionnel mais a été repris par Oracle et est maintenant moins populaire. MariaDB est un remplacement Open Source à intégrer avec des fonctionnalités supplémentaires. Les deux fonctionnent avec Joomla! 5 mais il n'est pas facile de passer de l'un à l'autre. Les tables doivent être exportées et importées. Joomla! 5 nécessite des versions minimums spécifiques que Linux Mint propose via le Gestionnaire de paquets Synaptic.

Ouvrez l'interface graphique du Gestionnaire de paquets Synaptic et recherchez soit mysql-server soit mariadb-server. Cochez la case pour l'élément se terminant par -server. Sélectionnez `Marquer pour installation` puis `Appliquer` dans la barre d'outils en haut. Vous pouvez ouvrir le panneau Détails pour voir ce qui se passe pendant l'installation. Sélectionnez `Fermer` une fois terminé.

Vous pouvez tester si votre base de données fonctionne en entrant `mysql` dans la ligne de commande. C'est la même chose pour MySQL et MariaDB. Vous devriez voir un message d'erreur `Access denied`, ce qui est correct car cela indique que votre installation de base de données fonctionne effectivement.

## Installer phpMyAdmin

phpMyAdmin est un outil de gestion de base de données avec interface graphique que vous devrez utiliser pour créer et gérer vos bases de données. Dans l'interface graphique du Synaptic Package Manager, recherchez **phpmyadmin**. Sélectionnez sa case à cocher et `Marquer pour installation`. Après le téléchargement, une invite demande de sélectionner le `Serveur Web à reconfigurer automatiquement`. Cochez la case pour `apache2`, puis cliquez sur le bouton `Suivant`. À l'écran de configuration suivant, laissez la case `Configurer la base de données...` cochée et sélectionnez `Suivant`.

Choisissez un mot de passe application pour l'utilisateur phpmyadmin. Test : dans votre navigateur, entrez localhost/phpmyadmin dans la barre d'URL. Vous devriez voir l'écran de connexion à phpMyAdmin. Avec le nom d'utilisateur phpmyadmin et le mot de passe que vous avez entré durant l'installation, vous pourrez vous connecter. Mais vous ne pourrez pas créer de bases de données ! Pour résoudre ce problème, vous devez modifier le fichier de configuration en tant que root dans la fenêtre Terminal :

```bash
sudo nano /etc/phpmyadmin/config.inc.php
```
Trouvez les deux lignes contenant // $cfg['Servers'][$i]['AllowNoPassword'] = TRUE; et retirez les barres obliques initiales pour les décommenter. Les deux !

Ensuite, connectez-vous à mysql à partir de la ligne de commande et créez un nouvel utilisateur, puis accordez à cet utilisateur tous les privilèges :
```bash
sudo mysql
CREATE USER 'admin'@'localhost' IDENTIFIED BY '';
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'localhost' WITH GRANT OPTION;
exit
```
Ensuite, retournez sur phpMyAdmin et essayez de vous connecter avec le nom d'utilisateur **admin** et sans mot de passe. Vous devriez voir toutes les bases de données et être capable de créer de nouvelles bases de données.

## Priorité du Fichier Index

L'emplacement par défaut pour les pages web sous Ubuntu/Linux Mint est /var/www/html. Si vous listez le contenu de ce répertoire, vous verrez qu'il contient index.html avec le contenu de la page par défaut d'Apache2 sur Ubuntu. Créez un fichier nommé index.php dans ce répertoire avec le contenu suivant :

```php
<?php echo phpinfo();
```
Rechargez localhost. Il n'y a pas de changement ! Entrez **localhost/index.php** dans la barre d'URL et vous verrez une page contenant des informations sur la version de PHP. Ce comportement est contrôlé par la configuration par défaut d'Apache qui peut être modifiée en activant le module `dir` d'Apache et en éditant sa configuration :

```bash
sudo a2enmod dir
sudo nano /etc/apache2/mods-enabled/dir.conf
```

Déplacez index.php en premier dans la liste. Puis redémarrez Apache :

```bash
sudo systemctl restart apache2
```

Cette fois, en utilisant **localhost** seul dans la barre d'URL, vous devriez voir le contenu du fichier index.php, une page d'informations PHP.

## Hôtes virtuels

Dans une installation par défaut de Linux, les fichiers système se trouvent dans le dossier racine (/) et les fichiers de données utilisateur se trouvent dans le dossier personnel (/home/monnomdutilisateur). Cela pose un problème potentiel car l'utilisateur Apache par défaut, www-data, peut ne pas avoir les autorisations appropriées pour créer des fichiers dans l'espace de fichiers utilisateur. La meilleure solution est de créer des hôtes virtuels.

Tout d'abord, un module est nécessaire pour permettre à Apache de changer son utilisateur et son groupe pour convenir à chaque utilisateur :

```bash
sudo apt-get install libapache2-mpm-itk
sudo a2enmod mpm_itk
```

Ensuite, faites une copie du fichier de configuration du site par défaut et modifiez-la :

```bash
cd /etc/apache2/sites-available
sudo cp 000-default.conf monnomdutilisateur.localhost.conf
sudo nano monnomdutilisateur.localhost.conf
```

Le fichier de configuration du site par défaut contient des commentaires pour expliquer son contenu. Ils sont omis dans l'illustration ci-dessous. Décommentez la ligne ServerName et remplacez toutes les instances de `monnomdutilisateur` par votre propre nom d'utilisateur.

```xml
<VirtualHost *:80>
        ServerName monnomdutilisateur.localhost
        ServerAdmin webmaster@localhost
        DocumentRoot /home/monnomdutilisateur/public_html
        <IfModule mpm_itk_module>
                AssignUserId monnomdutilisateur monnomdutilisateur
        </IfModule>
        <Directory /home/monnomdutilisateur/public_html/ >
                Options Indexes FollowSymLinks
                AllowOverride None
                Require all granted
        </Directory>
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

Activez le nouveau site et redémarrez Apache :

```bash
sudo a2ensite monnomdutilisateur.localhost
sudo systemctl reload apache
```

Ajoutez une entrée dans le fichier /etc/hosts pour ajouter une entrée pour le nouvel hôte virtuel. Sinon, votre navigateur le recherchera sur Internet.

```bash
sudo nano /etc/hosts
```

Une fois terminé, il ressemblera à ceci :

```bash
127.0.0.1       localhost
127.0.0.1       monnomdutilisateur.localhost
127.0.1.1       nomdordinateur

# Les lignes suivantes sont souhaitables pour les hôtes compatibles IPv6
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

**Nom d’hôte :** C'est le nom que vous avez donné à votre ordinateur lors de l'installation de Linux. Vous en aurez besoin sous peu. Vous pouvez le changer si vous le souhaitez - mais il est préférable de se renseigner à ce sujet et de le faire d'abord.

Tout étant en ordre, avec une URL de la forme monnomdutilisateur.localhost, vous verrez un listing de répertoire de votre répertoire public_html. L'affichage public des listings de répertoires est généralement considéré comme une mauvaise pratique, un risque de sécurité, et généralement désactivé par un autre paramètre de configuration d'Apache. Cependant, pour un site personnel sur un ordinateur personnel utilisé pour le développement et les tests, c'est très utile. Plusieurs sites différents peuvent être configurés dans différents sous-répertoires. Par exemple, des sites Joomla 4 et Joomla 5, des tableaux d'affichage, des wikis, etc. Quand vous avez beaucoup de sites de test, il est difficile de se souvenir de tous les noms de sous-répertoires !

## Accès au Réseau Domestique

Si vous avez un autre ordinateur sur votre réseau domestique, vous voudrez probablement
accéder à votre site Linux depuis celui-ci aussi. Pour que cela fonctionne, vous avez besoin d'un autre
hôte virtuel. Copiez et modifiez celui que vous venez de créer :

```bash
cd /etc/apache2/sites-available
sudo cp username.localhost.conf username.conf
sudo nano username.conf
```
Changez le ServerName de username.localhost à username.hostname puis
activez le nouveau site virtuel et redémarrez Apache.

```bash
sudo a2ensite username
sudo apachectl restart
```
Allez sur votre autre ordinateur du réseau domestique et modifiez son fichier hosts personnel.
Par exemple, sur un Mac, modifiez /private/etc/hosts et ajoutez la ligne suivante
à la fin :

```bash
192.168.178.20 username.hostname www.username.hostname
```
Où 192.168.178.20 est l'adresse IP de votre ordinateur Linux.

Désormais, sur votre deuxième ordinateur, vous devriez pouvoir accéder au serveur web de
votre ordinateur Linux en entrant username.hostname dans la barre URL de
votre navigateur.

## Notes sur les partitions

Les logiciels installés à l'aide du gestionnaire de paquets Synaptic se trouvent généralement dans le répertoire racine de Linux (/). Les données utilisateur sont situées dans le répertoire personnel (/home). Dans une installation simple, ces répertoires se trouvent dans la même partition physique de disque.

Dans une installation plus complexe, peut-être avec l'option de démarrer différents systèmes d'exploitation (Windows ou Linux) ou différentes versions du même système d'exploitation, les données racine et utilisateur se trouvent souvent dans des partitions distinctes. Cela permet d'accéder aux mêmes données utilisateur depuis chaque système d'exploitation.

Il y a un problème : un site Joomla situé dans un répertoire /home/nom_utilisateur nécessite des données de base de données qui se trouvent habituellement dans le répertoire racine, plus précisément dans /var/lib/mysql. Vous pouvez déplacer le répertoire de données MySQL/MariaDB vers un emplacement accessible aux deux systèmes d'exploitation, soit dans la partition /home, soit dans une partition distincte. Ce tutoriel décrit comment changer le répertoire de données MySQL dans Ubuntu et Debian Linux. Cela doit être fait pour chaque système d'exploitation, mais n'est pas couvert ici.


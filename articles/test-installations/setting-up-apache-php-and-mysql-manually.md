<!-- Filename: Setting_up_Apache,_PHP_and_MySQL_manually / Display title: Configuration manuelle d'Apache, PHP et MySQL  -->

## Aperçu

Voici un bref aperçu des étapes pour configurer Apache, PHP et MySQL dans un environnement Windows et également se référer à divers outils connexes pour maintenir et travailler avec la plupart des tâches liées à Joomla!.

Pour rendre les instructions claires et concises, nous supposerons que, là où aucune instruction explicite n'est mentionnée, vous laisserez les chemins d'installation par défaut s'appliquer sans modification.

### Avertissement

Si vous avez déjà installé une des piles AMP préemballées sur votre machine :

- Revenir à votre pile AMP sera difficile. Les diverses installations que nous réaliserons ci-dessous écraseront des valeurs du registre et apporteront des modifications générales à l'environnement. (Cela s'applique au moins à l'environnement PC/Windows.)
- Si vous devez maintenir une configuration (Apache, MySQL ou PHP) ou des données (vos sites existants et les bases de données associées), avant de tenter de suivre cette instruction, effectuez des sauvegardes appropriées.

(besoin d'être complété avec des conseils spécifiques sur la façon d'atteindre ce qui précède...)

## Configuration de MySQL

1. Téléchargez l'<a href="https://dev.mysql.com/downloads/mysql/" rel="nofollow noreferrer noopener">installateur MySQL</a> approprié pour votre plateforme.
2. Démarrez l'installation et choisissez le chemin d'installation personnalisé.
3. Parcourez tout le processus d'installation et cliquez sur Terminer.
4. Vous verrez maintenant l'*Assistant de Configuration de l'Instance MySQL Server*.
    1. Assurez-vous que la *Configuration Standard* est sélectionnée et cliquez sur Suivant.
    2. Si vous avez déjà MySQL installé, vous pourriez recevoir le message *Un service Windows portant le nom MySQL existe déjà. Veuillez désinstaller ce service correctement ou choisir un nom différent pour le nouveau service.* Si c'est le cas, choisissez un nom de service alternatif.
    3. Dans la fenêtre suivante, cochez *Inclure le Répertoire Bin dans le Chemin Windows*. Cela vous permettra d'accéder aux divers utilitaires MySQL depuis la ligne de commande.
    4. Dans la fenêtre suivante, vous pourrez créer un mot de passe pour votre utilisateur root MySQL, l'utilisateur avec le plus haut niveau d'accès sur votre serveur.
    5. Dans la fenêtre finale, tous les changements que vous avez configurés jusqu'à présent seront enregistrés lorsque vous appuierez sur le bouton *Exécuter* et le service Windows pour cette instance sera démarré.

### Remarques

1. Afin de rendre l'instruction aussi accessible que possible, nous avons omis un certain nombre de scénarios de configuration de votre instance MySQL, comme la possibilité de déplacer vos fichiers de base de données.
2. MySQL s'installe par défaut en mode STRICT, ce qui pourrait provoquer des erreurs lors de l'utilisation d'extensions ou d'applications qui n'ont pas pris cela en compte.

### Ressources MySQL

- <a href="https://www.heidisql.com/" class="external text" rel="nofollow noreferrer noopener">HeidiSQL</a> Un remplacement complet et extensible de phpMyAdmin, facile à utiliser et en développement constant.
- <a href="https://dev.mysql.com/downloads/workbench/" class="external text" rel="nofollow noreferrer noopener">MySQL Workbench</a> Divers outils parmi lesquels vous apprécierez l'Administrateur, qui vous aide à configurer votre instance MySQL. Nécessite le <a href="https://dotnet.microsoft.com/en-us/" class="external text" rel="nofollow noreferrer noopener">framework .Net</a>.
- <a href="https://www.phpmyadmin.net/" class="external text" rel="nofollow noreferrer noopener">phpMyAdmin</a> Un client MySQL puissant basé sur le web pour administrer tout ce qui est lié à MySQL.
- <a href="https://dev.mysql.com/doc/" class="external text" rel="nofollow noreferrer noopener">Documentation MySQL</a>

## Configuration d'Apache

1.  <a href="https://httpd.apache.org/download.cgi" class="external text"
     rel="nofollow noreferrer noopener">Téléchargez l'installateur</a> de votre choix.
2.  Exécutez l'assistant d'installation et passez chaque étape jusqu'à atteindre la fenêtre d'informations du serveur. Indiquez respectivement les options ci-dessous dans l'ordre donné dans chacun des champs, sauf si vous avez des exigences spécifiques concernant la configuration de votre serveur web :
    1.  localhost,
    2.  localhost et
    3.  admin@localhost
3.  Passez en revue l'assistant qui installera et démarrera le serveur web Apache en tant que service Windows.
4.  Dans la barre d'état Windows, vous verrez maintenant une plume de couleur rose avec un bouton de lecture vert indiquant qu'Apache est opérationnel. Pointez votre navigateur vers <a href="http://localhost/" rel="nofollow noreferrer noopener">http://localhost/</a> et vous devriez obtenir une page indiquant que cela fonctionne.
5.  Nous allons maintenant nous rendre à l'emplacement où Apache est installé, qui est généralement à *C:\Program Files\Apache Software Foundation\Apache2.2* et parcourir les différents répertoires :
    1.  *bin* - contient les différents fichiers binaires dont certains sont listés ci-dessous. Pour accéder à ces applications, qui sont pour la plupart basées sur des commandes, nous devrons ajouter le chemin vers le répertoire *bin* dans notre variable PATH globale. Pour ce faire, cliquez avec le bouton droit sur Poste de travail \> Propriétés \> Avancé \> Variables d'environnement et dans la liste des variables système, localisez et sélectionnez la variable PATH, cliquez sur Modifier, et ajoutez un point-virgule final, s'il n'est pas déjà présent, suivi du chemin absolu vers votre répertoire bin. Quittez la boîte de dialogue des propriétés système en acceptant.
        1.  *httpd.exe* qui est le serveur web Apache lui-même, qui est lancé en plusieurs processus enfants tout en répondant à autant de requêtes clients simultanées que requis par la directive MaxClients ;
        2.  *ab.exe* est un outil de benchmarking fourni avec Apache vous permettant de voir comment votre application peut performer par unité de temps.
    2.  *conf* - dossier où se trouvent divers fichiers de configuration, parmi lesquels les suivants sont les plus intéressants dans notre cas :
        1.  *httpd.conf* - la plupart des directives serveur se trouvent dans ce fichier et pour un accès facile, vous devriez associer le type de fichier *.conf* avec un éditeur convivial, c'est-à-dire autre chose que le Bloc-notes par défaut.
        2.  *extra\httpd-vhosts.conf* - contient des directives qui vous permettraient d'utiliser votre serveur local en tant qu'hôte virtuel, c'est-à-dire de pouvoir exécuter plusieurs serveurs sur votre PC. Un scénario d'utilisation est que, pendant une phase de développement, si vous souhaitez mapper le domaine réel pour lequel vous travaillez à votre copie locale, vous pourriez le faire en apportant de légères modifications dans ce fichier. Nous en discuterons plus en détail ci-dessous.
    3.  *htdocs* - la racine du serveur Web par défaut, où <a href="http://localhost/" rel="nofollow noreferrer noopener">http://localhost/</a> est mappé, c'est-à-dire si vous ne le reconfigurez pas dans *httpd.conf* ci-dessus.
    4.  *logs* - les journaux d'accès et d'erreur, utiles pour traiter divers problèmes liés à votre serveur ou même à votre application.

### Ressources Apache

- La <a href="https://httpd.apache.org/docs/current/" class="external text" rel="nofollow noreferrer noopener">documentation de référence Apache</a>

## Configuration de PHP

1.  <a href="https://windows.php.net/download/" class="external text"
     rel="nofollow noreferrer noopener">Télécharger PHP</a>
    et choisissez généralement VC6 x86 Thread Safe au format Zip. Les différentes
    options concernent la manière dont le code source de PHP a été compilé en binaire
    et cela ne devrait probablement pas vous inquiéter pour l’instant.
2.  Créez un dossier sous votre C:\Program Files\\ (ou partout où se trouve votre
    répertoire de programmes) appelé PHP.
3.  Localisez votre fichier Zip téléchargé, déplacez-le vers le dossier nouvellement créé
    et décompressez-le directement dans le dossier.
4.  Ajoutons maintenant le chemin PHP à notre variable PATH globale en suivant
    les instructions ci-dessus.

### Configuration de PHP

La configuration consiste à éditer le fichier *php.ini*. Un fichier d'exemple
pour différents scénarios est déjà dans votre dossier PHP. Renommons
*php.ini-development* en *php.ini* et ouvrez-le dans votre éditeur de texte préféré. Les valeurs communes à ajuster sont les suivantes, et toutes ces
variables sont bien documentées dans le fichier *php.ini*. (Notez qu'il s'agit
d'un réglage applicable à tous vos projets sur le serveur) :

- *max_execution_time* - chaque fois que vous avez des scripts qui s'exécutent trop longtemps
  et que le serveur renvoie des résultats inattendus que vous pensez être dus à un processus non terminé
- *memory_limit*
- *error_reporting*
- *display_errors*
- *log_errors* - une variable dont vous devrez tenir compte dans les scénarios de production
- *upload_tmp_dir*
- *upload_max_filesize*
- *extension_dir* - afin d'éviter des complications, nous indiquerons
  le répertoire où les extensions suivantes sont situées en
  décommentant cette variable et en assignant l’emplacement absolu du
  dossier. La ligne complète devrait être la suivante :
    extension_dir = "C:\Program Files\PHP\ext"

- La section des extensions dynamiques contient divers modules supplémentaires que
  vous souhaitez charger, et celles commentées sont celles qui
  viennent prépackagées avec PHP et qui se trouvent dans le répertoire *ext* de
  votre dossier PHP. Si vous souhaitez activer l'une d’elles, supprimez simplement le
  commentaire comme vous devriez le faire avec les extensions suivantes :
  - php_curl.dll
  - php_gd2.dll
  - php_mbstring.dll
  - php_mysql.dll
  - php_mysqli.dll
  - php_pdo.dll
  - php_pdo_mysql.dll
  - php_xsl.dll
- session.save_path

### Configuration d'Apache pour fonctionner avec PHP

Maintenant que nous avons configuré PHP pour qu'il fonctionne comme nous le souhaitons, passons à
Apache et faisons la même chose.

- Ouvrez *httpd.conf* et dans la section "Dynamic Shared Object (DSO) Support",
  ajoutez les directives suivantes. (Si vous avez localisé différemment votre dossier PHP, apportez les modifications correspondantes au php5apache2_2.dll
  ci-dessous.) :
    LoadModule php5_module "C:/Program Files/PHP/php5apache2_2.dll"
    AddType application/x-httpd-php .php

- Dans le DirectoryIndex, ajoutez *index.php* et *index.htm* comme fichiers possibles
  à servir lorsque le répertoire est demandé comme suit :
    DirectoryIndex index.html index.htm index.php

- À la fin du fichier, ajoutez la ligne suivante, qui indiquera
  où se trouve le fichier *php.ini*
    PHPIniDir "C:/Program Files/PHP"

### Redémarrer et tester PHP

Dès que vous apportez une modification à *php.ini*, *httpd.conf* ou à tout autre
fichier de configuration, vous devez redémarrer Apache pour voir l'effet des
modifications. Redémarrons donc Apache en utilisant l'outil Apache Monitor
que vous pouvez trouver dans votre barre d'état Windows. Espérons que vous ne soyez pas
invité à entrer dans des dialogues et que l’Apache Monitor continue de fonctionner
en vert.

Nous allons maintenant tester que PHP fonctionne. Allez dans le répertoire
documentaire de votre serveur web (dans le cas par défaut *C:\Program Files\Apache Software
Foundation\Apache2.2\htdocs*) et ajoutez un fichier appelé *phpinfo.php* avec
le contenu suivant :

Cela affichera une page contenant des informations sur votre configuration PHP et
sur les différents modules/extensions actuellement chargés. Pointez votre navigateur vers
<a href="http://localhost/phpinfo.php"
rel="nofollow noreferrer noopener">http://localhost/phpinfo.php</a>.

### Installation et configuration de *xdebug*

1.  Pointez votre navigateur sur
    <a href="https://xdebug.org/wizard" class="external text"
     rel="nofollow noreferrer noopener">Assistant d'installation
    de Xdebug</a>. Cette page vous aidera à trouver une version adaptée
    de Xdebug.
2.  Copiez l'intégralité de la page *phpinfo* que nous avons exécutée ci-dessus et collez-la
    dans la zone de texte et suivez les instructions fournies pour l'installation.

### Ressources XDebug

- Le <a href="https://www.php.net/docs.php" class="external text"
   rel="nofollow noreferrer noopener">Manuel PHP</a>
  Excellente documentation à jour avec des commentaires supplémentaires précieux
  des utilisateurs. Des versions téléchargeables sont disponibles.
- La
  <a href="https://xdebug.org/docs/" class="external text"
  rel="nofollow noreferrer noopener">Documentation de Xdebug 3</a>

*Traduit par openai.com*


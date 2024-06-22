<!-- Filename: Copying_a_Joomla_website / Display title: Copier un site Joomla! -->

<span id="main-portal-heading">Didacticiel  
Copier un site Joomla!</span>

  
La copie d'un site web Joomla! est un processus à deux étapes : il vous
faut copier les fichiers et la base de données (emplacement de stockage
du contenu). Copier les fichiers et la base de données sont des
opérations distinctes. L'ordre de la procédure dépendra de votre
situation particulière mais, dans la plupart des cas, cela n'a pas
vraiment d'importance. Si votre site web est mis à jour fréquemment et
que vous avez besoin de mettre votre site hors ligne pendant le
déroulement de la copie, alors vous souhaiterez probablement effectuer
la copie de base de données en dernier de façon à minimiser la durée de
mise hors-ligne.

## Copier un site Web (méthode classique)

#### Akeeba

- Akeeba Backup génère un fichier `.jpa`.
- Le fichier .jpa contient tous les dossiers/fichiers et les fichiers de
  base de données.
- Le fichier .jpa contient également un programme d'installation.
- `kickstart.php` (via Akeeba) permet de décompresser le fichier `.jpa`
- Ensuite, exécutez le programme d'installation et installez votre site
  comme lors d'une installation classique de Joomla!.
- Le programme d'installation modifie la configuration en vue de sa
  restauration dans un emplacement différent et demande les informations
  de la nouvelle base de données.

Après avoir créé la base de données pour Joomla!, téléchargez et
installez Akeeba. Vous pouvez télécharger cette extension sur le <a
href="https://extensions.joomla.org/extensions/extension/access-a-security/site-security/akeeba-backup/"
class="external text" target="_blank"
rel="noreferrer noopener">Répertoires des Extensions Joomla!</a>. Vous y
trouverez également un lien vers des instructions complètes.

### Copier les fichiers via FTP

Une méthode de copie des fichiers d'une installation Joomla! vers une
autre est l'utilisation d'un logiciel FTP vous permettant de charger
tous les fichiers de votre site présents sur votre serveur web, puis de
les transférer à l'emplacement de la nouvelle installation Joomla!.
L'emplacement de la copie de votre site Joomla! peut varier, cela peut
être un répertoire différent sur le même serveur web ou un nouvel
emplacement sur un autre serveur web. Lors d'une copie de Joomla! sur le
même serveur (i.e. à des fins de tests), il est recommandé d'utiliser un
sous-domaine plutôt qu'un sous répertoire. Ceci évitera les erreurs et
d'éventuels problèmes en utilisant les deux installations en même temps.

Il est important de conserver la même structure de répertoire pour
l'ensemble des dossiers et fichiers que vous déplacez d'un emplacement
vers un autre. Heureusement, un logiciel FTP va gérer cela
automatiquement lors du chargement et téléchargement des ensembles de
fichiers et dossiers. (Votre logiciel FTP devrait contenir une
documentation vous expliquant le FTP et l'utilisation de l'interface du
logiciel). Notez qu'après avoir déplacé les fichiers vers un nouvel
emplacement, il vous faudra peut-être modifier les fichiers de
configuration Joomla! afin que votre copie puisse fonctionner dans ce
nouvel environnement ; il vous faudra peut-être également modifier
certains paramètres de votre serveur Web afin que votre copie
fonctionne.

Dans de rares cas, un fichier peut être endommagé lors d'un transfert
FTP, où seule une partie du fichier a été transmise avec succès. Après
avoir copié les fichiers, si vous rencontrez des erreurs étranges ou
inattendues avec votre nouvel installation Joomla, il vous faudra
essayer de télécharger à nouveau vos fichiers en cas de corruption au
cours du transfert.

#### Télécharger les fichiers d'un serveur vers votre ordinateur

1.  Utilisez un logiciel client FTP (par exemple FileZilla) pour vous
    connecter au serveur.
2.  Sélectionnez le répertoire que vous souhaitez télécharger (souvent :
    `/public_html/` ou `/htdocs/`).
3.  Faites un clic droit + sélectionnez les fichiers/dossiers à
    télécharger ou faites un glisser/déposer du dossier à partir de la
    vue *Site distant* vers la vue *Site local*.
4.  Le téléchargement des fichiers distants va alors commencer.
5.  Après avoir téléchargé les fichiers, vérifiez l'onglet *Transferts
    échoués* pour voir s'il y a des erreurs.

#### Télécharger des fichiers de votre ordinateur vers un serveur distant

1.  Assurez-vous que votre fichier configuration.php possède les bons
    paramètres pour le serveur (en particulier : *localhost*,
    *database*, *database user*, *database password*, *log_path*,
    *tmp_path*).
2.  Utilisez un logiciel client FTP (par exemple FileZilla) pour vous
    connecter au serveur.
3.  Sélectionnez le répertoire que vous souhaitez charger et
    l'emplacement du chargement (souvent vers `/public_html/` ou
    `/htdocs/`).
4.  Faites un clic droit + sélectionnez les fichiers/dossiers à charger
    ou faites un glisser/déposer du dossier à partir de la vue *Site
    local* vers la vue *Site distant*.
5.  Le chargement des fichiers locaux vers le serveur distant va alors
    commencer.
6.  Après avoir chargé les fichiers, vérifiez l'onglet *Transferts
    échoués* pour voir s'il y a des erreurs.

### Copier la base de données avec phpMyAdmin

L'outil phpMyAdmin peut être utilisé pour exporter et importer une base
de données, fournissant un moyen simple de dupliquer une copie d'une
base de données en utilisant un nom différent sur les serveurs.

#### Exporter une copie de la base de données sur votre ordinateur

1.  Connectez-vous à la base de données que vous souhaitez copier à
    l'aide de phpMyAdmin.
2.  Cliquez sur le nom de la base de données sur le côté gauche de la
    page.
3.  Sélectionnez l'onglet *Exporter*.
4.  S'il y a lieu, sélectionnez l'option Enregistrer en tant que
    fichier.
5.  Cliquez sur *Exécuter*.

Vous serez alors invité à enregistrer le fichier de base de données sur
votre ordinateur personnel.

#### Importer la copie dans une nouvelle base de données

Vous devez d'abord créer la nouvelle base de données vide sur votre
serveur depuis le panneau de configuration du compte. Elle doit être en
UTF8 (utf8_general_ci). Une fois la nouvelle base de données créée :

1.  Connectez-vous à la base de données avec phpMyAdmin
2.  Cliquez sur le nom de la base de données sur le côté gauche de la
    page.
3.  Sélectionnez l'onglet *Importer*.
4.  Cliquez sur le bouton *Parcourir* situé sous *Fichier à importer*,
    puis sélectionnez le fichier de base de données sur votre
    ordinateur.
5.  Cliquez sur *Exécuter* pour importer base de données.

**Astuce :** Si une erreur du type *Aucune base de données sélectionnée*
s'affiche, c'est probablement parce que vous avez oublié de cliquer tout
d'abord sur le nom de la base de données dans la colonne de gauche.

### Modifier le fichier configuration.php

Afin que votre site Joomla! fonctionne sur le nouveau serveur, vous
devez faire les changements nécessaires dans le fichier
*configuration.php* afin de refléter les paramètres du nouveau serveur.
Vous devriez vérifier/modifier les éléments suivants :

       var $host = 'localhost'; // usually "localhost". If it's different for your server then your hosting provider should be able to tell you that.
        var $user = 'the_db_username';
        var $db = 'the_databasename';
        var $password = 'the_db_password';
            var $live_site = ''; // is usually empty.
            var $cookie_domain = ''; // Should be empty.

Votre site Joomla! fonctionnera, même si \$log_path et \$tmp_path sont
incorrects, mais vous ne pourrez pas installer d'extensions.
Connectez-vous au backend de votre nouveau site Joomla.

Allez dans : Système **→** Informations Système **→** Permissions des
dossiers.  
Regardez les 4 lignes sur le bas :

    cache (Cache Directory) Writable
    administrator/cache (Cache Directory)  Writable
    /var/www/some/other/folder/example.com/logs/ (Log directory) Unwritable
    /var/www/some/other/folder/example.com/tmp (Temp directory)  Unwritable

Si `$log_path` et `$tmp_path` sont en *Lecture seule*, il vous faudra
modifier ces valeurs dans `configuration.php`.

Utilisez les valeurs du *Cache Folder* sans la partie */cache/* et
modifiez `$log_path` et `$tmp_path` en :

       var $log_path = '/var/www/example.com/logs';
       var $tmp_path = '/var/www/example.com/tmp';

Si les permissions de dossiers affichent que `$log_path` et `$tmp_path`
sont *Modifiable*, alors vous devriez être en mesure d'installer des
extensions.

## Copier un site web en utilisant la ligne de commande SSH (méthode pour utilisateurs expérimentés)

### Copier les fichiers en utilisant une méthode de fichier d'archive compressé

La copie d'un grand nombre de fichiers en utilisant le protocole FTP
peut se révéler peu fiable. Si vous avez accès aux lignes de commande
pour les systèmes de source et destination, alors vous pouvez créer un
fichier d'archive compressé contenant tous les fichiers du système
source, puis transférer ce fichier unique vers le système de destination
où il peut être décompressé.

#### Créer un fichier d'archive

Sur les systèmes de type Unix (par exemple, Linux), vous pouvez utiliser
le programme **gzip** pour créer des fichiers .zip, ou le programme
**tar** pour créer des fichiers .tar.gz ou .tar.bz2. Pour obtenir des
instructions détaillées, tapez la ligne de commande **man gzip** ou
**man tar**. Par exemple,

    tar cvfz joomlabackup.tar.gz /path-to-joomla

va créer un fichier d'archive compressé gzip, nommé
*joomlabackup.tar.gz* contenant tous les fichiers de votre installation
Joomla.

**Remarque importante !** Vous devez vous assurer que vous n'êtes PAS
dans le dossier que vous essayez de sauvegarder lorsque vous exécutez la
commande tar, sous peine de créer une boucle sans fin.

#### Extraire un fichier d'archive

Après avoir copié le fichier d'archive vers le système de destination,
il vous faudra le décompresser. Utilisez la commande équivalente à celle
que vous avez utilisée pour créer le fichier d'archive. Par exemple,
pour décompresser le fichier d'archive créé dans l'exemple ci-dessus,
entrez :

    cd /path-to-joomla
    tar xvfz joomlabackup.tar.gz

Si les ID d'utilisateur ou de groupe ne sont pas identiques dans les
systèmes source et destination, alors il vous faudra modifier le
propriétaire des fichiers que vous venez d'extraire. Par exemple, sous
un système Apache, vous pourriez avoir besoin d'entrer la commande :

    cd /path-to-joomla
    chown -R www-user:www-group *

afin qu'Apache ait la propriété des fichiers Joomla.

*Veuillez demander à votre hébergeur les bons noms de groupe et
utilisateur, `www-group` et `www-user`, de votre système.*

### Copier la base de données avec la méthode de la ligne de commande MySQL

Habituellement, vous exécutez la commande `mysqldump` pour créer une
copie de la base de données :

    $ mysqldump -u user -p db-name > db-name.out

Copiez le fichier `db-name.out` via sftp/ssh vers un serveur MySQL
distant :

    $ scp db-name.out user@remote.box.com:/backup

Restaurez la base de données sur le serveur distant (connexion via
ssh) :

    $ mysql -u user -p db-name < db-name.out

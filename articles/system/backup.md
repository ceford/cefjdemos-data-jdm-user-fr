<!-- Filename: jdocmanual?manual=user&heading=system&filename=backup.md / Display title: Sauvegarde   -->

## Les Accidents Arrivent !

Beaucoup de temps, d'efforts et d'argent sont investis dans la création et la maintenance d'un site web. Ce serait dommage de tout perdre à cause d'un accident imprévu. La sauvegarde est facile pour les sites moyens. Les sites plus grands ou spécialisés ont probablement besoin de conseils spécialisés.

## Stratégie de sauvegarde

Les sites Joomla! se composent de deux parties :

* Les **fichiers** situés dans le répertoire racine de Joomla. Entre les mises à jour, les fichiers peuvent ne pas beaucoup changer car ils sont principalement liés au code. De nouvelles images et documents peuvent être ajoutés, ainsi que des substitutions de modèles.
* La **base de données** située ailleurs sur le serveur hôte. La base de données contient la plupart du contenu du site et peut beaucoup changer à mesure que les utilisateurs ajoutent ou modifient du contenu.

Chaque propriétaire de site doit avoir une stratégie de récupération du site en cas de sinistre. Un conseil courant sur les forums est de **restaurer la dernière sauvegarde**. Décidez donc de ce qu'il faut sauvegarder et à quelle fréquence le faire.

Les services d'hébergement prennent souvent des **instantanés** des sites des clients et peuvent être en mesure de restaurer un site à son état d'hier, de la semaine dernière ou du mois dernier. Mais cela pourrait couvrir tout le compte, y compris les courriels et d'autres logiciels. Ne comptez pas là-dessus pour la récupération d'un site Joomla.

Cet article décrit quelques méthodes **gratuites** courantes pour sauvegarder des sites Joomla. Vous pouvez choisir de payer pour des outils et/ou services de sauvegarde, mais cela n'est pas abordé ici.

## Akeeba Backup

Si vous utilisez le menu Administrator pour naviguer vers **Système / Installer des Extensions / Installer depuis le Web**, le premier élément de la liste est *Akeeba Backup*. Il est en tête de liste car il a le plus grand nombre d'avis positifs. Inutile de dire qu'il a une longue histoire et une réputation irréprochable. Il existe une version gratuite et une version payante avec quelques fonctionnalités supplémentaires. C'est un modèle commercial courant pour les développeurs d'extensions. Ne soyez pas hésitant ! La version gratuite est facile à utiliser, sans distractions et suffit pour la plupart des sites. Voici ce qu'elle fait :

* Akeeba Backup analyse votre installation pour déterminer les paramètres optimaux afin de créer un fichier de sauvegarde.
* Elle crée un fichier de sauvegarde composite contenant tous les fichiers du site web et le contenu de la base de données.
* Elle stocke des sauvegardes datées pour les gérer, les télécharger ou les supprimer si nécessaire.
* Le téléchargement est un fichier .jpa. Elle recommande l'utilisation de FTP pour le téléchargement.
* Il existe une application séparée, Akeeba Kickstart, pour décompresser le fichier .jpa. Tout cela est décrit dans la page Gérer les Sauvegardes d'Akeeba.
* Après décompression, le site est installé avec un installateur Akeeba dans une séquence similaire à une installation Joomla.
* L'installateur modifie la configuration pour restaurer à un autre emplacement et demande les nouveaux détails de la base de données.

Le seul problème qui pourrait survenir est que le fichier de sauvegarde pourrait être très volumineux et que vous pourriez dépasser votre quota d'espace disque si vous permettez l'accumulation des sauvegardes.

Essayez-le ! Cela ne coûte rien et prend quelques minutes plutôt que des heures.

## Outils d'hébergement

La plupart des services d'hébergement fournissent des outils de sauvegarde. Exemple :

### cPanel

Sur la page **Outils**, l'élément *Fichiers* a un lien *Sauvegarde*. La page **Sauvegarde** propose trois options :

* **Sauvegarde complète :** Une sauvegarde complète crée une archive de tous les fichiers et configurations de votre site web. Vous pouvez utiliser ce fichier pour déplacer votre compte vers un autre serveur ou pour conserver une copie locale de vos fichiers.
* **Sauvegarde partielle**
  - Télécharger une sauvegarde du répertoire personnel
  - Télécharger une sauvegarde de base de données (avec une liste des bases de données)

Il existe également des options pour **Restaurer** chacun de ces types de sauvegarde. Des options pour produire des sauvegardes automatiques peuvent également être disponibles.

Des dossiers individuels peuvent être compressés dans divers formats adaptés au téléchargement en utilisant le gestionnaire de fichiers cPanel. Une base de données peut être exportée en utilisant phpMyAdmin. Aucune de ces méthodes n'est couverte ici.

## Outils Locaux

Il y a des occasions où vous pourriez avoir besoin de sauvegarder un site localement sur un ordinateur portable ou un ordinateur de bureau au bureau. Par exemple, vous pourriez vouloir copier un site vers/depuis un service d'hébergement vers/depuis votre ordinateur local. Si vous avez une installation locale de Joomla, vous pouvez utiliser Akeeba Backup comme décrit ci-dessus. Sinon, vous pouvez sauvegarder séparément la base de données et les fichiers Joomla.

### mysqldump

Si vous utilisez MySQL, il est probable que l'outil en ligne de commande *mysqldump* soit disponible. Essayez cette commande :

```bash
/usr/local/mysql/bin/mysqldump -u root -p dbname > ~/tmp/dbname-dump.sql
```
où `root` est un utilisateur qui a accès à la base de données et `dbname` est le nom de la base de données que vous souhaitez exporter. Il est possible que l'on vous demande de saisir le mot de passe.

Vous pouvez aussi rediriger la sortie vers une commande zip ou gzip :
```bash
/usr/local/mysql/bin/mysqldump -u root -p dbname | gzip > ~/tmp/dbname-dump.sql.gz
```

### phpMySQL

Pour réaliser le même travail avec votre installation locale de phpMyAdmin, ouvrez-la et sélectionnez la base de données que vous souhaitez exporter. Sélectionnez le bouton **Exporter** en haut de l'écran. Par défaut, l'exportation *Rapide* utilise SQL comme format de sortie. Sélectionnez le bouton **Exporter** pour essayer cela. Vous devrez choisir un fichier de sortie.

Si vous choisissez l'option *Personnalisée*, cela vous permet de sélectionner une option de Compression de Sortie, soit aucune, soit compressée en zip ou gzip. Essayez une exportation compressée et sélectionnez le bouton **Exporter**.

Il est nécessaire de **vérifier** la base de données exportée. Créez une nouvelle base de données, peut-être `animporttest` afin qu'elle soit en haut de votre liste de bases de données. Avec la nouvelle base de données vide sélectionnée, utilisez le bouton **Importer** en haut de l'écran. Dans le formulaire d'importation, utilisez **Parcourir** pour trouver le fichier que vous avez exporté, puis sélectionnez le bouton **Importer**.

Cela valait la peine de **vérifier**. L'exportation gzip n'a exporté que trois tables. L'exportation zip a fonctionné correctement. Cela se voyait dans les tailles des fichiers exportés. Le fichier zip faisait 4 Mo, mais le gzip faisait seulement 75 Ko. Il doit y avoir un bug quelque part !

### Zip et Gzip

Ces outils en ligne de commande sont assez répandus et sont souvent utilisés à partir d'interfaces graphiques. Par exemple, dans le Finder sur Mac, je peux sélectionner un répertoire contenant un site Joomla, faire un clic droit et sélectionner **Compresser**. Cela prend quelques secondes pour créer une archive zip et n'affecte pas l'original.

## Restauration d'une Sauvegarde

Conseils courants des Forums Joomla :

* Ne restaurez pas une sauvegarde par-dessus un site défaillant.
* Videz votre base de données en supprimant toutes les tables ou créez une nouvelle base de données et assignez-lui un utilisateur de base de données.
* Supprimez tous les répertoires et fichiers dans votre répertoire racine Joomla.

## Démarrage rapide Akeeba

Si vous avez utilisé Akeeba Backup, utilisez Akeeba Quickstart pour restaurer votre sauvegarde.
* Consultez le [Tutoriel Vidéo](http://akee.ba/abrestoreanywhere "").
* Téléchargez gratuitement Akeeba Quickstart (PDF 94Kb).
* Vérifiez que le site restauré fonctionne correctement !

Akeeba Quickstart restaure à la fois la base de données et les fichiers Joomla. D'autres méthodes restaurent la base de données et les fichiers Joomla séparément.

## Restaurer la base de données

Si vous disposez d'une sauvegarde de base de données, il est préférable d'utiliser des outils système pour la restaurer. *phpMyAdmin* peut installer des bases de données de taille modérée, mais il pourrait manquer de temps ou de mémoire pour les grandes bases de données.

Si vous utilisez cPanel sur un service d'hébergement, vous pouvez importer une base de données à partir de la page *Sauvegarde / Restauration*. Cela n'est pas décrit ici.

Si vous avez accès à la ligne de commande, soit sur un service d'hébergement soit sur votre ordinateur portable ou de bureau local, vous pouvez utiliser la ligne de commande `mysql` pour effectuer l'importation. Téléchargez l'archive de la base de données vers un emplacement temporaire en dehors de votre arborescence web et développez-la de sorte que vous ayez un fichier se terminant par `.sql`. Ensuite, utilisez la commande suivante :
```
mysql -u dbusername -p -D dbname < db_dump_file.sql
```
Remplacez `dbusername`, `dbname` et `db_dump_file.sql` par les valeurs réelles pour votre site. Il est possible que vous soyez invité à entrer un mot de passe pour le nom d'utilisateur de la base de données. Cela peut prendre un certain temps, mais cela devrait se terminer correctement.

## Restaurer les fichiers

Cela consiste simplement à décompresser le fichier de votre dernière sauvegarde. Sauf que ce n'est parfois pas si simple. Selon votre système d'exploitation et la méthode choisie, les répertoires et fichiers archivés peuvent tous apparaître dans le répertoire actuel ou dans un nouveau répertoire, ou il se peut qu'on vous demande de désigner un répertoire de destination. Jusqu'à ce que vous sachiez ce que fait votre système, il peut être préférable de placer l'archive dans un répertoire vide, de l'étendre là-bas puis de déplacer le répertoire contenant à l'endroit souhaité.

Certains utilisateurs préfèrent utiliser SFTP pour télécharger des fichiers vers un service d'hébergement à partir des fichiers d'archive extraits localement. Il y a des milliers de fichiers, donc cela prend assez de temps.

À la racine de votre site, il y a un fichier nommé `configuration.php`. Il contient le nom de la base de données et les identifiants d'accès. Assurez-vous qu'ils sont corrects pour votre site restauré. Les permissions d'accès du fichier sont définies sur 444. Il faut les modifier à 644 afin que vous puissiez enregistrer toute modification nécessaire.

Tout devrait bien se passer et votre site restauré devrait fonctionner et être dans l'état où il était lorsque la sauvegarde a été effectuée.

## Copier un site

Il existe plusieurs bonnes raisons de copier un site Web entier d'un serveur à un autre. Par exemple, les experts du forum recommandent souvent que les utilisateurs créent une version locale d'un site sur un ordinateur portable ou de bureau à des fins de test, comme essayer de nouvelles extensions ou de nouveaux designs. Parfois, une personne décide de changer de service d'hébergement pour des raisons de coût ou de performance.

Quelle que soit la raison, le processus est relativement simple : faites une sauvegarde sur le site d'origine et restaurez-la sur le site de destination. Il y a certains points à surveiller :

* Assurez-vous que l'hôte de destination répond aux exigences techniques minimales de Joomla. Cela signifie généralement les versions du serveur, de PHP et de la base de données.
* Après l'installation, vous pourriez constater que certains modules essentiels n'ont pas été activés. La plupart des services d'hébergement corrigent de tels problèmes sur demande.

*Traduit par openai.com*


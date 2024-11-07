<!-- Filename: J4.x:CLI_Database_Exporter_Importer / Display title: Exportation et Importation de Base de Données via CLI  -->

## Introduction

Avant de mettre à jour Joomla! ou d'installer une extension tierce, il est fortement recommandé de sauvegarder votre site. L'interface en ligne de commande de Joomla! (CLI) fournit des commandes pour exporter (sauvegarder) et importer (restaurer) votre base de données Joomla!. Notez qu'elle ne sauvegarde pas votre système de fichiers, ce qui doit être fait séparément.

## Exigences

Pour utiliser ces commandes, vous avez besoin d'un accès terminal à l'hôte sur lequel le site est installé. Cela peut poser un problème sur un hébergement mutualisé ! Vous avez également besoin de connaissances de base des commandes du shell Linux telles que ls et cd. Si tout cela vous est inconnu, vous devriez probablement utiliser Akeeba Backup, l'extension de sauvegarde et de restauration la plus populaire et gratuite pour une utilisation basique.

## Emplacement de Stockage Temporaire de Sauvegarde

Soyez prudent lors du choix d'un emplacement de stockage pour une sauvegarde. Il devrait se trouver dans votre espace de fichiers personnel mais en dehors de votre arborescence web. L'objectif est de créer un fichier de sauvegarde que vous pourrez télécharger sur votre ordinateur local ou un autre endroit sûr, après quoi vous pourrez supprimer le fichier de sauvegarde pour libérer de l'espace. Veillez également à ne pas utiliser le dossier /tmp du système qui peut être consulté par n'importe quel utilisateur. Le meilleur emplacement est votre dossier tmp personnel. La disposition de l'arborescence des dossiers :
```
|-/home/username/tmp - votre dossier tmp personnel
|-/home/username/public_html - votre dossier racine Joomla
```

## Instructions

Connectez-vous à votre hôte et accédez au dossier racine de votre site.
```
cd /home/username/public_html
```

- Listez toutes les commandes CLI disponibles :
```sh
  php cli/joomla.php list
```
- Exportez la base de données vers le dossier tmp du compte :
```sh
  php cli/joomla.php database:export --folder /home/username/tmp/mydbname
```
- Importez la base de données depuis le dossier :
```sh
php cli/joomla.php database:import --folder /home/username/tmp/mydbname
```

Vous pouvez également :

- Exporter la base de données en tant que fichier .zip :
```sh
php cli/joomla.php database:export --zip --folder /home/username/tmp/mydbname
```
- Exporter une table :
```sh
php cli/joomla.php database:export --table xxxxx_action_log_config --folder /home/username/tmp/mydbname
```
- Exporter une table en tant que fichier .zip :
```sh
php cli/joomla.php database:export --table xxxxx_action_log_config --zip --folder /home/username/tmp/mydbname
```
- Importer une table :
```sh
php cli/joomla.php database:import --table xxxxx_action_log_config --folder /home/username/tmp/mydbname
```
- Si vous avez besoin d'aide :
```sh
php cli/joomla.php database:export --help
php cli/joomla.php database:import --help
```

## Sauvegarde

Pour effectuer une sauvegarde complète des dossiers, fichiers et de la base de données, exécutez ces commandes :

1. Archivez votre répertoire racine Joomla :
```sh
tar --exclude='/home/nom_utilisateur/public_html/tmp' -zcvf /home/nom_utilisateur/tmp/joomla_bak.tgz /home/nom_utilisateur/public_html > /home/nom_utilisateur/tmp/joomla_bak.log
```
2. Exportez toute la base de données Joomla, depuis le dossier racine de Joomla :
```sh
php cli/joomla.php database:export --folder /home/nom_utilisateur/tmp/db_bak
```

## Restaurer

Et pour le restaurer, assurez-vous d'abord que la base de données et l'utilisateur de la base de données existent. Ensuite, exécutez ces commandes :

1. Extraire l'archive :
```sh
tar -xvf /home/username/tmp/joomla_bak.tgz --directory /home/username/public_html
```
2. Assurez-vous d'être à la racine de votre site :
```sh
cd /home/username/public_html
```
2. Importer la base de données Joomla :
```sh
php cli/joomla.php database:import --folder /home/username/tmp/db_bak
```

## Notes

Dans les options de la commande tar -zcvf et -xvf, le v signifie verbeux - une liste de
fichiers traités défile rapidement sur l'écran du terminal. Omettez le v pour
ne pas voir la liste,  
*Traduit par openai.com*


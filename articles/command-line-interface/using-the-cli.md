<!-- Filename: J4.x:Using_the_CLI / Display title: Utilisation de l'interface en ligne de commande   -->

## L'interface en ligne de commande (CLI)

Si vous avez accès au terminal du serveur qui héberge votre site web, vous pouvez utiliser le CLI de Joomla pour effectuer des tâches routinières sans avoir besoin d'utiliser les identifiants de connexion utilisateur de Joomla. Même sans accès au terminal, comme c'est le cas sur certains comptes d'hébergement partagé, vous pouvez exécuter des commandes CLI en utilisant des tâches cron. Les commandes CLI sont souvent plus rapides ou plus pratiques que leurs équivalents exécutés via l'interface d'administration de Joomla (ou cPanel). La sauvegarde du site et la mise en ligne/hors ligne du site sont des exemples où vous pourriez préférer utiliser le CLI.

Le noyau de Joomla dispose d'une trentaine de commandes utiles et vous pouvez en ajouter davantage avec des extensions supplémentaires. Par exemple, vous pourriez récupérer des données externes comme des données de géolocalisation ou des taux de change pour un composant personnalisé.

## Utilisation de la CLI

La CLI est utilisée en invoquant l'exécutable PHP en ligne de commande. Cela est souvent différent de celui utilisé par un serveur web tel qu'Apache. Si vous utilisez une tâche cron, vous devrez peut-être fournir le chemin complet vers l'exécutable PHP, comme ceci :

    /usr/local/bin/php /home/nomutilisateur/public_html/[sous-dossier facultatif]/cli/joomla.php

Sinon, lors de l'utilisation de la ligne de commande terminal, changez de répertoire vers le répertoire cli de Joomla et commencez à exécuter la commande sans paramètres :

    cd /home/nomutilisateur/public_html/[sous-dossier facultatif]/cli
    php joomla.php

![Liste des commandes](../../../en/images/command-line-interface/cli-command-list.png)

Et essayez quelques commandes d'aide pour vous familiariser avec ce à quoi vous attendre :

    php joomla.php help
    php joomla.php list
    php joomla.php help cache:clean
    php joomla.php help config:get

Chacune des descriptions et des chaînes d'utilisation d'Aide sont codées en dur dans les fichiers de la bibliothèque Console ou dans les plugins tiers.

Essayez quelques commandes d'action simples :

    php joomla.php config:get debug
    php joomla.php cache:clean
    php joomla.php site:down
    php joomla.php site:up

## Options

Si vous exécutez des commandes depuis un cron, vous ne souhaitez peut-être pas voir de sortie :

    php joomla.php -q cache:clean

Notez que les options peuvent utiliser un espace ou le signe =, mais les variables doivent utiliser le signe = :

    php joomla.php session:gc --application administrator
    php joomla.php session:gc --application=administrator

    php joomla.php config:set debug=true

## Commandes

Une brève explication de chaque commande principale.

### Cache

Effacer les entrées expirées du cache système :

    php joomla.php cache:clean --help
    php joomla.php cache:clean

![Sortie de cache clean](../../../en/images/command-line-interface/cli-cache-clean.png)

    php joomla.php cache:clean expired

![Sortie de cache clean expired](../../../en/images/command-line-interface/cli-cache-clean-expired.png)

### Config

Obtenir ou définir une variable de configuration, l'une des variables dans
configuration.php ou un groupe de variables. Les groupes valides sont db, session,
mail,

    php joomla.php config:get debug --help
    php joomla.php config:get debug

![Sortie de config get debug](../../../en/images/command-line-interface/cli-get-debug.png)

    php joomla.php config:set debug=true

![Sortie de config set debug](../../../en/images/command-line-interface/cli-set-debug.png)

    php joomla.php config:get --group session

![Sortie de config get group session](../../../en/images/command-line-interface/cli-config-get-group-session.png)

### Core

Vérifier les mises à jour ou mettre à jour Joomla.

    php joomla.php core:check-updates --help
    php joomla.php core:check-updates

![Sortie de core check updates](../../../en/images/command-line-interface/cli-check-updates.png)

    php joomla.php core:update --help
    php joomla.php core:update

![Sortie de core update](../../../en/images/command-line-interface/cli-core-update.png)

### Database

Exporter ou importer la base de données. Vous pouvez exporter ou importer toutes les tables ou une
table sélectionnée. N'utilisez pas cette fonctionnalité pour importer toutes les tables d'un
site multilingue. Il y a un problème qui pourrait empêcher la recherche intelligente
de fonctionner correctement.

    php joomla.php database:export --help
    php joomla.php database:export --table f4rc2_banners --folder /home/username/tmp/mydb (une table)
    php joomla.php database:export --folder /home/username/tmp/mydb (toutes les tables)

    php joomla.php database:import --help
    php joomla.php database:import --table /home/username/tmp/mydb/f4rc2_banners (une table)
    [ERREUR] Le fichier /home/username/tmp/mydb/f4rc2_banners.xml n'existe pas.
    php joomla.php database:import --folder /home/username/tmp/mydb (toutes les tables dans ce dossier)

### Extension

Lister, découvrir, installer ou supprimer des extensions.

    php joomla.php extension:list --help
    php joomla.php extension:list
    php joomla.php extension:list --type component
    php joomla.php extension:list --type file
    php joomla.php extension:list --type language
    php joomla.php extension:list --type library
    php joomla.php extension:list --type module
    php joomla.php extension:list --type package
    php joomla.php extension:list --type plugin
    php joomla.php extension:list --type template

    php joomla.php extension:discover --help
    php joomla.php extension:discover
    php joomla.php extension:discover:list
    php joomla.php extension:discover:install --eid=

    php joomla.php extension:install --help
    php joomla.php extension:install --path=
    php joomla.php extension:install --url=

    php joomla.php extension:remove --help
    php joomla.php extension:remove

### Finder

Purge et reconstruit l'index (les filtres de recherche sont préservés).

    php joomla.php finder:index --help
    php joomla.php finder:index
    php joomla.php finder:index purge

![Sortie de finder index purge](../../../en/images/command-line-interface/cli-finder-index-purge.png)

### Scheduler

Lister, changer l'état ou exécuter des tâches planifiées.

    php joomla.php scheduler:list --help
    php joomla.php scheduler:list

    php joomla.php scheduler:state --help
    php joomla.php scheduler:state (invite interactive pour l'identifiant de la tâche)

    php joomla.php scheduler:run --help
    php joomla.php scheduler:run --id ID
    php joomla.php scheduler:run --all

### Session

Effectuer la collecte des ordures de session.

    php joomla.php session:gc --help
    php joomla.php session:gc
    php joomla.php session:gc --application administrator

    php joomla.php session:metadata:gc --help
    php joomla.php session:metadata:gc

### Site

Mettre le site hors ligne ou en ligne.

    php joomla.php site:down --help
    php joomla.php site:down

    php joomla.php site:up --help
    php joomla.php site:up

### Update

Vérifie les mises à jour d'extension en attente. Supprime les anciens fichiers qui devraient
avoir été supprimés lors d'une mise à jour de Joomla

    php joomla.php update:extensions:check --help
    php joomla.php update:extensions:check

    php joomla.php update:joomla:remove-old-files --help
    php joomla.php update:joomla:remove-old-files

![Sortie de update joomla remove old files](../../../en/images/command-line-interface/cli-update-remove-old-files.png)

### User

Lister et gérer les utilisateurs.

    php joomla.php user:list --help
    php joomla.php user:list

    php joomla.php user:add --help
    php joomla.php user:add --username cinderella --name Cinderella --email cinders@localhost --usergroup Manager (invite pour le mot de passe)
    php joomla.php user:add (invite pour les données)

![Sortie de user add avec invites](../../../en/images/command-line-interface/cli-add-user.png)

    php joomla.php user:addtogroup --help
    php joomla.php user:addtogroup (invite pour les données)
    php joomla.php user:addtogroup --username=cinderella --group=Manager

    php joomla.php user:removefromgroup --help
    php joomla.php user:removefromgroup (invite pour les données)
    php joomla.php user:removefromgroup --username=cinderella --group=Manager

    php joomla.php user:reset-password --help
    php joomla.php user:reset-password (invite pour les données)
    php joomla.php user:reset-password --username=cinderella (invite pour le mot de passe)

    php joomla.php user:delete --help
    php joomla.php user:delete (invite pour le nom d'utilisateur)
    php joomla.php user:delete --username=cinderella (invite pour confirmation - y pour confirmer)

*Traduit par openai.com*


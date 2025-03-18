<!-- Filename: How_do_you_block_directory_scans_using_htaccess%3F / Display title: Interdire le Listing des Répertoires  -->

## Contexte

Par défaut, sur un serveur web Apache, un répertoire qui ne contient pas de fichier index de configuration défini (index.html ou index.php) affichera une liste de tous les fichiers et sous-répertoires dans le répertoire. Cela peut être utile sur un serveur de test personnel, mais représente un risque de sécurité majeur sur un serveur de production en direct.

Dans le passé, il était courant d'inclure un fichier index.html vide dans tous les répertoires Joomla pour éviter que ce problème n'apparaisse sur des serveurs mal configurés. Ce n'est plus le cas. Une configuration correcte du serveur est attendue, soit dans les fichiers de configuration du serveur, soit dans les fichiers .htaccess individuels. La première option est préférée car elle s'applique à tous les sites web sur le serveur.

Cependant, les sites dans un environnement d'hébergement partagé peuvent s'attendre à ce que chaque site modifie la configuration du serveur en utilisant des fichiers .htaccess. Le serveur doit être configuré avec "AllowOverride Options" ou "AllowOverride All" pour permettre les substitutions dans .htaccess.

## Utilisation de .htaccess

Le fichier htaccess.txt fourni avec Joomla peut être utilisé sur les serveurs Apache en le renommant ou en le copiant sous le nom .htaccess. Il contient de nombreux réglages pour contrer les attaques de hackers sur les sites Joomla. Parmi d'autres, vous verrez les réglages suivants pour empêcher les listings de répertoires :

```
Options -Indexes

## Pas de listes de répertoires
<IfModule mod_autoindex.c>
    IndexIgnore *
</IfModule>
```

## Tester votre site

Une manière de tester votre site est d'entrer l'URL de votre dossier d'images dans la barre d'URL du navigateur : `https://votredomaine.com/images/`. Comme le dossier d'images ne contient normalement pas de fichier index.html ou index.php, vous devriez voir une page complètement vide. Si vous voyez une liste de tous les fichiers et dossiers, alors vous ne prévenez pas les explorations de répertoires pour n'importe quelle partie de votre site. Corrigez cela !

*Traduit par openai.com*

<!-- Filename: Verifying_permissions / Display title: Permissions de fichier : Linux -->

## Introduction

Les informations suivantes concernent les serveurs basés sur Linux. Si votre serveur Web est un serveur basé sur Microsoft Windows (IIS), vous devriez consulter [Permissions : Windows](jdocmanual?article=user/test-installations/permissions-windows).

En fonction de la configuration de sécurité de votre serveur Web, les permissions par défaut recommandées sont :

- 755 pour les répertoires
- 644 pour les fichiers
- 444 pour le fichier `configuration.php` (lorsqu'une modification de la Configuration Globale est enregistrée, Joomla change d'abord la permission à 644, enregistre la modification, puis rétablit la permission à 444)

<div class="alert alert-warning">
Attention !

N'utilisez jamais 777 à moins de savoir exactement ce que vous faites ! N'utilisez pas d'extensions qui nécessitent des permissions 777 !
</div>

## Comment Localiser les Permissions

Il existe différentes méthodes pour afficher et modifier les autorisations des fichiers ou dossiers d'un site web. Le navigateur de fichiers du panneau de contrôle de l'hébergeur ou un programme commun de [Protocole de Transfert de Fichier (FTP)](https://fr.wikipedia.org/wiki/File_Transfer_Protocol) devrait chacun fournir une méthode pour voir et changer les autorisations des fichiers et dossiers. La ligne de commande est une bonne option pour ceux qui ont accès au terminal et sont familiers avec les commandes système.

Selon ce que vous utilisez, vous devriez voir quelque chose comme cette image d'une partie du système de fichiers racine de Joomla tel qu'observé dans cPanel :

![vérification des permissions dans cpanel](../../../en/images/test-installations/verifying-permissions-cpanel.png)

Les permissions sont à l'extrême droite et sont précédées d'un zéro pour indiquer qu'il s'agit de chiffres octaux. Il devrait y avoir un formulaire pour changer les permissions d'un ou plusieurs éléments sélectionnés :

![changement des permissions dans cpanel](../../../en/images/test-installations/verifying-permissions-cpanel-change.png)

Dans une fenêtre de terminal, les autorisations des fichiers et des dossiers sont affichées sous forme de groupes de lettres plutôt que de chiffres (le `d` en tête indique que l'élément est un répertoire) :

```sh
drwxr-xr-x   20 ceford  staff     640 14 Oct 22:23 components
-r--r--r--    1 ceford  staff    3485 27 Oct 06:56 configuration.php
drwxr-xr-x    2 ceford  staff      64 20 Oct 14:21 files
-rw-r--r--    1 ceford  staff    6899 30 Sep 09:27 htaccess.txt
drwxr-xr-x   15 ceford  staff     480 24 Oct 12:19 images
```

## Numéros de Permission

Dans un affichage de permissions sous la forme 777, chaque chiffre octal correspond à trois lettres pour trois groupes d'utilisateurs différents :

- Premier chiffre = propriétaire (le propriétaire de l'élément - `ceford` dans la liste de la ligne de commande ci-dessus)
- Deuxième chiffre = groupe (le groupe autorisé à accéder - `staff` dans la liste ci-dessus)
- Troisième chiffre = autres (tout le monde sur cet ordinateur)

## Signification des chiffres

Chaque chiffre octal est la somme des permissions accordées :
```sh
     r = Lecture   = 4
     w = Écriture  = 2
     x = Exécution = 1
```
Additionnez les chiffres pour chaque permission requise pour un utilisateur, un groupe ou autres :

| "Octal" \#  | (l)ecture | (é)criture | e(x)écution | Utilisateur ou Groupe ou Autres |
|-------------|-----------|------------|-------------|---------------------------------|
| 0           | non       | non        | non         | `---` 0+0+0 = 0                 |
| 1           | non       | non        | oui         | `--x` 0+0+1 = 1                 |
| 2           | non       | oui        | non         | `-w-` 0+2+0 = 2                 |
| 3           | non       | oui        | oui         | `-wx` 0+2+1 = 3                 |
| 4           | oui       | non        | non         | `r--` 4+0+0 = 4                 |
| 5           | oui       | non        | oui         | `r-x` 4+0+1 = 5                 |
| 6           | oui       | oui        | non         | `rw-` 4+2+0 = 6                 |
| 7           | oui       | oui        | oui         | `rwx` 4+2+1 = 7                 |


## Exemples

- 755 est rwx (propriétaire), r-x (groupe) et r-x (autres) ou, en d'autres termes, tout le monde peut lire et exécuter (exécuter) mais seul le propriétaire (vous) peut apporter des modifications au fichier. Cela ressemblerait à ceci lorsqu'il est entièrement assemblé : `-rwxr-xr-x`. C'est le paramètre normal pour les dossiers.
- 644 est rw-, r--, r-- ou TOUT LE MONDE peut lire le fichier mais seul le propriétaire peut écrire dans le fichier ou `-rw-r--r--`. C'est le paramètre normal pour les fichiers.
- 777 ou `-rwxrwxrwx` signifie que TOUT LE MONDE peut lire, écrire et exécuter n'importe quel fichier
  <div class="alert alert-warning">
  C'est quelque chose que vous ne devez **JAMAIS** autoriser sur votre serveur/site web à moins que vous ne soyez absolument sûr de ce que vous faites.
  </div>

Les autorisations sont utilisées pour les répertoires ainsi que pour les fichiers, c'est pourquoi vous pourriez voir ceci `drwxr-xr-x` où le `d` est pour le répertoire.

Pour une explication complète, lisez l'article de Wikipédia sur les 
[Permissions de système de fichiers](https://en.wikipedia.org/wiki/Filesystem_permissions)

*Traduit par openai.com*


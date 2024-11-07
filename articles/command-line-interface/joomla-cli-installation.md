<!-- Filename: J4.x:Joomla_CLI_Installation / Display title: Installation de Joomla via CLI  -->

## Introduction

Le CMS Joomla est généralement installé via une interface de navigateur web. Cependant, les utilisateurs expérimentés peuvent souhaiter installer Joomla en utilisant des commandes dans une interface terminal. Cela permet le déploiement rapide de plusieurs instances Joomla.

## Configuration Système

Joomla nécessite PHP, une base de données et un serveur web. Pour obtenir les dernières informations sur les logiciels pris en charge ainsi que sur les versions minimales et recommandées, veuillez visiter la page des <a href="https://manual.joomla.org/docs/next/get-started/technical-requirements/" rel="noreferrer noopener">Exigences Techniques</a>.

L'installation peut être effectuée de deux manières différentes :

1. Installation manuelle
2. Installation automatique pilotée par script

## Installation manuelle

L'installation manuelle offre un bon contrôle pendant le processus d'installation. Chaque étape est visible dans le terminal et peut être annulée avec `Ctrl+C` en cas d'entrée incorrecte.

### Étapes à réaliser

1. Téléchargez le fichier zip ou tar du package d'installation sur le serveur web.
2. Décompressez le fichier zip ou tar.
3. Renommez le dossier décompressé et déplacez-le à un emplacement approprié dans la racine des documents du serveur web.
4. Accédez au dossier contenant le code Joomla et exécutez la commande suivante :
   `php installation/joomla.php install`
5. Les paramètres requis pour l'installation vous seront demandés, comme dans l'exemple de transcript suivant :
```bash
php installation/joomla.php install

Installer Joomla
================

Vérification des exigences système...OK
Collecte de la configuration...

Entrez le nom de votre site Joomla :
> J51
Entrez le nom réel de votre Super Utilisateur :
> John Doe
Définissez le nom d'utilisateur pour votre compte Super Utilisateur :
> johndoe
Définissez le mot de passe pour votre compte Super Utilisateur :
>
Entrez l'adresse email du Super Utilisateur du site web :
> johndoe@example.com
Type de base de données. Pris en charge : mysql, mysqli, pgsql [mysqli] :
>
Hôte de la base de données [localhost] :
>
Nom d'utilisateur de la base de données :
> j4
Mot de passe de la base de données :
>
Nom de la base de données [joomla_db] :
> j51
Préfixe pour les tables de la base de données [u5dke_] :
>
Chiffrement pour la connexion à la base de données. Valeurs : 0=Aucun, 1=Unidirectionnel, 2=Bidirectionnel [0] :
>
Chemin relatif ou absolu vers le dossier public [] :
>
OK
Validation de la connexion DB...OK
Création et remplissage de la base de données...OK
Écriture de configuration.php et configuration supplémentaire ...OK
Suppression du dossier /installation...OK
[OK] Joomla a été installé
```

Une fois le script terminée avec succès, le nouveau site web peut être accédé via votre navigateur web.

### Notes

* Faites très attention à votre saisie. Il n’est pas possible de revenir en arrière dans le script. Si la saisie est incorrecte, le script doit être annulé.
* Le nom de votre site Joomla apparaît dans la barre de titre de l'Administrateur, donc gardez-le court et distinctif. Il peut être modifié plus tard.
* Le nom réel de votre Super Utilisateur peut être modifié plus tard.
* Le nom d'utilisateur de votre compte Super Utilisateur devrait éviter un nom similaire à *admin*. Cela peut être potentiellement peu sûr car il peut être facilement deviné par un pirate.
* Le mot de passe de l'Utilisateur doit contenir 12 caractères.
* Le type de base de données par défaut est *mysqli*. Les types de bases pris en charge sont MySQL (mysql) et PostgreSQL (pgsql) et les types compatibles comme MariaDB.
* L'hôte de la base de données est presque toujours `localhost`. Une adresse IP ou un nom d'hôte doivent être entrés ici uniquement si le serveur responsable de la base de données est installé sur un autre hôte. Cependant, l'utilisateur du terminal doit avoir des permissions d'écriture sur l'hôte sélectionné. Vous obtiendrez cette information de votre fournisseur d'accès à Internet (FAI).
* Le nom d'utilisateur de la base de données est généralement différent du nom du Super Utilisateur.
* Le mot de passe de la base de données pour la base Joomla est presque toujours différent du mot de passe du Super Utilisateur.
* Le nom de la base de données par défaut est `joomla_db`, mais d'autres noms sont souvent utilisés.
* Le Préfixe pour les tables de la base de données est défini par une sélection aléatoire de cinq caractères. La valeur est utilisée pour séparer les tables Joomla des autres tables contenues dans la base si elle est également utilisée par d'autres applications.
* Le paramètre de Chiffrement pour la connexion à la base de données est rarement utilisé. Sauf avis contraire de votre FAI, laissez cette valeur par défaut [0].

## Installation automatique pilotée par script

L'installation de Joomla est contrôlée par un fichier *joomla.php* situé dans le sous-dossier *installation* après avoir décompressé le fichier du package Joomla. Tout langage de programmation permettant d'appeler et d'exécuter des fichiers PHP vous permet de créer un script qui automatise les préparations nécessaires et l'installation réelle en utilisant des variables personnalisées. Une liste de paramètres peut être obtenue avec la commande suivante :
```bash
php installation/joomla.php help install
```
Voici un exemple de script shell nommé jinstall.sh, placé dans le dossier racine de Joomla, créé pour une installation simple de Joomla :
```
#!/bin/bash

php installation/joomla.php install \
--site-name=NOM-DU-SITE \
--admin-user=UTILISATEUR-ADMIN \
--admin-username=IDENTIFIANT-ADMIN \
--admin-password=MOT-DE-PASSE-ADMIN \
--admin-email=johndoe@example.com \
--db-type=mysqli \
--db-host=localhost \
--db-user=j51 \
--db-pass=Garbage1n0ut \
--db-name=j51 \
--db-prefix=xyz12_ \
--db-encryption=0 \
--public-folder=j51
```
Avec ses permissions définies à 700, il s'agit simplement d'appeler le script depuis la ligne de commande avec `./jinstall.sh` et Joomla est installé littéralement en un éclair. Le script aurait pu être modifié pour changer les valeurs de remplacement ou elles pourraient être changées plus tard après la connexion de l'administrateur.

Si vous utilisez cette approche, n'oubliez pas de supprimer votre script jinstall.sh ou de le déplacer hors de votre arbre web pour une utilisation ultérieure ailleurs. Le dossier d'installation est supprimé à la fin du processus d'installation. Ainsi, exécuter le script jinstall.sh une seconde fois ne fonctionnera pas.


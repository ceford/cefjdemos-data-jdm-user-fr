<!-- Filename: J4.x:Hosting_Setup / Display title: Hébergement cPanel -->

## Introduction

## Hébergement cPanel

Lorsque vous vous connectez à votre service d'hébergement cPanel, voici ce à quoi vous devez vous attendre :

![panneau de contrôle d'hébergement cPanel](../../../en/images/hosting/cpanel-hosting.png)

### Configuration de la base de données

Le panneau Bases de données est utilisé pour créer une base de données et un utilisateur de base de données pour Joomla.

Sélectionnez l'élément Bases de données MySQL et entrez un nom de base de données dans le formulaire. La première partie du formulaire est prédéfinie. Le reste est à votre discrétion. Il doit être court et peut-être pas évident - *jblog* par exemple.

Dans le même formulaire, descendez à la section *Ajouter un nouvel utilisateur*. Entrez un nom d'utilisateur. Cela peut être ce que vous voulez. Il sera utilisé dans votre fichier de configuration Joomla, donc ce n'est pas quelque chose dont vous avez besoin de vous souvenir. Utilisez le générateur de mot de passe pour créer un mot de passe inoubliable et copiez-le dans un éditeur de texte - vous en aurez besoin lors de l'installation de Joomla.

Dans le même formulaire, descendez à *Ajouter un utilisateur à la base de données*. Sélectionnez l'utilisateur que vous avez créé et la base de données que vous avez créée dans les listes déroulantes, puis cliquez sur le bouton Ajouter. Un formulaire pour Gérer les privilèges s'ouvre. Cochez la case *Tous les privilèges* puis cliquez sur le bouton *Apporter des modifications*.

C'est tout - vous avez maintenant une base de données prête pour une installation Joomla.

### Téléchargement des sources de Joomla

À un certain moment, vous aurez téléchargé le fichier zip du code source de Joomla sur votre ordinateur portable ou de bureau. Vous devez maintenant décider comment structurer votre site. La racine des documents pour votre site est le dossier *public_html*. Vous pourriez y mettre Joomla. Cependant, cela vous empêche d'utiliser une autre application sur le même site. Par exemple, vous pourriez avoir deux installations Joomla complètement séparées, une pour la production (visualisation publique) et une pour les tests (visualisation privée). Ainsi, vous pourriez créer un dossier dans *public_html*, nommé *j4* par exemple, et y télécharger Joomla. Vous pourriez avoir un autre dossier nommé *j4test* et y mettre une autre copie de Joomla. L'illustration ci-dessous montre une telle configuration avec deux sites Joomla.

![gestionnaire de fichiers d'hébergement cPanel](../../../en/images/hosting/cpanel-file-manager.png)

Lorsque vous avez décidé de votre structure, sélectionnez le dossier Joomla choisi dans le gestionnaire de fichiers et cliquez sur le bouton Télécharger. Dans le formulaire de téléchargement, sélectionnez le fichier zip source de Joomla sur votre ordinateur local pour le télécharger dans le dossier sélectionné. Après le téléchargement, retournez dans le gestionnaire de fichiers, sélectionnez le fichier *zip* et cliquez sur le bouton Extraire. Après extraction, vous pouvez sélectionner et supprimer le fichier *zip*.

Voilà ! Vous êtes prêt à installer Joomla.


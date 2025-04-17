<!-- Filename: jdocmanual?manual=user&heading=plugins&filename=about-plugins.md / Display title: À propos des plugins  -->

## Introduction

Les plugins sont des extensions de Joomla! qui font quelque chose *en coulisses* en réponse à un déclencheur. Il y a environ 160 plugins de base répartis en plus de 20 groupes. De nombreux autres sont fournis par des développeurs tiers. L'image suivante montre le début de la liste des plugins avec la longueur de la liste réglée sur 5 pour la commodité de la capture d'écran.

![Liste des plugins](../../../en/images/plugins/plugins-list.png)

## Types de Plugins

Dans le dossier des plugins de votre site, vous verrez les types. Par exemple, vous
verrez un dossier **content**, qui contient des plugins manipulant le contenu,
et un dossier **user**, qui contient des plugins concernant les utilisateurs. Vous pouvez filtrer
la liste par Type ou par Élément, tel que *contact*, qui peut inclure plusieurs
Types.

## Paramètres des plugins

Les plugins peuvent avoir peu ou beaucoup de paramètres. Par exemple, le plugin *Contenu - Masquage d'email* offre un choix de deux méthodes de masquage, tandis que le plugin *Éditeurs - TinyMCE* dispose d'une longue liste de paramètres optionnels. Tous les plugins ont des valeurs par défaut appropriées. Souvent, il suffit simplement d'*Activer* ou de *Désactiver* un plugin particulier selon les besoins.

## Exécution du Plugin

L'exécution du plugin est déclenchée par un *événement*. Par exemple, le code qui assemble un article pour l'affichage comporte des événements nommés `onContentAfterTitle`, `onContentBeforeDisplay` et `onContentAfterDisplay`. Ils sont utilisés pour positionner tous les champs définis par l'utilisateur aux emplacements sélectionnés.

## Plugins individuels

Très peu de plugins individuels sont documentés ici. Ils sont couverts dans la page d'Aide de chaque plugin.

*Traduit par openai.com*


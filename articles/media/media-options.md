<!-- Filename: J4.x:Media:_Options / Display title: Médias : Options -->

## Introduction

La page *Média : Options* est utilisée pour contrôler le téléchargement et le stockage des médias, à la fois des images et des fichiers. **Attention :** il y a des implications de sécurité associées à certains types de fichiers - une porte d'entrée pour un pirate.

Pour accéder au formulaire *Média : Options*, sélectionnez le bouton **Options** dans la barre d'outils sur la page Média. Les champs sont bien commentés et fournis avec des valeurs par défaut qui devraient convenir à presque tous les sites. Vous avez généralement besoin d'utiliser le formulaire d'options uniquement si vous souhaitez séparer les fichiers des images ou si vous avez un format de fichier inhabituel non inclus dans la liste par défaut.

## Capture d'écran

![Le formulaire d'options des médias](../../../en/images/media/media-options.png)

## Chemin vers les Fichiers et les Dossiers

Ce sont des éléments distincts dans le formulaire de configuration, mais ils pointent tous deux vers le dossier *images* dans une nouvelle installation de Joomla. Si vous souhaitez stocker des médias non-images séparément (par exemple, des PDFs, des Tableurs et des fichiers Texte), utilisez les étapes suivantes :

1. Créez un dossier nommé *files* à la racine de votre installation Joomla.
2. Activez le plugin *FileSystem - Local* et configurez-le, comme décrit dans l'article sur les [Emplacements de Fichiers Média](jdocmanual?article=user/media/media-file-locations).
3. Entrez le nom du dossier, *files*, dans le champ *Chemin vers le Dossier de Fichiers* du formulaire d'Options Média.

Dans le formulaire d'Options, entrez le nom du dossier dans le champ **Chemin vers le Dossier de Fichiers**. Assurez-vous de ne pas utiliser le nom d'un dossier principal existant de Joomla.

Une fois configuré, vous pourrez choisir entre les dossiers images et fichiers dans la partie Locale de la vue Média.

![La page des médias](../../../en/images/media/media-sample-data-cassiopeia.png)

## Types d'images ou de documents supplémentaires

Il se peut que vous ne puissiez pas télécharger une image ou un document. Dans ce cas, vérifiez que son extension fait partie des *Extensions autorisées*, que son extension fait partie des *Types d'extensions légales* pour le média, et qu'il fait partie des *Types MIME légaux* (vous devrez peut-être vérifier cela). Les trois doivent être corrects, sinon le téléchargement sera refusé.
*Traduit par openai.com*


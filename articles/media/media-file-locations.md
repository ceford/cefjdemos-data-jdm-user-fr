<!-- Filename: J6.x:Media_File_Locations / Display title: Emplacements des fichiers multimédias -->

## Introduction

Par défaut, Joomla stocke les images des utilisateurs et les fichiers de documents dans le dossier */images* de l'installation de Joomla. Tous les liens vers ces médias ne sont pas traités directement par Joomla. Le serveur web les envoie lorsque le navigateur les demande.

Si vous avez beaucoup de documents, vous voudrez peut-être les conserver dans un dossier séparé, de préférence un dossier */files* également à la racine du site Joomla.

Pour configurer un emplacement pour les fichiers séparé des images, créez d'abord un nouveau dossier à la racine de votre installation, par exemple **files**. Rappelez-vous que cela fera partie d'un lien URL, donc utilisez des minuscules, pas d'espaces ni de signes de ponctuation.

### Plug-in FileSystem - Local

Trouvez le plug-in *FileSystem - Local* dans la liste des plug-ins et ouvrez-le. Ajoutez votre dossier *files* nouvellement créé à la liste des emplacements où vous pouvez conserver des médias. Cliquez simplement sur le bouton + et sélectionnez **files** dans la liste des dossiers disponibles.

![Plug-in Système de Fichiers](../../../en/images/plugins/plugin-group-file-system-local.png)

L'option **Créer des Miniatures** réglée sur **Oui** entraîne la création de petites images avec une hauteur ou une largeur maximale de 200 pixels dans media/cache/com_media/thumbs, avec la même structure de dossiers que le dossier de médias. Cela devrait grandement augmenter la vitesse d'affichage d'un dossier contenant de nombreuses images. Ce n'est pas nécessaire pour les fichiers car ils sont représentés par des icônes.

Assurez-vous que le plug-in est activé. **Enregistrer & Fermer**.

*Traduit par openai.com*


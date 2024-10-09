<!-- Filename: Adding_an_image_to_an_article / Display title: Ajouter une image à un article -->

## Introduction

How best to add images to an article depends on which version of Joomla
and which editor are in use. This article has illustrations for Joomla
4, with notes on differences in Joomla 3, and TinyMCE the Joomla default
editor. To get started, open an article for editing:

- **Select** **Content **→** Articles** in the Administrator menu.
- **Select** the title of the article you wish to edit

After inserting the article text, place the cursor at the location where
the image should appear.

## Adding a local image

If the image is located in the images folder of your Joomla installation
you should insert the image using the **CMS Content **→** Media** button
In the TinyMCE edit toolbar (In Joomla 3: Select the Image button):

<img
src="https://docs.joomla.org/images/5/5e/Adding-an-image-to-an-article-cms-content-media.png"
decoding="async" data-file-width="1000" data-file-height="508"
width="1000" height="508" alt="Adding an image" />

In the popup window, navigate to the image you want to use and click to
select it. On selection a form will appear prompting for additional
data. In Joomla 4 the form is to the left. In joomla 3 the form is at
the bottom (scroll down):

<img
src="https://docs.joomla.org/images/d/d4/Adding-an-image-to-an-article-selected-image.png"
decoding="async" data-file-width="1000" data-file-height="508"
width="1000" height="508" alt="Selecting an image" />

1.  Définissez les propriétés de l'image :
1.  - **Description** : l'attribut **alt** de l'image, une
      caractéristique importante pour l'accessibilité et la conformité
      avec les standards du web.

- **Image Class**: If an image is used without a caption some custom
  classes may be applied here. For example, in Joomla 4, **float-end
  ms-2 mb-1** will align the image to the right and float text around it
  with margins to the left and below to prevent text touching the image.
  In Joomla 3 the equivalent style is **pull-right**.
- **Figure Class**: If a caption is set then an alignment class, if any,
  should be applied to the Figure. It is a html tag that encloses the
  img tag. Note that in Cassiopeia margins are applied by the template
  style sheet.

1.  - **Légende** : permet de définir la légende qui s'affiche en tant
      que titre sous l'image.

**In Joomla 3**

1.  - **Alignement** : définit l'alignement de l'image. Par défaut,
      l'alignement est paramétré sur **Non défini**.
1.  - **Classe de légende** : permet d'appliquer la classe définie à
      l'élément *figcaption*.
1.  Cliquez sur le bouton **Insérer** pour insérer l'image. L'écran
    d'insertion de l'image va se fermer et l'image sera affichée dans
    l'éditeur. Sinon, vous pouvez cliquer sur le bouton **Annuler** pour
    quitter l'écran d'insertion de l'image.

**Tip:** select the Toggle Editor button to see the applied Image and
Caption styles.

### Using Drag and Drop for Local images

In both Joomla 4 and Joomla 3 you can drag an image from the desktop or
a file browser directly into the article text and the image will be
uploaded to the media folder and placed in the article. The only snag is
that all such uploaded images will be placed in the same media folder.
The location of the Images Directory used for upload and whether this
feature is enabled (On by default) are set in the TinyMCE configuration
Options.

## Adding a remote image

If the image you wish to use is not in the images folder of your Joomla
installation a slightly different procedure is needed.

- **Select** **Insert **→** Image** from the TinyMCE toolbar to open a
  dialog box. In Jooml 3, use the Image icon and the same dialog as used
  for local images.
- **Insert** the image url in the Source field.
- **Fill out** the other fields as required.
- **Advanced** provides some formatting options applied as in-line
  styles. Experiment with 1rem, 2, groove. (This feature is incomplete)

<img
src="https://docs.joomla.org/images/3/39/Adding-an-image-to-an-article-insert-edit-image.png"
class="thumbborder" decoding="async" data-file-width="480"
data-file-height="477" width="480" height="477"
alt="Data for a remote image" />

### Using Drag and Drop for Remote images

You can drag and drop an image from a remote web site directly into your
article text. But be aware that this may also copy the image container
html with class statements not valid for your site.

## Chargement d'images avec l'écran d'insertion d'images

Vous pouvez également charger de nouvelles images à l'aide de la section
de chargement situé en bas de l'écran d'insertion d'images.

- First open the Media browser and navigate to the folder where you wish
  to store new images for the current article.

1.  Cliquez sur le bouton *Parcourir* pour ouvrir un navigateur de
    fichiers.
1.  Sélectionnez les images que vous souhaitez charger. Cliquez sur
    Ouvrir dans le navigateur de fichiers pour confirmer la sélection.
    Remarque : le style et la mise en page dépend du navigateur et du
    système d'exploitation que vous utilisez.
1.  Le(s) fichier(s) sélectionné(s) s'affichent en bas de l'écran
    d'insertion d'images. Cliquez sur *Démarrer l'envoi* pour lancer le
    chargement des fichiers.
1.  - Lorsque le chargement est terminé, un encart vert s'affiche en
      haut de l'écran.
1.  Vous pouvez maintenant sélectionner et insérer l'image chargée comme
    précédemment.

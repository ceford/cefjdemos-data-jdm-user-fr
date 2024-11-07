<!-- Filename: J3.x:Adding_custom_fields/Editor_Field / Display title: Champ de l'éditeur -->

## Objet

Le champ Éditeur permet la saisie de données WYSIWYG pour certains contenus liés à l'article en plus du contenu principal.


## Création de Champ

Les options spéciales dans ce champ sont

- **Boutons** Afficher ou masquer la liste déroulante du contenu CMS. Pour le texte supplémentaire de l'article, il peut ne pas être approprié d'afficher certains ou tous les boutons de la liste. La valeur par défaut du plugin est Masquer.
- **Masquer les Boutons** Si *Boutons* est défini sur *Oui* ou la valeur par défaut du plugin est *Afficher*, masquer les boutons sélectionnés dans la liste déroulante du contenu CMS.
- **Largeur et Hauteur** les valeurs incluent l'espace occupé par la barre d'outils de l'éditeur, il est donc préférable de les laisser initialement vides.
- **Largeur** La valeur de la largeur définit la largeur de l'éditeur WYSIWYG en % ou en pixels. La valeur par défaut est 100%.
- **Hauteur** La valeur pour la hauteur définit la hauteur (en pixels) de l'éditeur WYSIWYG. La valeur par défaut est 250px. La valeur peut être représentée comme une fraction de la hauteur de la fenêtre, par exemple 50vh.
- **Filtre** Permettre au système de sauvegarder certaines balises html ou des données brutes.

## Saisie de Données

Dans le formulaire de modification de l'article, le champ Éditeur supplémentaire est similaire au champ Éditeur de contenu principal.

![champ éditeur](../../../en/images/fields/fields-editor-entry.png "Champ Éditeur")


## Affichage des données

La capture d'écran du site suivante montre le champ affiché dans un article. L'option *Affichage automatique* est responsable de la position du champ, et votre modèle est responsable du design du champ.

Dans l'affichage de l'article, le texte saisi apparaît sous le titre, mais fait partie de la liste à puces pour cet élément de champ.

Recherchez l'élément **Notes de culture**.

![Affichage de tous les champs](../../../en/images/fields/fields-display.png "Affichage des champs")


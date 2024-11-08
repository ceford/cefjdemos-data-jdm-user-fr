<!-- Filename: J3.x:Adding_custom_fields/Editor_Field / Display title: Champ de l'Éditeur -->

## Objectif

Le champ Éditeur permet la saisie de données WYSIWYG pour certains contenus liés à des articles en plus du contenu principal.


## Création de champ

Les options spéciales dans ce champ sont

- **Boutons** Afficher ou masquer la liste déroulante du contenu du CMS. Pour le texte supplémentaire d'un article, il peut ne pas être approprié d'afficher certains ou tous les boutons dans la liste. La valeur par défaut du plugin est Masquer.
- **Masquer les boutons** Si *Boutons* est réglé sur *Oui* ou si la valeur par défaut du plugin est *Afficher*, masquer les boutons sélectionnés dans la liste déroulante du contenu du CMS.
- **Largeur et Hauteur** Les valeurs incluent l'espace occupé par la barre d'outils de l'éditeur, il est donc probablement préférable de les laisser vides initialement.
- **Largeur** La valeur pour la largeur définit la largeur de l'éditeur WYSIWYG en % ou en pixels. La valeur par défaut est 100%.
- **Hauteur** La valeur pour la hauteur définit la hauteur (en pixels) de l'éditeur WYSIWYG. La valeur par défaut est de 250px. La valeur peut être représentée comme une fraction de la hauteur de la fenêtre, par exemple 50vh.
- **Filtre** Permettre au système de sauvegarder certaines balises html ou des données brutes.

![Création de champ d'éditeur](../../../en/images/fields/fields-editor-edit.png)

**Remarque :** Dans cet exemple, l'inclusion du type de champ dans le titre est uniquement à des fins de démonstration. Ne l’incluez pas dans vos propres titres de champ.

## Saisie de Données

Dans le formulaire de modification d'article, le champ Éditeur supplémentaire est similaire au champ Éditeur de contenu principal.

![saisie de données dans le champ éditeur](../../../en/images/fields/fields-editor-data-entry.png)

## Affichage des Données

La capture d'écran du site suivante montre le champ affiché dans un article. L'option *Affichage automatique* est responsable de la position du champ et votre modèle est responsable du design du champ.

Dans l'affichage de l'article, le texte saisi apparaît sous le titre mais fait partie de la liste à puces pour cet élément de champ.

Cherchez l'élément **Notes de culture**.

![affichage du champ de l'éditeur sur le site](../../../en/images/fields/fields-editor-site.png)


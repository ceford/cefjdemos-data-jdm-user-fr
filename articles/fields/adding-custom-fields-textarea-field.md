<!-- Filename: J3.x:Adding_custom_fields/Textarea_Field / Display title: Champ de zone de texte -->

## Objectif

Le champ Textarea est une zone d'entrée pour du texte multiligne. Un simple textarea n'a pas d'éditeur WYSIWYG.

### Options

Les options spéciales dans ce champ sont :

- **Lignes** La hauteur de la zone de texte visible en lignes. Si omis, la hauteur est déterminée par le navigateur. La valeur ne limite pas le nombre de lignes qui peuvent être saisies. Les lignes sont actives dans le backend lors de la création d'un article ou d'un contact ou d'un composant tiers qui prend en charge les champs personnalisés. Cette option n’a aucun impact sur la taille du champ dans le frontend.
- **Colonnes** La largeur de la zone de texte visible en caractères. Si omis, la largeur est déterminée par le navigateur. La valeur ne limite pas le nombre de caractères qui peuvent être saisis. Les colonnes sont actives dans le backend lors de la création d'un article ou d'un contact ou d'un composant tiers qui prend en charge les champs personnalisés. Cette option n’a aucun impact sur la taille du champ dans le frontend.
- **Longueur maximale** Le nombre maximum de caractères qui peuvent être saisis.
- **Filtre** Permet au système de sauvegarder certaines balises HTML ou des données brutes.

![création de champ textarea](../../../en/images/fields/fields-textarea-edit.png)

**Remarque :** Dans cet exemple, l'inclusion du type de champ dans le titre est à des fins de démonstration uniquement. N'incluez pas cela dans vos propres titres de champ.

## Saisie de Données

Simple : saisissez le texte à afficher.

![zone de saisie de texte](../../../en/images/fields/fields-textarea-data-entry.png)


## Affichage des Données

La capture d'écran du site suivante montre le champ affiché dans un article. L'option *Affichage automatique* est responsable de la position du champ et votre modèle est responsable du design du champ.

![affichage du champ zone de texte sur le site](../../../en/images/fields/fields-textarea-site.png)

L'étiquette du champ commence un seul bloc de texte à moins que vous n'ayez entré des balises HTML telles que `<p>...</p>`.


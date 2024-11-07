<!-- Filename: J3.x:Adding_custom_fields/Textarea_Field / Display title: Champ de zone de texte -->
## Objectif

Le champ de texte est une zone destinée à l'entrée de texte multiligne. Un champ de texte simple n'a pas d'éditeur WYSIWYG.

### Options

Les options spéciales dans ce champ sont :

- **Lignes** La hauteur de la zone de texte visible en lignes. Si elle est omise, la hauteur est déterminée par le navigateur. La valeur ne limite pas le nombre de lignes qui peuvent être saisies. Les lignes sont actives dans le backend lors de la création d'un article, d'un contact ou d'un composant tiers qui prend en charge les champs personnalisés. Cette option n'a aucun impact sur la taille du champ dans le frontend.
- **Colonnes** La largeur de la zone de texte visible en caractères. Si elle est omise, la largeur est déterminée par le navigateur. La valeur ne limite pas le nombre de caractères qui peuvent être saisis. Les colonnes sont actives dans le backend lors de la création d'un article, d'un contact ou d'un composant tiers qui prend en charge les champs personnalisés. Cette option n'a aucun impact sur la taille du champ dans le frontend.
- **Longueur Maximum** Le nombre maximum de caractères qui peuvent être saisis.
- **Filtre** Permettre au système de conserver certaines balises HTML ou des données brutes.

## Saisie de Données

Simple : entrez le texte à afficher.


## Affichage des Données

La capture d'écran suivante du site montre le champ affiché dans un article. L'option *Affichage automatique* est responsable de la position du champ et votre modèle est responsable du design du champ.

Recherchez l'élément **Classification**.

![Affichage de tous les champs](../../../en/images/fields/fields-display.png "Affichage des champs")

L'étiquette du champ commence un seul bloc de texte, sauf si vous avez entré des balises HTML telles que `<p>...</p>`.


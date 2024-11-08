<!-- Filename: J3.x:Adding_custom_fields/List_Field / Display title: Champ de Liste -->

## Objectif

Le type de champ de formulaire de liste fournit une liste déroulante ou une boîte de liste d'entrées définies par l'utilisateur. Si le champ a une valeur enregistrée, celle-ci est sélectionnée lorsque la page est chargée pour la première fois. Sinon, la valeur par défaut (le cas échéant) est sélectionnée.

## Création de champ

Les options spéciales de ce champ sont :

- **Multiple** Permettre la sélection de plusieurs valeurs. Si réglé sur *Non*, un seul élément est affiché dans la liste. Si réglé sur *Oui*, trois éléments sont affichés. La liste défile pour permettre la sélection de un ou plusieurs éléments.
- **Valeurs de liste** Ajouter des éléments selon les besoins et utiliser l'icône de glissement pour changer leur ordre. Commencez la liste avec le texte réglé sur *- Sélectionner -* et la valeur vide. Cela offre une valeur par défaut vide, si bien que cette liste est absente de l'article.
- **Classe de champ** Régler sur *w-auto* pour que la liste soit juste assez large pour son ensemble d'étiquettes.

![Création de champ de liste](../../../en/images/fields/fields-list-edit.png)

**Remarque :** Dans cet exemple, l'inclusion du type de champ dans le titre est uniquement à des fins de démonstration. N'incluez pas ceci dans vos propres titres de champ.

## Saisie de données

Simple : sélectionnez simplement un élément dans la liste ou plusieurs éléments si *Multiple* est *Oui*.

![Saisie de données du champ de liste](../../../en/images/fields/fields-list-data-entry.png)

## Affichage des Données

La capture d'écran suivante du site montre le champ affiché dans un article. L'option *Affichage automatique* est responsable de la position du champ et votre modèle est responsable du design du champ.

La sortie est un seul élément ou une liste séparée par des virgules.

![affichage du champ de liste site](../../../en/images/fields/fields-list-site.png)

*Traduit par openai.com*  


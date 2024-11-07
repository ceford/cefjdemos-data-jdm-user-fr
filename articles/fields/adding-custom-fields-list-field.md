<!-- Filename: J3.x:Adding_custom_fields/List_Field / Display title: # Champ de Liste -->

## Objectif

Le type de champ de formulaire en liste fournit une liste déroulante ou une liste de choix avec des entrées définies sur mesure. Si le champ a une valeur enregistrée, celle-ci est sélectionnée lorsque la page est chargée pour la première fois. Sinon, la valeur par défaut (le cas échéant) est sélectionnée.

## Création de champ

Les options spéciales dans ce champ sont :

- **Multiple** Permet de sélectionner plusieurs valeurs. Si l'option est définie sur *Non*, un seul élément est affiché dans la liste. Si l'option est définie sur *Oui*, trois éléments sont affichés. La liste défile pour permettre la sélection d'un ou plusieurs éléments.
- **Valeurs de la liste** Ajoutez des éléments selon les besoins et utilisez l'icône de glisser pour changer leur ordre. Commencez la liste avec le Texte défini sur *- Sélectionner -* et la Valeur vide. Cela fournit un défaut vide, ce qui fait que cette liste est absente de l'Article.
- **Classe du champ** Définissez sur *w-auto* pour que la liste soit juste assez large pour ses étiquettes.

![Création de champ de liste](../../../en/images/fields/fields-list.png "Création de champ de liste")

## Saisie de données

Simple : il suffit de sélectionner un élément dans la liste ou plusieurs éléments si *Multiple* est *Oui*.

## Affichage des Données

La capture d'écran suivante du site montre le champ affiché dans un article. L'option *Affichage automatique* est responsable de la position du champ et votre modèle est responsable du design du champ.

Le résultat est un seul élément ou une liste séparée par des virgules.

Cherchez l'élément **Origine**.

![Affichage de tous les champs](../../../en/images/fields/fields-display.png "Affichage des champs")

*Traduit par openai.com*


<!-- Filename: J3.x:Adding_custom_fields/Calendar_Field / Display title: Champ de calendrier -->

## Objectif

Le champ Calendrier fournit une zone de texte pour la saisie d'une date. Une icône à côté de la zone de texte invoque un sélecteur de calendrier contextuel, qui peut être utilisé pour sélectionner une date à partir d'un calendrier graphique.

## Création de champ

Les paramètres communs des champs sont décrits dans un article séparé.

* **Titre** Vous pouvez avoir plusieurs champs de date dans un article, il est donc nécessaire de faire attention en définissant le titre pour éviter toute ambiguïté dans le résultat.
* **Libellé** C'est ce qui est affiché dans le résultat. Si laissé vide, il est défini à partir du contenu du champ Titre mais peut être modifié.
* **Afficher l'heure** Si cette option est réglée sur *Oui*, l'heure est ajoutée au champ de date, au sélecteur de date et à la date du résultat. **Attention** : Même si vous ne spécifiez pas l'heure dans la date par défaut, l'heure est affichée lorsque l'option *Afficher l'heure* est active.
* **Espace réservé** Peut être défini sur un format de date tel que *AAAA-MM-JJ* pour rappeler aux utilisateurs le format requis et/ou un rappel de la finalité de la date, comme *Date d'arrivée*.

## Saisie de données

L'utilisation du champ Calendrier est simple. Vous pouvez taper la date dans le format requis ou sélectionner une date à l'aide du sélecteur de date. Il est important de faire attention lorsque vous saisissez les dates. Une erreur dans la date est corrigée lors de l'enregistrement à une nouvelle date. Par exemple, une date de 2024-14-02 est corrigée en 2025-02-02.

La capture d'écran suivante montre une date d'acquisition :

![saisie de date d'acquisition](../../../en/images/fields/fields-date-entry.png "Date d'acquisition")

Les champs n'apparaissent dans un article que s'ils sont renseignés dans le formulaire de saisie de données de l'article. 


## Affichage des données

La capture d'écran du site suivante montre le champ affiché dans un article. L'option *Affichage automatique* est responsable de la position du champ et votre modèle est responsable du design du champ.

Recherchez l'élément **Date d'acquisition**.

![Affichage de tous les champs](../../../en/images/fields/fields-display.png "Affichage des champs")

Les formats de date sont localisés à l'aide de chaînes de langue.

*Traduit par openai.com*


<!-- Filename: J3.x:Adding_custom_fields/Calendar_Field / Display title: Champ de Calendrier -->

## Objectif

Le champ Calendrier fournit une zone de texte pour la saisie d'une date. Une icône à côté de la zone de texte invoque un sélecteur de calendrier contextuel, qui peut être utilisé pour sélectionner une date à partir d'un calendrier graphique.

## Création de champ

Les paramètres communs des champs sont décrits dans un article séparé.

* **Titre** Vous pouvez avoir plusieurs champs de date dans un article, il est donc nécessaire de faire attention à la définition du titre pour éviter toute ambiguïté dans le rendu.
* **Étiquette** C'est ce qui est affiché dans le rendu. Si laissé vide, il est défini à partir du contenu du champ Titre mais peut être modifié.
* **Afficher l'heure** Si cette option est définie sur *Oui*, l'heure est ajoutée au champ de date, au sélecteur de date et à la date affichée. **Attention** : Même si vous ne spécifiez pas l'heure dans la date par défaut, l'heure s'affiche lorsque l'option *Afficher l'heure* est active.
* **Espace réservé** Cela se trouve dans l'onglet Options. Il peut être défini sur un format de date tel que *AAAA-MM-JJ* pour rappeler aux utilisateurs le format requis et/ou un rappel de la finalité de la date, comme *Date d'arrivée*.

![création de champ de calendrier](../../../en/images/fields/fields-calendar-edit.png)

**Remarque :** Dans cet exemple, l'inclusion du type de champ dans le Titre est uniquement à des fins de démonstration. Omettez-le dans vos propres titres de champs. 


## Saisie de données

L'utilisation du champ Calendrier est simple. Vous pouvez entrer la date au format requis ou sélectionner une date à l'aide du sélecteur de date. Il faut faire attention en saisissant les dates. Une erreur dans la date est corrigée lors de l'enregistrement pour donner une nouvelle date. Par exemple, une date du 2024-14-02 est corrigée en 2025-02-02.

La capture d'écran suivante montre une date d'acquisition :

![saisie de données du champ calendrier](../../../en/images/fields/fields-calendar-data-entry.png)

Les champs n'apparaissent dans un article que s'ils sont remplis dans le formulaire de saisie de données de l'article.

## Affichage des Données

La capture d'écran suivante du Site montre le champ affiché dans un article. L'option *Affichage automatique* est responsable de la position du champ et votre modèle est responsable du design du champ.

![affichage du champ calendrier sur le site](../../../en/images/fields/fields-calendar-site.png)

Les formats de date sont localisés à l'aide de chaînes de langue.

*Traduit par openai.com*


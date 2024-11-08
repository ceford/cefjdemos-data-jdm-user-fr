<!-- Filename: J3.x:Adding_custom_fields/Url_Field / Display title: Champ URL -->

## Objectif

Le champ URL fournit un lien URL vers un autre document. Si vous préférez utiliser une balise d'ancrage comme `<a href="url">Texte explicatif</a>`, utilisez un champ de texte.


## Création de champ

Les options spéciales de ce champ sont :

- **Schémas** Les schémas autorisés sont HTTP, HTTPS, FTP, FTPS, MAILTO, URL et
FILE. Tous sont autorisés par défaut. Ceux qui sont sélectionnés dans la liste sont autorisés tandis que ceux qui ne sont pas sélectionnés sont interdits. Cela est évident lors de la saisie de données : lorsqu'un type non sélectionné est entré, par exemple http://, il y a un message d'erreur et le champ n'est pas enregistré.
- **Relatif** Utilisez cette option pour déterminer si les URL relatives sont
autorisées ou non.
- **Afficher l'URL** Si ce paramètre est défini sur *Non*, lors de l'affichage d'un article, l'URL est remplacée par les mots *Visiter le site*.

![création de champ url](../../../en/images/fields/fields-url-edit.png)

**Remarque :** Dans cet exemple, l'inclusion du type de champ dans le titre est uniquement à des fins de démonstration. Ne l'incluez pas dans vos propres titres de champs.

## Saisie de données

Simple : il suffit de saisir une URL de destination.

![saisie de données dans le champ url](../../../en/images/fields/fields-url-data-entry.png)


## Affichage des Données

La capture d'écran suivante du site montre le champ affiché dans un article. L'option *Affichage automatique* est responsable de la position du champ et votre modèle est responsable du design du champ.

![affichage du champ URL sur le site](../../../en/images/fields/fields-url-site.png)

L'URL suit l'étiquette du champ.

*Traduit par openai.com*


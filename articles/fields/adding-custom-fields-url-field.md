<!-- Filename: J3.x:Adding_custom_fields/Url_Field / Display title: Champ d'URL -->

## Objectif

Le champ URL fournit un lien URL vers un autre document. Si vous préférez utiliser une balise d'ancrage telle que `<a href="url">Texte explicatif</a>`, utilisez un champ de texte.


## Création de champ

Les options spéciales dans ce champ sont :

- **Schémas** Les schémas autorisés sont HTTP, HTTPS, FTP, FTPS, MAILTO, URL et
  FILE. Tous sont autorisés par défaut. Ceux sélectionnés dans la liste sont autorisés tandis
  que ceux non sélectionnés sont interdits. Cela est évident lors de la saisie de données : lorsqu'un
  type non sélectionné est entré, par exemple http://, un message d'erreur apparaît et
  le champ n'est pas enregistré.
- **Relatif** Utilisez cette option pour déterminer si les URL relatives sont
  autorisées ou non.
- **Afficher l'URL** Si l'option est réglée sur *Non*, lors de l'affichage des articles, l'URL est remplacée par les mots *Visitez le site*.

## Saisie de Données

Simple : il suffit de saisir une URL de destination.


## Affichage des Données

La capture d'écran du site suivante montre le champ affiché dans un article. L'option *Affichage automatique* est responsable de la position du champ et votre modèle est responsable du design du champ.

Recherchez l'élément **Informations complémentaires**.

![Affichage de tous les champs](../../../en/images/fields/fields-display.png "Affichage des champs")

L'URL suit l'étiquette du champ. La destination s'ouvre dans un nouvel onglet ou une nouvelle fenêtre.

*Traduit par openai.com*


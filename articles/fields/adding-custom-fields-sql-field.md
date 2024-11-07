<!-- Filename: J3.x:Adding_custom_fields/Sql_Field / Display title: Champ SQL -->

## Objectif

Le champ SQL offre une liste déroulante des entrées obtenues à partir d'une requête de base de données. Pour utiliser ce champ, vous devez savoir comment construire une requête et vous devriez la tester dans phpMyAdmin.

## Création de Champ

Les options spéciales dans ce champ sont :

- **Multiple** Permet la sélection de plusieurs valeurs. Si réglé sur *Oui*, la liste affiche 4 éléments. Sinon, elle affiche 1 élément. Dans les deux cas, il y a une longue liste à faire défiler pour faire des sélections - si activée.
- **Requête** La requête SQL qui fournira les données pour la liste déroulante. La requête doit retourner deux colonnes : une appelée 'value' qui contiendra les valeurs des éléments de la liste et l'autre appelée 'text' contenant le texte dans la liste déroulante.

Dans cet exemple, une table contenant une liste de noms de pays est utilisée. Voici la requête :
```
SELECT `id` AS value, `title` AS text
FROM `#__countrybase_countries`
WHERE `state` = 1
ORDER BY `title` ASC
```
![Champ SQL](../../../en/images/fields/fields-sql.png "Champ SQL")

## Saisie de données

Simple - sélectionnez dans la liste.


## Affichage des données

La capture d'écran suivante du site montre le champ affiché dans un article. L'option *Affichage automatique* est responsable de la position du champ et votre modèle est responsable du design du champ.

Recherchez l'élément **Pays d'origine**.

![Affichage de tous les champs](../../../en/images/fields/fields-display.png "Affichage des champs")

La sortie est un seul élément ou une liste d'éléments séparés par des virgules (noms de pays) suivant l'étiquette du champ (Pays d'origine).


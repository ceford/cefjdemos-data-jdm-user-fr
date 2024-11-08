<!-- Filename: J3.x:Adding_custom_fields/Sql_Field / Display title: Champ SQL -->

## Objectif

Le champ SQL offre une liste déroulante d'entrées obtenues à partir d'une requête de base de données. Pour utiliser ce champ, vous devez savoir comment construire une requête et vous devriez la tester dans phpMyAdmin.

## Création de champ

Les options spéciales pour ce champ sont :

- **Multiple** Permettre de sélectionner plusieurs valeurs. Si l'option est définie sur *Oui*, la liste affiche 4 éléments. Sinon, elle affiche 1 élément. Dans les deux cas, il y a une longue liste à faire défiler pour faire des sélections - si elle est activée.
- **Requête** La requête SQL qui fournira les données pour la liste déroulante. La requête doit retourner deux colonnes : l'une appelée 'valeur' qui contiendra les valeurs des éléments de la liste ; l'autre appelée 'texte' contenant le texte dans la liste déroulante.

Dans cet exemple, une table contenant une liste de noms de pays est utilisée. Voici la requête :
```
SELECT `id` AS valeur, `title` AS texte
FROM `#__countrybase_countries`
WHERE `state` = 1
ORDER BY `title` ASC
```
![Création de champ SQL](../../../en/images/fields/fields-sql-edit.png)

**Note :** Dans cet exemple, l'inclusion du type de champ dans le titre est uniquement à des fins de démonstration. Ne l'incluez pas dans vos propres titres de champs.

## Saisie de Données

Simple - sélectionnez dans la liste.

![Saisie de données dans le champ SQL](../../../en/images/fields/fields-sql-data-entry.png)


## Affichage des Données

La capture d'écran suivante du site montre le champ affiché dans un article. L'option *Affichage automatique* est responsable de la position du champ et votre modèle est responsable du design du champ.

![Affichage du champ SQL sur le site](../../../en/images/fields/fields-sql-site.png)

La sortie est un seul élément ou une liste d'éléments séparés par des virgules (noms de pays) suivant le label du champ (Pays d'origine).

*Traduit par openai.com*


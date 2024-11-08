<!-- Filename: J3.x:Adding_custom_fields/Color_Field / Display title: Champ de couleur -->

## Objectif

Le champ Couleur offre un sélecteur pour la sélection visuelle d'une couleur. Le champ
affiche la valeur hexadécimale résultante.


## Création de champ

Options spéciales pour ce champ :

- **Classe de champ** Régler sur *w-auto* pour que le champ soit juste assez large pour le nuancier et la valeur.

![Création de champ de couleur](../../../en/images/fields/fields-colour-edit.png)

**Remarque :** Dans cet exemple, l'inclusion du type de champ dans le titre est uniquement à des fins de démonstration. Ne l'incluez pas dans les titres de vos propres champs.

## Saisie de données

Vous pouvez saisir une valeur de couleur hexadécimale si vous savez que les numéros hexadécimaux vont de 0 à 9 puis de a à f, et que les paires de chiffres représentent le rouge, le vert et le bleu. Ainsi, #00ff00 signifie pas de rouge, maximum de vert et pas de bleu. Vous pouvez également utiliser un curseur pour sélectionner une couleur visuellement.

![Saisie de données de champ de couleur](../../../en/images/fields/fields-colour-data-entry.png)


## Affichage des Données

La capture d'écran suivante du site montre le champ affiché dans un article. L'option *Affichage automatique* est responsable de la position du champ et votre modèle est responsable du design du champ.

L'affichage des données par défaut est la valeur de la couleur hexadécimale, ce qui n'est pas très utile. La solution simple est de créer une substitution de modèle pour les champs / plugin de couleur. Il suffit de remplacer cette ligne :
```
echo htmlentities($value);
```
par ces lignes :
```
$value = htmlentities($value);
echo '<span style="background-color: ' . $value . ';"> ' . $value . '</span>';
```
Et la valeur hexadécimale sera précédée d'un échantillon avec la couleur d'arrière-plan de la valeur.

Recherchez l'élément **Couleur des Fleurs**.

![affichage du champ couleur sur le site](../../../en/images/fields/fields-colour-site.png)


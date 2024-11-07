<!-- Filename: J3.x:Adding_custom_fields/Color_Field / Display title: Champ de couleur -->

## Objectif

Le champ Couleur fournit un sélecteur pour la sélection visuelle d'une couleur. Le champ affiche la valeur hexadécimale résultante.

## Création de champ

Options spéciales pour ce champ :

- **Classe du champ** Régler sur *w-auto* pour que le champ soit juste assez large pour
l'échantillon et la valeur.


## Saisie de données

Vous pouvez saisir une valeur de couleur hexadécimale si vous savez que les nombres hexadécimaux vont de 0 à 9 et ensuite de a à f, et que les paires de nombres représentent le rouge, le vert et le bleu. Ainsi, #00ff00 signifie pas de rouge, maximum de vert et pas de bleu. Vous pouvez également utiliser un curseur pour sélectionner une couleur visuellement.

![Sélecteur de couleur](../../../en/images/fields/fields-colour-entry.png "Sélecteur de couleur")


## Affichage des Données

La capture d'écran suivante du site montre le champ affiché dans un article. L'option *Affichage automatique* est responsable de la position du champ et votre modèle est responsable du design du champ.

L'affichage par défaut des données est la valeur hexadécimale de la couleur, ce qui n'est pas très utile. La solution facile est de créer une surcharge de modèle pour les champs / plugin de couleur. Il suffit de remplacer cette ligne :
```
echo htmlentities($value);
```
par ces lignes :
```
$value = htmlentities($value);
echo '<span style="background-color: ' . $value . ';"> ' . $value . '</span>';
```
Et la valeur hexadécimale sera précédée d'un nuancier avec la couleur de fond de la valeur.

Recherchez l'élément **Couleur de la Fleur**.

![Affichage de tous les champs](../../../en/images/fields/fields-display.png "Affichage des champs")


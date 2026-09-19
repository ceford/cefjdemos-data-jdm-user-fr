<!--
{
    "source": "https://docs.joomla.org/localhost",
    "title": "Champ num\u00e9rique",
    "description": "",
    "author": ""
}
-->

## Objectif

Le champ numérique permet de saisir un nombre réel, avec la possibilité d’ajouter une devise ou un autre symbole avant ou après le nombre. Le contrôle peut être utilisé comme un champ entier avec des flèches d’incrémentation et de décrémentation, avec une plage par défaut de 1 à 100. Toutefois, des valeurs réelles, positives ou négatives, peuvent être saisies dans le champ. Exemple : `99.99` peut être mis en forme pour apparaître sous la forme `£99.99` pour l’utilisateur final. De même, `-273.15` peut apparaître sous la forme `-273.15C` pour l’utilisateur final.

## Création du champ

### Onglet Général

![Création d'un champ numérique](../../../en/images/fields/adding-custom-fields-number-field/01-fields-number-edit.png)

- **Type** Numérique, qui ne peut pas être modifié après la sélection.
- **Name** Le nom unique du champ.
- **Label** Une étiquette traduisible pour le champ.
- **Description** Une description facultative et traduisible du champ.
- **Required** Sélectionnez *Oui* si ce champ est obligatoire ?
- **Only Use in Subform** *Oui ou *Non*.
- **Default Value** Une valeur par défaut facultative.
- **Minimum** Valeur minimale pouvant être sélectionnée à l'aide des flèches haut/bas, la valeur par défaut étant 1. Il peut s'agir d'un nombre négatif ; définissez-la donc à une valeur inférieure au plus petit nombre prévu, **sinon la sélection de la flèche vers le bas peut effacer le nombre existant**.
- **Maximum** Valeur maximale pouvant être sélectionnée à l'aide des flèches haut/bas, la valeur par défaut étant 100. Définissez-la à une valeur supérieure au plus grand nombre prévu, **sinon la sélection de la flèche vers le haut peut effacer le nombre existant**.
- **Pas d’incrémentation** La taille de l’incrément ajouté ou soustrait à la valeur actuelle du champ à l’aide des flèches haut/bas. Il peut s’agir d’un entier, la valeur par défaut étant 1, ou d’une valeur décimale telle que 0,01. **Définissez-le sur la plus petite valeur selon laquelle vous souhaitez incrémenter ou décrémenter la valeur**.
- **Formater en devise** Si cette option est sélectionnée, des champs supplémentaires sont disponibles :
    - **Symbole monétaire** Il peut s’agir d’un symbole unique, tel que `£` ou `$`, ou d’une chaîne de caractères, telle que `&deg;C`, qui s’affiche sous la forme *&deg;C*.
    - **Position du symbole** Sélectionnez *Avant* ou *Après* le nombre.
    - **Nombre de décimales** Généralement 2 pour les devises, mais cela peut être différent dans d’autres contextes.

### Onglet Options

#### Panneau des options du formulaire :

- **Texte indicatif**  Texte indicatif qui s’affichera dans le champ comme indication pour l’utilisateur concernant la saisie requise.
- **Classe du champ** Classe facultative ajoutée au champ du formulaire de saisie des données.
- **Classe du libellé** Classe facultative ajoutée au libellé du formulaire de saisie des données.
- **Modifiable dans** Interfaces d’édition autorisées : *Site*, *Administration* ou *Les deux*. 
- **Attribut Showon** Affiche ou masque conditionnellement le champ en fonction de la valeur d’autres champs.

#### Panneau des options d’affichage :

- **Classe d’affichage** La classe du conteneur du champ dans la sortie.
- **Classe de valeur** La classe de la valeur du champ dans la sortie.
- **Étiquette** *Afficher* ou *Masquer* l’étiquette dans la sortie. Si cette option est définie sur Afficher :
    - **Classe de l’étiquette (sortie)** Une classe pour l’étiquette de sortie.
- **Affichage automatique** Indique si et où afficher le champ :
    - **Après le titre**
    - **Avant le contenu affiché**
    - **Après le contenu affiché**
    - **Ne pas afficher automatiquement**
- **Préfixe** Texte qui apparaîtra avant la valeur du champ.
- **Suffixe** Texte qui apparaîtra après la valeur du champ.
- **Mise en page** Une liste des mises en page disponibles.
- **Afficher en lecture seule** Choix entre *Hériter*, *Oui* ou *Non*.

#### Panneau de recherche intelligente

- **Index de recherche** Choix d’effectuer ou non une recherche et de la méthode de recherche.

### Onglets Publication et autorisations

Le contenu de ces onglets est évident et est traité ailleurs.

## Saisie de données

Saisie de données : saisissez simplement la valeur souhaitée. Cet exemple correspond au point d’ébullition de l’argon :

![Saisie de données dans un champ numérique](../../../en/images/fields/adding-custom-fields-number-field/02-fields-number-data-entry.png)

**Attention :** si le nombre que vous saisissez est en dehors de la plage minimale et maximale définie dans les options de création du champ, une étiquette au survol du navigateur vous l’indiquera, mais cette information n’est pas appliquée. Vous pouvez saisir un nombre en dehors de la plage, et il sera accepté.

## Affichage des données

L’image suivante montre l’affichage d’un élément avec une valeur négative :

![Affichage d’un champ numérique sur le site](../../../en/images/fields/adding-custom-fields-number-field/03-fields-number-site.png)

*Traduit par openai.com*
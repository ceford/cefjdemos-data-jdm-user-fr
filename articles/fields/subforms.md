<!-- Filename: jdocmanual?manual=user&heading=fields&filename=subform.md / Display title: Champ de sous-formulaire   -->

## Objectif

Le champ de sous-formulaire permet de regrouper une sélection de champs dans une liste répétable.

## Création de champ

Commencez par créer les champs nécessaires dans le sous-formulaire. Dans l'exemple décrit ici, il y a un champ Calendrier (Date d'acquisition), un champ Texte (Prix) et un champ Couleur (Couleur des fleurs) à utiliser pour une liste de plusieurs spécimens.

**Bug :** Il y a un bug dans le code du champ Calendrier qui entraîne une erreur fatale lors de l'enregistrement d'un article pour la deuxième fois. Pour éviter ce problème, réglez la valeur *Afficher l'heure* du champ Calendrier sur *Oui*.

Options spéciales pour ce champ :

- **Titre** et **Libellé** Dans cet exemple, ceux-ci sont définis sur *Spécimens*.
- **Champs** Ajoutez les champs requis dans le sous-formulaire un par un. Chaque ligne dispose d'une liste déroulante des champs disponibles et d'un basculement Oui/Non pour afficher les valeurs. L'ordre des éléments peut être modifié avec l'icône de glissement.

![Création de sous-formulaire](../../../en/images/fields/fields-subform-edit.png)

**Remarque :** Dans cet exemple, l'inclusion du type de champ dans le titre est uniquement à des fins de démonstration. Laissez-le de côté dans vos propres titres de champs.

## Saisie de données

Dans le formulaire de saisie de données, vous devez ajouter des lignes pour chaque spécimen. Chaque ligne
contient un champ Calendrier, un champ Texte et un champ Couleur.

![Saisie de données dans un sous-formulaire](../../../en/images/fields/fields-subform-data-entry.png)

## Affichage des données

Dans l'article, le sous-formulaire intitulé Spécimens a une ligne pour chaque spécimen.
Recherchez l'élément **Spécimens** dans cette capture d'écran :

![affichage du site de sous-formulaire](../../../en/images/fields/fields-subform-site.png)

*Traduit par openai.com*


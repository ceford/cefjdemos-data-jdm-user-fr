<!-- Filename: jdocmanual?manual=user&heading=fields&filename=subform.md / Display title: Champ du Sous-formulaire -->

## Objectif

Le champ sous-formulaire permet de regrouper une sélection de champs dans une liste répétable.

## Création de Champ

Commencez par créer les champs nécessaires dans le sous-formulaire. Dans l'exemple décrit ici, il y a un champ Calendrier (Date d'acquisition), un champ Texte (Prix) et un champ Couleur (Couleur de la Fleur) à utiliser pour une liste de plusieurs spécimens.

**Bogue :** Il y a un bogue dans le code du champ Calendrier qui entraîne une erreur fatale lors de l'enregistrement d'un article une deuxième fois. Pour éviter ce problème, réglez la valeur *Afficher l'heure* du champ Calendrier sur *Oui*.

Options spéciales pour ce champ :

- **Titre** et **Étiquette** Dans cet exemple, ceux-ci sont définis sur *Spécimens*.
- **Champs** Ajoutez les champs requis dans le sous-formulaire un par un. Chaque ligne a une liste déroulante de champs disponibles et un bouton bascule Oui/Non pour Afficher les Valeurs. L'ordre des éléments peut être modifié avec l'icône de glisser-déposer.

![Création de sous-formulaire](../../../en/images/fields/fields-subform.png "Création de sous-formulaire")

## Saisie de données

Dans le formulaire de saisie de données, vous devez ajouter des lignes pour chaque spécimen. Chaque ligne contient un champ Calendrier, un champ Texte et un champ Couleur. 

![Saisie de données du sous-formulaire](../../../en/images/fields/fields-subform-entry.png "Saisie de données du sous-formulaire")

## Affichage des données

Dans l'article, le sous-formulaire intitulé Spécimens a une ligne pour chaque spécimen. Recherchez l'élément **Spécimens** dans cette capture d'écran :

![Affichage de tous les champs](../../../en/images/fields/fields-display.png "Affichage des champs")

*Traduit par openai.com*


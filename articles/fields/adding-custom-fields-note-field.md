<!--
{
    "source": "https://docs.joomla.org/localhost",
    "title": "Champ de note",
    "description": "",
    "author": ""
}
-->

## Objectif

Le type de champ de formulaire de note permet de créer des titres, des textes, des descriptions et même des encadrés d’alerte. Il permet également de structurer les paramètres des extensions en les séparant à l’aide de titres utiles. Ou d’ajouter des descriptions pour certains paramètres (sans avoir à utiliser les info-bulles). Ou d’ajouter tout autre texte de votre choix.

## Création du champ

### Onglet Général

![Création d’un champ de note](../../../en/images/fields/adding-custom-fields-note-field/01-fields-note-edit.png)

- **Type** Nombre, qui ne peut pas être modifié après sélection.
- **Name** Le nom unique du champ.
- **Label** Un libellé traduisible pour le champ.
- **Description** Une description facultative et traduisible du champ.
- **Only Use in Subform** *Oui ou *Non*.
- **Note Heading** Ce texte sera visible dans le formulaire de saisie des données.
- **Note Content** Le texte de la note.
- **Note Class** Toute classe existante ou nouvelle. La classe par défaut *alert alert-info* produit une boîte d’alerte Bootstrap.
- **Heading Tag** Sélectionnez un niveau de titre dans la liste.
- **Show Close Button**  Ce champ contrôle l’affichage d’un « x » pour fermer la note. Il accepte la valeur « true » (pour les alertes) ou la valeur de l’attribut data-dismiss de l’icône de fermeture Bootstrap.

### Onglet Options

- **Affichage automatique** Indique si et où afficher le champ :
    - **Après le titre**
    - **Avant le contenu affiché**
    - **Après le contenu affiché**
    - **Ne pas afficher automatiquement**
- **Mise en page** une liste des mises en page disponibles.
- **Afficher dans l’interface publique** *Oui* ou *Non*.

## Saisie des données

Dans le formulaire de saisie des données, le champ de note apparaît parmi les autres champs sous forme de texte stylisé conformément aux choix de style définis dans le champ. Il peut contenir des instructions ou des informations.

![Saisie des données du champ numérique](../../../en/images/fields/adding-custom-fields-note-field/02-fields-note-data-entry.png)

**Astuce :** Utilisez le mécanisme de tri des champs pour classer la note parmi les autres champs. Vous pouvez disposer de plusieurs champs de note différents pour structurer et documenter vos champs.

## Affichage des données

Si *Afficher dans l’interface publique* est défini sur *Oui*, le champ de note apparaît parmi les autres champs dans l’interface publique. Il peut alors contenir des informations générales communes à un groupe d’articles.

*Traduit par openai.com*
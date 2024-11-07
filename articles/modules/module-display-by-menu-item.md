<!-- Filename: J4.x:Module_Display_by_Menu_Item / Display title: Affichage du Module par Élément de Menu  -->

## Introduction

Dans Joomla, il arrive souvent que différents modules apparaissent sur différentes pages. Et parfois, différents modules sont présentés à différents groupes d'utilisateurs. Le comportement d'affichage des modules est contrôlé par une combinaison d'assignation de menu et de permission d'accès dans le formulaire d'édition de module. Par défaut, un module est affiché sur toutes les pages et pour tous les groupes d'utilisateurs.

## Accès

Ce champ se trouve dans l'onglet Module du formulaire de saisie des données du module. Il est dans le panneau de droite et ne doit pas être confondu avec l'onglet Permissions. Les options disponibles sont :

- Public - visible pour tous les groupes d'utilisateurs.
- Invité - non visible après connexion.
- Enregistré - visible uniquement après connexion.
- Spécial - visible uniquement après connexion pour les groupes d'utilisateurs autres qu'Enregistré.
- Super Utilisateur - visible uniquement pour ce groupe d'utilisateurs.

## Affectation du Menu

Il existe quatre options d'affectation de menu :

- Sur toutes les pages
- Sur aucune page
- Uniquement sur les pages sélectionnées
- Sur toutes les pages sauf celles sélectionnées

Pour les deux dernières options, un panneau de sélection de menu est affiché. Initialement, les menus qu'il contient sont entièrement développés, mais ils peuvent être réduits avec le bouton **Développer les sous-arborescences du menu** *Aucun*. Ensuite, développez le menu qui vous intéresse.
![affectation du menu du module](../../../en/images/modules/module-display-by-menu.png)

Sélectionnez les éléments de menu pour afficher ou ne pas afficher le module comme souhaité.

## Exemples

### Fil d'Ariane pas sur la page d'accueil

- Ouvrez le module Fil d'Ariane.
- Sélectionnez *Sur toutes les pages sauf celles sélectionnées*
- Sélectionnez *Aucun* après **Assigner aux éléments du menu**
- Trouvez l'élément de menu de la page d'accueil et cochez sa case.
- Enregistrez
- Vérifiez le site - le fil d'Ariane devrait être présent sur toutes les pages sauf la page d'accueil.

*Traduit par openai.com*


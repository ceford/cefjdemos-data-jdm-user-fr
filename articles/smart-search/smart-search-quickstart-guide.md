<!-- Filename: Smart_Search_quickstart_guide / Display title: Démarrage rapide de la recherche intelligente  -->

## Contexte

La recherche a été une fonctionnalité de Joomla! depuis ses débuts. Elle permettait aux utilisateurs de chercher des mots ou des phrases dans la base de données et de retourner les résultats dans l'ordre de la première occurrence. Cette forme de recherche a été supprimée et remplacée par la Recherche Intelligente, qui pré-indexe les mots significatifs et utilise des algorithmes de scoring et de filtrage pour aider à retourner les meilleurs résultats. La Recherche Intelligente est activée par défaut dans Joomla 4 et 5.

### Soyez conscient

Si vous avez des éléments de contenu qui ne sont pas disponibles pour le public, la fonction d'auto-complétion affichera tout de même les termes contenus dans ces éléments. Les éléments de contenu eux-mêmes ne peuvent pas être consultés et ne seront pas répertoriés dans les résultats de recherche mais si révéler la présence d'un mot ou d'une phrase dans un élément de contenu restreint est une source de préoccupation, alors vous devriez désactiver l'auto-complétion. Pour désactiver l'auto-complétion, utilisez la procédure suivante :

1. Connectez-vous à l'Administrateur.
2. Sélectionnez **Composants → Recherche Intelligente**.
3. Sélectionnez le bouton de la barre d'outils **Options**.
4. Changez *Suggestions de recherche* de **Afficher** à **Cacher**.
5. Sélectionnez **Enregistrer & Fermer**.

## Préparer les plugins de recherche intelligente

Pour que le contenu soit affiché dans les résultats de recherche, il doit d'abord être indexé par l'un des plugins de recherche intelligente. Avant de démarrer l'indexeur, il est recommandé de revoir les plugins disponibles et de désactiver ceux qui ne seront pas nécessaires pour votre site. Pour examiner les plugins de recherche intelligente disponibles, utilisez la procédure suivante :

1. Connectez-vous à l'administrateur.
2. Sélectionnez les **Plugins** depuis le *Tableau de bord Accueil*.
3. Filtrez les plugins en utilisant l'élément **finder** dans la liste **- Sélectionner le type -**.
4. Examinez la liste des plugins et désactivez ceux qui ne seront pas nécessaires pour votre site en sélectionnant l'icône de coche verte dans la colonne Statut pour le plugin. Cela devrait changer en une croix/cercle gris pour indiquer que le plugin est désactivé.

## Exécuter l'indexeur

Après avoir passé en revue les plug-ins de recherche, il est temps de démarrer l'indexeur Smart Search. Celui-ci va scanner le contenu de votre site Web et construire un index qui permettra une recherche rapide et intelligente par vos visiteurs. Il existe deux façons de lancer l'indexeur :

* Depuis le menu **Administrateur / Smart Search / Index**. Cela convient aux sites plus petits.
* Depuis la ligne de commande. Cela convient aux sites plus grands et ne devrait pas entraîner de défauts de dépassement de délai. Cependant, les sites très grands pourraient vraiment avoir besoin d'un service de recherche externe.

### Indexer depuis l'interface Administrateur

1. Connectez-vous à l'Administrateur.
2. Sélectionnez les éléments du menu **Composants → Smart Search → Index**.
3. Sélectionnez le bouton **Indexer** dans la barre d'outils pour démarrer l'indexeur. Cela ouvrira une fenêtre modale avec des informations sur l'état de l'indexeur et une barre de progression.

En fonction de la taille de votre site, l'indexation peut prendre de quelques minutes à quelques heures. L'indexeur utilise des requêtes AJAX pour réaliser le processus global par petites étapes afin d'éviter les expirations et les problèmes de mémoire. L'indexation est terminée lorsque la barre de progression disparaît et que la fenêtre modale se ferme.

### Indexer depuis le CLI

1. Ouvrez une fenêtre de terminal.
2. Accédez au dossier cli à la racine de votre site.
3. Utilisez la commande suivante :<br>
   php joomla.php finder:index
4. Lorsque l'indexeur a terminé, allez à la page du Contenu Indexé de Smart Search de l'Administrateur.

## Contenu Indexé

La page Contenu Indexé répertorie tout le contenu indexé. Si vous préférez que certains éléments ne soient pas affichés dans les résultats de recherche, vous pouvez les dépublier de la base de données Smart Search en cochant la case à côté du titre de l'élément, puis en appuyant sur le bouton Dépublier.

**NOTE IMPORTANTE** : Si votre site contient une grande quantité de contenu, ou des éléments de contenu particulièrement volumineux, ou si vous disposez d'un espace disque limité, vous devriez lire à propos de [Smart Search sur les grands sites](jdocmanual?article=user/smart-search/smart-search-on-large-sites "Smart Search sur les grands sites").

## Exposition de la recherche intelligente aux utilisateurs du site

Maintenant que l'index de recherche intelligente est préparé et prêt, vous devez exposer la recherche intelligente aux utilisateurs de votre site web. La recherche intelligente offre deux moyens de le faire :

### L'interface du module

La recherche intelligente inclut un module qui peut être activé pour afficher un simple formulaire de recherche sur n'importe quelle page et pratiquement à n'importe quelle position. Pour activer le module de recherche intelligente, utilisez la procédure suivante :

1. Connectez-vous à l'administrateur.
2. Sélectionnez l'élément de menu Extensions → Gestion des modules.
3. Cliquez sur le bouton Nouveau dans la barre d'outils du gestionnaire de modules.
4. Sélectionnez "Module de recherche intelligente" dans la liste des types de modules affichés.
5. Configurez le module en saisissant (au minimum) un titre, en sélectionnant la position du module et en ajustant les pages sur lesquelles il doit s'afficher si désiré. Des options de configuration supplémentaires pour le module sont décrites dans l'écran d'aide du module de recherche intelligente.
6. Sélectionnez le bouton Enregistrer dans la barre d'outils pour publier le module.

### L'interface de l'élément de menu

La recherche intelligente peut également être liée via un élément de menu Joomla afin que les utilisateurs puissent naviguer directement vers le formulaire de recherche principal. Pour créer un lien d'élément de menu vers la recherche intelligente, utilisez la procédure suivante :

1. Connectez-vous à l'administrateur.
2. Sélectionnez l'élément de menu Extensions → Gestion des modules.
3. Appuyez sur le bouton Nouveau dans la barre d'outils du gestionnaire de menus.
4. Cliquez sur le bouton Sélectionner à côté du champ Type d'élément de menu.
5. Sélectionnez "Recherche" sous l'entrée "Recherche intelligente" dans la liste des types d'éléments de menu affichés.
6. Configurez l'élément de menu en saisissant (au minimum) un titre de menu et en ajustant l'élément parent si désiré.
7. Sélectionnez le bouton Enregistrer dans la barre d'outils pour publier l'élément de menu.

## Test, Test, Test

Pour tester la Recherche Intelligente, accédez à l'un des éléments de menu que vous avez créés et entrez une requête dans le formulaire de recherche ou saisissez une requête dans l'une des instances du module de Recherche Intelligente. Vous devriez être dirigé vers une liste de résultats de recherche si des résultats ont pu être trouvés pour le mot ou la phrase que vous avez saisi. Si aucun résultat n'a pu être trouvé, un message s'affichera indiquant qu'aucun résultat n'a pu être trouvé. Si aucun résultat n'a pu être trouvé et que le système dispose d'une suggestion de recherche basée sur votre terme, l'expression de recherche suggérée s'affichera au-dessus du message indiquant qu'aucun résultat n'a pu être trouvé.


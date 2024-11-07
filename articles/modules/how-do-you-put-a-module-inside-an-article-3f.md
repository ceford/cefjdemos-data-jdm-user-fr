<!-- Filename: How_do_you_put_a_module_inside_an_article%3F / Display title: Modules à l'intérieur des articles -->

## Introduction

Vous souhaiterez généralement associer des modules à des articles d'une certaine manière. Les modules sont généralement attribués à des positions de module, et ces positions apparaissent quelque part sur la page web, tel que déterminé par le modèle. Cependant, il est parfois utile d'avoir un module directement intégré dans un article. Joomla dispose d'un plugin nommé *Content - Load Modules* pour cela. Lorsqu'il est activé, un module peut être intégré dans un article de trois manières différentes :

```
    {loadposition position,[style]}
    {loadmodule mod_type,titre,[style]}
    {loadmoduleid moduleId}
```

Où `style` est l'une des valeurs de Style de Module de l'onglet Avancé du formulaire de saisie des données du module, par exemple html, outline, table, card ou noCard.

## chargerposition

Pour insérer un module à l'intérieur d'un article, vous publiez le module à une position et chargez cette position dans l'article comme suit :

1. Créez un module et définissez sa position sur ***maposition***. ***maposition*** peut être n'importe quelle valeur qui ne soit pas en conflit avec une position de modèle existante. Dans le formulaire d'édition du module, saisissez la position ***maposition*** et appuyez sur Entrée au lieu de la sélectionner dans la liste déroulante.
2. Assignez le module à **Tous** les éléments de menu. Cela garantira qu'il apparaît toujours, peu importe comment le visiteur est arrivé à l'article. Le module ne s'affichera pas à moins que vous n'utilisiez la commande pour charger le module dans un article.
3. Modifiez l'article et insérez le texte ***{chargerposition maposition}*** à l'endroit où vous souhaitez que le module apparaisse.

**Remarque :** Si le plugin *Contenu - Charger les modules* est désactivé, le texte *{chargerposition maposition}* apparaîtra inchangé dans l'article. En outre, le nom de la position doit être tout en minuscules. Les majuscules dans les noms échoueront.

## loadmodule

La syntaxe *{loadmodule yyy}* recherche le premier module dont le **type** correspond à la chaîne 'yyy'. Ainsi, vous pourriez charger un module *mod_login* en plaçant {loadmodule login} dans votre texte. Le type n'est pas si évident ! Par exemple, le sélecteur de langue est de type **languages**. Pour trouver le type, vous devez parcourir la liste des dossiers de modules avec un gestionnaire/explorateur de fichiers et supprimer la partie *mod_* du nom du dossier.

Si vous souhaitez charger une instance spécifique d'un module parce que vous avez plus d'un module de connexion, par exemple intitulé Login 1, Login 2, etc., vous devez utiliser {loadmodule mod_modType, modTitle} où **mod_modType** serait mod_login et **modTitle** serait le nom/titre donné à votre instance de ce module. Donc, dans l'exemple ci-dessus, vous obtenez **{loadmodule mod_login Login 2}**.

Vous pouvez également ajouter le style utilisé pour rendre le module. Pour ce faire, ajoutez le style en tant que troisième paramètre comme {loadmodule login,Login 2,xhtml}. Si vous n'ajoutez pas de style, alors aucun n'est utilisé.

## loadmoduleid

La syntaxe *{loadmoduleid z}* recherche le module dont l'`id` correspond au numéro `z`. Ainsi, vous pouvez charger le module avec l'id 200 en plaçant *{loadmoduleid 200}* dans votre texte. Cette variante n'utilise pas de paramètres supplémentaires comme le paramètre `style`.

## Bouton de l'Éditeur

Si le plugin editor-xtd *Bouton - Module* est activé, vous pouvez utiliser le bouton de l'éditeur *Module* pour insérer plus facilement les balises décrites ci-dessus dans le texte de l'éditeur. La liste des modules a un bouton dans la colonne Titre pour insérer par ID et un bouton dans la colonne Position pour insérer par position.

## Modules dans les Modules

Il est possible d'inclure un module dans un module *HTML Personnalisé*. Ils sont traités par les plugins de contenu de la même manière que les articles.

Il peut y avoir des problèmes de formatage puisque le style du module *HTML Personnalisé* entourera le style du module inclus. C'est la raison pour laquelle le bouton d'édition *Module* n'est pas disponible dans les modules de type *Personnalisé*.

*Traduit par openai.com*


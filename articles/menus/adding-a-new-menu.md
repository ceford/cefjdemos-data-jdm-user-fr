<!-- Filename: J4.x:Adding_a_New_Menu / Display title: Ajouter un nouveau menu  -->

## Introduction

Pour que le contenu soit accessible sur votre site Joomla!, les éléments doivent être assignés à un menu. Une installation standard de Joomla! crée un **Menu Principal** pour vous. Dans de nombreux cas, vous utiliserez un seul menu, mais vous pouvez en avoir plusieurs. Cela vous permet de créer des menus pour différents types de contenu, du contenu caché, du contenu spécifique à un rôle utilisateur, et plus encore.

Il y a trois étapes dans la création d'un menu utilisable :

1. Créer le menu. Il s'agit d'un conteneur pour les éléments de menu.
2. Créer un module de menu. Cela permet de placer le menu sur une page.
3. Créer des éléments de menu. Ce sont les éléments sélectionnables par l'utilisateur menant à des pages spécifiques.

Cette capture d'écran montre les menus disponibles dans un site multilingue. Dans une installation initiale de Joomla, il y a un seul *Menu Principal*.

![Liste des menus](../../../en/images/menus/menus-manage.png)

La liste vous permet de sélectionner n'importe lequel des boutons verts ou rouges pour accéder directement à la liste des éléments de menu dans ce menu et cet état.

Ce tutoriel couvre les étapes impliquées dans la création d'un menu dans un site Joomla!.

## Créer un nouveau menu

Utilisez l'une des étapes suivantes pour créer un nouveau menu :

- À partir du menu Administrateur, sélectionnez l'icône *Tableau de bord des menus* pour accéder au tableau de bord des menus, puis sélectionnez **Gérer**. Ou...
- À partir du menu Administrateur, développez la section *Menus* puis sélectionnez **Gérer**.
- Sélectionnez le bouton **+ Nouveau** dans la barre d'outils.
- Dans le formulaire de saisie des données du menu, complétez les champs suivants :
  - **Titre** : Un titre approprié pour le menu. Celui-ci est utilisé pour identifier le menu dans le gestionnaire de menus.
  - **Nom Unique** : Il s'agit d'un nom d'identification unique utilisé par Joomla! pour identifier ce menu. Les espaces ne sont pas autorisés, mais vous pouvez utiliser le caractère '-' comme dans le cas de resources-menu.
  - **Description** : Bien que non requise, cette information est souvent utile sur un site comportant de nombreux menus. Elle apparaît sous le *Titre* dans la liste des menus comme illustré ci-dessus.<br>
    ![Nouveau menu](../../../en/images/menus/menus-new.png)
- **Enregistrer & Fermer**

Dans la liste des menus, le menu nouvellement créé comporte un bouton intitulé **Ajouter un module pour ce menu**, ce qui est l'étape suivante dans la création du menu. Vous pouvez commencer à ajouter des éléments de menu et revenir plus tard pour créer le module de menu.  

## Créer un Module pour le Menu

Dans la liste des Menus, la colonne *Modules Liés* permet de sélectionner n'importe quel module de menu existant à des fins d'édition. Vous pouvez jeter un coup d'œil puis *Fermer* sans apporter de modifications. Pour votre nouveau menu, sélectionnez le bouton **Ajouter un module pour ce menu** pour ouvrir un cadre modal contenant le formulaire de saisie de données du module Menu.

![Formulaire de saisie de données du module Menu](../../../en/images/menus/menus-module.png)

Champs à compléter :

* Le champ **Titre** est obligatoire, créez donc un titre descriptif.
* Le bouton **Afficher le Titre** à droite sert à *Afficher* ou *Masquer* le titre du module, une fonctionnalité commune à tous les modules.
* Le champ **Sélectionner un Menu** doit afficher le nom du Menu que vous venez de créer.
* Le champ **Position** est utilisé pour sélectionner une position dans votre modèle où vous souhaitez que votre menu apparaisse.
* Sélectionnez **Enregistrer & Fermer** une fois que les informations essentielles ont été ajoutées.

Il y a de nombreuses options à choisir dans le formulaire *Paramètres d'édition du module*. Elles sont mentionnées dans l'écran d'aide disponible dans le formulaire *Module : Édition*. Il s'agit du même formulaire mais dans une page normale plutôt qu'un cadre modal. Accédez-y via le menu Administrateur, itinéraire Contenu / Modules du site pour la liste des Modules du site.

Remarque : obtenir l'apparence souhaitée pour le Menu dépend de la mise en forme de votre modèle.

## Ajouter des éléments au Menu

Pour créer les liens dans votre menu, vous devez ajouter des **éléments de menu**. Il existe de nombreux *types d'éléments de menu* dans Joomla, et les composants tiers peuvent ajouter d'autres types. Pour ce tutoriel, un lien vers un seul article sera ajouté.

Vous pouvez créer un article à l'avance ou vous pouvez créer un article pendant le processus de création du menu. Dans tous les cas, l'article doit exister avant qu'un élément de menu puisse être créé pour lui. Dans cet exemple, l'article sera également nommé *Ressources*. Il est destiné à contenir une liste de liens vers des fichiers PDF.

Dans la liste des **Menus**, dans la colonne **Éléments de menu**, sélectionnez l'icône pour le menu nouvellement créé, *Ressources* dans cet exemple. Initialement, il n'y a pas d'éléments de menu, donc la liste ne fait que dire *Aucun résultat correspondant*.

- Sélectionnez le bouton **Nouveau** dans la barre d'outils pour créer un nouvel élément de menu.
- Dans le champ **Titre**, ajoutez le titre que vous souhaitez voir apparaître dans le Menu.
- Dans le champ **Type d'élément de menu**, sélectionnez le bouton **Sélectionner** pour ouvrir une boîte de dialogue modale contenant une liste de composants. Chacun a une liste déroulante révélant une liste de types d'éléments de menu disponibles.
  - Sélectionnez **Articles** puis **Article unique**.
- Dans le champ **Sélectionner un article**: **Soit:**
  - Utilisez le bouton **Sélectionner** pour choisir un article existant. Cela ouvrira une liste d'articles parmi lesquels choisir. **Ou:**
  - Utilisez le bouton **Créer** pour créer un nouvel article. Tout ce que vous devez saisir est le titre de l'article. Il est probablement préférable de laisser le contenu détaillé pour plus tard.
- Vérifiez que le champ **Menu** est défini sur le nouveau Menu.
- Le champ **Statut** doit être défini sur **Publié**.
- Sélectionnez **Enregistrer & Fermer**.

![Formulaire de saisie de données de l'élément de menu](../../../en/images/menus/menus-single-article.png)

Ajoutez plus d'éléments au nouveau Menu selon les besoins.

Une fois que des éléments ont été ajoutés au Menu, vérifiez que le Menu est affiché sur le site web à la position correcte.

![Affichage du menu](../../../en/images/menus/menus-display.png)


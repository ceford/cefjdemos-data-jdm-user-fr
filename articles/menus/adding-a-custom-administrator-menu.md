<!-- Filename: J4.x:Adding_a_Custom_Administrator_Menu / Display title: Menu Administrateur Personnalisé -->
## Introduction

Supposons que vous ayez un utilisateur à qui vous souhaitez permettre d'effectuer uniquement une tâche sur votre site web. Prenons le cas d'une organisation qui a des branches partout dans le monde et la seule tâche que chaque branche est autorisée à accomplir est de placer des emplacements sur une carte pour les afficher sur le site. Le composant pour cette tâche est Ffmap, mais cela ne sera pas couvert ici, à part les éléments du menu Administrateur impliqués.

Pour accomplir cette tâche, vous devez créer un groupe d'utilisateurs personnalisé, assigner un utilisateur à ce groupe et créer un menu personnalisé à utiliser par cet utilisateur.

## Créer un Groupe d'Utilisateurs

- Sélectionnez **Utilisateur → Utilisateurs → Groupes** dans le menu Administrateur.
- Sélectionnez le bouton **Nouveau** dans la barre d'outils.
  - Entrez un **Titre pour le Groupe,** *Filiale* dans ce cas.
  - Sélectionnez **Public** comme groupe parent. C'est important - vous ne voulez pas hériter des autorisations d'un autre groupe.
- Sélectionnez **Enregistrer et Fermer** dans la barre d'outils.

## Définir les Permissions Globales pour le Groupe

- Sélectionnez **Configuration Globale** depuis le tableau de bord d'accueil.
- Sélectionnez l'onglet **Permissions**.
- Sélectionnez l'élément **Branche**.
- Définissez l'option **Connexion Administrateur** sur **Autorisé**.
- Sélectionnez **Enregistrer et Fermer** dans la barre d'outils.

À ce stade, tout utilisateur assigné au groupe d'utilisateurs Branche pourra se connecter à l'interface Administrateur et voir le tableau de bord d'accueil. Certains modules du tableau de bord peuvent être visibles car leur niveau d'accès a été défini sur Public, par exemple : Utilisateurs Connectés, Articles Populaires et Articles Récemment Ajoutés. Il est préférable de définir l'accès à ces modules sur Spécial. Il n'y aura aucun élément de menu visible pour l'utilisateur.

## Définir l'autorisation de composant pour le groupe

Soit :

- Sélectionnez le composant **Ffmap** dans le menu Administrateur.
- Sélectionnez le bouton **Options** de FFmap dans la barre d'outils pour ouvrir son écran de configuration.

Ou :

- Sélectionnez **Configuration Globale** depuis le Tableau de bord principal.
- Sélectionnez Ffmap dans la liste des composants.

Ensuite :

- Sélectionnez l'onglet **Permissions** puis l'élément **Branche**.
- Réglez l'Interface d'administration d'accès, Créer, Supprimer, Modifier, Modifier l'état, Modifier les propres valeurs et Modifier la valeur de champ personnalisée à **Autorisé**.
- Sélectionnez **Enregistrer et Fermer** dans la barre d'outils.

## Créer un nouveau menu Administrateur

- Sélectionnez **Menu → Gérer** dans le menu Administrateur.
- Sélectionnez **Administrateur** dans la liste déroulante Site/Administrateur.
- Sélectionnez le bouton **Nouveau** dans la barre d'outils.
- Entrez un titre pour le menu, par exemple **Menu Branche**, et un identifiant unique, par exemple **menu-branche**.
- Sélectionnez **Enregistrer et Fermer** dans la barre d'outils.

## Créer un module pour le menu

Dans la liste des menus, sélectionnez le bouton **Modules Liés** dans l'enregistrement du menu de la branche.

- Entrez un titre pour le module, par exemple **Menu de la Branche**.
- Sélectionnez le menu à afficher : **Menu de la Branche**.
- Réglez Vérifier le menu sur **Non**, sinon des messages d'avertissement apparaissent concernant les fonctions d'administrateur manquantes.
- Sélectionnez la position : **menu**.

## Créer un Conteneur de Menu de Composants

- Dans la liste des Menus, sélectionnez l'icône Éléments de Menu pour le Menu de la Branche. Cela ouvrira la liste des éléments, vide à ce stade.
- Sélectionnez le bouton **Nouveau** dans la barre d'outils.
- Entrez un titre pour l'élément de menu : **Composants de la Branche**.
- Sélectionnez le Type d'Élément de Menu **Bouton de Sélection**.
  - Dans la boîte de dialogue modale, faites défiler vers le bas jusqu'à l'élément **Liens Système** et développez le panneau.
  - Sélectionnez le type d'élément **Conteneur de Menu de Composants**.
- De retour dans le formulaire de configuration du menu, sélectionnez **Afficher Aucun** pour masquer tous les éléments du menu des Composants (en rouge).
- Faites défiler vers le bas jusqu'aux éléments Ffmap et cliquez sur les boutons Masquer pour les activer à Afficher (en vert).
- Sélectionnez **Enregistrer et Fermer** dans la barre d'outils.

## Capture d'écran

![sélection du composant de menu administrateur personnalisé](../../../en/images/menus/menus-custom-administrator-menu.png)

## Résultat

Créez un utilisateur dans le groupe Branch pour vous-même afin de tester. Connectez-vous à l'interface Administrateur en tant que cet utilisateur pour voir le résultat :

![résultat du menu administrateur personnalisé](../../../en/images/menus/menus-custom-administrator-menu-result.png)

## Notes

Si vous ajoutez ultérieurement un autre composant, il sera ajouté au Conteneur du menu des composants et visible par défaut. Vous devrez retourner à l'élément de menu Administrateur et définir le nouveau contenu sur Masquer.

Si le composant est configuré pour inclure des éléments de menu dans chacune des vues de liste Administrateur, par l'inclusion de fichiers default.xml, vous pourriez ajouter les éléments de menu directement au menu personnalisé et éviter d'utiliser le Conteneur du menu des composants.

Le menu des composants de la branche restera une partie du menu Administrateur - duplication inévitable !

*Traduit par openai.com*


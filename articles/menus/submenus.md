<!-- Filename: J4.x:Submenus / Display title: Sous-menus  -->

## Notions de base sur les menus

Dans Joomla, trois éléments contribuent à l'affichage d'un menu pour l'utilisateur :

- Un Menu est un conteneur pour les éléments de menu.
- Un Élément de Menu est un lien vers une page du site ou une page externe.
- Un Module de Menu fournit une méthode pour attribuer le menu à une position sur la page et pour contrôler les aspects de l'apparence ou du comportement du menu ou de la page.

Les menus simples se composent de listes de liens. Parfois, les membres d'une liste ont des relations parent-enfant affichées comme des sous-listes en retrait ou des listes déroulantes. Les relations parent-enfant peuvent être imbriquées à tous les niveaux. Cependant, un imbriquement au-delà de deux niveaux peut rendre les listes peu attrayantes et difficiles à utiliser.

Il y a des occasions où vous souhaiterez peut-être afficher les enfants d'un menu parent comme un sous-menu distinct. Un cas d'utilisation courant est de montrer un sous-menu à gauche d'une page, le contenu de la page au centre et une table des matières de la page à droite. Ce tutoriel explique comment procéder.

### Exemple de données

Supposons que vous ayez une série d'articles sur les animaux. Cela pourrait être des animaux de compagnie, une fiche d'information vétérinaire ou un zoo. Voici un exemple de structure courte à des fins de démonstration :

    Animaux
        Chats
            Birmans
            Bleus Russes
        Chiens
            Colleys
            Poméraniens

Les listes pourraient être assez longues, vous souhaiterez donc peut-être afficher uniquement une liste de races de chats sur les pages concernant les chats et uniquement une liste de races de chiens sur les pages concernant les chiens. La capture d'écran suivante montre la disposition cible que l'utilisateur souhaite obtenir :

![objectifs sous-menus animaux chats](../../../en/images/menus/submenus-objectives-animals-cats.png)

Dans cet exemple, lorsque l'utilisateur sélectionne l'élément de menu Animaux, la page Animaux est chargée et le module de menu Chats disparaît (pas de module Chiens non plus). Sélectionnez l'élément de menu Chats et le module de menu Chats apparaît à côté de la page Chats. Sélectionnez l'élément de menu Birmans et la page Birmans apparaît. Sélectionnez l'élément de menu Chiens et le module de menu Chats est remplacé par un module de menu Chiens à côté de la page Chiens.

Pour essayer ce tutoriel par vous-même, vous aurez besoin de créer quelques articles, un menu avec des éléments de menu et trois modules de menu.

## Créer des articles

Si vous êtes super efficace, vous pouvez créer un article, puis créer un élément de menu à partir de cet article. Pour cela, vous devrez d'abord créer un nouveau menu et suivre quelques étapes supplémentaires lors de la création de l'article. Il est donc préférable de faire simple au début et de commencer par vos nouveaux articles :

- Sélectionnez **Contenu **→** Articles **→** +** dans le menu de l'administrateur.
  Ou sélectionnez le bouton `Nouveau` dans la liste des articles.
- Remplissez le formulaire comme vous le feriez pour n'importe quel article.
- Sélectionnez le bouton `Enregistrer & Nouveau` à partir du `Enregistrer & Fermer` pour passer au nouvel article suivant.

Les données d'exemple présentées ci-dessus nécessitent sept articles.

## Créer un Nouveau Menu

Depuis le menu Administrateur :

- Sélectionnez **Menus **→** Gérer**.
- Dans la liste des menus, sélectionnez le bouton `Nouveau` pour créer un nouveau menu.
- Dans le formulaire Ajouter un Menu, donnez un titre au menu : Animaux et un nom unique : animaux.
- Dans certains cas, vous pourriez avoir besoin de vous rappeler à quoi sert ce menu. Remplissez donc le champ de description.
- Enregistrez ou Enregistrez & Fermez.

![nouveau menu de sous-menus](../../../en/images/menus/submenus-new-menu.png)

## Créer des éléments de menu

Il y a sept éléments de menu à créer.

### Élément de menu Animaux

Les nouveaux éléments de menu seront situés dans le menu Animaux.

- Sélectionnez **Menus **→** Animaux **→** +** dans le menu Administrateur.
- Remplissez le formulaire Menu : Modifier l'élément.
  - Titre : Animaux
  - Type d'élément de menu : Article unique
  - Sélectionner un article : Animaux - il s'agit de l'article parent utilisé pour introduire la série sur les Animaux
  - Menu : Animaux
  - Parent : - Pas de parent - ceci est la racine du menu
- Sélectionnez **Enregistrer & Nouveau** depuis la liste déroulante `Enregistrer & Fermer`.

### Élément de menu Chats

C'est en grande partie une répétition de l'élément de menu Animaux. Sauf :

- Le titre doit être Chats.
- L'article sélectionné dans le champ Sélectionner un article doit être `Chats`.
- L'élément parent doit être défini sur `Animaux`.

### Élément de menu Birmans

Répétez encore une fois. Sauf :

- Le titre doit être Birmans.
- L'article sélectionné dans le champ Sélectionner un article doit être `Birmans`.
- L'élément parent doit être défini sur `Chats`.

### Plus d'éléments de menu

Continuez jusqu'à ce que vous ayez sept éléments de menu, un pour chaque article.

## Liste des éléments du menu

Lorsque vous avez créé tous vos éléments de menu, vérifiez qu'ils ont les bonnes relations parent-enfant et qu'ils sont dans le bon ordre. Vous pouvez trier selon la colonne "Ordre" (la deuxième colonne) et utiliser les poignées de saisie (points de suspension verticaux) pour faire glisser les éléments dans le bon ordre. Si un élément a un mauvais parent, il vous suffit de sélectionner le titre de l'élément et de changer le parent dans le formulaire "Menus : Modifier l’élément".

![listes des éléments de sous-menus](../../../en/images/menus/submenus-menu-items-list.png)

## Modules de Menu

À cette étape, vous avez un menu, mais il n'a pas de module à attribuer à une position sur la page. Vous pourriez utiliser l'ensemble du menu comme un menu standard ou un menu déroulant. Cependant, le but de ce tutoriel est de montrer comment créer des sous-menus. Pour cela, vous avez besoin de trois modules différents :

- Un module Animaux pour un sous-menu avec des éléments de menu sur les Animaux, les Chats et les Chiens.
- Un module Chats pour un sous-menu avec des éléments de menu sur les races de chats.
- Un module Chiens pour un sous-menu avec des éléments de menu sur les races de chiens.

## Module de sous-menu Animaux

Depuis le menu Administrateur :

- Sélectionnez **Contenu** → **Modules du site** → **+** ou sélectionnez `Nouveau` depuis la liste des Modules (Site).
- Sélectionnez le module **Menu**.
- Dans le formulaire d'édition des Modules : Menu, saisissez les données suivantes :
  - Titre : Animaux
  - Sélectionner le menu : Animaux
  - Élément de base : Animaux (c'est l'élément de menu parent)
  - Niveau de départ : 1
  - Niveau de fin : 2 (cela limite les éléments aux éléments de menu sur Chats et Chiens)
  - Position : sidebar-gauche (ou à l'endroit qui vous convient)

![module sous-menus animaux](../../../en/images/menus/submenus-animals-module.png)

### Attribution du menu Animaux

Les sous-menus sont généralement affichés uniquement sur les pages où ils sont pertinents, dans ce cas sur seulement trois pages. Depuis l'onglet Attribution de menu :

- Définissez le champ Affectation du module sur `Uniquement sur les pages sélectionnées`. Cela révèle une liste hiérarchique de tous les éléments dans tous les menus.
- Cochez les cases contre Animaux, Chats et Chiens.
- Cochez les cases contre les races de chats et de chiens. Sinon, le sous-menu Animaux disparaîtra sur les pages concernant les races.
- Assurez-vous qu'aucune autre case n'est cochée.
- Enregistrez et Fermez

![attribution du menu module sous-menus animaux](../../../en/images/menus/submenus-animals-module-menu-assignment.png)

## Module de sous-menu pour les chats

C'est très similaire :

- Sélectionnez **Contenu** → **Modules du site** → **+** ou sélectionnez `Nouveau` dans la
  liste des modules (Site).
- Sélectionnez le module **Menu**.
- Dans le formulaire d'édition Modules : Menu, entrez les données suivantes :
  - Titre : Chats
  - Sélectionner Menu : Animaux
  - Élément de base : Chats (il s'agit de l'élément parent du menu)
  - Niveau de début : 3
  - Niveau de fin : Tous
  - Position : sidebar-left (ou où cela convient)

### Assignation du menu des chats

Depuis l'assignation du menu

- Réglez le champ d'assignation du module sur `Uniquement sur les pages sélectionnées`. Cela
  révèle une liste hiérarchique de tous les éléments dans tous les menus.
- Cochez les cases pour Chats, Burmese et Bleu Russe. Assurez-vous qu'aucune
  autre case n'est cochée.
- Enregistrez & Fermez

## Module du sous-menu des chiens

Encore plus de la même chose ...

## Alias de l'Élément de Menu

Tout va bien jusqu'ici ! Mais il n'y a pas de lien vers la page des Animaux depuis le Menu Principal ou l'un des autres menus du site. La manière simple de corriger cela est d'utiliser un Alias d'Élément de Menu. Pour cet exemple, une entrée est faite dans le menu en haut de la page, intitulé Menu Principal Blog. Depuis le menu Administrateur :

- Sélectionnez **Menus** → **Menu Principal Blog** (ou celui de votre menu préféré du site).
- Sélectionnez le bouton `Nouveau` dans la barre d'outils.
- Remplissez le formulaire Éditer Élément de Menu :
  - Titre : Animaux
  - Alias : créatures - il y a déjà un élément de menu nommé Animaux, vous devez donc utiliser un alias différent.
  - Type d'Élément de Menu : Alias d'Élément de Menu
  - Élément de Menu : Animaux - sélectionné dans la liste des éléments de menu existants.

![sous-menus alias animaux](../../../en/images/menus/submenus-animals-alias.png)

- Enregistrer
- Tri - après l'enregistrement, l'ordre peut être modifié. Dans cet exemple, il est placé en premier.

## Vérifier le Résultat

Consultez les pages sur votre site. Dans cet exemple, la plupart des pages ne montreront pas les sous-menus sur la position gauche. Le lien "Animaux" dans le menu supérieur ouvrira la page des animaux à partir de laquelle il est possible de naviguer vers les pages "Chats" ou "Chiens" :

![objectifs sous-menus animaux chiens](../../../en/images/menus/submenus-objectives-animals-dogs.png)


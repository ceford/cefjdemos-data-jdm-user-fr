<!-- Filename: J4.x:Adding_a_New_Article / Display title: Ajouter un nouvel article -->

Joomla!  4.0 <span id="main-portal-heading">**Didacticiel**
Ajouter un nouvel article</span>

## Introduction

Ce didacticiel fait partie d'une série sur le travail avec les articles
de Joomla !

Elle couvre les méthodes permettant d'ajouter un nouvel article après
s'être connecté au tableau de bord de l'administrateur et se base sur
une installation standard de Joomla utilisant l'éditeur de contenu par
défaut.

Pour plus d'informations sur les différents éditeurs disponibles dans
Joomla, lisez :  Créateurs de
contenu.

Avant de commencer, outre le contenu, si vous en utilisez, vous devrez
savoir quelle catégorie et quels tags vous allez attribuer à l'article.

- Connectez-vous au tableau de bord de l'administrateur. Plus
  d'informations à ce sujet : [Se connecter ou se déconnecter du tableau
  de bord de
  l'administrateur](https://docs.joomla.org/J4.x:Logging_in_to_Joomla "Special:MyLanguage/J4.x:Logging in to Joomla").

## Par où commencer ?

### Directement à partir du tableau de bord d'accueil

<img
src="https://docs.joomla.org/images/thumb/4/4e/J4x_add_article_at_home_dashboard-en.png/800px-J4x_add_article_at_home_dashboard-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/4/4e/J4x_add_article_at_home_dashboard-en.png 1.5x"
data-file-width="1000" data-file-height="254" width="800" height="203"
alt="J4x add article at home dashboard-en.png" />

Selon que votre tableau de bord d'accueil a été personnalisé après
l'installation, vous aurez une ou deux options pour générer un nouvel
article :

1.  Dans le menu latéral, cliquez sur le lien **Contenu**, puis dans le
    menu déroulant, cliquez sur le symbole **plus (+)** à droite du lien
    Articles.
2.  S'il est affiché, dans le panneau de site du tableau de bord
    d'accueil, cliquez sur le symbole **plus (+)** à droite de l'icône
    Articles.

### Via le gestionnaire d'articles

<img
src="https://docs.joomla.org/images/thumb/2/24/J4x_home_dashboard_add_article_en.png/800px-J4x_home_dashboard_add_article_en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/2/24/J4x_home_dashboard_add_article_en.png 1.5x"
data-file-width="1000" data-file-height="147" width="800" height="118"
alt="J4x home dashboard add article en.png" />

L'une ou l'autre de ces options ouvrira une page : **Articles :
Nouveau** qui est prête à être saisie.

## Préparation de l'article

<img
src="https://docs.joomla.org/images/thumb/0/05/J4x_add_article_basic_en.png/800px-J4x_add_article_basic_en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/0/05/J4x_add_article_basic_en.png 1.5x"
data-file-width="1000" data-file-height="341" width="800" height="273"
alt="J4x add article basic en.png" />

Lorsqu'un nouvel article est généré, il s'ouvre sur un panneau à onglets
avec l'onglet **Contenu** sélectionné. Il est possible d'enregistrer un
nouvel article avec seulement deux éléments d'information requis :

1.  Saisissez un titre dans le champ *Titre*. Ce titre est utilisé
    partout où le titre de l'article est affiché. (**Obligatoire**) Le
    champ *Alias* à côté du champ titre n'est pas un champ obligatoire
    car s'il est laissé vide, Joomla créera l'alias lorsque l'article
    sera enregistré. L'alias est utilisé pour faire référence à
    l'article et est important pour les [Caractéristiques des adresses
    URLs adaptées aux moteurs de
    recherche](https://docs.joomla.org/Search_Engine_Friendly_URLs "Special:MyLanguage/Search Engine Friendly URLs").
    L'alias peut également être utilisé par d'autres fonctionnalités du
    site, comme les plugins et les modules, pour trouver l'article.
2.  Choisissez une **Catégorie**. Voir Paramètres des articles
    ci-dessous pour plus d'informations.
3.  Bien que cela ne soit pas strictement nécessaire pour ajouter et
    sauvegarder un article, saisissez votre contenu en utilisant
    l'éditeur.

### Paramètres de l'article

Les autres onglets situés au-dessus de l'éditeur de contenu comprennent
plusieurs options ou paramètres pour l'article. Il est possible que vous
ne voyiez pas tous les onglets suivants, car l'administrateur du site
peut en masquer certains afin de préserver la cohérence de la
présentation des articles sur l'ensemble du site. Vous pouvez également
voir des onglets supplémentaires pour les *Champs personnalisés* s'ils
ont été configurés.

1.  La fonction *Images et liens* vous permet de définir une image
    d'introduction et une image épinglée et/ou des liens qui
    apparaîtront à des positions prédéfinies. Ceci peut être utilisé si
    votre article sera affiché dans une catégorie de blog.
2.  Les *Options* vous permettent de spécifier la mise en page de
    l'article et les informations associées telles que le titre, la
    catégorie, les balises, les détails de publication, etc. Ces
    informations sont normalement définies de manière globale mais
    peuvent être spécifiques à un article grâce à ces options.
3.  La rubrique *Publication* vous permet de définir des dates et des
    heures de publication pour programmer la publication d'un article.
    Par défaut, lorsqu'un article est enregistré, il est publié
    immédiatement. Vous pouvez également définir les métadonnées de
    l'article.
4.  La fonction *Configurer l'écran d'édition* permet d'afficher ou de
    masquer les paramètres de l'article.
5.  *Permissions* montre les permissions pour chaque groupe
    d'utilisateurs qui contrôlent ce qui peut ou ne peut pas être fait.

### Paramètres des articles

Outre le contenu, un article comporte des paramètres permettant de gérer
sa publication, la manière dont il sera affiché et les personnes qui
pourront le voir une fois publié. Dans de nombreux cas, certains de ces
paramètres seront laissés à leur valeur par défaut :

<img
src="https://docs.joomla.org/images/thumb/b/bc/J4x_add_article_info_right_en.png/300px-J4x_add_article_info_right_en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/b/bc/J4x_add_article_info_right_en.png 1.5x"
data-file-width="392" data-file-height="629" width="300" height="481"
alt="J4x add article info right en.png" />

1.  Sélectionnez le *Statut* : Publié, Non publié, Archivé, ou Mis à la
    Corbeille - Par défaut c'est *Publié*.
2.  Sélectionnez une **catégorie** en utilisant le menu déroulant -
    c'est un champ **obligatoire**. Notez que bien qu'il soit
    obligatoire, si vous ne le définissez pas, l'article sera tout de
    même sauvegardé mais sera défini dans la catégorie par défaut de
    Joomla, à savoir *non catégorisé*. Vous pouvez ajouter une nouvelle
    catégorie dans ce champ en la saisissant et en appuyant sur la
    touche "Entrée".
3.  Activez le paramètre **épinglé** sur off, pour afficher ou non
    l'article sur la page d'accueil.
4.  Sélectionnez le niveau d'accès pour l'article : Public, Enregistré,
    Super utilisateurs, etc.
5.  Sélectionnez un ou plusieurs **Tags** pour votre article. Commencez
    à saisir pour trouver et sélectionner des balises prédéfinies ou
    vous pouvez en ajouter une nouvelle en la tapant et en **appuyant
    sur la touche entrée**.
6.  Vous pouvez ajouter une **Note** qui sera visible dans le
    gestionnaire d'articles.
7.  Vous pouvez également ajouter une **Note de version** qui apparaîtra
    dans l'historique des versions de l'article.

## Saving the Article

Une fois que vous avez ajouté les informations et le contenu requis,
vous pouvez enregistrer l'article.

Il existe plusieurs façons de procéder, en fonction de ce que vous
souhaitez faire ensuite dans Joomla.

Pour sauvegarder l'article, vous pouvez choisir de *Sauvegarder*,
*Sauvegarder et fermer*, *Sauvegarder dans le menu* ou Sauvegarder &
Nouveau comme suit :

<img
src="https://docs.joomla.org/images/thumb/1/1b/J4x_add_article_saving_en.png/300px-J4x_add_article_saving_en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/thumb/1/1b/J4x_add_article_saving_en.png/450px-J4x_add_article_saving_en.png 1.5x, https://docs.joomla.org/images/1/1b/J4x_add_article_saving_en.png 2x"
data-file-width="500" data-file-height="234" width="300" height="140"
alt="J4x add article saving en.png" />

1.  Cliquez sur le bouton *Enregistrer* de la barre d'outils pour
    sauvegarder vos modifications. L'article restera ouvert. Il est bon
    de sauvegarder régulièrement votre travail sur les articles plus
    longs.
2.  Cliquez sur le bouton **Enregistrer et fermer** de la barre d'outils
    pour enregistrer l'article et accéder à la liste des articles. Le
    bouton Sauvegarder et fermer comporte deux autres options
    déroulantes :
    1.  Cliquez sur le bouton **Enregistrer dans le menu** de la barre
        d'outils pour ajouter l'article à un menu en ouvrant une page
        **Menus : Nouvel article**.
    2.  Cliquez sur le bouton de la barre d'outils **Sauvegarder &
        Nouveau' *pour sauvegarder l'article et ouvrir une page***
        *Articles : Nouveau*. Cette option permet de gagner du temps
        lors de l'ajout de plusieurs articles.

Un message système indiquera que l'article a été sauvegardé avec succès.

#### Erreurs lors de la tentative d'enregistrement:

- Si vous n'avez pas rempli les champs obligatoires, un message d'erreur
  rouge apparaîtra, indiquant les informations manquantes que vous devez
  ajouter.
- Vous verrez un message d'erreur si l'article a un alias qui existe
  déjà. Vous pouvez contourner ce problème en modifiant le champ de
  l'alias.

## Astuces

- Si vous n'êtes pas le super utilisateur ou l'administrateur, prenez le
  temps de comprendre comment le site Web est configuré. Ce n'est pas
  parce que vous avez enregistré un article qu'il est visible sur le
  site Web. Si des pages de blog de catégorie sont utilisées,
  l'attribution de la catégorie correcte affichera l'article. Sinon, un
  article doit être affecté à un élément de menu. Vous pouvez le faire
  dans l'article ou via **Menus** puis **Gérer**.
- Essayez de garder des titres d'articles courts et spécifiques.
- Bien que cela soit possible, si plusieurs utilisateurs ajoutent des
  articles sur le site, évitez de créer de nouvelles catégories et de
  nouveaux tags dans les articles. Les erreurs d'orthographe et les
  différences peuvent facilement empêcher les articles de s'afficher là
  où ils étaient prévus. La création de catégories et d'étiquettes dans
  leur page de liste respective assure la cohérence du site Web.
- Si le besoin s'en fait sentir, utilisez les notes d'articles. Elles
  peuvent être très utiles, surtout lorsque plusieurs personnes ajoutent
  des articles.
- Où que vous soyez dans Joomla, vous pouvez ajouter un article sans
  aller dans le tableau de bord d'accueil - utilisez le menu latéral de
  Joomla.

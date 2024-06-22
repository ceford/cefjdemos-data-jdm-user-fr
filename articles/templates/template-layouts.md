<!-- Filename: J4.x:Template_Layouts / Display title: Mises en page de template -->

## Mises en page de template

En Joomla!, chaque extension qui génère une sortie HTML place le code de sortie dans un fichier de template au sein de la structure de fichiers de l'extension, souvent dans un dossier nommé tmpl. Voici quelques exemples :

* /modules/mod_login/tmpl/default.php
* /modules/mod_login/tmpl/default_logout.php
* /components/com_content/tmpl/article/default.php
* /plugins/content/vote/tmpl/vote.php

### Substitutions de template

Dans une substitution de template, un fichier portant le même nom est créé au sein de la structure de fichiers du template et est utilisé à la place du fichier dans la structure de fichiers de l'extension. Exemples correspondants :

* /templates/cassiopeia/html/mod_login/default.php
* /templates/cassiopeia/html/mod_login/default_logout.php
* /templates/cassiopeia/html/com_content/article/default.php
* /templates/cassiopeia/html/plg_content_vote/vote.php

Cela vous permet de personnaliser la sortie pour l'adapter à vos besoins. Cependant, vous n'avez pas la possibilité de choisir d'utiliser ou non votre substitution. Elle est toujours utilisée.

### Mises en page de template

Dans une mise en page de template, vous créez un fichier avec un nom différent de l'original mais dans le même dossier de template. Le nouveau nom ne doit pas contenir de caractère de soulignement. Vous créez également tout fichier qui partage la première partie du nom d'origine. Un exemple

    /templates/cassiopeia/html/mod_login/expires.php
    /templates/cassiopeia/html/mod_login/expires_logout.php

Il devient alors possible de choisir d'utiliser la mise en page par défaut d'origine ou la mise en page alternative. Le choix se fait dans le formulaire d'édition du module ou du composant (onglet Avancé pour les modules, onglet Options pour les articles). Notez que toutes les extensions ne permettent pas les substitutions ni les mises en page alternatives.

**Attention :** les plugins ne fournissent pas de mécanisme pour sélectionner des mises en page alternatives.

## Mises en page alternatives des modules

Créer une mise en page alternative pour un module est similaire à créer une substitution de template pour un module. Dans les deux cas, vous créez un dossier appelé templates/<votre modèle>/html/<nom du module>. Par exemple, le dossier pour une substitution ou une mise en page alternative du module "mod_login" pour le template Cassiopeia serait templates/cassiopeia/html/mod_login/.

Il existe deux différences importantes entre une substitution de template et une mise en page alternative. La première concerne le nom du fichier. Pour la substitution de template, vous nommeriez le fichier default.php pour correspondre au nom de fichier principal. Pour une mise en page alternative, vous utilisez un nom différent. La seule règle est que **le nom du fichier ne doit contenir aucun caractère de soulignement**.

La deuxième différence importante est que, contrairement aux fichiers de substitution de template qui sont utilisés automatiquement chaque fois que le module est affiché en utilisant le template avec la substitution, un fichier de mise en page alternative n'est utilisé que si vous le sélectionnez comme paramètre dans les réglages du module.

### Un exemple pratique - mod_login

* Allez sur **Système → Templates de site → Détails et fichiers de Cassiopeia**
* Sélectionnez l'onglet **Créer des substitutions**.
* Dans la liste des Modules, sélectionnez l'élément **mod_login**.
* Dans l'onglet Éditeur, sélectionnez **html → mod_login** pour voir vos nouvelles copies des templates de sortie de mod_login.
* Renommez **default.php** en quelque chose d'autre sans soulignement, par exemple expires.php.
* Renommez **default_logout.php** en **expires_logout.php**.

Vous avez maintenant deux fichiers avec exactement le même contenu que les originaux. Modifiez le contenu de expires_logout.php pour ajouter un message informant l'utilisateur de l'heure à laquelle la session expirera après chaque chargement de page.

À la ligne 16, juste en dessous des déclarations d'utilisation existantes, ajoutez ce qui suit :
```
    use Joomla\CMS\Factory;

    date_default_timezone_set('Europe/London');
    $config = Factory::getContainer()->get('config');
    $lifetime = $config->get('lifetime', 0);
    $time = time() + $lifetime * 60;
    $endTime = date('H:i:s', $time); // time() returns a time in seconds already
```
Et à la ligne 36, immédiatement après la ligne contenant une instruction endif, ajoutez ce code :

```html
<p class="text-center">
Your session will expire at <br><?php echo $endTime; ?>
</p>
```

Fermez les fichiers de Cassiopeia. Sélectionnez **Contenu → Modules du site** et ouvrez le module de connexion. Dans l'onglet Avancé, sous l'élément de mise en page, vous constaterez que vous avez le choix entre **-- Depuis le module -- / Par défaut** et **-- Depuis le template de Cassiopeia -- / expires**.

<img
src="https://docs.joomla.org/images/e/ee/J4x-alternative-layouts-example-en.png"
class="thumbborder" decoding="async" data-file-width="742"
data-file-height="546" width="742" height="546"
alt="screenshot of modules login form showing alternative layouts" />

Une façon dont vous pourriez utiliser cette fonctionnalité est d'avoir deux formulaires de connexion, l'un avec un accès public et l'autre avec un accès Super Utilisateurs. Dans ce dernier, sélectionnez l'option **expires** et seuls les Super Utilisateurs verront le rappel de l'heure d'expiration de la session.

Il est important de comprendre que si spécifié dans l'écran des paramètres du module, un fichier de mise en page alternative pour un module sera utilisé pour ce module indépendamment du template utilisé pour afficher la page où le module est affiché. Il incombe donc à l'administrateur de s'assurer que le fichier de mise en page fonctionnera comme souhaité dans tous les templates où ce module peut être affiché.

### Les traductions

Vous pouvez traduire le nom de fichier en utilisant les Substitutions de Langue. Essayez la procédure suivante :

* Sélectionnez **Système → Gérer le panneau → Substitutions de langue**.
* Sélectionnez votre langue et l'emplacement de l'administrateur.
* Sélectionnez le bouton **Nouveau** et remplissez le formulaire. Dans cet exemple, la clé de langue est **TPL_CASSIOPEIA_MOD_LOGIN_LAYOUT_EXPIRES** et le texte pourrait être **Connexion / Déconnexion avec heure d'expiration**
* Enregistrez et fermez, puis revenez au formulaire du module de connexion.

<img
src="https://docs.joomla.org/images/3/32/J4x-alternative-layouts-language-override-form-en.png"
class="thumbborder" decoding="async" data-file-width="1000"
data-file-height="508" width="1000" height="508"
alt="screenshot of languages edit override form" />

Le champ de sélection de la mise en page du module avec **expires** traduit :

<img
src="https://docs.joomla.org/images/c/c3/J4x-alternative-layouts-example-translated-en.png"
decoding="async" data-file-width="312" data-file-height="98" width="312"
height="98" alt="small screenshot of alternative layouts example" />

## Mises en page alternatives des composants

Les mises en page alternatives des composants fonctionnent de manière similaire aux mises en page des modules. Un fichier est placé dans le même dossier où vous placeriez un fichier de substitution de template . Par exemple, pour créer une mise en page alternative pour un article pour le template "cassiopeia", vous placeriez un fichier dans le dossier `templates/cassiopeia/html/com_content/article/`. Comme pour les mises en page des modules, le fichier ne doit pas avoir le même nom que le fichier principal et ne doit pas contenir de caractères de soulignement dans le nom. De plus, il ne doit pas y avoir de fichier XML du même nom dans ce dossier. (Nous discuterons des fichiers XML ci-dessous dans les mises en page alternatives des liens de menu.)

Vous pouvez définir une valeur globale pour les mises en page des composants dans la fenêtre Options du composant. Par exemple, dans la fenêtre Options de l'article, il existe un paramètre `Choisir une mise en page` comme illustré ci-dessous :

<img
src="https://docs.joomla.org/images/thumb/7/7a/J4x-article-global-alternative-layouts-en.png/800px-J4x-article-global-alternative-layouts-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/7/7a/J4x-article-global-alternative-layouts-en.png 1.5x"
data-file-width="1000" data-file-height="508" width="800" height="406"
alt="screenshot of articles options form with alternative layouts list" />

Tout comme les mises en page des modules, les mises en page des composants sont affichées comme des options de paramètres dans l'écran d'édition individuel du composant. Par exemple, pour un article, le paramètre s'affiche dans l'onglet Options de modification des articles, comme illustré ci-dessous.

<img
src="https://docs.joomla.org/images/thumb/b/b0/J4x-article-alternative-layout-en.png/800px-J4x-article-alternative-layout-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/b/b0/J4x-article-alternative-layout-en.png 1.5x"
data-file-width="1000" data-file-height="507" width="800" height="406"
alt="screenshot of article edit form showing alternative layouts list" />

Comme pour les autres paramètres, le réglage Utiliser le paramètre global utilisera le paramètre de la fenêtre Paramètres. Le réglage Par défaut du composant utilisera la mise en page par défaut du composant. Les mises en page alternatives que vous avez créées pour différents modèles sont affichées sous chaque en-tête de template.

Les noms de fichier peuvent être traduits. La ligne ci-dessous :
```
    TPL_CASSIOPEIA_COM_CONTENT_ARTICLE_LAYOUT_MYLAYOUT="Title Only No XML"
```
traduira un fichier appelé "mylayout.php" en "Titre uniquement sans XML".

Vous pouvez avoir plus d'un fichier pour une disposition. Le fichier initial doit être nommé sans underscores et tout fichier supplémentaire doit avoir des underscores.

Les mises en page alternatives des composants peuvent être utilisées avec les articles, les contacts ou les flux d'actualités.

Les mise en page alternatives des composants ne sont utilisées que lorsque deux conditions sont remplies : (1) elles sont spécifiées dans les paramètres du composant ; et (2) il n'y a pas de lien de menu pour ce composant spécifique. Par exemple, si vous avez un ou plusieurs liens de menu de type "Article unique" configurés pour un article donné, alors la mise en page alternative pour cet article ne sera pas utilisée. À la place, la mise en page spécifiée dans le lien de menu sera utilisée. Cela est conforme à la façon générale dont fonctionnent les paramètres du composant, où le plus spécifique (dans ce cas, un lien de menu d'article unique) remplace le moins spécifique (dans ce cas, les paramètres de l'article).

## Mises en page alternatives des catégories

Les mises en page alternatives des catégories fonctionnent comme les mises en page des composants. Les règles pour spécifier les fichiers de mise en page sont les mêmes. La seule différence est que le dossier est le dossier de la catégorie, et non pas le dossier du composant. Par exemple, une mise en page alternative de catégorie de contact pour Cassiopeia irait dans le dossier `templates/cassiopeia/html/com_contact/category`.

Vous pouvez définir les mises en page de catégorie de manière globale, dans l'écran paramètres de chaque composant. Voici un exemple de la fenêtre paramètres / Catégorie des Contacts :

<img
src="https://docs.joomla.org/images/thumb/e/ea/J4x-contact-component-options-category-alternative-layout-en.png/800px-J4x-contact-component-options-category-alternative-layout-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/e/ea/J4x-contact-component-options-category-alternative-layout-en.png 1.5x"
data-file-width="1000" data-file-height="385" width="800" height="308"
alt="screenshot of contacts component options form showing alternative layouts" />

Les mises en page alternatives des catégories apparaissent lorsque vous ajoutez ou modifiez une catégorie dans le formulaire Options / Catégorie de l'édition du composant, comme illustré ci-dessous.

<img
src="https://docs.joomla.org/images/thumb/b/b0/J4x-category-options-alternative-layout-en.png/800px-J4x-category-options-alternative-layout-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/b/b0/J4x-category-options-alternative-layout-en.png 1.5x"
data-file-width="1000" data-file-height="494" width="800" height="395"
alt="screenshot of contacts edit category form shwoing alternative layouts" />

Les mises en page alternatives des catégories peuvent être utilisées pour les articles, les bannières, les contacts et les flux d'actualités.

Tout comme les mises en page des composants, une disposition de catégorie ne sera utilisée que si :

1. elle est sélectionnée dans les paramètres globaux ou de catégorie.
22. il n'y a pas de lien de de menu spécifique pour la catégorie.

Si un lien de menu est configuré pour une catégorie spécifique, la mise en page sélectionnée dans le menu sera utilisée à la place de la mise en page alternative de la catégorie.

## Blog et Liste de catégories d'articles

Pour les articles, il existe deux mises en page de catégorie de base disponibles : Blog et Liste. Chacune de ces dispositions apparaît dans l'onglet Catégorie du formulaire Options des Articles sous le titre "Depuis le composant". Les mises en page alternatives apparaissent également dans la liste, permettant de sélectionner la mise en page de catégorie par défaut, qu'il s'agisse de Blog, de Liste ou de mises en page alternatives de templates, soit globalement, soit lors de la modification d'une catégorie d'article individuelle.

<img
src="https://docs.joomla.org/images/thumb/3/3c/J4x-articles-options-category-alternative-layout-en.png/800px-J4x-articles-options-category-alternative-layout-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/3/3c/J4x-articles-options-category-alternative-layout-en.png 1.5x"
data-file-width="1000" data-file-height="425" width="800" height="340"
alt="screenshot of articles options category showing alternative layouts" />

Cela signifie que, comme pour d'autres options de mise en page, vous pouvez contrôler si les liens de catégorie d'article utilisent les mises en page de blog ou de liste. Il est important de comprendre que, comme pour d'autres paramètres de mise en page, cette option ne prendra effet que lorsqu'il n'y a pas de lien de menu à catégorie unique pour la catégorie.

## Liens de menu alternatifs

Les liens de menu alternatifs ont une différence importante avec les autres. Pour créer une disposition alternative de lien de menu, vous devez inclure un fichier XML dont le nom correspond au fichier de disposition initial. Par exemple, pour créer un lien de menu alternatif appelé "monarticle" pour un article dans le template cassiopeia, vous créeriez deux fichiers dans le dossier `templates/cassiopeia/html/com_content/article` appelés monarticle.php et monarticle.xml. Si vous vouliez inclure d'autres fichiers de mises en page, vous ajouteriez ces fichiers avec des underscores (tirets bas) dans les noms de fichier.

Le fichier XML utilise le même format que les fichiers XML de lien de menu de base. Cela vous permet non seulement de créer une mise en page personnalisée pour ce lien de menu, mais vous permet également de créer des paramètres personnalisés. Par exemple, vous pourriez masquer certains paramètres ou ajouter de nouveaux paramètres.

Les liens de menu alternatifs apparaissent lorsque vous sélectionnez un type de liens de menu dans le Gestionnaire de menu, comme illustré ci-dessous.

<img
src="https://docs.joomla.org/images/thumb/e/e3/J4x-template-layouts-menu-blog-alternate-layout-en.png/800px-J4x-template-layouts-menu-blog-alternate-layout-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/e/e3/J4x-template-layouts-menu-blog-alternate-layout-en.png 1.5x"
data-file-width="1000" data-file-height="508" width="800" height="406"
alt="screenshot of menu item selection list" />

Les liens de menu alternatifs sont utilisés et fonctionnent de la même manière que les liens de menu standard. Étant donné qu'ils sont déjà basés sur des mises en page personnalisées, les substitutions de templates ne s'appliquent pas aux liens de menu alternatifs.

Comme indiqué ci-dessus, les mises en page des liens de menu ont la priorité sur les mises en page alternatives des composants ou des catégories.

La traduction des liens de menu alternatifs est réalisée avec les balises suivantes dans les fichiers XML. Le format est `"TPL_"<template name>_<component>_<view>_<menu item name>_<tag type>`. Par exemple, ces lignes ci-dessous traduiront le titre, l'option et la description pour un lien de menu alternatif appelé "catmenuitem".
```
    TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_TITLE="cassiopeia Custom Category Layout"
    TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_OPTION="cassiopeia Custom"
    TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_DESC="Description for cassiopeia custom category layout."
```
Ces chaînes doivent être ajoutées à `administrator/language/overrides/en-GB.override.ini`, mais vous pouvez également utiliser le formulaire de Substitutions de Langue décrit ci-dessus.

Le catmenuitem.xml devrait commencer par :

```xml
<?xml version="1.0" encoding="utf-8"?>
<metadata>
   <layout title="TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_TITLE" option="TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_OPTION">
      <help
         key = "JHELP_MENUS_MENU_ITEM_ARTICLE_SINGLE_ARTICLE"
      />
      <message>
         <![CDATA[TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_DESC]]>
      </message>
   </layout>
```

## Contrôler le template pour les liens de menu alternatifs

Comme discuté précédemment, la présence d'un fichier XML rend une disposition alternative un lien de menu. Le format du fichier XML est le même que celui des fichiers XML d'élément de menu de base. Avec ce fichier XML, vous pouvez ajouter les paramètres que vous souhaitez inclure pour ce lien de menu. Ils peuvent être les mêmes que pour l'un des liens de menu de base, ou vous pouvez omettre les paramètres de base ou en ajouter de nouveaux. Notez que si vous ajoutez de nouveaux paramètres, ceux-ci peuvent être utilisés dans le fichier de mise en page mais ne seront pas utilisés dans les fichiers de modèle ou de vue de base.

Il est également possible de remplacer les paramètres des paramètres de base. Un exemple de cela est de contrôler quels templates une disposition alternative de liens de menu peut être affichée avec. Dans certains cas, vous voudrez peut-être permettre à un lien de menu personnalisé d'être affiché avec n'importe quel template pour le site. Dans d'autres cas, vous souhaiterez peut-être limiter la mise en page de ce lien de menu à un template spécifique. Dans cette situation, vous ajouteriez simplement le paramètre suivant au fichier XML du lien de menu :

```xml
<fields>
  <field
    name="template_style_id"
    type="templatestyle"
    label="COM_MENUS_ITEM_FIELD_TEMPLATE_LABEL"
    description="COM_MENUS_ITEM_FIELD_TEMPLATE_DESC"
    filter="int"
    template="cassiopeia"
    class="inputbox">
  </field>
 </fields>
 ```

Cela remplacera le paramètre de base template_style_id. En définissant le modèle sur "cassiopeia" dans ce cas, l'utilisateur sera limité à ne sélectionner que les styles de template pour le template "cassiopeia".

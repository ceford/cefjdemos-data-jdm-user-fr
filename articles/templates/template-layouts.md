<!-- Filename: J4.x:Template_Layouts / Display title: Modèles de mise en page -->

## Structures de Fichiers de Gabarit

Dans un **gabarit**, chaque extension qui génère du code html place le code de sortie dans un fichier de gabarit au sein de la structure de fichiers de l'extension, souvent dans un dossier nommé tmpl. Quelques exemples :

- /modules/mod_login/tmpl/default.php
- /modules/mod_login/tmpl/default_logout.php
- /components/com_content/tmpl/article/default.php
- /plugins/content/vote/tmpl/vote.php

Dans un **surcharge de gabarit**, un fichier du même nom est créé au sein de la structure de fichiers du gabarit et est utilisé à la place du fichier dans la structure de fichiers de l'extension. Exemples correspondants :

- /templates/cassiopeia/html/mod_login/default.php
- /templates/cassiopeia/html/mod_login/default_logout.php
- /templates/cassiopeia/html/com_content/article/default.php
- /templates/cassiopeia/html/plg_content_vote/vote.php

Cela vous permet de personnaliser le rendu pour répondre à vos besoins. Cependant, vous n'avez pas l'option de choisir d'utiliser ou non votre surcharge. Elle est toujours utilisée.

Dans une **mise en page alternative de gabarit**, vous créez un fichier avec un nom différent de l'original mais dans le même dossier de gabarit. Le nouveau nom ne doit pas contenir de caractère de soulignement. Vous créez également tout fichier qui partage la première partie du nom original. Un exemple :

- /templates/cassiopeia/html/mod_login/expires.php
- /templates/cassiopeia/html/mod_login/expires_logout.php

Il devient alors possible de choisir d'utiliser la mise en page par défaut originale ou la mise en page alternative. Le choix est fait dans le formulaire d'édition du module ou du composant (onglet Avancé pour les modules, onglet Options pour les Articles). Notez que toutes les extensions ne permettent pas les surcharges ou les mises en page alternatives.

**Attention :** les plugins ne fournissent pas de mécanisme pour sélectionner des mises en page alternatives.

## Dispositions Alternatives de Module

Créer une disposition alternative pour un module est similaire à créer une surcharge de modèle pour un module. Dans les deux cas, vous créez un dossier appelé `templates/.../html/`. Par exemple, le dossier pour une surcharge de modèle "mod_login" ou une disposition alternative pour le modèle cassiopeia serait `templates/cassiopeia/html/mod_login/`.

Il y a deux différences importantes entre une surcharge de modèle et une disposition alternative. La première est le nom du fichier. Pour la surcharge de modèle, vous nommez le fichier `default.php` pour correspondre au nom du fichier central. Pour une disposition alternative, vous utilisez un nom différent. La seule règle est que **le nom du fichier ne doit pas contenir de tirets bas**.

La seconde différence importante est que, contrairement aux fichiers de surcharge de modèle qui sont utilisés automatiquement chaque fois que le module est affiché à l'aide du modèle avec la surcharge, un fichier de disposition alternative n'est utilisé que si vous le sélectionnez comme paramètre dans les paramètres du module.

### Un exemple pratique - mod_login

- Allez dans **Système** → **Templates de Site** → **Détails et Fichiers Cassiopeia**
- Sélectionnez l'onglet **Créer des Surcharges**.
- Dans la liste des Modules, sélectionnez l'élément **mod_login**.
- Dans l'onglet Éditeur, sélectionnez **html** → **mod_login** pour voir vos copies nouvellement créées des modèles de sortie mod_login.
- Renommez **default.php** en quelque chose d'autre sans tiret bas, **expires.php** dans cet exemple.
- Renommez **default_logout.php** en **expires_logout.php**.

Vous avez maintenant deux fichiers avec exactement le même contenu que les originaux. Modifiez le contenu de expires_logout.php pour ajouter un message informant l'utilisateur de l'heure à laquelle la session expirera après chaque chargement de page.

À la ligne 16, juste en dessous des instructions existantes, ajoutez ce qui suit :

```php
use Joomla\CMS\Factory;

date_default_timezone_set('Europe/London');
$config = Factory::getContainer()->get('config');
$lifetime = $config->get('lifetime', 0);
$time = time() + $lifetime * 60;
$endTime = date('H:i:s', $time); // time() retourne un temps en secondes déjà
```

Et à la ligne 36, immédiatement après la ligne contenant une instruction endif, ajoutez ce code :

```html
<p class="text-center">
Votre session expirera à <br><?php echo $endTime; ?>
</p>
```

Fermez les fichiers Cassiopeia. Sélectionnez **Contenu** → **Modules du Site** et ouvrez le module Login. Dans l'onglet Avancé, élément Disposition, vous trouverez que vous avez le choix entre **-- From Module -- / Default** et **-- From cassiopeia Template -- / expires**.

![module de connexion montrant des dispositions alternatives](../../../en/images/templates/layouts-module-login.png)

Une façon d'utiliser cette fonctionnalité est d'avoir deux formulaires de connexion, l'un avec un accès public et l'autre avec un accès aux Super Users. Dans ce dernier, sélectionnez l'option **expires** et uniquement les Super Users verront le rappel du temps d'expiration de la session.

Il est important de comprendre que si spécifié dans l'écran des paramètres du module, un fichier de disposition alternative pour un module sera utilisé pour ce module, quel que soit le modèle utilisé pour afficher la page où le module est affiché. Il est donc de la responsabilité de l'administrateur de s'assurer que le fichier de disposition fonctionnera comme souhaité dans tous les modèles où ce module peut être affiché.

### Traduction

Vous pouvez traduire le nom du fichier en utilisant des Surcharges de Langue. Essayez la procédure suivante :

- Sélectionnez **Système** → **Panneau de Gestion** → **Surcharges de Langue**
- Sélectionnez votre langue et l'emplacement Administrateur.
- Sélectionnez le bouton **Nouveau** et remplissez le formulaire. Dans cet exemple, la clé de langue est **TPL_CASSIOPEIA_MOD_LOGIN_LAYOUT_EXPIRES** et le texte pourrait être **Connexion / Déconnexion avec expiration du temps**
- Enregistrez et fermez et retournez au formulaire du module Login.

![formulaire de modification de surcharge de langues](../../../en/images/templates/layouts-language-override-form.png)

Le champ de sélection de disposition de module avec **expires** traduit :

![formulaire alternatif de sélection des dispositions du module](../../../en/images/templates/layouts-example-translated.png)


## Dispositions Alternatives des Composants

Les dispositions alternatives des composants fonctionnent de manière similaire aux dispositions des modules. Un fichier est placé dans le même dossier où vous placeriez un fichier de remplacement de modèle. Par exemple, pour créer une disposition alternative pour un article pour le modèle "cassiopeia", vous placeriez un fichier dans le dossier `templates/cassiopeia/html/com_content/article/`. Comme pour les dispositions de module, le fichier ne doit pas avoir le même nom que le fichier central et ne doit pas inclure de tirets bas dans le nom. De plus, il ne doit pas y avoir de fichier XML du même nom dans ce dossier. (Nous discuterons des fichiers XML ci-dessous, sous Dispositions Alternatives des Éléments de Menu.)

Vous pouvez définir une valeur globale pour les dispositions de composants dans la fenêtre Options du composant. Par exemple, dans la fenêtre Article : Options, il y a un paramètre *Choisir une Disposition* comme illustré ci-dessous :

![formulaire des options d'articles avec la liste des dispositions alternatives](../../../en/images/templates/layouts-articles-options.png)

Comme pour les dispositions de module, les dispositions de composant sont affichées comme options de paramètre dans l'écran d'édition de chaque composant. Par exemple, pour un article, le paramètre s'affiche dans l'onglet Articles : Modifier les Options, comme illustré ci-dessous.

![formulaire d'édition d'article montrant la liste des dispositions alternatives](../../../en/images/templates/layout-article-edit.png)

Comme pour d'autres paramètres, le paramètre Utiliser Global utilisera le paramètre des Options. Le paramètre Par Défaut du Composant utilisera la disposition par défaut du composant. Les dispositions alternatives que vous avez créées pour différents modèles s'affichent sous chaque en-tête de modèle.

Les noms de fichiers peuvent être traduits. La ligne ci-dessous :
```ini
    TPL_CASSIOPEIA_COM_CONTENT_ARTICLE_LAYOUT_MYLAYOUT="Titre Seulement Pas de XML"
```
traduira un fichier appelé "mylayout.php" par "Titre Seulement Pas de XML".

Vous pouvez avoir plus d'un fichier pour une disposition. Le fichier initial doit être nommé sans tirets bas et tous les fichiers supplémentaires doivent avoir des tirets bas.

Les dispositions alternatives de composants peuvent être utilisées avec des articles, des contacts ou des flux d'actualités.

Les dispositions alternatives de composants ne sont utilisées que lorsque deux conditions sont remplies : (1) elles sont spécifiées dans les paramètres du composant ; et (2) il n'y a pas d'élément de menu pour ce composant spécifique. Par exemple, si vous avez un ou plusieurs éléments de menu de type "Article Seul" configurés pour un article donné, alors la disposition alternative pour cet article ne sera pas utilisée. Au lieu de cela, la disposition spécifiée dans l'élément de menu sera utilisée. Cela est cohérent avec la manière générale dont fonctionnent les paramètres de composants, où le plus spécifique (dans ce cas un élément de menu pour un seul article) remplace le moins spécifique (dans ce cas, les paramètres de l'article).

## Dispositions Alternatives de Catégorie

Les dispositions alternatives de catégorie fonctionnent comme les dispositions de composants. Les règles pour spécifier les fichiers de disposition sont les mêmes. La seule différence est que le dossier est le dossier de la catégorie, et non celui du composant. Par exemple, une disposition alternative de catégorie de contact pour cassiopeia se trouverait dans le dossier `templates/cassiopeia/html/com_contact/category`.

Vous pouvez définir des dispositions de catégorie globalement, dans l'écran Options de chaque composant. Voici un exemple tiré des Contacts : Options / Formulaire de Catégorie :

![formulaire des options du composant contacts montrant des dispositions alternatives](../../../en/images/templates/layouts-contacts-options.png)

Les dispositions alternatives de catégorie apparaissent lorsque vous ajoutez ou modifiez une catégorie dans le formulaire Composant : Modifier une Catégorie / Options comme montré ci-dessous.

![formulaire des options du composant contacts montrant des dispositions alternatives](../../../en/images/templates/layouts-contacts-category-options.png)

Les dispositions alternatives de catégorie peuvent être utilisées pour des articles, des bannières, des contacts et des flux de nouvelles.

Comme pour les dispositions des composants, une disposition de catégorie ne sera utilisée que si :

1. elle est sélectionnée dans les paramètres globaux ou de catégorie.
2. il n’existe pas d’élément de menu spécifiquement pour la catégorie.

S'il existe un élément de menu configuré pour une catégorie spécifique, la disposition sélectionnée dans le menu sera utilisée à la place de la disposition alternative de catégorie.

## Catégorie d'Articles Blog et Liste

Pour les articles, il existe deux mises en page principales pour les catégories disponibles : Blog et Liste. Chacune de ces mises en page apparaît dans le formulaire Options des Articles sous l’onglet Catégorie, sous le titre "Depuis le Composant". Des mises en page alternatives apparaissent également dans la liste, permettant de choisir les mises en page Blog, Liste ou des modèles alternatifs comme mise en page par défaut pour les catégories, soit globalement, soit lors de la modification d'une seule catégorie d'article.

![formulaire d'options du composant contacts montrant les mises en page alternatives](../../../en/images/templates/layouts-articles-options-category.png)

Cela signifie que, comme pour d'autres options de mise en page, vous pouvez contrôler si les liens des catégories d'articles utilisent une mise en page de blog ou de liste. Il est important de comprendre que, comme pour d'autres paramètres de mise en page, cette option ne prendra effet que lorsqu'il n'y a pas d'élément de menu pour une seule catégorie.

## Éléments de Menu Alternatifs

Les éléments de menu alternatifs ont une différence importante avec les autres. Pour créer une mise en page alternative d'un élément de menu, vous devez inclure un fichier XML dont le nom correspond au fichier de mise en page initial. Par exemple, pour créer un élément de menu alternatif appelé "myarticle" pour un article dans le modèle cassiopeia, vous devez créer deux fichiers dans le dossier `templates/cassiopeia/html/com_content/article` appelés `myarticle.php` et `myarticle.xml`. Si vous souhaitez inclure plus de fichiers de mise en page, vous pouvez ajouter ces fichiers avec des underscores dans les noms de fichiers.

Le fichier XML utilise le même format que les fichiers XML des éléments de menu du noyau. Cela vous permet non seulement de créer une mise en page personnalisée pour cet élément de menu, mais aussi de créer des paramètres personnalisés. Par exemple, vous pourriez masquer certains paramètres ou ajouter de nouveaux paramètres.

Les éléments de menu alternatifs apparaissent lorsque vous sélectionnez un type d'élément de menu comme indiqué ci-dessous.

![liste de sélection des éléments de menu](../../../en/images/templates/layouts-menu-blog-menu-creation.png)

Les éléments de menu alternatifs sont utilisés et fonctionnent de la même manière que les éléments de menu standard. Puisqu'ils sont déjà basés sur des mises en page personnalisées, les substitutions de modèle ne s'appliquent pas aux éléments de menu alternatifs.

Comme indiqué ci-dessus, les mises en page des éléments de menu ont la priorité sur les mises en page alternatives des composants ou des catégories.

La traduction des éléments de menu alternatifs se fait avec les balises suivantes dans les fichiers XML. Le format est `"TPL_"<nom du modèle>_<composant>_<vue>_<nom de l'élément de menu>_<type de balise>`. Par exemple, les lignes ci-dessous traduiront le titre, l'option, et la description pour un élément de menu alternatif appelé "catmenuitem".
```
    TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_TITLE="Mise en page personnalisée de catégorie cassiopeia"
    TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_OPTION="cassiopeia Personnalisé"
    TPL_CASSIOPEIA_COM_CONTENT_CATEGORY_VIEW_CATMENUITEM_DESC="Description pour mise en page personnalisée de catégorie cassiopeia."
```
Ces chaînes doivent être ajoutées à `administrator/language/overrides/en-GB.override.ini` mais vous pouvez utiliser le formulaire de Substitutions de Langue décrit ci-dessus.

Le fichier catmenuitem.xml commencerait par :

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

## Contrôler le Modèle pour les Éléments de Menu Alternatifs

Comme discuté ci-dessus, la présence d'un fichier XML transforme une disposition alternative en un élément de menu. Le format du fichier XML est le même que celui des fichiers XML des éléments de menu principaux. Avec ce fichier XML, vous pouvez ajouter les paramètres que vous souhaitez inclure pour cet élément de menu. Ils peuvent être identiques à ceux de l'un des éléments de menu principaux, ou vous pouvez omettre des paramètres principaux ou en ajouter de nouveaux. Notez que si vous ajoutez de nouveaux paramètres, ceux-ci peuvent être utilisés dans le fichier de disposition mais ne seront pas utilisés dans les fichiers de modèle ou de vue principaux.

Il est également possible de remplacer les paramètres pour les paramètres principaux. Un exemple de cela est de contrôler avec quels modèles une disposition alternative d'un élément de menu peut être affichée. Dans certains cas, vous voudrez peut-être permettre qu'un élément de menu personnalisé soit affiché avec n'importe quel modèle du site. Dans d'autres cas, vous souhaiterez peut-être limiter la disposition de cet élément de menu à un modèle spécifique. Dans cette situation, vous ajouteriez simplement le paramètre suivant au fichier XML de l'élément de menu :

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

Cela remplacera le paramètre principal `template_style_id`. En définissant le modèle égal à "cassiopeia" dans ce cas, vous limiterez l'utilisateur à ne sélectionner que les styles de modèle pour le modèle "cassiopeia".

## Informations supplémentaires

- Notions de base du modèle
- Dossiers et fichiers du modèle Cassiopeia
- Personnalisation du modèle Cassiopeia
- Substitutions de modèle
- Dispositions du modèle
- Cassiopeia Template Simplifié - Une étude de cas - un modèle simple basé sur Cassiopeia

*Traduit par openai.com*  


<!-- Filename: J4.x:Articles_and_categories / Display title: Concepts de base -->

## Introduction

Pour commencer avec Joomla, vous devez être conscient de certains des éléments de base : Articles, Catégories, Éléments de menu, Menus et Modules. Ils sont brièvement décrits ici si vous souhaitez vous lancer et créer du contenu.

## Articles

Dans Joomla!, un article est une unité d'information écrite autonome à afficher sur un site web. Il contient normalement du texte et peut contenir des images et d'autres types de contenu. Pour de nombreux sites Joomla!, les articles constituent la majorité des informations présentées.

Il est important de comprendre que le contenu du site est totalement distinct de la mise en forme du site, de son apparence sur la page. Il est donc préférable de considérer les articles comme du contenu pur, indépendant de la présentation. Le même article peut être affiché avec différentes polices, couleurs, en-têtes et arrière-plans, et peut être affiché à différents endroits sur la page, le tout dépendant d'autres paramètres dans le CMS Joomla!.

## Catégories

Imaginez une bibliothèque sans système de classification : les livres sont simplement placés sur les étagères dans l'ordre de leur réception. Ce n'est pas très utile si la bibliothèque possède des millions de livres et que vous recherchez quelque chose sur l'Histoire, le Jardinage ou la Science. Le même type d'argument s'applique aux articles. Si vous avez des dizaines, des centaines ou des milliers d'articles, vous avez vraiment besoin d'une méthode pour les classer afin de pouvoir facilement trouver ce dont vous avez besoin. C'est à cela que servent les catégories.

Une catégorie Joomla! peut contenir à la fois des articles et des catégories dans une structure arborescente. Si une catégorie se trouve dans une autre catégorie, elle est appelée une sous-catégorie de cette catégorie. Les sous-catégories peuvent également avoir d'autres sous-catégories, bien qu'il soit peu probable que vous souhaitiez aller au-delà d'une profondeur de trois ou quatre.

Par exemple, si vos articles traitent de la nature, vous pourriez les classer de la manière suivante :

- Animaux
  - Oiseaux
    - Faucons
    - Pinsons
    - Mouettes
  - Mammifères
    - Singes anthropoïdes
    - Singes
    - Rongeurs
- Plantes
  - Fleurs
    - Marguerites
    - Roses
  - Arbres
    - Chênes
    - Ormes

Dans cet exemple, la catégorie Animaux pourrait contenir des articles sur les animaux en général ainsi que des sous-catégories pour des articles sur différents types d'animaux.

Les catégories vous permettent également de sélectionner les articles que vous souhaitez afficher sur chaque page du site web. Par conséquent, vous voudrez peut-être regrouper dans la même catégorie tous les articles destinés à être sur la même page.

Un article ne peut appartenir qu'à une seule catégorie dans l'arborescence des catégories. Par exemple, vous pourriez avoir une catégorie appelée Plantes et, dans cette catégorie, une sous-catégorie appelée Arbres et une autre appelée Fleurs. Les articles sur les fleurs seraient assignés à la catégorie Fleurs et ceux sur les arbres à la catégorie Arbres. Vous ne pouvez pas avoir un article qui est à la fois dans les catégories Fleurs et Arbres. Si vous avez un article qui concerne les deux, vous le mettriez dans la catégorie Plantes. Dans certaines circonstances, vous pourriez avoir besoin d'un moyen plus flexible pour classifier vos articles. C'est là que les étiquettes deviennent utiles. Elles sont traitées ailleurs.

Les catégories sont également utilisées par d'autres composants, y compris Bannières, Contacts et Flux d'actualités. Ces catégories sont complètement distinctes des catégories d'Articles et sont configurées dans différentes pages de l'administrateur Joomla!. Donc, lorsque vous voyez quelque chose à propos des catégories, cela peut se référer aux catégories d'Articles ou aux catégories de ces autres composants.

## Éléments du menu

De nouveaux articles peuvent ne pas être visibles sur le site web. Ils ont besoin d'éléments de menu pour contrôler leur affichage. Les éléments de menu sont les unités de navigation de base d'un site Joomla!. Après l'arrivée sur une page du site web, la plupart des éléments de menu mènent à d'autres pages du site.

Il existe de nombreux types d'éléments de menu. Le plus simple est l'élément de menu Article Unique, qui mène à une page contenant un seul article. Un autre type d'élément de menu est le Blog de Catégorie. Celui-ci mène à une page qui affiche tous les articles d'une catégorie. Dans les deux cas, l'URL de la page de destination est établie par l'élément de menu. La mise en page (c'est-à-dire la manière dont le contenu est organisé sur la page) de la page de destination est également établie par l'élément de menu. Par exemple, dans le cas du Blog de Catégorie, il peut afficher une introduction à chaque article. Ces introductions sont appelées "dégustations". Et ces dégustations peuvent être affichées dans une ou plusieurs colonnes. Leur ordre peut également être personnalisé. Les articles peuvent apparaître chronologiquement en commençant par le plus récent. Dans ce cas, lorsque vous attribuez un nouvel Article à la Catégorie sélectionnée, il s'affichera automatiquement en première position sur la page.

Une page d'accueil de site est souvent un type d'élément de menu Blog de catégorie ou un type d'élément de menu Articles en vedette.

## Menus

Un menu est un conteneur pour les éléments de menu. Une installation standard de Joomla! crée un menu principal pour vous avec un seul élément de menu intitulé Accueil. Dans de nombreux cas, vous utiliserez un seul menu, mais vous pouvez en avoir plusieurs. Les menus peuvent avoir une structure arborescente avec certains éléments étant parents d'autres.

## Modules

Les modules sont de petites extensions utilisées à des fins spéciales. Pour afficher un Menu sur le site web, vous devez l'assigner à un Module de Menu. Ensuite, vous pouvez spécifier l'emplacement du Menu sur la page (au-dessus, en dessous ou à côté du contenu principal de la page). Un formulaire de connexion est un autre type de module souvent affiché à droite du contenu principal d'une page.

*Traduit par openai.com*


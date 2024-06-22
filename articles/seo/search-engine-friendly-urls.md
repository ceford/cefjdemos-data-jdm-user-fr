<!-- Filename: Search_Engine_Friendly_URLs / Display title: Réécriture des URL en clair (Search Engine Friendly URLs) -->

La **réécriture d'URL en clair (SEF Search Engine Friendly)**, **lisible
par l'utilisateur** ou
<a href="https://en.wikipedia.org/wiki/Clean_URL" class="extiw"
title="wikipedia:Clean URL">URL propres</a> sont des URLs
compréhensibles aussi bien par les utilisateurs que par les moteurs de
recherche car elles expliquent le chemin d'accès de la page vers
laquelle elles pointent. Depuis la version Joomla! 1.5, Joomla! est
capable de créer et d'analyser tout format d'URL, y compris les URL SEF.
Cela ne dépend pas de la réécriture d'URL exécutée par le serveur, de
sorte que cela fonctionne également si Joomla! n'est pas exécuté sur un
serveur Apache utilisant le module mod_rewrite. Les URL SEF répondent à
une certaine forme fixe, mais l'utilisateur peut définir un [court texte
descriptif
(alias)](https://docs.joomla.org/Alias "Special:MyLanguage/Alias") pour
chaque segment de l'URL.

En interne, la partie d'une URL SEF (la partie située après le nom de
domaine) est appelée **route**. La création et le traitement des URLs
SEF sont donc appelés le **routage**, et le code correspondant, un
**routeur**.

Un bon exemple de routage est celui de l'URL de l'article "Bienvenue sur
Joomla!" dans les données d'exemples.

- Si la fonction URL SEF est désactivée, l'URL sera :
  `http://www.exemple.com/index.php?option=com_content&view=article&id=1:bienevnue-sur-joomla&catid=1:latest-news&Itemid=50`
- Si la fonction URL SEF est activée mais que le mod_rewrite est
  désactivé, l'URL sera :
  `http://www.exemple.com/index.php/the-­news/1-­latest­-news/1­-bienvenue-sur-joomla`
- Si la fonction URL SEF et le mod_rewrite sont tous deux activés, l'URL
  sera :
  `http://www.example.com/the-­news/1­-latest-­news/1-­bienvenue-sur-joomla`

La réécriture d'URL en clair peut être activée dans "Configuration"
option **Réécriture d'URL en clair**. Cette option est activée par
défaut depuis Joomla! 1.6. Pour plus d'informations, voir [Activer la
réécriture d'URL en clair
(SEF)](https://docs.joomla.org/Enabling_Search_Engine_Friendly_(SEF)_URLs "Special:MyLanguage/Enabling Search Engine Friendly (SEF) URLs").

## FAQ

### Que signifient les nombres présents dans une URL ?

En comparant l'ancienne et la nouvelle URL, on peut voir des nombres
dans l'ancienne URL :

    http://www.exemple.com/index.php?option=com_content&view=article&id=1:bienvenue-sur-joomla&catid=1:latest-news&Itemid=50

mais également dans la nouvelle URL :

    http://www.exemple.com/the-­news/1­-latest-­news/1-­bienvenue-sur-joomla

Ces nombres sont des paramètres nécessaires à Joomla! afin d'obtenir
l'URL interne et afficher la page que vous souhaitez voir. (Dans ce cas,
le premier numéro correspond à l'ID de la catégorie ; le second à l'ID
de l'article.)

### Il n'y a plus de `index.php` dans l'URL. Puis-je supprimer le fichier ?

Non ! L'URL ne contient peut-être plus le `index.php`, mais en interne
le mod_rewrite va seulement rediriger vers le chemin d'origine sans vous
l'afficher.

### Alias ? Et comment est-il créé ?

Un Alias est répertorié sous le champ Titre dans les Articles,
Catégories, Sections et Eléments de Menu. Joomla! peut vous créer
automatiquement l'alias. Un alias automatique commence par le titre.
Toutes les lettres majuscules sont changées en minuscule. Les espaces et
caractères spéciaux n'étant pas autorisés dans une URL, ils sont
remplacés par des tirets.

### Je veux spécifier mon propre Alias.

Si vous n'aimez pas l'alias généré par Joomla!, vous pouvez indiquer la
valeur de votre choix dans le champ Alias. Beaucoup pense que
l'utilisation de bons mots clés dans les URL aident à l’optimisation
pour les moteurs de recherche. Vous pouvez ajouter ces mots clés dans
votre titre, ainsi Joomla! les intègrera à votre alias ou vous pouvez le
créer vous-même.

### Comment une URL utilise-t-elle un Alias ?

Pour un élément de menu, Joomla! utilise l'alias comme URL de cette
partie. Supposons que vous activiez les deux premières options du
panneau de paramètres SEO et que vous créiez un élément de menu nommé
Produits. Votre URL serait alors : exemple.com/produits.

Joomla! utilise également des valeurs clés primaires de données dans
l'URL pour aider le routeur à accéder à la bonne page. Pour reprendre
l'exemple précédent, si votre élément de menu 'produits' était un
Article / Catégorie de Blog, le lien pour le Titre de l'article et / ou
le lien En savoir plus aurait trois parties:

- L'URL de l'élément de menu - exemple.com/produits ;
- Auquel vient s'ajouter la clé primaire de la Catégorie et l'alias de
  la Catégorie - 32-fruit ;
- Auquel vient s'ajouter la clé primaire de l'Article et l'alias de
  l'Article - 1-pomme ;

L'URL complète est donc : `http://exemple.com/produits/32-fruit/1-pomme`

### Comment puis-je me débarrasser des nombres dans les URL SEF ?

Les nombres d'une URL SEF sont nécessaires au routeur de Joomla! afin de
savoir comment diriger le trafic du site. Une fois que la logique du
routeur est stabilisée, de simples plugins système tiers peuvent être
développer afin d'augmenter les capacités du router en permettant
davantage de possibilité. Les nombres seront enclin à disparaître des
URL.

## Formats de Route et Mécanisme de Routage

*Cette section décrit le mécanisme de routage natif du Core Joomla!. Les
extensions de routage peuvent modifier la façon dont les routes sont
créées dans notre système.*

### Formats de Route

Afin de décrire plus en détail le mécanisme de routage de Joomla!, il
nous faut tout d'abord expliquer ce que nous entendons par **route**.
Supposons que Joomla! ait été installé sur
`http://exemple.com/sites/first/`. Le chemin d'installation est
généralement considéré comme l' **URL de base**. Un exemple possible
d'URL est `http://exemple.com/sites/first/produits/32-fruit/1-pomme`. La
première partie de cette URL correspond à l'URL de base mentionnée
ci-dessus, ni Joomla! ni aucun composant de routeur ne peut créer une
première partie d'URL différente. La seconde partie,
`produits/32-fruit/1-pomme`, constitue une **route**, composée de trois
**segments**.

Le premier segment d'une route correspond, dans le cadre d'URLs
traditionnelles, à l'alias d'un élément de menu. L'URL SEF est
**acheminée** par cet élément de menu. Les autres segments sont
entièrement déterminés par le routeur du composant qui fournit le type
de l'élément de menu. Par exemple, le type d'élément de menu
*Catégorie - Blog* est fourni par le composant de
Contenu,
et donc le routeur de ce composant est responsable de la construction et
de l'analyse des segments restants.

Il est également possible (pour les extensions) de demander au système
de créer une route sans fournir d'élément de menu pour l'acheminer. Dans
ce cas, le système va généralement décider de créer une route spéciale
qui contiendra comme premier segment le terme `component`. Ces routes
sont créées en utilisant un format fixe : le nom du composant (sans le
`com_`) est sélectionné en qualité de second segment et les autres
paramètres éventuels constitueront les autres segments.

### Limites

Il est important de souligner que la création d'un élément de menu est
la *seule* façon pour un utilisateur Joomla! de définir la route qui
conduit à un composant en particulier. Il est toutefois possible de
créer une route sans pour autant l'afficher sur le site (dans un menu).
Une méthode souvent appliquée est de créer un élément de menu dans un
menu qui ne s'affiche nulle part. Un tel menu est généralement appelé un
menu caché.

Le précédent paragraphe implique qu'il n'est pas possible de rendre un
composant responsable du traitement de toutes les routes. Par exemple,
il n'est pas possible de spécifier que l'URL `http://exemple.com/alias`
doit afficher l'élément de Contenu contenant l'alias `alias`, là où
`alias` pourrait être n'importe quel mot. Si cela doit être fait pour un
petit nombre d'articles, des éléments de menu peuvent être créés
manuellement. Sinon, une extension de routage sera nécessaire.

Ce mécanisme de routage n'est donc pas aussi flexible que peuvent
parfois l'exiger les utilisateurs. D'autre part, il a un grand avantage:
il réduit le risque de routes ambiguës (des routes qui pourraient
conduire à deux pages différentes). Le premier segment d'une route étant
toujours un alias d'élément menu, le système sait immédiatement quel
routeur de composant doit être utilisé pour l'analyser.

## Détails d'Implémentation

### Gestion des Routes

*Cette section décrit l'implémentation du routage. Si vous développez
des extensions, consultez  Supporter des URL SEF dans votre
composant.*

Les routes Joomla! sont créées et réglées par la
<a href="https://docs.joomla.org/JRouter" class="new"
title="Special:MyLanguage/JRouter (page does not exist)">classe
JRouter</a>. Cette classe regarde dans la racine du composant actif
(spécifié dans le paramètre `option` de la chaîne de requête) et inclut
le fichier `router.php` dans le répertoire racine de ce composant. Il
appelle ensuite l'une des deux fonctions : l'une pour créer l'URL SEF et
l'autre pour interpréter l'URL SEF.

La classe JRouter est remplacée par le CMS Joomla! dans
`/includes/router.php`. Dans ce fichier, les fonctions de construction
et d'analyse sont remplacées afin de construire et analyser correctement
les URL pour le CMS Joomla!.

Le fichier `router.php` dans chaque composant (par exemple,
`/components/com_content/router.php`) doit contenir les deux fonctions
suivantes :

- ContentBuildRoute - permet de construire l'URL SEF
  - Paramètres
    - \$query - il s'agit d'un tableau contenant les variables de chaîne
      de requête
  - Renvoi : une structure de données de segments où chaque segment est
    séparé par un '/' lorsqu'ils sont combinés pour créer l'URL (les
    éléments dans cette structure ne doivent pas contenir de '/')
- ContentParseRoute - permet d'interpréter une URL SEF
  - Paramètres
    - \$segments - il s'agit d'un tableau contenant les segments de
      l'URL demandée.
  - Renvoi : un nom =\> tableau de valeurs des variables de chaîne de
    requête que le lien mappe

### Le Plugin SEF

Le plugin *System - SEF* de Joomla! hérite du `JPlugin` et met en œuvre
la fonction `onAfterRender()`. Dans cette fonction, le corps de la
réponse qui sera envoyée au navigateur est récupérée à l'aide du
`JResponse::getBody()`. Le corps de la réponse est alors recherché dans
les liens contenant `/index.php...` puis les remplace par une URL SEF
correcte en appelant `JRoute::_(`*`url`*`)`.

JRoute construit des URL SEF par l'instanciation d'un objet `JRouter` et
en lui demandant de construire le bon lien d'URL.

### Traitement des URL SEF

Par défaut, les URL SEF sont gérées par l'objet `JRouterSite` (depuis
`/includes/router.php`) et sont appelées par un appel à
`JApplication::route()` dans l'index.php. Cet appel est effectué par la
variable `$app` qui est en fait une instance de `JSite` (depuis
`/includes/application.php`).

`JApplication::route()` a un résultat non destructif sur le tableau
`$_GET`. Ainsi, `JApplication::route()` définit les variables dans
`$_GET` en appelant `JRequest::set()` avec l'overwrite flag paramétré
sur la valeur false. Ainsi, si un nom de variable est retourné depuis
`JRouter::route()` alors qu'il est d'ores et déjà présent dans `$_GET`,
il ne mettra pas cette valeur dans `$_GET`. Cela permet un routage
personnalisé.

### Routage personnalisé

Joomla! vous permet de créer votre propre mécanisme de routage. Afin de
créer ce mécanisme, vous avez besoin d'un plugin pour remplacer la
fonction `JPlugin::onAfterInitialise()`. Cette fonction va analyser
l'URL et créer les variables nécessaires au `$ _GET` avant que le
routage standard de Joomla! ne soit fait.

*A titre d'exemple, voir  Création d'un Plugin Système pour augmenter
JRouter.*

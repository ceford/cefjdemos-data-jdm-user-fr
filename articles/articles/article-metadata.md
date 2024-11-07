<!-- Filename: J6.x:_Article_Metadata / Display title: Article : Modifier - Métadonnées  -->

## Introduction

Les métadonnées sont des informations sur une page web contenues dans la première partie de la page entre les balises `<head>...</head>`. La plupart de ces informations ne sont pas visibles par les visiteurs du site, mais elles sont utilisées par les moteurs de recherche pour fournir des résultats appropriés aux requêtes de recherche. Il est donc dans votre intérêt d'utiliser des métadonnées informatives.

Certains éléments de métadonnées sont fournis par le modèle utilisé et vous n'avez pas besoin de les définir vous-même. Exemples courants :

```html
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="generator" content="Joomla! - Open Source Content Management">
```
Il existe d'autres formes de métadonnées telles que les données Open Graph utilisées par Facebook et les schémas utilisés pour décrire des types spécifiques de page comme Personne, Lieu ou Produit. Elles ne sont pas abordées ici.

Les éléments de métadonnées qui sont souvent négligés sont le **Titre** de la page, qui apparaît entre les balises `<title>...</title>` dans le `<head>` de la page, et la **Description** de la page, qui apparaît dans les balises `<meta>` mais peut être absente. Ils sont abordés ici.

## Le titre de la page

Un titre d'article est requis pour toute nouvelle page. Voici quelques lignes directrices et conseils du réseau Mozilla Developer Network pour composer de bons titres :

>* Évitez les titres d'un ou deux mots. Utilisez une phrase descriptive, ou une paire terme-définition pour des pages de glossaire ou de référence.
>* Les moteurs de recherche affichent généralement les 55 à 60 premiers caractères d'un titre de page. Le texte au-delà peut être perdu, alors essayez de ne pas avoir des titres plus longs. Si vous devez utiliser un titre plus long, assurez-vous que les parties importantes viennent en premier et que rien de crucial ne se trouve dans la partie du titre susceptible d'être tronquée.
>* N'utilisez pas de "mots-clés en vrac". Si votre titre n'est qu'une liste de mots, les algorithmes peuvent souvent réduire la position de votre page dans les résultats de recherche.
>* Essayez de vous assurer que vos titres sont aussi uniques que possible sur votre propre site. Des titres en double - ou presque en double - peuvent contribuer à des résultats de recherche inexacts.

Recommandations supplémentaires de Google :

>- Spécifiez un titre unique pour chaque page
>- Faites en sorte que votre titre décrive le contenu de la page, et qu'il soit concis
>- Évitez la surcharge de mots-clés (utilisation répétée de mots similaires comme "Foobar, foo bar, foobars, foo bars")
>- Évitez d'utiliser des titres génériques - chaque page doit avoir un titre unique, idéalement mis à jour dynamiquement en fonction du contenu affiché
>- Marquez vos titres, mais faites-le de manière concise et en relation avec le contenu diffusé

Il existe divers outils pour webmasters qui peuvent être utilisés pour identifier si des problèmes existent avec vos listings dans un moteur de recherche particulier - il vaut toujours la peine de prêter attention et de corriger les problèmes éventuels. Un exemple :

[Article de support de Google sur l'utilisation des titres pour vos pages web](http://support.google.com/webmasters/bin/answer.py?hl=en&amp;answer=35624)

Dans Joomla, pour une seule page, le titre de l'article devient le titre de la page utilisé dans le head et affiché dans l'onglet du navigateur. Pour une page composite, comme *Articles en vedette* ou un *Blog de catégorie*, le titre de l'élément de menu devient le titre de la page. Il est donc nécessaire de bien réfléchir à la composition de bons titres descriptifs pour les articles et les éléments de menu.

## La description de la page

L'article *Meta Description* est un champ dans l'onglet *Publication* du formulaire de saisie de données de l'article :

![L'onglet de publication du formulaire d'édition d'article](../../../en/images/articles/articles-edit-publishing-tab.png)

S'il n'y a pas de description de métadonnées d'article, alors une description de métadonnées de l'élément de menu d'un seul article sera utilisée si elle est définie. S'il n'y a pas de description de métadonnées de l'élément de menu, alors la méta description globale du site est utilisée si elle est définie. Sinon, le champ de description de métadonnées est omis.

Google recommande les points suivants pour vous assurer d'obtenir le meilleur de votre indexation par moteur de recherche :

>- Assurez-vous que chaque page a des méta descriptions uniques et pertinentes
>- Assurez-vous d'appliquer des métadonnées pour les pages de liste (par exemple, mises en page de blog et de listes) en plus des articles individuels - cela est souvent négligé sur les sites Joomla!
>- Incluez des informations factuelles si pertinent (par exemple, les articles de blog peuvent inclure l'auteur, les produits pourraient inclure le prix ou le fabricant)
>- Envisagez d'utiliser des métadonnées générées automatiquement - mais assurez-vous qu'elles sont pertinentes, lisibles et précises.
>- Rendez vos descriptions descriptives !

Autre référence :

[Article de support Google sur l'utilisation des métadonnées](http://support.google.com/webmasters/bin/answer.py?hl=fr&amp;answer=35624)

## Mots-clés

Il était une fois, les moteurs de recherche utilisaient des mots-clés pour aider à classer le contenu. Alors, les auteurs remplissaient leurs métadonnées de mots-clés avec un grand nombre de termes espérant augmenter leur classement SEO. En réponse, Google a cessé d'utiliser les mots-clés à des fins de classement. Cherchez des conseils sur le web et vous trouverez certaines sources disant de ne pas s'en soucier et d'autres disant qu'ils ont encore de la valeur.

Les mots-clés ne sont pas utilisés par le noyau de Joomla. En cas de doute, ne vous en occupez pas.

## Robots

La valeur par défaut de *Utiliser Global* n'ajoute pas de balise méta dans l'en-tête de la page HTML. D'autres valeurs le font. Il y a un fichier `robots.txt` à la racine du site Joomla. Si vous souhaitez contrôler les robots, vous devriez lire ce fichier. Il contient une explication sur la façon de l'utiliser.

## Auteur

Vous pouvez entrer le nom officiel de l'auteur qui apparaîtra en tant que métadonnées. 

## Droits

Vous pouvez entrer un avis de droits d'auteur pour qu'il apparaisse en tant que métadonnées.

## Exemple de métadonnées

Voici à quoi ressemblent les métadonnées dans la vue source de l'article :
Voici un exemple du contenu de la balise `<head>` après la complétion de tous les champs de métadonnées :

```html
    <meta charset="utf-8">
    <meta name="rights" content="Charles Darwin © 1859">
    <meta name="author" content="Charles Darwin">
    <meta name="robots" content="noindex, nofollow">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="description" content="Publicité pour L'Origine des espèces.">
    <meta name="generator" content="Joomla! - Gestion de contenu open source">
    <title>Publicité</title>
```
Notez que le champ de sortie des mots-clés est absent.

*Traduit par openai.com*


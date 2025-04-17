<!-- Filename: jdocmanual?manual=user&heading=news&filename=news-feeds.md / Display title: Flux d'actualités   -->

## Introduction aux flux d'actualités

Il fut un temps où il était courant pour un site web d'afficher des articles d'actualité provenant de sites distants dans une page ou un panneau. Les navigateurs avaient même des lecteurs de nouvelles intégrés pour faire exactement cela. Les temps changent et les principaux navigateurs n'offrent plus cette option. Il existe de nouvelles méthodes pour partager le contenu des sites, notamment avec les réseaux sociaux.

La méthode pour partager des actualités est la *Really Simple Syndication*, généralement abrégée en **RSS**, et cela a toujours sa place dans la promotion des sites web. La capture d'écran suivante montre *NetNewsWire*, un lecteur RSS gratuit et open source pour Mac. D'autres lecteurs RSS sont disponibles pour d'autres plateformes. L'illustration montre le flux RSS des **Annonces de Joomla!** sélectionné. Dix annonces sont répertoriées avec le titre et une brève description. L'annonce sélectionnée est affichée en entier dans la colonne de droite.

![Flux RSS des annonces de Joomla](../../../en/images/news-feeds/news-netnewswire-display.png)

Imaginez ce qu'un ou plusieurs flux RSS pourraient faire pour votre site web !

## Configuration d'un flux d'actualités

Votre site Web dispose de flux d'actualités configurés par défaut. Un site Joomla 5 nouvellement installé a ces deux lignes près du haut du code source de la page d'accueil :

```
<link href="/j51/index.php?format=feed&amp;type=rss" rel="alternate" type="application/rss+xml" title="Home">
<link href="/j51/index.php?format=feed&amp;type=atom" rel="alternate" type="application/atom+xml" title="Home">
```
Ces lignes permettent aux systèmes automatisés d'utiliser les flux RSS ou Atom. Atom est une spécification de syndication d'informations plus récente et légèrement différente. Les lignes seront présentes sur toutes les pages **En vedette** et les pages **Blog de catégorie**, mais pas sur la plupart des autres types de pages. Vous pouvez désactiver l'inclusion de ces flux RSS si vous le souhaitez.

## Basculer le lien du flux RSS

Le paramètre global du lien du flux RSS se trouve dans l'onglet **Intégration** de la page Options : Articles. Réglez-le sur *Afficher* ou *Masquer* selon vos besoins. Par défaut, il est réglé sur **Afficher**.

Le paramètre global peut être remplacé dans un élément de menu de blog de catégorie. Encore une fois, sélectionnez l'onglet *Intégration* et réglez le *Lien du flux RSS* sur *Afficher* ou *Masquer*.

Le flux RSS ne peut pas être masqué dans une page d'accueil d'Articles en vedette (bug?) !

## Le Module de Flux de Syndication

Il existe un module de base que vous pouvez placer sur les pages de blog en vedette ou de catégorie pour fournir un lien de syndication. Remplissez les champs dans l'onglet du module. La plupart ont des valeurs par défaut appropriées. Si le champ Étiquette est laissé vide, l'étiquette par défaut en anglais est *Entrées de flux*. Dans l'onglet *Affectation du menu*, sélectionnez **Sur toutes les pages**. Le module n'apparaîtra que sur les pages de blog en vedette et de catégorie.

![Saisie de données des flux de syndication](../../../en/images/news-feeds/news-syndication-feeds-form.png)

N'oubliez pas d'assigner le module à une *Position* et de le marquer comme *Publié*.

Dans l'affichage de la page du site, le module affiche un lien. Il n'est pas destiné à être cliqué à moins que vous n'ayez un lecteur de nouvelles local configuré. Le lien doit être copié pour être utilisé dans un lecteur de nouvelles sur un autre site ou une application de lecteur de nouvelles.

![Affichage des flux de syndication](../../../en/images/news-feeds/news-syndication-feeds-display.png)

Notez que le lien concerne les éléments de cette page. Donc, si votre site a plusieurs pages de blog de catégorie, vous aurez plusieurs flux RSS différents.


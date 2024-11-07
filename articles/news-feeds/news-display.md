<!-- Filename: jdocmanual?manual=user&heading=news&filename=news-display.md / Display title: Affichage des Nouvelles -->

## Le Module d'Affichage de Flux

Il existe un module de base *Affichage de Flux* disponible pour afficher les actualités d'autres sites. La capture d'écran suivante montre le formulaire de saisie avec l'URL du flux d'actualités des annonces de Joomla. Remarquez que le Nombre de Mots est réglé sur 100. Sinon, la longueur d'une annonce peut être excessive pour un module de la barre latérale.

![Module d'affichage de flux, saisie de données](../../../en/images/news-feeds/news-joomla-news-form.png "Module d'affichage de flux, saisie de données")

Le résultat peut être peu attrayant mais peut être amélioré avec quelques styles personnalisés dans user.css :

![Module d'affichage de flux, saisie de données](../../../en/images/news-feeds/news-joomla-news-display.png "Module d'affichage de flux, saisie de données")

## Pages d'affichage des flux

En alternative à l'affichage des actualités dans un module, vous pouvez créer un élément de menu pour afficher un flux d'actualités sur une page web. Depuis le menu Administrateur :

* Sélectionnez **Composants / NewsFeeds / Flux**. Vous pouvez d'abord créer une Catégorie pour les actualités.
* Sélectionnez le bouton **Nouveau** dans la *Barre d'outils*.
* Remplissez le formulaire **Flux d'actualités : Éditer** :
    - Le **Lien** est le lien RSS copié à partir d'une source distante.
    - La **Description** est optionnelle.
    - L'onglet **Options** contient des éléments pour contrôler l'affichage du flux.
* **Enregistrer & Fermer**

![Saisie des données du composant NewsFeed](../../../en/images/news-feeds/news-feed-data-entry.png "Saisie des données du composant NewsFeed")

Créez un élément de menu à partir du menu Administrateur :

* Sélectionnez **Menus / Menu principal** ou tout autre menu pour cet élément.
* Sélectionnez **Nouveau** dans la Barre d'outils *Menus : Éléments*.
* Dans le **Type d'élément de menu**, utilisez le bouton **Sélectionner** pour trouver et sélectionner *News Feeds / Flux d'actualités unique*.
* Remplissez le reste du formulaire comme il convient.
* **Enregistrer & Fermer**

![Saisie des données de l'élément de menu NewsFeed](../../../en/images/news-feeds/news-feed-data-entry.png "Saisie des données de l'élément de menu NewsFeed")

Testez-le : allez dans le menu du site et sélectionnez l'élément de menu de flux.

![Affichage du NewsFeed](../../../en/images/news-feeds/news-feed-display.png "Affichage du NewsFeed")

Chaque élément du flux est un `<li>` dans une balise `<ul>`, donc par défaut, il apparaît marqué par un point. Cela n'est pas si évident si les éléments sont longs. Vous pouvez appliquer vos propres styles dans *user.css*. Le suivant placera chaque élément dans une boîte distincte :

```
ul.com-newsfeeds-newsfeed__items {
  list-style-type: none;
  padding-left: 0;
}

ul.com-newsfeeds-newsfeed__items > li {
  padding: 1rem;
  margin-bottom: 1rem;
  border: 2px solid navy;
}
```

Ce qui apparaît comme ceci :

![Affichage personnalisé du NewsFeed](../../../en/images/news-feeds/news-feed-custom-display.png "Affichage personnalisé du NewsFeed")

## Lister les flux d'actualités dans une catégorie

La page *Joomla! RSS News Feeds* répertorie huit flux d'actualités séparés. Vous pouvez créer un flux pour certains ou tous ces flux et les attribuer à une catégorie, par exemple *Actualités Joomla*. Ensuite, vous pouvez créer un élément de menu avec le *Type d'élément de menu* défini sur *Lister les flux d'actualités dans une catégorie* et la catégorie définie sur *Actualités Joomla*.

![Formulaire de menu des flux d'actualités par catégorie](../../../en/images/news-feeds/news-feed-menu-category-form.png "Formulaire de menu des flux d'actualités par catégorie")

Essayez-le pour voir le résultat !
*Traduit par openai.com*


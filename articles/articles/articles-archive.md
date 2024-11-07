<!-- Filename: J4.x:How_to_Archive_an_Article / Display title: Articles : Archive   -->

## Introduction

Au fur et à mesure que le contenu de votre site web se développe, il est probable qu'une partie de ce contenu doive être mise à jour ou remplacée. Vous pourriez choisir de dépublier certains articles, mais vous pourriez avoir besoin de les conserver d'une manière qui permette aux gens de les consulter.

Joomla! simplifie l'archivage des articles en vous permettant de changer le statut d'un article en **Archivé**. Un avantage de l'archivage est qu'il facilite la gestion du contenu, et l'archivage est structuré par année.

Cette approche basée sur le statut est un élément clé de la capacité de Joomla à gérer le contenu de manière efficace et efficiente. Une fois archivés, Joomla fournit des méthodes pour accéder au contenu archivé et l'afficher.

## Archivage des articles

Vous pouvez archiver un article à plusieurs endroits :

- Un article précédent sur 
  [Ajouter un article](jdocmnaual?article=user/getting-started/adding-an-article)
  montrait une capture d'écran de la page de liste des *Articles* avec un article sélectionné et
  la liste des *Actions* dans la barre d'outils ouverte pour montrer les options disponibles. L'une
  d'elles est *Archiver*. C'est probablement la meilleure façon d'archiver un article. Notez 
  que vous pouvez archiver plusieurs articles à la fois. La sélection d'un ou plusieurs articles 
  activera la liste déroulante **Actions**.
- Chaque article a un paramètre *Statut* dans le formulaire d'édition de l'article. *Archivé*
  peut être défini ici.
- À partir d'un élément de menu *Article unique*. Le champ *Sélectionner un article* 
  dispose d'une option *Modifier* qui ouvre un formulaire contextuel *Modifier l'article* où le champ *Statut*
  peut être défini comme dans un formulaire d'édition d'article standard. L'élément de menu 
  de l'article unique reste lié à l'article archivé.

Les articles archivés n'apparaissent plus dans la liste des articles *par défaut*. Sélectionnez le
bouton *Options de filtrage* puis *Archivé* dans le filtre *- Sélectionner le statut -* 
pour voir la liste des articles archivés.

## Vue du site des articles archivés

Une fois que des articles ont été archivés, il existe plusieurs façons de les consulter à partir de l'interface du site.

### Via un menu

Il existe un type d'élément de menu [Articles archivés](jdocmanual?article=user/menus/menu-item-type-archived-articles) que vous pouvez utiliser pour créer un lien dans votre menu vers les articles archivés.

### Via un module

Il y a un module [Articles – Archivés](jdocmanual?article=user/modules/articles-archived-module) que vous pouvez utiliser pour l'afficher dans l'une des positions de module de votre modèle de site Web.

La capture d'écran suivante montre une page d'*Articles archivés* obtenue avec un élément de menu. Il y a des filtres pour le *Mois* et l'*Année* et une limite de liste avec des réglages de 5 à 100 et Tous. Veillez toujours à l’utilisation de *Tous*. Si vous obtenez des milliers de résultats, il se peut que votre page prenne du temps à charger et ne réponde pas. Vous risquez de manquer de temps ou de mémoire, ce qui entraînerait le retour d'une erreur serveur.

![Vue de la page des articles archivés](../../../en/images/articles/articles-archived-site.png)

Au bas de la colonne de droite se trouve le module *Articles archivés*.

## Désarchiver des articles

Pour désarchiver un article, le même processus s'applique : le statut de l'article est modifié de **Archivé** à **Publié**.

## Conseils

* N'oubliez pas que les articles archivés sont filtrés dans la vue de la liste des *Articles*. Vous devez changer le filtre *Statut* en *Archivé* pour les consulter.
* L'archivage ne dépublie pas un article.
* Vous pouvez également archiver des articles depuis le frontend lorsque vous êtes connecté pour l'édition frontend.

*Traduit par openai.com*


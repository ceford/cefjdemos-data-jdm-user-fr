<!-- Filename: J4.x:Getting_Started:_Adding_a_Category / Display title: Ajouter une catégorie  -->

## Introduction

Les propriétaires de sites web ayant plus qu'une poignée d'articles devraient penser à la meilleure façon de présenter le contenu pour faciliter la navigation. Par exemple, si vous avez un zoo, un musée, une collection de minéraux ou juste un grand jardin, vous pourriez avoir environ 1000 spécimens à décrire. Un article pour chaque spécimen, avec des photographies, nécessite une certaine structure organisationnelle. Si les articles étaient des fichiers, vous les placeriez probablement dans une hiérarchie de fichiers. Dans un CMS, les articles ne sont pas des fichiers, mais les catégories fournissent une structure arborescente similaire. Exemple :

| Catégorie   | Sous-catégories                        |
|-------------|----------------------------------------|
| Mammifères  | Grands singes, Singes, Ongulés, Chiens, Chats |
| Reptiles    | Serpents, Lézards, Crocodiles, Tortues |
| Amphibiens  | Grenouilles, Crapauds                   |
| Oiseaux     | Rapaces, Canards, Mouettes, Pinsons, Mésanges |
| Arthropodes | Araignées, Papillons, Abeilles, Sauterelles |
| Poissons    | Requins, Saumon, Morue, Hareng, Maquereau |

Les sous-catégories peuvent elles aussi avoir d'autres sous-catégories. Une profondeur maximale gérable semble être d'environ sept. Pour le tableau ci-dessus, un musée pourrait ajouter plus de catégories parentes :

```text
nature -> vie -> animaux -> mammifères...
nature -> vie -> plantes -> arbres...
nature -> minéraux...
histoire -> Égypte...
science -> astronomie...
science -> chimie...
```

Imaginez combien de spécimens un musée national ou d'une petite ville détient !  

## Types d'Éléments de Menu

Il existe plusieurs types d'éléments de menu conçus pour fonctionner avec les Catégories :

- **Blog de Catégorie** Il s'agit d'une mise en page qui présente un ou deux extraits d'articles principaux, souvent sur toute la largeur de la page, puis plusieurs autres extraits d'articles en deux ou trois colonnes, et enfin un mécanisme de pagination pour lier à d'autres articles de la même catégorie. L'extrait est le contenu avant un saut de page, souvent les un ou deux premiers paragraphes. Une page d'accueil de site est souvent un blog de catégorie qui inclut *Toutes les Catégories*. Une disposition d'*Articles en vedette* est similaire à un blog de catégorie et souvent utilisée comme page d'accueil également.
- **Liste de Catégories** Il s'agit d'une mise en page de liste qui affiche une liste d'articles dans une catégorie. Elle peut être affichée avec un filtre de recherche pour permettre la recherche d'articles par Titre, Auteur, Visites, Tags ou Mois de publication.
- **Lister Toutes les Catégories dans un Arbre de Catégories d’Article** Cette mise en page liste un arbre de catégories en partant d'un parent choisi. Chaque branche est rétractable et est très utile pour les structures d'arbres de catégories grandes et complexes.

Les éléments de menu sont abordés dans un article ultérieur.  

## Créer une Catégorie

L'exemple suivant utilise une catégorie Mammifères inspirée de la liste ci-dessus pour démontrer comment créer une nouvelle Catégorie :

![Formulaire d'édition de catégorie](../../../en/images/getting-started/article-category-edit.png)

- Sélectionnez l'élément **Contenu** dans le menu Administrateur pour le déplier.
- Sélectionnez l'icône **+** à côté de l'élément de menu *Catégories* pour ouvrir le formulaire d'édition de Catégorie.
- Le formulaire **Articles : Nouvelle Catégorie** ne comporte qu'un seul champ obligatoire : le *Titre*, dans ce cas *Mammifères*.
- Le champ **Description** est facultatif, mais il est préférable de le remplir car il est utilisé dans certaines listes. Suggestion :<br>
  *Les mammifères sont des animaux à sang chaud qui donnent naissance à des petits vivants.*
- Le champ **Parent** spécifie si c'est une catégorie principale (-Pas de Parent-) ou une sous-catégorie sélectionnée dans la liste des catégories.
- **Enregistrer et Fermer** pour revenir à la page de liste **Articles : Catégories**.

Cette catégorie est maintenant disponible pour être utilisée avec les articles.

*Traduit par openai.com*


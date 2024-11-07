<!-- Filename: J6.x:Articles:_Filter_Options / Display title: Articles : Options de filtre -->

## Introduction

Après avoir créé votre premier article, comme décrit dans l'article de démarrage sur [Ajouter un article](jdocmanual?article=user/getting-started/adding-an-article), votre liste d'articles contiendra un seul article. Un an plus tard, vous pourriez avoir un millier d'articles et devoir utiliser les *options de filtrage* pour trouver ce dont vous avez besoin.

La capture d'écran suivante montre les articles utilisés pour préparer cet ensemble de tutoriels. La taille du lot de la liste a été définie sur 5 pour limiter la longueur de la capture d'écran.

Les *Options de filtre* ont été ouvertes pour montrer les filtres disponibles.

![Liste des articles](../../../en/images/articles/articles-filter-options.png)

Cette liste contient plus de 20 articles créés à partir de l'installation des *Données d'exemple multilingues* et quelques autres articles ajoutés par la suite.

## Ordre de Tri

Notez que l'ordre de tri par défaut est *ID Décrément*. Cela place le dernier article en haut de la liste, ce qui est généralement ce que vous souhaitez.  

## Pagination

Si le nombre d'articles est supérieur à la *taille du lot*, une barre de pagination s'affiche en dessous de la liste. Elle comporte des icônes pour aller à la *première page*, *page précédente*, *page suivante* ou *dernière page*. Les numéros mènent aux articles de la page numérotée correspondante. La barre de pagination est utile si vous avez besoin de parcourir la liste des articles.

## Filtres

Tous les filtres fonctionnent *À la modification*, mais les filtres sont mémorisés et les *Options de filtre* restent visibles tant qu'un filtre est sélectionné.

### Sélectionner les Articles en Vedette

- **- Articles en Vedette Sélectionnés -** Sélectionne à la fois les articles en vedette et non en vedette.
- **Articles non en Vedette** Sélectionne uniquement les articles non en vedette.
- **Articles en Vedette** Sélectionne uniquement les articles en vedette.

### Sélectionner le Statut

La sélection par défaut des articles inclut les articles *Publiés* et *Non publiés*. Cela permet de basculer l'état de publication à l'aide de l'icône dans la colonne *Statut*. Les éléments *Dans la corbeille* et *Archivés* ne sont inclus que si *Tous* est sélectionné.

- **Dans la corbeille** Sélectionne uniquement les articles dans la corbeille. L'icône *Statut* affiche une icône de corbeille qui peut être utilisée pour publier l'article. Un bouton *Supprimer* dans la barre d'outils permet la suppression complète de tout article sélectionné. Un message d'avertissement est affiché. Après suppression, utilisez le bouton *Effacer* pour revenir à la liste non filtrée.
- **Non publié** Sélectionne uniquement les articles non publiés.
- **Publié** Sélectionne uniquement les articles publiés.
- **Archivé** Sélectionne uniquement les articles archivés. L'icône de statut permet de changer le statut de l'article en Non publié. Les articles archivés ne sont plus nécessaires mais peuvent être rendus disponibles via un élément de menu *Articles archivés*.
- **Tous** Sélectionne tous les articles quel que soit leur statut.

Si un article nécessite un changement de statut autrement que par l'utilisation de l'icône dans la colonne Statut, cela peut être fait depuis le formulaire d'édition de l'article.

### Sélectionner la Catégorie

La liste déroulante montre toutes les catégories du site dans un arbre similaire à celui utilisé dans la page de liste *Articles : Catégories*. Si vous sélectionnez une seule catégorie, tous les articles de cette catégorie seront sélectionnés ainsi que tous les articles de ses sous-catégories, sauf si le filtre *Sélectionner Niveaux Max* est défini.

Vous pouvez sélectionner plusieurs catégories qui ne se trouvent pas dans le même arbre de catégories.

### Sélectionner l'Accès

La liste déroulante permet de sélectionner des articles selon des *Niveaux d'accès* spécifiés. Le contrôle d'accès est couvert dans un article séparé. En bref, cela restreint la visibilité des articles du site comme suit :

- **Public** Articles disponibles pour tout le monde.
- **Invité** Articles disponibles pour ceux qui ne sont pas connectés.
- **Enregistré** Articles disponibles pour ceux qui sont connectés.
- **Spécial** Articles disponibles pour ceux qui sont connectés et appartiennent à un groupe d'utilisateurs ayant un accès spécial.
- **Super Utilisateurs** Articles restreints à ceux connectés en tant que Super Utilisateur.

### Sélectionner l'Auteur

La liste déroulante permet de sélectionner des articles par un auteur précis.

- **Aucun** C'est un cas particulier où un article existe mais l'auteur original n'existe pas. Il peut y avoir plusieurs auteurs qui ont contribué à des articles mais qui n'ont plus de comptes utilisateurs.
- **Créé par moi** Une liste de vos propres articles.
- **Nom de l'auteur** Une liste d'auteurs d'articles nommés pouvant être assez longue. Le vrai nom est utilisé plutôt que le nom de connexion. Sélectionnez un auteur selon vos besoins pour voir les articles de cet auteur.

### Sélectionner la Langue

Ce filtre est présent uniquement dans les sites multilingues. Lorsqu'un article est créé, il peut être attribué à *Toutes* les langues ou à une seule langue spécifique ayant le nom et le code pays dans le champ *Langue* du formulaire de saisie de données, par exemple *Anglais (en-GB)* ou *Espagnol (es-ES)*. Dans le filtre de langue :

- **Toutes** Filtre les articles attribués à *Toutes* les langues. Cela ne signifie pas tous les articles !
- **Nom de la langue (xx-YY)** Une liste des langues installées. Sélectionnez une langue spécifique pour voir les articles attribués à cette langue.

### Sélectionner le Tag

Une liste de tags. Sélectionnez n'importe quel tag pour voir les articles ayant ce tag. Plusieurs tags peuvent être sélectionnés.

### Sélectionner Niveaux Max

Cela restreint la liste des articles au nombre de niveaux spécifiés dans une hiérarchie. Lorsqu'aucune valeur n'est sélectionnée, tous les niveaux sont inclus. Si défini à 1, seuls les articles du premier niveau d'un arbre de catégories seront inclus.

## Filtres multiples

Sur les sites grands et complexes, vous pouvez avoir besoin d'utiliser plusieurs filtres. Les filtres sont mémorisés au sein d'une session, jusqu'à la déconnexion ou l'expiration de la session en raison de l'inactivité.

*Traduit par openai.com*


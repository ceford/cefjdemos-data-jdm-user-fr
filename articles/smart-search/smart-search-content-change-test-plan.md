<!-- Filename: Smart_Search_content_change_test_plan / Display title: Plan de Test de Recherche Intelligente -->

Ce qui suit est un plan de test approximatif couvrant (principalement) la mise à jour de l'index de la Recherche Intelligente lorsque divers types de mises à jour de contenu se produisent.

La Recherche Intelligente doit être testée pour chacun des types de contenu principaux pris en charge. Ils sont :

- Articles
- Catégories
- Contacts
- Flux de nouvelles
- Liens web

Pour chacun des types de contenu ci-dessus, nous devons tester les éléments suivants :
## Modifications de texte

La modification de divers champs de texte dans un élément de contenu doit changer les termes de recherche dans l'index (à une exception notable décrite ci-dessous). Il n'est pas nécessaire de tester tous les champs de texte pour un type de contenu donné, car si cela fonctionne pour l'un, cela fonctionnera pour tous, il suffit donc d'en choisir un pour chaque type de contenu. Les champs de texte suivants sont indexés pour les composants principaux :

- Articles
  - Titre
  - Alias
  - Texte de l'article
  - Description des métadonnées
  - Mots-clés des métadonnées
  - Auteur des métadonnées
  - Auteur
  - Créé par alias
- Catégories
  - Titre
  - Alias
  - Description
  - Lien ??? (pas sûr qu'un tel champ existe)
  - Description des métadonnées
  - Mots-clés des métadonnées
  - Auteur des métadonnées
  - Auteur
- Contacts
  - Nom
  - Alias
  - Nom d'utilisateur lié
  - Autres informations
  - Poste (si activé dans les options)
  - Adresse (si activée dans les options)
  - Ville (si activée dans les options)
  - Région (si activée dans les options)
  - Pays (si activé dans les options)
  - Code postal (si activé dans les options)
  - Téléphone (si activé dans les options)
  - Fax (si activé dans les options)
  - Email (si activé dans les options)
  - Mobile (si activé dans les options)
  - Page web (si activée dans les options)
- Fils d'actualités
  - Titre
  - Alias
  - Lien
  - Description des métadonnées
  - Mots-clés des métadonnées
  - Auteur des métadonnées
  - Auteur
  - Créé par alias
- Liens web
  - Titre
  - Alias
  - URL
  - Description
  - Description des métadonnées
  - Mots-clés des métadonnées
  - Auteur des métadonnées
  - Auteur
  - Créé par alias

Pour tester, ajoutez simplement une chaîne de caractères aléatoire, comme "xyz", dans un lot de texte régulier et vers le haut du contenu, puis essayez de rechercher ce terme sur l'interface utilisateur.

- votre chaîne de caractères aléatoire doit apparaître dans la liste de saisie semi-automatique au fur et à mesure de sa saisie.
- votre chaîne aléatoire devrait apparaître 3 fois dans la liste de saisie semi-automatique.
  - seule
  - avec le mot suivant
  - avec les 2 mots suivants
- l'élément de contenu contenant votre chaîne de caractères aléatoire doit apparaître dans la liste des résultats de recherche.
- votre chaîne de caractères aléatoire doit être surlignée dans les résultats de recherche, à condition que vous l'ayez entrée près du haut du texte (car le texte dans les résultats de recherche est tronqué).

Supprimez votre chaîne de caractères aléatoire du texte : Cela devrait supprimer les 3 termes/expressions de recherche de l'index. La recherche de l'un des 3 termes de recherche ne devrait produire aucun résultat.

Supprimez l'élément de contenu : Cela supprimera tous les termes/expressions de recherche utilisés dans l'élément de contenu de l'index, sauf lorsque ces termes/expressions de recherche sont encore utilisés dans d'autres éléments de contenu.<sup>[\[1\]](#cite_note-1)</sup>

L'élément de contenu supprimé ne doit apparaître dans aucune liste de résultats de recherche.

## Modifications de l'état de l'élément de contenu

Trouvez un élément de contenu du type requis en utilisant la Recherche intelligente. Ensuite, effectuez ces tests :

- Mettez l’élément à la corbeille et répétez la recherche. L’élément ne devrait plus apparaître dans les résultats de recherche.
- Publiez à nouveau l’élément et répétez la recherche. L’élément devrait apparaître à nouveau dans les résultats de recherche.
- Dépubliez l'élément et répétez la recherche. L'élément ne devrait plus apparaître dans les résultats de recherche.
- Archivez l’élément et répétez la recherche. L’élément devrait apparaître à nouveau dans les résultats de recherche.

## Modifications de la carte de contenu (taxonomie)

Bien que les modifications de catégorie soient un cas particulier de changements de carte de contenu, nous devons également tester les modifications des branches de la carte de contenu non catégorisées, car les changements de catégorie font appel à un code différent. Voici les champs non catégorisés qui sont soumis aux cartes de contenu dans les composants principaux :

- Articles
  - Auteur
  - Catégorie
  - Langue
- Contacts
  - Catégorie
  - Pays
  - Langue
  - Région
- Flux d’actualités
  - Catégorie
  - Langue
- Liens web
  - Catégorie
  - Langue

Ainsi, choisissez un champ (si l'un fonctionne, ils fonctionneront tous pour ce type de contenu) parmi ceux ci-dessus qui est approprié au type de contenu et vérifiez que :

- la modification du champ entraîne l'apparition de l'élément dans une recherche utilisant le menu déroulant pertinent (dans la recherche avancée) pour le champ que vous avez changé. <sup>[\[2\]](#cite_note-2)</sup>
- l'élément de contenu n'apparaît pas dans une recherche utilisant l'ancienne valeur du champ.

Supprimez l'élément de contenu et vérifiez qu'il n'apparaît plus dans les résultats de recherche en utilisant le filtre déroulant pertinent. Notez qu'il n'est **pas** attendu qu'un nœud inutilisé soit retiré du filtre déroulant pertinent. <sup>[\[3\]](#cite_note-3)</sup>

## Modifications de l'état de la catégorie

Modifier l'état de la catégorie à laquelle appartient un article doit mettre à jour l'index pour cet article. De plus, changer l'état d'une catégorie parente de la catégorie à laquelle un article appartient doit également mettre à jour l'index pour cet article. Pour tester, trouvez ou créez un article avec la structure suivante :

    Catégorie A contenant la catégorie A.1 contenant l'article de contenu

Changez le statut de la Catégorie A.1 et testez comme suit :

- Placez la Catégorie A.1 dans la corbeille et refaites la recherche. L'article ne devrait plus apparaître dans les résultats de recherche.
- Publiez à nouveau la Catégorie A.1 et refaites la recherche. L'article devrait réapparaître dans les résultats de recherche.
- Dépubliez la Catégorie A.1 et refaites la recherche. L'article ne devrait plus apparaître dans les résultats de recherche.
- Archivez la Catégorie A.1 et refaites la recherche. L'article devrait apparaître de nouveau dans les résultats de recherche.

Restaurez la Catégorie A.1, puis changez le statut de la Catégorie A et testez comme suit :

- Placez la Catégorie A dans la corbeille et refaites la recherche. L'article ne devrait plus apparaître dans les résultats de recherche.
- Publiez à nouveau la Catégorie A et refaites la recherche. L'article devrait réapparaître dans les résultats de recherche.
- Dépubliez la Catégorie A et refaites la recherche. L'article ne devrait plus apparaître dans les résultats de recherche.
- Archivez la Catégorie A et refaites la recherche. L'article devrait apparaître de nouveau dans les résultats de recherche.

## Modifications du niveau d'accès des éléments de contenu

Changez le niveau d'accès d'un élément de contenu pour qu'il soit quelque chose qu'un utilisateur front-end ne devrait pas pouvoir voir.

- assurez-vous que l'élément de contenu n'apparaît pas dans les listes de résultats de recherche.

Rétablissez le niveau d'accès à quelque chose qu'un utilisateur front-end devrait pouvoir voir.

- assurez-vous que l'élément de contenu apparaît maintenant dans les listes de résultats de recherche.

Notez que les termes de recherche dans l'élément de contenu apparaîtront toujours dans la liste de saisie semi-automatique même si l'utilisateur n'a pas accès à l'élément de contenu lui-même. C'est un comportement attendu, bien que cela puisse être quelque chose que nous voudrions examiner. <sup>[\[4\]](#cite_note-4)</sup>

## Modifications du niveau d'accès de la catégorie

Changer le niveau d'accès de la catégorie à laquelle appartient un élément doit mettre à jour l'index de cet élément. De plus, changer le niveau d'accès d'une catégorie parente de la catégorie à laquelle appartient un élément doit également mettre à jour l'index de cet élément. Pour tester, trouvez ou créez un élément avec la structure suivante :

    Catégorie A contenant Catégorie A.1 contenant un élément de contenu

Effectuez les tests suivants :

- Changez le niveau d'accès de la Catégorie A.1 à quelque chose qu'un utilisateur du front-end ne devrait pas pouvoir voir.
  Vérifiez que l'élément de contenu n'apparaît pas dans les listes de résultats de recherche.
- Changez le niveau d'accès de la Catégorie A.1 à nouveau à quelque chose qu'un utilisateur du front-end devrait pouvoir voir.
  Vérifiez que l'élément de contenu apparaît maintenant dans les listes de résultats de recherche.
- Changez le niveau d'accès de la Catégorie A à quelque chose qu'un utilisateur du front-end ne devrait pas pouvoir voir.
  Vérifiez que l'élément de contenu n'apparaît pas dans les listes de résultats de recherche.
- Changez le niveau d'accès de la Catégorie A à nouveau à quelque chose qu'un utilisateur du front-end devrait pouvoir voir.
  Vérifiez que l'élément de contenu apparaît maintenant dans les listes de résultats de recherche.

## Changements d'état de recherche intelligente

Dans l'écran Administrateur → Composants → Recherche intelligente → Cartes de contenu, il est possible de modifier l'état de publication/dépublication des branches et des nœuds de la carte de contenu. Les tests suivants doivent être effectués :

- Dépublier une branche de la carte de contenu (par exemple, Auteur).
  Vérifiez que le menu déroulant de filtre pour cette branche n'est plus visible dans la recherche avancée.
- Dépublier un nœud de la carte de contenu (au sein d'une branche publiée). Par exemple, "Animaux" dans la branche "Catégorie".
  Vérifiez que le nœud n'est pas répertorié dans le menu déroulant de filtre pour la branche dans la recherche avancée.

Dans l'écran Administrateur → Composants → Recherche intelligente → Contenu indexé, effectuez le test suivant :

- Dépublier un élément de contenu.
  Vérifiez que l'élément de contenu n'apparaît plus dans les résultats de recherche.

Dans l'écran Administrateur → Extensions → Gestionnaire de plug-ins, effectuez le test suivant :

- Réglez le filtre "Sélectionner le type" sur "finder" ou "recherche intelligente".
- Choisissez l'un des plug-ins de type de contenu et dépubliez-le.
  Toutes les données pour ce type de contenu doivent être supprimées de l'index.

Remarque : Si vous republiez le plug-in, cela n'ajoutera pas les données à nouveau dans l'index. Ceci est un comportement attendu. Vous devrez exécuter l'indexeur à nouveau pour récupérer les données.


<!-- Filename: J3.x:Adding_custom_fields/Parameters_for_all_Custom_Fields / Display title: Paramètres de champ -->

## Formulaire de Saisie de Données

Il y a 16 types de champs ou plus disponibles dans la liste de sélection Type du formulaire de saisie de données. La plupart des champs du formulaire sont les mêmes pour tous les types de champs, mais d'autres changent en fonction du type sélectionné. Cet article décrit les paramètres communs à tous les champs. Le formulaire de saisie de données est également le même pour les champs **Article**, **Contact** et **Utilisateur** ainsi que leurs champs Catégorie.

Une liste des champs sera initialement vide. Pour commencer, par exemple avec les champs Article :
* Sélectionnez **Nouveau** dans la barre d'outils de la liste Articles : Champs.

Le formulaire comprend un champ Titre et quatre onglets.

![Paramètres généraux des champs onglet](../../../en/images/fields/fields-parameters-general-tab.png)

## Titre

Le titre est affiché dans la page de liste *Articles: Champs* où il peut être sélectionné pour ouvrir le champ à des fins de modification. Le titre n'est pas affiché lors de la création d'un article ou dans le frontal. Cependant, l'étiquette peut être créée à partir du titre et elle est affichée dans le formulaire de saisie de données de l'article et peut être affichée dans l'affichage de l'article.

### Onglet Général

#### Dans le panneau de gauche :

- **Type** Sélectionnez l'un des 16 types de champs dans la liste déroulante. Lorsque vous enregistrez le champ, ce type est permanent. Vous ne pouvez pas le changer plus tard.
- **Nom** Le nom sera utilisé pour identifier le champ. Laissez ceci vide et Joomla remplira une valeur par défaut à partir du titre.
- **Étiquette** Utilisez une étiquette descriptive pour le champ. Ce texte n'est pas traduisible. Si vous n'entrez aucun texte pour une étiquette, le texte du titre sera utilisé en tant que texte de l'étiquette.
- **Description** Texte qui sera affiché comme une info-bulle pour décrire l'objectif du champ pendant la saisie de données. Ce texte n'est pas traduisible et ne sera pas affiché dans le frontal.
- **Obligatoire** Réglez sur *Oui* si c'est un champ obligatoire qui doit être rempli avant de soumettre un article.
- **Utiliser Uniquement Dans le Sous-formulaire** Explication requise [À faire]
- **Valeur par Défaut** Définissez une valeur par défaut si approprié. Ce texte n'est pas traduisible.
- **Filtre** Choisissez une des options disponibles dans la liste déroulante. Le champ sera validé pour sa conformité avec le type de données sélectionné.
- **Longueur Maximale** Réglez ceci pour limiter la longueur de texte qui peut être entré.

### Dans le panneau de droite :

- **Statut** Définissez un état de publication sélectionné parmi *Publié*, *Non publié*, *Archivé* ou *Mis à la corbeille*.
  - Publié : Le champ est visible lors de la modification d'un article ou d'un contact. Et il est visible dans le Frontal.
  - Non publié : Le champ ne sera pas visible pour les utilisateurs lors de la modification d'un article ou d'un contact.
  - Archivé : Le champ ne s'affichera plus lors de l'édition d'un article ou d'un contact. Vous pouvez l'ouvrir dans le gestionnaire de champs lorsque vous réglez le filtre sur archivé.
  - Mis à la corbeille : Le champ est supprimé mais toujours dans la base de données. Il peut être définitivement supprimé de la base de données avec la fonction Vider la corbeille dans le Gestionnaire de champs.
- **Groupe de Champs** Sélectionnez Aucun ou un Groupe sélectionné dans une liste prédéfinie. Les groupes apparaissent comme des onglets séparés dans le formulaire de saisie de données de l'article.
- **Catégorie** Vous pouvez attribuer un champ à une ou plusieurs catégories de champ. Notez que le *Tout* par défaut n'inclut pas les articles *non-catégorisés*.
- **Accès** Le niveau d'accès de visualisation pour ce champ.
- **Langue** Sélectionnez la langue pour ce champ personnalisé. Si vous n'utilisez pas la fonctionnalité multilingue de Joomla, conservez le paramètre par défaut *Tout*.
- **Note** Un champ optionnel pour faire vos notes personnelles pour le champ.

### Onglet Options

![Paramètres des champs onglet général](../../../en/images/fields/fields-parameters-options-tab.png)

#### Options du Formulaire

- **Marque Place** Un texte indicatif qui apparaîtra à l'intérieur du champ personnalisé comme un indice pour l'entrée. Le marque-place est actif dans le Back-end lors de la création d'un article. Vous ne le voyez pas dans le Frontal.
- **Classe de Champ** Les attributs de classe du champ lorsque le champ est rendu. Si différents classes sont nécessaires, listez-les avec des espaces.
- **Classe de l'Étiquette (Formulaire)** Les attributs de classe du champ dans le formulaire d'édition. Si différents classes sont nécessaires, listez-les avec des espaces.
- **Éditable Dans** Sur quelle partie du site le champ doit-il être affiché : Site, Administrateur ou les Deux.
- **Attribut Showon** Afficher ou masquer conditionnellement le champ selon la valeur d'autres champs. La syntaxe à utiliser ici, par exemple :
  - `liste-des-éléments:valeur1[OU]liste-des-éléments:valeur2` où
  - liste-des-éléments : Le nom d'un champ déjà créé dont dépend ce champ.
  - valeur1 : La valeur nécessaire dans le champ de la liste des éléments pour que ce champ soit affiché.
  - [OU] Pour créer un choix parmi plusieurs champs. Dans l'exemple, ce champ sera affiché lorsque le champ de la liste des éléments a une valeur de valeur1 OU valeur2.
  - [ET] Pour combiner plusieurs champs. Ce champ sera affiché seulement lorsque les champs de la liste des éléments ont la valeur valeur1 ET valeur2.
  - Vous pouvez aussi utiliser la valeur 'n'est pas égale' comme dans liste-des-éléments!:valeur1. La syntaxe affichera ce champ uniquement lorsque liste-des-éléments n'est pas égal à valeur1.
  - Pour afficher ce champ lorsque le champ de la liste-des-éléments a été sélectionné et n'a pas de valeur vide, utilisez la syntaxe liste-des-éléments!: (sans valeur spécifiée).
  - Remarque : Les champs de sous-formulaire traitent le nom de la liste-des-éléments différemment. Si vous créez un champ de sous-formulaire et que vous ajoutez ce champ conditionnel pour un champ que vous créez là, vous devez utiliser champ[ID] au lieu de liste-des-éléments, où ID est l'identifiant du champ liste-des-éléments. Par conséquent, l'attribut showon pour ce champ conditionnel que vous créez doit être : champ36:valeur1[OU]champ36:valeur2 où 36 est l'ID du champ 'Liste des éléments'. Cela nécessite une clarification !

#### Options d'Affichage

- **Classe d'Affichage** La classe du conteneur de champ dans la sortie.
- **Classe de Valeur** La classe de la valeur du champ dans la sortie.
- **Étiquette** Afficher ou cacher l'étiquette.
- **Classe de l'Étiquette (Sortie)** La classe de sortie de l'étiquette si l'étiquette est affichée.
- **Affichage Automatique** Joomla propose certains événements de contenu qui sont déclenchés lors du processus de création de contenu. C'est là qu'il faut définir comment les champs personnalisés doivent être intégrés au contenu. Vous pouvez choisir *Après le Titre*, *Avant le Contenu Affiché*, *Après le Contenu Affiché* ou *Ne pas afficher automatiquement*.
- **Préfixe** Texte fixe à afficher avant un champ, par exemple £.
- **Suffixe** Texte fixe à afficher après un champ, par exemple EUR.
- **Mise en page** Sélectionnez une mise en page parmi les modèles et les remplacements disponibles.
- **Afficher Lorsqu'en Lecture Seule** Sélectionnez parmi *Hériter*, *Oui* ou *Non*. Si le champ est en lecture seule (peut-être que l'utilisateur n'a pas le niveau d'accès), le champ doit-il être affiché ou caché.

#### Recherche Intelligente

- **Index de Recherche** Sélectionnez parmi la liste d'options. Avertissement : Lorsque *Rendre recherchable* est sélectionné, le contenu du champ est indexé avec les permissions de visualisation de l'élément de contenu. Cela pourrait conduire à une divulgation d'informations inattendue.

### Onglet Publication

![Paramètres des champs onglet général](../../../en/images/fields/fields-parameters-publishing-tab.png)

### Onglet Permissions

Les autorisations pour chaque groupe d'utilisateurs sont explicites pour les actions *Supprimer*, *Modifier* et *Modifier l'état*. Les autorisations indiquent qui peut faire quoi avec le champ dans son ensemble, comme le supprimer, le modifier ou le dépublier.

![Paramètres des champs onglet général](../../../en/images/fields/fields-parameters-permissions-tab.png)

L’autorisation *Modifier la valeur du champ personnalisé* peut prêter à confusion. Elle indique qui peut modifier le contenu du champ. Par défaut, elle est définie sur **Non autorisé (hérité)** pour tous les groupes sauf les super utilisateurs. Deux exemples :

* **Données personnalisées d'enregistrement utilisateur**
  Supposons que vous créiez un champ utilisateur pour le *genre* à ajouter à un formulaire d'inscription. Il pourrait s'agir d'une liste ou de boutons radio permettant à l'utilisateur de sélectionner *Homme* ou *Femme*. Dans ce cas, l'autorisation pour le groupe Public doit être définie sur *Autorisé*. Sinon, un utilisateur invité ne pourra pas sélectionner de genre. Comme tous les autres groupes héritent du groupe Public, un utilisateur enregistré pourra modifier le genre de son profil après s'être connecté.
* **Commentaire d'article**
  Supposons que vous souhaitiez permettre à un auteur d’ajouter un commentaire à un article. Il pourrait s’agir d’un champ texte de longueur limitée. Dans ce cas, l’autorisation pour le groupe Auteur doit être définie sur *Autorisé*. Les groupes Éditeur et Publieur hériteront de ce paramètre lors de l’enregistrement du formulaire. Les groupes Gestionnaire et Administrateur ont la permission de modifier les articles, mais pas les valeurs des champs personnalisés, sauf si la valeur pour le groupe Gestionnaire est également définie sur *Autorisé*.

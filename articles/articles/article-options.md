<!-- Filename: J6.x:_Article_Options / Display title: Article : Modifier - Options  -->

## Introduction

Le terme *Options* est ambigu dans Joomla ! Il est parfois interchangeable avec *Paramètres* et la plupart des vues de liste de composants ont un bouton *Options* dans la barre d'outils. Cela conduit à une page des Options où les paramètres pour l'ensemble du composant sont définis. De plus, de nombreux formulaires d'édition d'éléments de composant ont un onglet intitulé *Options* utilisé pour définir les paramètres pour cet élément spécifique.

Cet article concerne l'onglet *Options* dans le formulaire *Article : Modifier*. C'est là où les paramètres sont définis pour influencer l'apparence générale de l'article en cours de modification. Les options pour les articles dans leur ensemble sont traitées dans un article séparé.

## Capture d'écran

L'onglet *Options* du formulaire *Article : Édition* comprend une série de panneaux offrant principalement le choix entre *Utiliser global (Masquer ou Afficher)*, *Masquer* ou *Afficher*. La capture d'écran partielle suivante montre la disposition générale.

![Onglet des options d'édition d'articles](../../../en/images/articles/articles-edit-options-tab.png)

## Panneau de disposition

Un article, ou une partie de celui-ci, peut apparaître en tant que page unique ou dans une disposition de blog de catégorie contrôlée par un élément de menu. Dans un élément de menu de blog, la plupart des champs de disposition ont des options *Utiliser Globale*, *Oui/Non* ou *Afficher/Masquer* et *Utiliser les paramètres de l'article*. Les options de ce panneau n'ont aucun effet dans les dispositions de blog à moins que l'option *Utiliser les paramètres de l'article* ne soit sélectionnée dans l'élément de menu.

Autrement, ces options affectent l'apparence de l'article unique en cours d'édition.

- **Disposition** Dans une installation par défaut, les deux premiers choix sont proposés :
  - **---Depuis les Options Globales--- / Utiliser Globale** Cela se réfère au paramètre *Articles : Options* disponible via le bouton *Options* dans la barre d'outils de la vue liste des *Articles*. Sa valeur *Choisir une disposition* est définie sur *Par défaut*.
  - **---Depuis le Composant--- / Par défaut** Cela se réfère au paramètre dans les réglages *Articles : Options*. Dans une installation par défaut, c’est effectivement la même chose que l’option *Utiliser Globale*. Mais si une substitution existe avec le nom default.php alors cette substitution est utilisée pour la disposition.
  - **---Depuis le modèle cassiopeia--- / nomdelasubstitution** Si une substitution de modèle a été créée avec un nom autre que *default*, elle apparaîtra ici et pourra être sélectionnée comme disposition alternative.
- **Titre** Il est normal d'afficher le titre d'un article, mais il peut y avoir des circonstances où cela n'est pas approprié. Sélectionnez *Masquer* pour omettre le titre de l'article de l'affichage de la page.
- **Titres liés** Le comportement par défaut est de faire du titre d'un article un lien vers l'article où il apparaît dans des dispositions de blog ou de liste. Ce paramètre est contrôlé par l'élément de menu. Il peut être réglé sur *Utiliser Globale (Oui)*, *Utiliser les paramètres de l'article*, *Non* ou *Oui*. Si l'élément de menu est défini sur *Utiliser les paramètres de l'article*, alors la valeur *Titres liés* dans l'article sera utilisée. Sinon, ce paramètre n'a aucun effet. Si le titre n'est pas lié, vous pouvez utiliser un lien *Lire la suite* pour accéder à l'article depuis une disposition de blog ou de liste.
- **Étiquettes** Montrer ou masquer les étiquettes sur la page de l'article unique.
- **Texte d'intro** Afficher ou masquer le texte d'intro sur la page de l'article unique. Il y a certaines circonstances où vous pouvez souhaiter avoir un texte d'intro complètement différent pour les dispositions de blog qui est laissé de côté dans le texte de l'article complet.
- **Position des infos sur l'article** Cela fait référence au bloc d'informations sur un article intitulé *Détails* et contenant les informations comme *Auteur*, *Catégorie*, *Publié* et *Vues*. Par défaut, ces informations se trouvent au-dessus du texte de l'article. Réglez sur *En dessous* pour déplacer ces informations en dessous du texte de l'article dans une vue d'article unique. Si réglé sur *Scindé*, l'élément *Vues* est déplacé en dessous du texte de l'article.
- **Titre des infos sur l'article** Afficher ou masquer le mot *Détails* au-dessus de la liste des informations de l'article en vue d'article unique.

## Panneau de catégorie

Les champs de ce panneau fonctionnent comme vous pourriez vous y attendre. Dans les vues de blog, les paramètres de l'élément de menu prennent le dessus, sauf s'ils sont réglés sur *Utiliser les paramètres de l'article*.

- **Catégorie** Afficher ou masquer le nom de la catégorie.
- **Lier la catégorie** Lier (Oui ou Non) le nom de la catégorie. Si réglé sur *Oui*, le nom de la catégorie est lié à son blog de catégorie.
- **Catégorie parente** Si réglé sur Oui, la catégorie parente apparaît comme un élément distinct au-dessus de la catégorie dans les informations de l'article *Détails* dans la disposition d'un seul article.
- **Lier la catégorie parente** Si réglé sur Oui, le nom de la catégorie parente est lié à sa page de blog de catégorie.

## Panneau des associations

Ce panneau est uniquement présent sur les sites multilingues.

- **Associations** Si défini sur Afficher, un élément supplémentaire est placé dans les informations de l'article commençant par *Également disponible :* suivi de drapeaux pour représenter les versions de cet article disponibles dans d'autres langues.
- **Utiliser les drapeaux d'images** Cet élément apparaît si *Associations* est défini sur *Afficher*. Le paramètre par défaut *Oui* affiche des boutons sous forme de drapeaux de langue. L'alternative *Non* affiche des boutons sous forme de codes de langue, par exemple *en-GB*.

## Panneau de l'auteur

- **Auteur** Afficher ou masquer le nom de l'auteur de cet article dans la vue d'un seul article. La ligne dans les informations de l'article indique *Écrit par : Nomdel'auteur*
- **Lien vers la page de contact de l'auteur** Oui ou non pour lier le Nomdel'auteur à la page de contact de l'auteur s'il y en a une.

## Panneau des dates

Les articles Joomla stockent plusieurs dates. Si elles sont affichées, chacune des dates suivantes apparaît comme des lignes séparées dans les informations d’un seul article. Rappelez-vous, les mises en page de blog utilisent les paramètres de l’élément de menu, sauf s’il est défini sur *Utiliser les paramètres de l’article*. Le format de la date est 03 novembre 2024, mais cela peut être modifié ...[À Faire]

- **Date de création** Cachée par défaut.
- **Date de modification** Cachée par défaut.
- **Date de publication** Affichée par défaut.

## Panneau d'options

- **Navigation** Pour un article qui fait partie d'une série d'articles dans une catégorie, il y a des boutons *Précédent* et *Suivant* sous le texte de l'article pour naviguer vers les pages précédentes ou suivantes. Si l'option est réglée sur *Masquer*, les boutons de navigation ne sont pas affichés sur les pages d'un article unique.
- **Affichages** Le nombre total de fois que l'article a été affiché en tant qu'article unique, indiqué dans la liste d'informations de l'article.
- **Liens non autorisés** Cela affecte les mises en page du blog, donc l'élément de menu du blog de la catégorie concernée doit avoir sa valeur *Options : Liens non autorisés* réglée sur *Oui* ou *Utiliser les paramètres de l'article*. Ensuite, si l'*Accès* de cet article est réglé sur *Enregistré* et que le paramètre dans l'article n'est pas *Non*, le *Texte d'introduction* de l'article s'affichera dans la mise en page du blog mais l'étiquette du bouton Lire la suite sera *Inscrivez-vous pour lire la suite...*. Cliquer sur le lien Lire la suite nécessitera de se connecter pour voir le contenu complet de l'article.
- **Position des liens** Cela se réfère au positionnement des liens dans l'onglet Images et Liens, Liens A, B et C. La position par défaut est au-dessus du texte de l'article. Cette option permet de placer les liens sous le texte de l'article ou de ne pas les afficher du tout.
- **Texte Lire la suite** Le texte normal, *Lire la suite :* suivi du titre de l'article est tiré des valeurs de clé/chaîne de langue. Une substitution personnalisée pour cet article uniquement peut être saisie ici, par exemple *Voir l'article complet :* suivi du titre de l'article.
- **Titre de la page du navigateur** Le titre de la page est généralement le titre de l'article. Si cela n'est pas pratique, un titre de page alternatif peut être saisi ici pour être utilisé sur la page de l'article unique. Il apparaît dans l'onglet du navigateur et dans la zone `<head>...</head>` de la page. Il sera utilisé par les moteurs de recherche.
*Traduit par openai.com*


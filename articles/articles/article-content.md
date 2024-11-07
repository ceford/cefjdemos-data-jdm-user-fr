<!-- Filename: J4.x:Adding_a_New_Article / Display title: Article : Modifier - Contenu -->

## Introduction

*Ajouter un article* a été abordé dans un article *Pour commencer*. C'est le premier d'une série d'articles fournissant plus de détails sur le formulaire *Article : Édition*. Il couvre l'onglet *Contenu* et certains aspects de l'éditeur TinyMCE, l'éditeur par défaut fourni avec Joomla.

La capture d'écran suivante montre le formulaire d'édition avec un article qui a déjà été enregistré.

![Le formulaire d'édition de contenu](../../../en/images/articles/articles-edit-content.png)

## Saisie de Données

Le formulaire d'édition d'article dispose de panneaux à onglets. Un nouvel article a l'onglet **Contenu** sélectionné par défaut. Sinon, le dernier onglet ouvert est sélectionné.

### Le champ Titre

Le champ **Titre** est *Obligatoire* et est utilisé partout où le titre de l'article est affiché. C'est le seul champ qui doit contenir du texte afin de pouvoir enregistrer un formulaire d'édition.

Les titres doivent être courts mais descriptifs du contenu de l'article car ils apparaissent dans les listes et les éléments de menu où l'espace est limité.

Les titres n'ont pas besoin d'être uniques, bien qu'il soit préférable qu'ils le soient. Par exemple, si vous sélectionnez *Enregistrer sous copie* dans la liste déroulante *Enregistrer & Fermer*, le processus d'enregistrement enregistrera l'article actuel et générera un nouveau avec un numéro ajouté au Titre et à l'Aliase. Vous pouvez supprimer le numéro du Titre mais pas de l'Aliase et *Enregistrer* la copie. Cela donne deux articles avec le même titre d'affichage.

### Le champ Alias

Le champ *Alias* est généralement laissé vide. Lorsqu'un article est enregistré, l'Aliase est générée à partir du titre en mettant tout en minuscules et en remplaçant les caractères non alphanumériques par des tirets.

Si vous modifiez le titre de l'article, vous pouvez supprimer l'Aliase et une nouvelle sera générée. Si l'Aliase a été utilisée pour faire référence à l'article dans des liens internes et externes, cela cassera les liens. Il est donc préférable de ne pas changer l'Aliase d'un ancien article.

### L'onglet Contenu - Texte de l'Article

La capture d'écran ci-dessus montre le texte de l'article dans un éditeur WYSIWYG qui ressemble plutôt à un traitement de texte. Cependant, vous devez être conscient que le texte de l'article est stocké sous forme de HTML et que le champ de saisie de données est en réalité un champ de zone de texte contenant ce HTML. Vous pouvez le voir par vous-même en sélectionnant le bouton *Basculer Éditeur* sous la zone d'édition. L'éditeur est en fait une application JavaScript qui réaffiche le HTML pour le rendre facile à lire et à manipuler.

#### Balises et Attributs HTML Interdits

Joomla ainsi que l'éditeur TinyMCE ont des paramètres qui interdisent certaines balises et attributs HTML. Par exemple, la liste interdite par défaut de Joomla inclut *iframe* donc si vous essayez d'inclure cette balise dans un article, elle sera supprimée sans avertissement lors de l'enregistrement. Les filtres de texte sont définis dans la *Configuration Globale*. Le plugin TinyMCE a une option pour *Utiliser le Filtre de Texte Joomla*. S'il est réglé sur *Off*, il liste *script,applet,iframe* en tant qu'*Éléments Interdits*.

#### Barres d'Outils de l'Éditeur

Au-dessus de la zone de texte se trouvent des rangées de barres d'outils. Deux sont affichées par défaut. Les autres peuvent être basculées en sélectionnant le symbole des points de suspension (...) à la fin de la deuxième barre d'outils. Les barres d'outils peuvent être configurées pour montrer différentes barres et contenus de barres à différents groupes d'utilisateurs.

Il y a trop d'outils pour décrire chacun ici. Cela créerait une meule de foin pour que vous cherchiez une aiguille. Explorez simplement !

Cependant, il y a certaines fonctionnalités qui méritent une explication supplémentaire.

#### Contenu CMS

Ce bouton dévoile une liste déroulante qui permet l'inclusion d'éléments dans un article obtenus d'ailleurs dans le CMS.

- **Article** Ce lien affiche une liste contextuelle d'articles. Sélectionnez un article pour inclure un lien vers cet article dans l'article actuel.
- **Contact** Inclure un lien vers un Contact dans l'article actuel.
- **Champ** Inclure un champ dans l'article. Il est affiché sous la forme `{field 1}`.
- **Média** Inclure une image ou un fichier à partir d'une fenêtre contextuelle de composant Média.
- **Menu** Inclure un lien vers un élément de Menu à partir d'une liste contextuelle de Menu.
- **Saut de Page** Une invite pour un *Titre de Page* et un *Alias du Sommaire* est affichée. Cette fonctionnalité est utilisée pour diviser de longs documents en plusieurs pages.
- **Lire la suite** Un séparateur *Lire la suite...* est inséré à la position du curseur. Choisissez une coupure entre les paragraphes avant la sélection.

#### Liens Externes

L'élément **Insérer** dans la première barre d'outils propose des options pour insérer un *Lien...*, une *Image...* ou un *Média...*. Ceux-ci sont pour des éléments externes, préparez donc l'URL de l'élément à utiliser.

### L'onglet Contenu - Paramètres

L'onglet **Contenu** est principalement occupé par l'éditeur TinyMCE.

Parallèlement au contenu, il y a des champs pour gérer la publication, comment et où l'article sera affiché et qui peut le voir lorsqu'il est publié. Dans la plupart des cas, ces paramètres peuvent être laissés à leurs valeurs par défaut.

1. **Statut** *Publié*, *Non publié*, *Archivé* ou *Corbeille* - La valeur par défaut est *Publié*.
2. **Catégorie** C'est un champ *Obligatoire*, mais il sera par défaut sur *Non Catégorisé*. Vous pouvez sélectionner une catégorie dans la liste ou taper quelques caractères d'un nom de catégorie pour raccourcir la liste des catégories à choisir.
3. **En vedette** Basculer entre *Non* et *Oui* pour afficher l'article sur la page d'accueil si celle-ci utilise une mise en page *Articles en vedette*.
4. **Accès** Le niveau d'accès peut être modifié pour restreindre l'article aux Groupes d'Utilisateurs assignés à des *Niveaux d'Accès* spécifiques : *Public*, *Invité*, *Enregistré*, *Spécial* ou *Super Utilisateurs*.
5. **Étiquettes** Commencez à taper pour trouver et sélectionner des étiquettes prédéfinies ou vous pouvez en ajouter une nouvelle en la tapant et en **appuyant sur entrer**.
6. **Note** Tout commentaire sur cet article qui sera visible sous le Titre dans la page de liste des Articles.
7. **Note de Version** Ajoutez des commentaires pour indiquer ce qui a changé dans cette version. Ceci est affiché dans la boîte de dialogue modale *Versions* et le champ revient à vide après l'enregistrement.

### Autres Onglets

**Vous pourriez ne pas voir tous les onglets suivants** car un Administrateur de Site peut en cacher certains pour aider à maintenir la cohérence de la mise en page des articles à travers le site web. Vous pouvez également voir des onglets supplémentaires pour les *Champs Personnalisés* s'ils ont été configurés.

1. **Images et Liens** vous permet de définir une image d'introduction et une image à la une et/ou des liens à apparaître dans des positions prédéfinies. Cela peut être utilisé si votre article sera affiché dans un blog de catégorie.
2. **Options** vous permet de spécifier la mise en page de l'article et les informations associées telles que le titre, la catégorie, les étiquettes, les détails de publication, etc. Ceci est normalement défini globalement mais peut être spécifique à l'article grâce à ces options.
3. **Schéma** est une méthode pour ajouter des métadonnées à un article. Elle est utilisée par les robots mais non vue par les humains.
3. **Publication** vous permet de définir des dates et heures de publication pour planifier la publication d'un article. Par défaut, lorsqu'un article est enregistré, il sera publié immédiatement. Vous pouvez également définir les Métadonnées pour l'article.
4. **Configurer l'Écran d'Édition** vous permet de montrer ou de cacher des paramètres pour l'article.
5. **Permissions** montre les permissions pour chaque groupe d'utilisateurs qui contrôlent ce qui peut ou ne peut pas être fait.

Il existe des articles distincts sur chacun de ces onglets.


## Enregistrement de l'Article

Une fois que vous avez ajouté les informations et le contenu requis, vous pouvez enregistrer l'article. Il existe plusieurs façons de procéder, selon ce que vous souhaitez faire ensuite dans Joomla.

Pour enregistrer l'article, vous pouvez choisir *Enregistrer* ou *Enregistrer & Fermer*. Ce dernier a des options déroulantes pour *Enregistrer & Nouveau*, *Enregistrer dans le Menu* et *Enregistrer comme Copie*.

- **Enregistrer** Enregistrez l'article et gardez-le ouvert pour d'autres modifications. Il est conseillé de sauvegarder régulièrement votre travail sur des articles plus longs.
- **Enregistrer & Fermer** Enregistrez l'article et accédez à la liste des articles. Le bouton Enregistrer & Fermer propose d'autres options déroulantes :
  - **Enregistrer & Nouveau** Enregistrez l'article puis ouvrez une page **Articles: Nouveau**. Cette option permet de gagner du temps lorsque vous ajoutez plusieurs articles.
  - **Enregistrer dans le Menu** Enregistrez l'article et ouvrez une page **Menus: Nouvel Élément**.
  - **Enregistrer comme Copie** Enregistrez l'article puis ouvrez une page **Articles: Édition** avec un numéro entre parenthèses ajouté au titre et le même numéro suivant un tiret, -2 par exemple, dans le champ alias. Vous pouvez modifier le titre et changer ou supprimer l'alias du nouvel article qui a déjà été créé.

Un message système indiquera que l'article a été enregistré avec succès.

### Erreurs lors de la tentative d'enregistrement :

- Si vous n'avez pas rempli les champs requis, un message d'erreur rouge apparaîtra indiquant les informations manquantes que vous devez ajouter.
- Vous verrez un message d'erreur si l'article a un alias qui existe déjà. Vous pouvez résoudre ce problème en modifiant le champ alias.

## Conseils

- Si vous n'êtes pas le Super Utilisateur ou l'Administrateur, prenez le temps de comprendre comment le site web est configuré. Ce n'est pas parce que vous avez enregistré un article qu'il est visible sur le site. Si des pages de type Blog Catégorie sont utilisées, attribuer la bonne catégorie affichera l'article. Sinon, un article doit être attribué à un élément de menu. Vous pouvez le faire dans l'article ou via le menu **Menus** de l'Administrateur.
- Essayez de garder les titres des articles courts et spécifiques.
- Bien que ce soit possible, si plusieurs utilisateurs ajoutent des articles au site, évitez de créer de nouvelles catégories et étiquettes dans les articles. Les fautes d'orthographe et les différences peuvent facilement empêcher les articles d'apparaître là où ils étaient prévus. Créer des catégories et des étiquettes sur leur page de liste respective assure la cohérence sur l'ensemble du site.
- Si nécessaire, utilisez les notes d'article. Elles peuvent être très utiles, surtout lorsque plusieurs personnes ajoutent des articles.
- Où que vous soyez dans Joomla, vous pouvez ajouter un article sans passer par le Tableau de Bord Accueil - utilisez le Menu Administrateur Joomla.


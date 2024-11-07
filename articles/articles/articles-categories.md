<!-- Filename: J4.x:Create_and_Manage_Article_Categories / Display title: Articles : Catégories  -->

## Introduction

Imaginez une bibliothèque sans système de classification : les livres sont simplement placés sur les étagères dans l'ordre où ils ont été reçus. Ce n'est pas très utile si la bibliothèque contient des millions de livres et que vous cherchez quelque chose sur l'Histoire, le Jardinage ou la Science. Le même type de raisonnement s'applique aux articles. Si vous avez des dizaines, des centaines ou des milliers d'articles, vous avez vraiment besoin d'une méthode pour les classer afin de pouvoir facilement trouver ce dont vous avez besoin. C'est à cela que servent les Catégories.

Une catégorie Joomla ! peut contenir à la fois des articles et des sous-catégories dans une structure arborescente imbriquée à n'importe quelle profondeur, bien qu'il soit peu probable que vous souhaitiez aller au-delà d'une profondeur de trois ou quatre. Par exemple, si vos articles parlent de la Nature, vous pourriez les classer comme suit :

- Animaux
  - Oiseaux
    - Faucons
    - Pinsons
    - Goélands
  - Mammifères
    - Singes
    - Primates
    - Rongeurs
- Plantes
  - Fleurs
    - Marguerites
    - Roses
  - Arbres
    - Chênes
    - Ormes

Dans cet exemple, la catégorie *Animaux* pourrait contenir des articles sur les animaux en général ainsi que des sous-catégories pour des articles sur différents types d'animaux.

Joomla fournit une unique catégorie par défaut nommée Non classé. Tout article non assigné à une catégorie spécifique que vous avez créée devient membre de la catégorie Non classé. Vous créez les catégories nécessaires pour s'adapter à la nature de vos articles.

Un article ne peut appartenir qu'à une seule catégorie. Dans certaines circonstances, cela ne suffit pas tout à fait. Supposons par exemple que vous souhaitiez rechercher tous les livres écrits dans une langue particulière, ou toutes les plantes qui sont toxiques ou tous les animaux qui sont dangereux. C'est là que les Tags deviennent utiles. Ils sont abordés ailleurs.

### Utilisation des Catégories

Dans la page *Articles* de l'administrateur, le formulaire *Options de Filtrage* dispose d'une liste déroulante **- Sélectionner une catégorie -** qui affiche un arbre de catégories vous permettant de filtrer les articles dans une Catégorie sélectionnée. Vous pouvez également créer des types d'éléments de menu *Blog de Catégorie* et *Liste de Catégorie* pour afficher les articles d'une catégorie sélectionnée aux visiteurs du site.

## Ajout de Catégories et Sous-catégories

Il existe plusieurs chemins vers la page *Articles : Nouvelle Catégorie* :

- Via le **Tableau de Bord d'Accueil** Sélectionnez le **symbole plus (+)** à droite 
  du lien *Catégories d'Articles*. Ce lien mène à la page de liste *Articles : Catégories*.
- Via le **Menu Administrateur** Sélectionnez l'élément *Contenu* pour développer la liste 
  puis sélectionnez le **symbole plus (+)** à droite du lien *Catégories*.
- Via le **Tableau de Bord du Contenu** Sélectionnez l'icône du Tableau de Bord à droite du 
  lien *Contenu* dans le menu Administrateur, puis dans le panneau *Contenu* du tableau de bord, 
  sélectionnez le **symbole plus (+)** à droite du lien *Catégories*.
- Via **Articles : Catégories** Suivez l'un des chemins vers la page de liste et 
  sélectionnez le bouton **Nouveau** dans la barre d'outils.

La capture d'écran suivante montre le lien *Catégories d'Articles* sur le Tableau de Bord d'Accueil 
vers la liste des catégories et le *Symbole Plus* adjacent qui mène au formulaire 
*Articles : Nouvelle Catégorie*.

![L'icône d'ajout de catégorie mise en évidence sur le tableau de bord d'accueil](../../../en/images/articles/category-add-via-home-dashboard.png)  

## Les articles : Formulaire de nouvelle catégorie

![Le formulaire d'édition de nouvelle catégorie d'articles](../../../en/images/getting-started/article-category-edit.png)

La capture d'écran ci-dessus montre le formulaire rempli. Il n'y a que deux champs qui nécessitent un contenu. Tout le reste a des valeurs par défaut ou nulles que vous pouvez laisser pour l'instant et remplir plus tard si besoin est.

- **Titre** C'est le seul champ obligatoire. Il doit être court mais descriptif de la catégorie.

### L'onglet Catégorie

- **Description** Bien que non obligatoire, ce champ peut être affiché dans les pages de liste de catégories du site contrôlées par des éléments de menu. Vous devrez peut-être revenir et mettre à jour la Description plus tard.
- **Parent** Si réglé sur *- Pas de parent -*, cet élément est une catégorie parent potentielle pour d'autres catégories. Si une autre catégorie est sélectionnée comme parent, cet élément est une sous-catégorie.
- **Statut** Par défaut, une nouvelle catégorie est définie sur *Publié*. Vous pouvez changer le statut d'une catégorie en *Publié*, *Non publié*, *Archivé* ou *Mis à la corbeille*. 
  [À faire] Expliquer ce qui se passe lorsqu'une catégorie est non publiée...
- **Accès** Par défaut, l'accès est réglé sur *Public*. D'autres options pour restreindre l'accès sont *Invité*, *Enregistré*, *Spécial* et *Super Utilisateurs*.
  [À faire] Expliquer comment l'accès à une catégorie peut être utilisé...
- **Langue** Dans les sites multilingues, définir ceci sur *Tous* rendra la nouvelle catégorie indépendante de la langue du site. Si réglé sur une langue spécifique, elle ne sera disponible que sur les pages utilisant cette langue.
- **Tags** Si vous les utilisez, vous pouvez ajouter un ou plusieurs tags à la catégorie. Définir des tags au niveau de la catégorie est un bon moyen de maintenir la cohérence. Pour ce tutoriel, un tag *Nature* a été créé et utilisé pour filtrer les listes afin de n'afficher que les éléments liés aux tutoriels.
- **Note** et **Note de version** Utilisez-les pour ajouter des notes pertinentes si nécessaire.

### L'onglet Options

Les paramètres de cet onglet affectent l'apparence de cette catégorie dans les pages du site.

- **Mise en page** Cela se réfère au placement du contenu sur la page. Il peut y avoir un choix de mises en page selon le composant et le modèle utilisés.
  [À faire] Exemples...
- **Image** Vous pouvez souhaiter utiliser une image pour agir comme une icône de sorte que cette catégorie puisse être immédiatement reconnue dans une liste de catégories. Si utilisée à cette fin, une *Description de l'image (texte alterné)* n'est pas nécessaire mais la case *Pas de description* doit être cochée.

### Enregistrer & Fermer

- **Enregistrer & Fermer** Pour terminer l'édition de cette catégorie. Ou dans la liste déroulante...
  - **Enregistrer & Nouveau** Enregistrer cette catégorie et ouvrir un nouveau formulaire d'édition pour une nouvelle catégorie. Par exemple, vous pouvez souhaiter commencer à construire un arbre de catégories en ajoutant une catégorie *Singes* avec *Mammifères* comme parent.
  - **Enregistrer dans le menu en tant que liste** ...
  - **Enregistrer dans le menu en tant que blog** ...
  - **Enregistrer comme copie** ...

Fermer le formulaire d'édition mène à la page de liste **Articles : Catégories**.

![Une liste de catégories filtrée par tag Nature](../../../en/images/articles/categories-list.png)

### Enregistrer dans le menu en tant que liste

La sélection de cet élément dans le menu déroulant *Enregistrer & Fermer* enregistrera et fermera le formulaire d'édition de la catégorie et ouvrira un nouveau formulaire d'élément de menu avec toutes les données nécessaires pour créer une *Liste de Catégorie* pour cette catégorie. Vous pouvez souhaiter changer le *Titre*. Par exemple, cela pourrait être *Liste d'articles sur les mammifères* pour indiquer clairement qu'il s'agit probablement d'une liste d'articles.

Dans l'onglet *Affichage de la page*, essayez de régler le champ *Afficher l'en-tête de la page* sur *Afficher*. Cela affiche *Liste d'articles sur les mammifères* en tant qu'en-tête en gras en haut de la page, lui donnant une apparence globalement plus complète.

### Enregistrer dans le menu en tant que blog

La sélection de cet élément dans le menu déroulant *Enregistrer & Fermer* enregistrera et fermera le formulaire d'édition de la catégorie et ouvrira un nouveau formulaire d'élément de menu avec toutes les données nécessaires pour créer un *Blog de Catégorie* pour cette catégorie. Vous pouvez souhaiter changer le *Titre*. Par exemple, cela pourrait être *Blog d'articles sur les mammifères* pour que les derniers articles sur les mammifères soient mis en avant.

Dans l'onglet *Affichage de la page*, essayez de régler le champ *Afficher l'en-tête de la page* sur *Afficher*. Cela affiche *Blog d'articles sur les mammifères* en tant qu'en-tête en gras en haut de la page, lui donnant une apparence globalement plus complète.

La capture d'écran suivante montre l'affichage du site d'une page de blog de catégorie en développement.

![Page de blog de la catégorie Mammifères](../../../en/images/articles/article-mammals-articles-blog-site-view.png)

## Conseils

- Vous pouvez également créer des catégories d'articles depuis un article.
- N'oubliez pas que vous ne pouvez attribuer un article qu'à une seule catégorie.
- Étant donné que les catégories parentes et les sous-catégories peuvent avoir d'autres sous-catégories, planifiez et organisez les catégories avec soin. Une hiérarchie de catégories complexe peut devenir un défi à gérer.
- Une autre méthode pour regrouper le contenu dans Joomla est l'utilisation du composant **Tags**, qui vous permet d'ajouter plusieurs tags à vos articles. L'utilisation de catégories et de tags peut aider à minimiser le nombre de sous-catégories et offre un moyen efficace de structurer le contenu du site web et de fournir aux visiteurs plus de fonctionnalités pour naviguer dans le contenu du site.

*Traduit par openai.com*


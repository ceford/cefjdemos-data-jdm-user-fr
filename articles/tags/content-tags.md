<!--
{
    "source": "https://docs.joomla.org/J4.x:How_To_Use_Content_Tags_in_Joomla",
    "title": "\u00c9tiquettes de contenu",
    "description": " ",
    "author": ""
}
-->

## Introduction

Les étiquettes offrent un moyen simple et efficace d’organiser et d’afficher le contenu. 
Le **composant Étiquettes** permet d’utiliser des étiquettes individuelles pour différents 
types de contenu, notamment les articles, les catégories, les contacts et les fils d’actualité. Il permet également de créer des étiquettes parentes et enfants.

Contrairement aux **catégories** Joomla, où une seule catégorie peut être affectée à
un élément, plusieurs étiquettes peuvent être affectées à un même élément, mais il n’est pas 
obligatoire d’affecter des étiquettes aux éléments.

Une fois qu’un élément est associé à une étiquette spécifique, cliquer sur le bouton de l’étiquette dans
un contenu affichant des étiquettes vous redirigera vers une page qui affiche une liste de
tous les éléments associés à cette étiquette. Pour cette
raison, les étiquettes sont souvent utilisées pour présenter des listes de contenu *filtrées*.

Les étiquettes peuvent être ajoutées à plusieurs endroits, ce qui offre une grande flexibilité lors de leur création.

## Considérations

Avant de commencer, réfléchissez à l’objectif des étiquettes sur le site, en particulier
si d’autres personnes ajoutent du contenu. Si elles ne sont pas ajoutées et gérées
correctement, les étiquettes peuvent devenir contre-productives. Parmi les problèmes courants figurent
l’ajout, par les rédacteurs, de nouvelles étiquettes inutiles et de noms d’étiquettes mal orthographiés.
Certains administrateurs du site peuvent choisir de modifier les permissions d’accès afin que 
seuls certains utilisateurs puissent ajouter de nouvelles étiquettes.

La capture d’écran suivante montre des étiquettes utilisées sur un site contenant des articles sur les 
sites du patrimoine mondial de l’UNESCO. Dans ce cas, chaque étiquette possède une couleur distinctive. 

![la page de liste des étiquettes](../../../en/images/tags/content-tags/01-tags-example.png)

Lorsque des étiquettes sont créées, elles s’affichent sous forme de liens dans les éléments associés. 
Les styles et les positions des étiquettes sont définis par le modèle du site. Elles sont souvent 
présentées sous forme de boutons ou de libellés.

L’affichage des étiquettes peut être désactivé pour certains articles ou pour tous les articles ! Cela
peut sembler illogique, mais il s’agit d’une fonctionnalité utile lorsque les étiquettes sont utilisées, par 
exemple, pour filtrer le contenu selon des cas d’utilisation spécifiques.

## La liste des étiquettes

- Sélectionnez **Composants → Étiquettes** dans le menu d’administration.

Cette capture d’écran montre des étiquettes dans une structure utilisée pour un site multilingue.
Chaque langue possède une liste d’étiquettes avec une étiquette de langue comme parent. 
L’étiquette parente est utilisée dans les modules *Étiquettes populaires* et *Étiquettes similaires*.

![la page de liste des étiquettes](../../../en/images/tags/content-tags/02-tags-list.png)

Quelles que soient les méthodes utilisées pour créer les étiquettes, elles peuvent être trouvées dans cette liste.

- Sélectionnez le bouton **Nouveau** dans la barre d’outils pour créer une nouvelle étiquette.
- Sélectionnez le **Titre** d’une étiquette pour modifier une étiquette existante.

### L’onglet Détails de l’étiquette

![onglet d’options du formulaire de modification d’une étiquette affichant les classes CSS Bootstrap](../../../en/images/tags/content-tags/03-edit-tag-details-tab.png)

- **Titre** Il s’agit du seul champ *obligatoire*. 
- **Alias** Il est créé à partir du titre lors de l’enregistrement.
- **Description** Il est toujours préférable d’ajouter une description. Elle s’affiche dans 
  les formulaires de l’administration et peut être utile lorsque de nombreuses étiquettes sont utilisées.
- **Parent** Laissez *Aucun* s’il s’agit d’une étiquette qui n’a pas de parent. Ou choisissez une 
  étiquette parente dans la liste pour en faire une étiquette enfant.
- **Statut** Ce champ est défini sur *Publié* par défaut. Il peut être défini sur 
  *Non publié*, *Archivé* ou *Mis à la corbeille*.
- **Accès** Le niveau d’accès est Public par défaut.
- **Note** et **Note de version :** Si nécessaire, vous pouvez ajouter des notes.
- **Enregistrer et fermer** Si vous créez plusieurs étiquettes, vous pouvez sélectionner **Enregistrer et nouveau** pour créer une nouvelle étiquette.

### L’onglet Options

- **Mise en page** Plusieurs mises en page peuvent être proposées et vous pouvez créer votre propre mise en page avec une surcharge de modèle.
- **Classe CSS du lien de l’étiquette** Par défaut, les étiquettes s’affichent sous forme de bouton bleu. Vous pouvez saisir ici des déclarations de classe pour personnaliser l’apparence des étiquettes et attribuer des couleurs différentes à chacune. Exemple : `bg-danger-subtle border border-danger` sont des classes Bootstrap qui produisent un bouton rose avec une bordure rouge.
- **Image d’accroche et image complète** Définissez des images pour l’étiquette : une image d’accroche pour la liste des étiquettes et/ou une image complète pour la page de l’étiquette.

![onglet d’options du formulaire de modification d’une étiquette affichant les classes CSS Bootstrap](../../../en/images/tags/content-tags/04-edit-tag-options-tab.png)

### L’onglet Publication

- Définissez les métadonnées de la page de l’étiquette pour l’optimisation pour les moteurs de recherche (SEO).

## Méthodes de création alternatives

### Depuis un article

Il est possible d’ajouter de nouvelles étiquettes lors de la création ou de la modification d’un article. Dans
l’onglet Contenu de l’article, dans le **champ Étiquettes**, saisissez le nom de la nouvelle étiquette et
appuyez sur **Entrée** pour l’enregistrer et l’associer à l’article.

### Depuis une catégorie

Des étiquettes peuvent être ajoutées lors de la création ou de la modification d’une catégorie. Dans l’onglet **Catégorie**,
saisissez le nom de l’étiquette dans le **champ Étiquettes** et appuyez sur **Entrée** pour créer
et associer la nouvelle étiquette.

### Depuis un contact

Des étiquettes peuvent être ajoutées lors de la création ou de la modification d’un contact. Dans l’onglet 
**Nouveau contact/Modifier le contact**, saisissez le nom de l’étiquette dans le **champ Étiquettes** et appuyez sur 
**Entrée** pour créer et associer la nouvelle étiquette. Vous pouvez également ajouter de nouvelles étiquettes lors de la création de catégories de contacts.

### Depuis un fil d’actualités

Des tags peuvent être ajoutés lors de la création ou de la modification d’un nouveau fil d’actualités. Dans l’onglet **Nouveau/Modifier le fil d’actualités**, saisissez le nom du tag dans le **champ Tags** et appuyez sur **Entrée** pour créer et attribuer le nouveau tag. Vous pouvez également ajouter de nouveaux tags lors de la création de catégories de fils d’actualités.

## Gestion des tags

Où que vous ajoutiez de nouveaux tags dans Joomla, ils apparaîtront tous dans la liste des tags.
Utilisez la liste des tags pour rechercher, ouvrir et ajuster les paramètres des tags.

Vous pouvez manipuler la liste de plusieurs façons :

- Rechercher un tag en utilisant tout ou partie de son titre ou de son alias dans le champ de recherche.
- Réorganiser la liste par glisser-déposer afin d’optimiser l’ordre d’affichage.
- Publier ou dépublier des tags à l’aide du bouton de la colonne Statut.
- Sélectionner un ou plusieurs tags et utiliser le bouton **Actions** pour publier, dépublier, archiver, déverrouiller ou mettre à la corbeille les tags sélectionnés.
- Sélectionner un ou plusieurs tags et utiliser le bouton **Actions → Traitement par lots** pour définir la langue ou le niveau d’accès.

## Affichage des tags

Une fois les tags créés sur votre site, ils sont disponibles pour être utilisés dans le contenu et dans des modules tels que **Tags populaires** et **Tags similaires**. Les exemples suivants montrent à quoi cela peut ressembler sur un site utilisant le template par défaut **Cassiopeia**.

![tags affichés dans un article et dans les modules de tags populaires et de tags similaires](../../../en/images/tags/content-tags/05-tag-modules-site-view.png)

Lorsque vous sélectionnez l’un des tags, vous êtes dirigé vers une page qui répertorie
tous les éléments associés à ce tag particulier :

![exemple d’utilisation des tags sur un site avec un labrador noir](../../../en/images/tags/content-tags/06-items-with-cultural-site-tag.png)

La liste des éléments est une liste filtrée du contenu du site comportant le tag sélectionné.
Une zone de filtre est fournie pour faciliter la recherche d’éléments à mesure que la liste s’allonge. 
Vous pouvez également définir le nombre de résultats à afficher dans une seule vue.

## Configuration des tags

Les tags individuels héritent des paramètres définis dans les options du composant Tags. Sélectionnez le bouton **Options** dans la barre d’outils de la page de la liste des tags pour afficher les options par défaut disponibles pour les tags.

Les options de configuration du composant Tags peuvent être remplacées au niveau de l’élément de contenu et/ou de l’élément de menu.

## Conseils

- N’oubliez pas que les tags sont utilisés dans plusieurs types de contenu.
- Vous pouvez ajouter plusieurs tags à un élément.
- Utilisez le bouton d’aide de la barre d’outils en cas de doute.

*Traduit par openai.com*
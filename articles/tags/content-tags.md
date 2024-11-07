<!-- Filename: J4.x:How_To_Use_Content_Tags_in_Joomla / Display title: Balises de Contenu  -->

## Introduction

Les balises offrent un moyen simple et efficace d'organiser et d'afficher le contenu. Le **Composant de Balises** permet d'utiliser des balises à travers différents types de contenu, y compris les articles, les catégories, les contacts et les flux d'actualités. Il permet également la création de balises parentes et enfants.

Contrairement aux **Catégories** de Joomla, où une seule catégorie peut être assignée à un élément, plusieurs balises peuvent être attribuées à un même élément, mais il n'est pas obligatoire d'attribuer des balises aux éléments.

Lorsqu'un élément est balisé avec une balise spécifique, cliquer sur le bouton de la balise sur un contenu affichant des balises vous redirigera vers une page affichant une liste de tous les éléments qui ont été marqués avec cette balise particulière. Pour cette raison, les balises sont souvent utilisées comme un moyen de présenter des listes *filtrées* de contenu.

Les balises peuvent être ajoutées à plusieurs endroits, offrant ainsi une flexibilité dans la création de balises.

## Considérations

Avant de commencer, considérez l'objectif des tags sur le site web, en particulier si d'autres personnes ajouteront du contenu. À moins qu'ils ne soient ajoutés et gérés correctement, les tags peuvent devenir contre-productifs. Les problèmes courants incluent les rédacteurs de contenu qui ajoutent de nouveaux tags inutiles et des noms de tags mal orthographiés. Certains administrateurs de site peuvent choisir de modifier les autorisations d'accès afin que seuls des utilisateurs spécifiques puissent ajouter de nouveaux tags.

Lorsqu'ils sont créés, les tags s'afficheront sous forme de liens dans les éléments tagués. Les styles et positions des tags sont définis par le modèle du site. Ils sont souvent stylisés comme des boutons ou des étiquettes.

L'affichage des tags peut être désactivé ! Cela peut sembler illogique, mais c'est une fonctionnalité utile lorsque les tags sont utilisés, par exemple, pour filtrer le contenu pour des cas d'utilisation spécifiques.  

## La liste des balises

- Sélectionnez **Composants → Balises** dans le menu Administrateur.

![la page de la liste des balises](../../../en/images/tags/tags-list.png)

Quel que soit le mode de création des balises, elles peuvent être trouvées dans cette liste.

## Ajout de Tags

### Via la Liste des Tags

Sélectionnez le bouton **Nouveau** dans la barre d'outils de la liste des Tags.

![nouveau tag nommé predator](../../../en/images/tags/new-tag-predator.png)

- **Titre** C'est le seul champ *obligatoire*.
- **Alias** Celui-ci est créé à partir du Titre lors de la sauvegarde.
- **Description** Il est toujours préférable d'ajouter une Description. Elle est affichée dans les formulaires de l'Administrateur et peut être utile lorsque de nombreux tags sont utilisés.
- **Parent** Laissez défini sur *Aucun* si c'est un tag parent racine. Ou choisissez un tag parent dans la liste si c'est un tag enfant.
- **Statut** Ce champ est défini par défaut sur *Publié*. Il peut être réglé sur *Non publié*, *Archivé* ou *Mis à la corbeille*.
- **Accès** Le niveau d'accès est Public par défaut.
- **Note** et **Note de version :** Si nécessaire, vous pouvez ajouter des notes.
- **Enregistrer & Fermer** Le nouveau tag apparaîtra dans la liste des Tags. Si vous créez plusieurs tags, vous pouvez choisir de cliquer sur **Enregistrer & Nouveau** pour en créer un autre.

Une fois sauvegardé, le tag sera disponible pour être utilisé dans les divers types de contenus qui les utilisent.

### Depuis un Article

Il est possible d'ajouter de nouveaux tags lors de la création ou la modification d'un article. Dans l'onglet Contenu de l'article, dans **Champ de Tags**, entrez le nom du nouveau tag et appuyez sur **Entrée** pour enregistrer et assigner le tag à l'article.

### Depuis une Catégorie

Les tags peuvent être ajoutés lors de la création ou de la modification d'une catégorie. Dans l'onglet **Catégorie**, entrez le nom du tag dans le **Champ de Tags** et appuyez sur **Entrée** pour créer et assigner le nouveau tag.

### Depuis un Contact

Les tags peuvent être ajoutés lors de la création ou la modification d'un Contact. Dans l'onglet **Nouveau/Modifier le Contact**, entrez le nom du tag dans le **Champ de Tags** et appuyez sur **Entrée** pour créer et assigner le nouveau tag. Vous pouvez également ajouter de nouveaux tags lors de la création de Catégories de Contacts.

### Depuis un Flux d'informations

Les tags peuvent être ajoutés lors de la création ou la modification d'un nouveau Flux d'informations. Dans l'onglet **Nouveau/Modifier le Flux d'informations**, entrez le nom du tag dans le **Champ de Tags** et appuyez sur **Entrée** pour créer et assigner le nouveau tag. Vous pouvez également ajouter de nouveaux tags lors de la création de Catégories de Flux d'informations.

## Gestion des Tags

Lorsque vous ajoutez de nouveaux Tags dans Joomla, ils apparaissent tous dans la liste des Tags. Utilisez la liste des Tags pour trouver, ouvrir et ajuster les paramètres des tags.

### Le Filtre de la Liste des Tags

![filtre de la liste des tags par type](../../../en/images/tags/tags-list-filter.png)

Vous pouvez manipuler la liste de plusieurs manières :

- Recherchez un tag en utilisant une partie ou l'ensemble de son titre dans le champ de recherche.
- Réorganisez la liste par glisser-déposer pour optimiser l'ordre de sortie.
- Publiez ou dépubliez des tags en utilisant le bouton dans la colonne Statut.
- Sélectionnez un ou plusieurs tags et utilisez le bouton **Actions** pour Publier, Dépublier, Archiver, Vérifier ou Mettre à la corbeille les tags sélectionnés.
- Sélectionnez un ou plusieurs tags et utilisez le bouton **Actions → Batch** pour définir la Langue ou le Niveau d'accès.

### Paramètres du Tag

- Sélectionnez un **Titre** de tag pour apporter des modifications à ses paramètres.

Dans le formulaire d'édition du tag :

- Les paramètres de l'onglet **Détails du Tag** ont été abordés ci-dessus.
- L'onglet **Options** :
  - Modifiez la mise en page de la page du tag (la page qui apparaît lorsque vous cliquez sur le lien du tag - par exemple, monsite.com/tags/mon-tag). Cette mise en page est normalement le réglage par défaut et dépend du modèle.
  - Ajoutez une classe CSS pour appliquer un style différent (apparence) au lien pour le tag. Ceci est normalement utilisé uniquement par l'Administrateur du Site.
  - Définissez des images pour le tag - une image d'accroche pour la liste des tags et/ou une image complète pour la page du tag.
- L'onglet **Publication** : Définissez les métadonnées pour la page du tag pour l'Optimisation pour les Moteurs de Recherche (SEO).

## Comment Joomla Génère des Balises

Une fois que les balises ont été créées sur votre site, elles sont disponibles pour une utilisation non seulement dans le contenu, mais aussi dans certains modules utiles tels que **Balises Populaires** et **Balises Similaires**. Les exemples suivants montrent à quoi cela ressemble sur une installation standard utilisant le modèle par défaut **Cassiopeia**.

![exemple d'utilisation des balises site labrador jaune](../../../en/images/tags/tag-examples-yellow-labrador.png)

Lorsque vous cliquez sur l'une des balises, vous serez dirigé vers une page qui liste tous les éléments attribués à cette balise particulière :

![exemple d'utilisation des balises site labrador noir](../../../en/images/tags/tag-examples-black-labrador.png)

Cliquer sur une balise vous amènera à une page qui affiche une liste de tous les éléments assignés à cette balise particulière - il s'agit en effet d'une liste filtrée du contenu de votre site web balisé. Une boîte de filtre est fournie pour faciliter la recherche d'éléments à mesure que la liste s'allonge. Vous pouvez également définir le nombre de résultats que vous souhaitez voir dans une seule vue.

## Configuration des balises

Les balises individuelles héritent des paramètres des options du composant de balises. Cela est couvert dans un tutoriel séparé. [À faire] Sélectionnez le bouton **Options** dans la barre d'outils de la page Liste des balises.

La configuration du composant de balises peut être remplacée au niveau des éléments de menu.

## Conseils

- N'oubliez pas que les Tags sont utilisés pour plusieurs types de contenu
- Vous pouvez ajouter plus d'un Tag à un élément
- Utilisez le bouton Aide en cas de doute

*Traduit par openai.com*


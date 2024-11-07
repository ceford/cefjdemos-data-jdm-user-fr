<!-- Filename: J4.x:Managing_Media / Display title: Gestion des Médias   -->

## Introduction

Dans Joomla, les médias sont des images et des fichiers qui apparaissent comme des illustrations ou des liens dans les articles, modules, modèles, etc. Une caractéristique importante des médias est qu'ils sont livrés directement par le serveur web sans être traités par le code Joomla. C'est rapide et efficace. Sachez également que les médias sont généralement stockés dans le dossier **images** de votre site Joomla. Ne confondez pas cela avec le dossier **media**, qui contient des fichiers JavaScript et de feuilles de style.

Les médias d'images et de fichiers sont gérés avec le composant Média de Joomla. Il vous permet d'organiser le contenu multimédia dans un arbre de dossiers, de télécharger des éléments individuels, d'effectuer certaines fonctions élémentaires de retouche d'image, et de placer des images et des liens directement dans les articles.

## Comment accéder

Depuis l'interface d'administration de Joomla, il existe plusieurs façons d'ouvrir le composant Média :

- Sélectionnez **Contenu → Médias** dans le menu de l'administrateur.
- Sélectionnez **Panneau du site → Médias** depuis le tableau de bord principal.
- Sélectionnez **Contenu CMS → Médias** depuis l'écran de modification d'un article.

Dans les deux premiers cas, le composant Média apparaît dans un écran de composant normal. Dans le dernier cas, il apparaît dans une boîte de dialogue modale.

## Capture d'écran

L'image suivante montre la page Média juste après l'installation de Joomla, mais avec le dossier cassiopeia/sampledata sélectionné. Un dossier *fichiers* a été ajouté pour stocker des fichiers non-images et un dossier supplémentaire nommé *poubelle* a été ajouté pour illustrer la suppression de dossiers :

![Page Média montrant les données d'exemple cassiopeia](../../../en/images/media/media-sample-data-cassiopeia.png)

## Gestion des Dossiers

Les noms des sous-dossiers dans votre arborescence de dossiers d'images deviennent une partie de l'URL de l'image. Il est donc important, pour des raisons de lien et d'optimisation pour les moteurs de recherche, que les noms respectent une convention :

- tout en minuscules
- pas d'espaces ou de ponctuation
- si nécessaire, utilisez un tiret pour créer des mots lisibles, par exemple arbres-à-feuillage-caduque plutôt qu'arbres_feuillage_caduque.

Avant de créer beaucoup de contenu pour votre site, il peut être judicieux de réfléchir à la manière dont vous pourriez catégoriser votre contenu et peut-être créer une arborescence de dossiers d'images similaire à votre arborescence de catégories. Sinon, vous pourriez vous retrouver avec un très grand nombre d'images et de fichiers à la racine de votre arborescence d'images, ce qui deviendrait difficile à gérer. Si vous décidez de déplacer les images dans une meilleure structure plus tard, vous devrez retrouver les liens vers ces images dans vos articles et les modifier. Cela pourrait être une tâche longue et décourageante !

### Navigation dans les Dossiers

Utilisez l'arborescence de dossiers dans la colonne **Locale** pour sélectionner un dossier. Dans l'exemple illustré ci-dessus, le dossier cassiopeia a d'abord été sélectionné. Cela a révélé le dossier *sampledata*, qui a ensuite été sélectionné pour montrer son contenu.

L'emplacement actuel est également indiqué dans le fil d'Ariane au-dessus des images. Dans ce cas **images → cassiopeia → sampledata**.

Si vous sélectionnez un dossier différent, le dossier précédent au même niveau se ferme.

### Création d'un dossier

- Sélectionnez le dossier parent sous lequel le nouveau dossier doit être créé.
- Sélectionnez le bouton **Créer Nouveau Dossier**.
- Dans la fenêtre contextuelle *Créer Nouveau Dossier*, entrez un nom pour le dossier dans le champ **Nom du Dossier**.
- Cliquez sur le bouton **Créer**.
- Le nouveau dossier apparaîtra dans le dossier parent sélectionné avec un message système de succès vert.

### Suppression d'un dossier

**Attention : la suppression d'un dossier supprimera également tout le contenu du dossier !**

- Sélectionnez le parent du dossier à supprimer en utilisant l'arborescence de répertoires affichée sous **Locale**. Cela montrera tous les dossiers et fichiers dans le parent.
- Déplacez le curseur sur le dossier à supprimer dans la zone des médias. Il deviendra gris et un bouton apparaîtra près du coin supérieur gauche.
- Sélectionnez le bouton. Une coche apparaîtra pour indiquer qu'il est sélectionné.
- Sélectionnez le bouton **Supprimer** dans la barre d'outils.
- Dans la boîte de dialogue contextuelle **Confirmer la Suppression**, sélectionnez le bouton **Supprimer**. Le dossier sera supprimé avec tous ses fichiers, sous-dossiers et leurs fichiers.

Le dossier sélectionné pour la suppression est illustré ci-dessous :

![Page Média montrant le dossier poubelle](../../../en/images/media/media-sample-data-garbage-select.png)

## Barre d'outils de la zone média

Ceci est la barre au-dessus de la liste des images, fichiers et dossiers qui possède des boutons pour une variété de tâches.

### Case à cocher

Une case à cocher qui vous permet de sélectionner tous les éléments du dossier affiché dans la zone média. Vous pourriez l'utiliser pour supprimer tous les éléments actuels sans supprimer le dossier.

### Fil d'Ariane

Utilisez les noms de dossiers au-dessus de la zone média pour revenir en arrière dans la hiérarchie des dossiers.

Double-cliquez sur un nom de dossier dans la zone média pour ouvrir ce dossier.

### Recherche

Si vous avez une longue liste d'images et de fichiers, vous pouvez rechercher des éléments contenant n'importe quel groupe de caractères. La recherche est progressive : à mesure que vous ajoutez des caractères au terme de recherche, la liste se réduit pour n'inclure que ceux contenant cette chaîne de caractères.

### Agrandir

Utilisez les boutons d'agrandissement pour augmenter ou réduire la taille de la vignette. Selon la taille de votre écran, vous pouvez voir 2, 4, 6 ou 8 images vignette côte à côte.

### Vues en Liste ou Vignettes

En vue vignette, sélectionnez le symbole de liste pour passer à la vue liste. En vue liste, sélectionnez le symbole de vignette pour passer à la vue vignette. En vue liste, vous verrez des informations sur la taille et les dimensions de l'image, entre autres données.

### Icône d'Information

Sélectionnez l'icône d'information pour ouvrir un panneau latéral affichant des informations sur ce qui est sélectionné.

*Traduit par openai.com*


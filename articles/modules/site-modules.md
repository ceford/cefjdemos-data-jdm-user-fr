<!-- Filename: J4.x:Site_Modules / Display title: Modules du Site  -->

## Introduction

Les modules sont des extensions légères et flexibles utilisées pour afficher des extraits
d'informations dans des **boîtes** disposées autour d'un composant sur une page. Un
exemple bien connu est le module de connexion. Les modules sont attribués par élément de menu, vous pouvez donc décider d'afficher ou de masquer un module en fonction de la page
que l'utilisateur consulte actuellement.

Certains modules sont liés à des composants. Par exemple, le module **Dernières Nouvelles**
est lié au composant de contenu pour afficher des liens vers les articles les plus récents. Les modules n'ont pas besoin d'être liés à des composants. Ils n'ont même pas besoin d'être liés à quoi que ce soit et peuvent être simplement du HTML statique ou du texte.

Il peut y avoir plusieurs instances du même module. Par exemple, vous pouvez
utiliser une instance du module Image Aléatoire pour certaines pages et une autre
instance pour d'autres pages, chacune utilisant un dossier d'images différent pour sélectionner les images.

## Positions des modules

Les modules sont assignés à une position sur une page définie par le modèle en cours d'utilisation. L'illustration suivante montre une disposition schématique du modèle Cassiopeia :

![Diagramme de position du modèle Cassiopeia](../../../en/images/modules/cassiopeia-template-positions.png)

Et la liste suivante montre les positions de module disponibles par nom :

```xml
    <positions>
        <position>bandeau-supérieur</position>
        <position>sous-haut</position>
        <position>menu</position>
        <position>recherche</position>
        <position>bannière</position>
        <position>haut-a</position>
        <position>haut-b</position>
        <position>principal-haut</position>
        <position>principal-bas</position>
        <position>fil-ariane</position>
        <position>barre-latérale-gauche</position>
        <position>barre-latérale-droite</position>
        <position>bas-a</position>
        <position>bas-b</position>
        <position>pied-de-page</position>
        <position>debug</position>
    </positions>
```

## Ajouter un module de base

Les modules de base sont ceux fournis avec une nouvelle installation de Joomla. Il existe des milliers de modules supplémentaires disponibles auprès de fournisseurs tiers. Supposons que vous souhaitiez afficher une image aléatoire pour rendre votre site plus intéressant pour les visiteurs. Dans le menu Administrateur, sélectionnez **Contenu → Modules du site** pour voir la liste des modules de site déjà en cours d'utilisation :

![Liste des modules du site](../../../en/images/modules/cassiopeia-modules-list.png)

Sélectionnez le bouton Nouveau pour voir une liste des modules de site disponibles à installer :

![Modules du site disponibles](../../../en/images/modules/cassiopeia-modules-available.png)

Faites défiler la liste et sélectionnez le module Image aléatoire. Cela ouvrira le formulaire d'édition **Modules : Image aléatoire** prêt à être complété.

![Module d'image aléatoire](../../../en/images/modules/cassiopeia-module-random-image.png)

- **Titre** Il s'agit d'un champ obligatoire.
- **Type d'image** Le format par défaut est jpg.
- **Dossier d'images** Indiquez un chemin vers un dossier qui contient effectivement des images du type que vous avez sélectionné.
- **Lien** Une URL vers laquelle rediriger si l'image est sélectionnée.
- **Largeur** Force toutes les images à s'afficher avec cette largeur en pixels.
- **Hauteur** Laissez vide pour conserver le rapport d'aspect de l'image.
- **Position** Sélectionnez une position de module pour que le module apparaisse réellement sur une page. Dans l'illustration, sidebar-right a été sélectionné.
- **Enregistrer & Fermer** Ou utilisez le bouton Aide dans la barre d'outils pour découvrir ce que font les autres champs.

## Ordre des Modules

Après avoir enregistré, vous pourriez avoir besoin de changer l’ordre des modules dans la position choisie. Procédez comme suit :

- Dans la liste des modules, sélectionnez l’icône de tri des colonnes dans l’en-tête du tableau des modules, c’est un triangle combiné haut/bas. Cela triera le tableau et affichera des symboles de saisie, une ellipsis verticale. Sélectionnez à nouveau pour inverser l’ordre de tri ! Le symbole de tri de colonne change : triangle vers le haut pour indiquer l’ordre de tri normal, triangle vers le bas pour indiquer l’ordre de tri inversé.
- Saisissez et faites glisser l’ellipsis de l’image aléatoire pour le déplacer vers le haut ou vers le bas. Relâchez lorsque l’élément est à la position souhaitée.

## Voir le Site

![Vue du site du module d'image aléatoire](../../../en/images/modules/cassiopeia-module-random-image-site.png)

Vérifiez l'apparence du site. Dans ce cas, il pourrait être judicieux de centrer l'image. Cela peut être fait comme suit :

- Retournez au formulaire de modification et sélectionnez l'onglet Avancé.
- Dans le champ Classe du module, entrez `text-center` et enregistrez.
- Visualisez le résultat en rechargeant la page du site.

Tout est terminé ?

## Liste des modules principaux

- **Articles - Archivés** Ce module affiche une liste des mois du calendrier contenant des articles archivés. Après avoir changé le statut d'un article en Archivé, cette liste sera automatiquement générée.
- **Articles - Catégories** Ce module affiche une liste de catégories à partir d'une catégorie parente.
- **Articles - Catégorie** Ce module affiche une liste d'articles provenant d'une ou plusieurs catégories.
- **Articles - Derniers** Ce module montre une liste des articles les plus récemment publiés et actuels.
- **Articles - Les plus lus** Ce module montre une liste des articles publiés qui ont le plus grand nombre de vues de page.
- **Articles - Flash Info** Le module Flash Info affichera un nombre fixe d'articles d'une catégorie spécifique.
- **Articles - Relatifs** Ce module affiche d'autres articles qui sont liés à celui qui est consulté. Ces relations sont établies par les mots-clés. Tous les mots-clés de l'article actuel sont recherchés par rapport à tous les...
- **Bannières** Le module Bannière affiche les bannières actives du composant.
- **Fil d'Ariane** Ce module affiche le fil d'Ariane.
- **Personnalisé** Ce module vous permet de créer votre propre module en utilisant un éditeur WYSIWYG.
- **Affichage de flux** Ce module permet d'afficher un flux syndiqué.
- **Pied de page** Ce module affiche les informations de copyright de Joomla!.
- **Sélecteur de langue** Ce module affiche un sélecteur de langue sur votre site Web pour les langues de contenu disponibles.
- **Derniers utilisateurs** Ce module affiche les derniers utilisateurs inscrits.
- **Connexion** Ce module affiche un formulaire de connexion avec nom d'utilisateur et mot de passe. Il affiche également un lien pour récupérer un mot de passe oublié. Si l'enregistrement des utilisateurs est activé (dans Utilisateurs → Gérer → Options),...
- **Menu** Ce module affiche un menu sur le Frontend.
- **Image aléatoire** Ce module affiche une image aléatoire de votre dossier choisi.
- **Recherche intelligente** Ceci est un module de recherche pour le système de Recherche Intelligente.
- **Statistiques** Le module des Statistiques montre des informations sur l'installation de votre serveur ainsi que des statistiques sur les utilisateurs du site et le nombre d'articles dans votre base de données.
- **Flux de syndication** Module de Syndication intelligent qui crée un flux syndiqué pour la page où le module est affiché.
- **Tags - Populaires** Ce module affiche les tags utilisés sur le site sous forme de liste ou de nuage. Les tags peuvent être triés par titre ou par le nombre d'éléments tagués et limités à une période spécifique.
- **Tags - Similaires** Le module Tags Similaires affiche des liens vers d'autres éléments avec des tags similaires. La proximité de la correspondance peut être spécifiée.
- **Qui est en ligne** Le module Qui est en ligne affiche le nombre d'utilisateurs anonymes (invités) et d'utilisateurs enregistrés (utilisateurs connectés) qui accèdent actuellement au site Web.
- **Wrapper** Ce module affiche une fenêtre iframe vers une localisation spécifiée.

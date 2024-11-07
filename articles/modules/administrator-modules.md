<!-- Filename: J4.x:Administrator_Modules / Display title: Modules administrateur -->

## Introduction

Le modèle Administrateur Atum est fourni avec un ensemble complet de modules Administrateur installés et configurés pour un usage quotidien. L'illustration suivante montre les positions du Tableau de Bord d'Accueil pour indiquer où les modules sont situés.

![positions du tableau de bord atum](../../../en/images/modules/atum-template-positions.png)

Dans l'illustration ci-dessus, les panneaux sont des instances du module Icône Rapide liées à des plugins quickicon.

### Notes sur certaines positions de Module

- **Haut Personnalisé** est au-dessus de la bannière et est utile si vous souhaitez publier un menu personnalisé ou un module personnalisé contenant un message important. Par exemple, pour avertir les administrateurs que le site fermera bientôt pour maintenance système.
- **Statut** est pour les icônes affichées alignées à droite dans la bannière.
- **Menu** est dans la barre latérale gauche de l'écran Atum.
- **Barre d'outils** est au-dessus de la zone de contenu principal dans les écrans de liste et d'édition mais n'est pas présente dans les écrans de tableau de bord.
- **Haut** est en dessous de la Barre d'outils mais au-dessus de tout Message Système et du contenu du composant.
- **Bas** est en dessous du contenu du composant.
- **Débogage** est en dessous de tout.

Positions du modèle Atum par nom

```xml
  <positions>
    <!-- utilisé directement dans le modèle -->
    <position>bas</position>
    <position>cpanel</position>
    <position>hautpersonnalise</position>
    <position>débogage</position>
    <position>icône</position>
    <position>connexion</position>
    <position>menu</position>
    <position>barrelatérale</position>
    <position>statut</position>
    <position>titre</position>
    <position>barredoutils</position>
    <position>haut</position>
  </positions>
```

## Ajouter un Module Personnalisé

Vous pouvez souhaiter ajouter un module personnalisé pour avertir les administrateurs d'un problème du système. Sélectionnez **Contenu → Modules Administrateur** dans le menu Administrateur. La liste des modules installés est assez longue :

![liste des modules admin atum](../../../en/images/modules/atum-admin-modules-list.png)

Sélectionnez le bouton Nouveau et ensuite le module Personnalisé. Dans le formulaire de modification Modules : Personnalisé, entrez un titre, un message personnalisé et sélectionnez une position pour le module. Dans l'exemple ci-dessous, la position Haut a été sélectionnée. De plus, dans l'onglet Avancé, champ Classe du module, certains styles ont été saisis pour centrer le texte et fournir un peu de marge intérieure : **alert alert-warning text-center**. Enregistrez pour voir le résultat. Fermez pour voir le résultat sur la page de la liste des modules.

![message système du module personnalisé atum](../../../en/images/modules/atum-admin-module-system-message.png)

Lorsque vous avez terminé avec le message, vous pouvez simplement sélectionner le bouton Statut dans la liste des modules pour Dépublier le module.

## Liste des Modules Administrateurs

- **Journaux d'Actions - Récents** Ce module affiche une liste des actions les plus récentes.
- **Menu Tableau de Bord Administrateur** Ce module affiche un sous-menu pour les administrateurs.
- **Menu Administrateur** Ce module affiche un menu pour les administrateurs.
- **Articles - Récents** Ce module affiche une liste des articles créés récemment.
- **Personnalisé** Ce module vous permet de créer votre propre module en utilisant un éditeur WYSIWYG.
- **Affichage de Flux** Ce module permet l'affichage d'un flux syndiqué.
- **Lien Frontend** Ce module montre un lien vers le frontend et doit être affiché dans la position 'statut'.
- **Informations sur la Version Joomla!** Ce module affiche la version de Joomla! et doit être affiché dans la position 'statut'.
- **Utilisateurs Connectés** Ce module affiche une liste des utilisateurs connectés.
- **Formulaire de Connexion** Ce module affiche un formulaire de connexion avec nom d'utilisateur et mot de passe. Il ne doit pas être dépublié.
- **Informations de Support à la Connexion** Ce module affiche quelques liens utiles vers les sites de support de Joomla sur l'écran de connexion.
- **Messages** Ce module montre le nombre de messages privés et doit être affiché dans la position 'statut'. Il est seulement affiché lorsqu'il y a des messages à lire.
- **Statut Multilingue** Ce module montre le statut des paramètres multilingues et doit être affiché dans la position 'statut'.
- **Articles Populaires** Ce module affiche une liste des articles publiés les plus populaires qui sont encore actuels. Certains articles affichés peuvent être expirés même s'ils sont les plus récents.
- **Messages Post-Installation** Ce module affiche un compteur et un lien vers les derniers messages post-installation. Il est seulement affiché lorsqu'il y a des messages à lire.
- **Tableau de Bord de Confidentialité** Le module Tableau de Bord de Confidentialité affiche des informations sur les demandes de confidentialité.
- **Vérification du Statut de Confidentialité** Le module Vérification du Statut de Confidentialité affiche des informations sur le statut de confidentialité de vos sites.
- **Icônes Rapides** Ce module affiche des icônes rapides visibles sur le tableau de bord d'accueil (page d'accueil de l'espace administrateur).
- **Données Exemples** Ce module vous permet d'installer des données exemples.
- **Statistiques** Le module Statistiques affiche des informations sur l'installation de votre serveur ainsi que des statistiques sur les utilisateurs du site et le nombre d'articles dans votre base de données.
- **Titre** Ce module affiche le titre du composant de la barre d'outils.
- **Barre d'outils** Ce module affiche les icônes de la barre d'outils utilisées pour contrôler les actions dans toute la zone d'administration.
- **Menu Utilisateur** Ce module affiche le Menu Utilisateur et doit être affiché dans la position 'statut'.


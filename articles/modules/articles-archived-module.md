<!-- Filename: J4.x:How_to_Show_a_Calendar_Month_List_of_Archived_Articles_Using_a_Module / Display title: Articles Archivés -->

## Introduction

L'archivage des articles est l'une des façons dont Joomla! aide à gérer les articles d'un site web, car cela contribue à réduire le désordre dans l'interface d'administration. Mais quels articles archivés les visiteurs du site devraient-ils pouvoir consulter ?

Une manière de le faire est d'afficher une liste mensuelle des articles archivés à l'aide de l'un des modules de base de Joomla. Dans cet exemple, un **module d'articles archivés** sera configuré pour s'afficher dans la barre latérale du site web.

## Créer le module *Articles - Archivés*

Utilisez l'une des méthodes suivantes :
* Sélectionnez l'élément **Modules** depuis le tableau de bord d'accueil. Ou bien...
* Sélectionnez **Contenu / Modules du site** dans le menu Administrateur.
* Sélectionnez l'élément **Articles archivés** dans la liste des modules (site).

Cela créera le nouveau module et ouvrira le module pour la configuration.

## Configuration du Module

Pour une utilisation standard du module, il suffit de régler quelques paramètres :

- **Titre** Entrez un nom pour le module.
- **\# de Mois** Définissez le nombre de mois que vous souhaitez afficher. Ceux-ci apparaîtront sous forme de liens sur le frontend. Réglez en utilisant les flèches haut/bas ou entrez directement un nombre dans le champ.
- **Afficher/Masquer le Titre** Choisissez d'afficher ou non le titre en basculant sur *Afficher* ou *Masquer*.
- **Position** Choisissez une position où vous souhaitez afficher le module sur le frontend. Les positions sont dictées par votre modèle. Cet exemple utilise la position *Sidebar Right* du modèle Cassiopeia de Joomla.
- **Statut** Par défaut, le statut du module est **Publié**. Les autres options sont **Non publié** et **Corbeille**.
- **Début de Publication** Vous pouvez planifier le début de la publication du module.
- **Fin de Publication** Vous pouvez planifier la fin de la publication du module.
- **Accès** Si vous souhaitez contrôler qui peut voir le module sur le frontend, vous pouvez choisir un niveau d'accès.
- **Ordre** Utilisé pour contrôler où le module s'affiche à l'intérieur de la position que vous avez sélectionnée. Par exemple, vous pouvez avoir plusieurs modules dans la barre latérale et vouloir que celui-ci soit au sommet ou en bas - ou quelque part entre d'autres dans la barre latérale. Cela peut être un peu déroutant au début car le champ montre une position numérotée et un nom de module. Le nom peut être un module qui n'est pas publié. Ce qu'il faut retenir, c'est que le nombre le plus bas sera en haut et le nombre le plus élevé en bas.
- **Note** Peut être utile d'utiliser le champ de note si, par exemple, vous utilisez le même type de module à plusieurs endroits.

### Onglet d'Attribution de Menu

Par défaut, le module sera publié **Sur toutes les pages**.

Vous pouvez alternativement choisir via une liste déroulante **Aucune page**, **Uniquement sur les pages sélectionnées** ou **Sur toutes les pages, sauf celles sélectionnées**. Les deux dernières options vous fournissent un arbre de menu des menus utilisés sur le site où vous pouvez sélectionner/désélectionner les pages.

### Autres Paramètres

L'onglet **Avancé** propose des paramètres liés à la mise en page du module lorsqu'il est affiché.

L'onglet **Permissions** vous permet de contrôler ce que les groupes d'utilisateurs peuvent faire avec le module.

## Publication du Module

Lorsque vous êtes prêt, sélectionnez le bouton **Sauvegarder & Fermer**.

Le module sera publié dans la barre latérale du site Web et affichera une liste de liens dictée par le nombre de mois à afficher définis dans le module.

![Exemple de Module d'Articles Archivés](../../../en/images/modules/modules-archived-articles.png)

## Conseils

Plus vous avez d'articles archivés, plus le nombre de liens affichés par le module est important. Il peut être plus approprié de limiter le nombre de liens en utilisant des catégories, ou vous pouvez utiliser plusieurs modules d'articles archivés nommés en conséquence.

*Traduit par openai.com*


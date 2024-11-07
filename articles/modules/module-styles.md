<!-- Filename: jdocmanual?manual=user&heading=modules&filename=module-styles.md / Display title: Styles de Module -->

## Concepts de Style

Un formulaire de saisie de données de module dispose d'un onglet **Avancé**. Ses champs varient en fonction du type de module, et vous pouvez le constater par vous-même en sélectionnant un module de Menu et en le comparant avec un module de Connexion ou un module de Fil d'Ariane. Vous verrez les trois champs de formulaire suivants liés au style :

* **Classe du Module** est un champ texte qui vous permet d'ajouter votre propre classe CSS à la balise conteneur du module, généralement un `<div>`.
* **Classe d'En-tête** est un champ texte qui vous permet d'ajouter votre propre classe CSS à la balise d'en-tête, par défaut une balise `<h3>`.
* **Style du Module** est une liste qui vous permet de sélectionner l'un parmi plusieurs styles standard. La liste comprend : aucun, html5, outline, table, card et noCard. Le style par défaut est card, issu des styles du modèle Cassiopeia.

Vous pouvez essayer les options de *Style du Module* en modifiant un module et en changeant sa valeur pour voir ce qu'il fait à l'affichage du site.

* **html5** donne `<div class="moduletable ">`
* **aucun** supprime complètement le `<div>` extérieur ainsi que la balise `<h3>` du module.
* **outline** donne `<div class="mod_preview_info">`, avec des informations de position et de style remplaçant la balise `<h3>` du module.
* **table** donne une mise en page de type tableau commençant par `<table class="moduletable ">` avec l'ancienne balise h3 maintenant une balise `<th>`.
* **card** donne `<div class="sidebar-right card ">`, par défaut.
* **noCard** donne `<div class="sidebar-right no-card ">`

## La Classe Module

À ce stade, vous devez connaître un peu les feuilles de style en cascade ou CSS. Si vous entrez un seul mot dans le champ de Classe de Module, disons **vert** puisque les classes CSS sont par convention en minuscules, et avec le Style du Module défini comme **hérité**, la sortie contient `<div class="sidebar-right card green">`.

Il n'y a aucun changement visible dans l'apparence du Site parce que la classe green n'est pas définie. Pour la définir, faites une entrée dans le fichier user.css du modèle.

Depuis le menu Administrateur :
* Sélectionnez **Système / Modèles de Site / Modèles et Fichiers Cassiopeia**.
* Sélectionnez **Nouveau Fichier** dans la *Barre d'outils*.
* Sélectionnez **css** dans la colonne de gauche, la destination pour le nouveau fichier.
* Tapez **user** dans le champ Nom de Fichier.
* Sélectionnez **css** dans la liste des Types de Fichier.
* Sélectionnez le bouton **Créer**.

Vous pouvez maintenant ouvrir le dossier css pour trouver et ouvrir le fichier user.css pour le modifier. Entrez ces déclarations de style et notez l'orthographe américaine de *color* :
```
.sidebar-right.card.green {
    background-color: #ddffdd;
}
.sidebar-right.card.green .card-body {
    background-color: #eeffee;
}
```
Le style aurait pu utiliser seulement `.green` mais cela aurait pu affecter d'autres balises avec ce style sur d'autres pages.

## La Classe d'En-tête

Retournez au formulaire d'édition du module et ajoutez **blue** dans le champ Classe d'En-tête. Le module n'a aucun changement visible sur le site, mais le titre apparaît maintenant comme `<h3 class="card-header blue">`. Retournez éditer le fichier user.css pour ajouter une entrée pour le style du titre :
```
.card-header.blue {
    color: navy;
}
```
Le titre du module est maintenant en bleu foncé. Il existe plusieurs façons de spécifier la couleur en CSS. Les plus courantes sont les valeurs hexadécimales et les noms de couleurs standards. Lisez tout à ce sujet ailleurs !

## Défi CSS

* Changez la couleur de la bordure du module en bleu marine !
* Changez également la bordure inférieure de l'en-tête.
* Appliquez ce style à plusieurs modules au lieu de les traiter un par un

![Exemple de module d'articles archivés](../../../en/images/modules/modules-archived-articles.png)

*Traduit par openai.com*


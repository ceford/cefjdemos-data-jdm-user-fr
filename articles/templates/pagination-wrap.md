<!--
{
    "source": "https://jdocmanual.org/jdocmanual?article=user/templates/pagination-wrap",
    "title": "Habillage de la pagination",
    "description": "D\u00e9couvrez une m\u00e9thode simple pour envelopper la liste de pagination sur les \u00e9crans \u00e9troits. ",
    "author": ""
}
-->

Dans Joomla, les listes d’articles, d’utilisateurs et d’autres éléments peuvent être très longues. Elles sont donc affichées par lots, de 20 éléments par défaut.

## La barre de pagination normale

Pour parcourir les lots, une barre de pagination située sous la liste des éléments permet à l’utilisateur de sélectionner le lot d’éléments suivant, comme dans cette illustration :

![barre de pagination normale d’une liste](../../../en/images/templates/pagination-wrap/01-pagination-wide-screen.png)

## Pagination sur les écrans étroits

La barre de pagination fonctionne bien sur les écrans larges. Cependant, sur les écrans étroits, la barre de pagination peut être plus large que l’écran. Cela oblige à faire défiler la page vers la droite pour trouver d’autres éléments sur la page, tels que les menus hamburger.

![la barre de pagination sur un écran étroit](../../../en/images/templates/pagination-wrap/02-pagination-narrow-screen.png)

Dans l’illustration ci-dessus, tous les éléments situés dans la zone grise à droite sont *initialement hors écran* et risquent de ne pas être vus. L’utilisateur doit faire défiler la page vers la droite pour les voir. Dans ce cas, les éléments hors écran sont l’icône de la barre d’outils en haut à droite et l’icône de menu en bas à droite.

## Correction avec une surcharge de modèle

Cette correction ajoute une classe *flex-wrap* dans le code qui génère la barre de pagination.

- Dans l’administration, allez dans Système > Modèles d’administration > Atum Details and Files
- Facultatif : sélectionnez html > layouts pour voir ce qui s’y trouve
- Sélectionnez l’onglet **Créer des surcharges**
- Dans la zone Layouts, sélectionnez **joomla**, puis **pagination**
- Dans l’onglet Éditeur, sélectionnez html > layouts > joomla > pagination > **links.php**
- Recherchez la ligne 70 contenant `<ul class="pagination ms-auto me-0">`
- Ajoutez `flex-wrap` à la liste des classes : `<ul class="pagination ms-auto me-0 flex-wrap">`
- **Enregistrer et fermer**
- Facultatif : vous pouvez supprimer /html/layouts/joomla/pagination/link.php et /html/layouts/joomla/pagination/links.php

Examinez le résultat sur des écrans larges et étroits. Sur un écran étroit, l’icône de la barre d’outils et l’icône du menu s’affichent désormais dans la largeur normale de l’écran :

![la barre de pagination modifiée sur un écran étroit](../../../en/images/templates/pagination-wrap/02-modified-pagination-narrow-screen.png)

Pour le modèle du site, suivez ces instructions, mais créez une surcharge dans le modèle Cassiopeia.

*Traduit par openai.com*
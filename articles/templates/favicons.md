<!-- Filename: J4.x:Favicons / Display title: Favicons  -->

## Les Favicons de Joomla!

Les favicons sont les petites icônes qui apparaissent dans l'onglet du navigateur à côté du nom de votre site. Près du haut du fichier index.php du modèle, il y a trois instructions pour charger des favicons dans la page :
```php
    // Les navigateurs prennent en charge les favicons SVG
    $this->addHeadLink(HTMLHelper::_('image', 'joomla-favicon.svg', '', [], true, 1), 'icon', 'rel', ['type' => 'image/svg+xml']);
    $this->addHeadLink(HTMLHelper::_('image', 'favicon.ico', '', [], true, 1), 'alternate icon', 'rel', ['type' => 'image/vnd.microsoft.icon']);
    $this->addHeadLink(HTMLHelper::_('image', 'joomla-favicon-pinned.svg', '', [], true, 1), 'mask-icon', 'rel', ['color' => '#000']);
```
Pour le modèle Cassiopeia, Joomla cherchera les favicons dans les emplacements suivants :

1.  **media/templates/site/cassiopeia/images** - ils ne s'y trouvent pas donc Joomla cherchera à l'emplacement suivant.
2.  **media/system/images** - ils s'y trouvent donc Joomla les utilisera à partir de là.

Si vous souhaitez utiliser vos propres favicons plutôt que les favicons Joomla, vous les téléchargez dans le premier emplacement :
**media/templates/site/cassiopeia/images**. Vous pouvez le faire en utilisant le formulaire Personnaliser : Modèles. Ils ne seront pas affectés par une mise à jour du modèle Cassiopeia.

Les favicons sont parfois utilisés à des tailles plus grandes et dans des endroits autres que l'onglet du navigateur. Par exemple, voici une capture d'écran d'une partie de la page de démarrage de Firefox montrant certains des emplacements favoris de l'utilisateur :

![exemples de favicons de la page de démarrage de Firefox](../../../en/images/templates/favicons-firefox-start-collection.png)

Tous les navigateurs modernes prennent en charge les icônes SVG, vous devriez donc donner la priorité à la création d'une icône SVG.

## À propos de SVG

SVG est un acronyme pour Scalable Vector Graphics (graphiques vectoriels évolutifs). Un fichier SVG contient du texte dans un format qui définit les emplacements et les formes des lignes avec des couleurs de ligne, des couleurs de remplissage, etc. La capture d'écran suivante montre le fichier *joomla-favicon.svg* ouvert dans un éditeur de texte. Les numéros de ligne sont créés par l'éditeur de texte. Ils ne sont pas présents dans le fichier. Les longues lignes représentent des courbes et sont tronquées ici pour des raisons d'affichage.

![contenu textuel du favicon joomla](../../../en/images/templates/favicons-joomla-favicon-svg-text.png)

Pour créer un fichier SVG, vous devez utiliser une application appropriée telle qu'Inkscape. Les applications de graphisme raster comme Photoshop ou The GIMP ne conviennent pas. Si vous préférez concevoir une icône dans une application de graphisme raster, ou si vous avez un logo graphique raster existant qui peut être adapté pour une icône, vous pouvez importer le fichier PNG résultant dans Inkscape et le tracer pour produire un fichier SVG. L'image tracée doit être supprimée après le traçage !

La création effective d'un favicon SVG dépasse le cadre de cet article. La création d'un fichier *favicon.ico* standard à partir d'un fichier *joomla-favicon.svg* est très simple — beaucoup de sites le font en ligne gratuitement.

## Comment créer des favicons

Si vous souhaitez créer vos propres favicons, la meilleure façon de procéder est de créer un favicon SVG, puis d'utiliser un outil en ligne pour générer tous les autres formats à partir de celui-ci comme entrée. Dans cet exemple, une icône est nécessaire pour convenir à un modèle enfant nommé Cassiopeia Green. Une icône doit être carrée et ne pas être trop élaborée, car la taille d'affichage minimale est de 16x16 pixels. Certains appareils nécessitent des résolutions plus élevées, telles que 32x32 ou 180x180, et Google recommande des multiples de 48x48 pixels. Si vous commencez avec un SVG, vous n'avez pas à vous soucier de tout cela - créez simplement une image presque carrée avec un design approprié. Dans cet exemple, le favicon sera les lettres *J4* en vert foncé.

### Inkscape

Inkscape est une application graphique vectorielle gratuite, open source et multiplateforme utilisée pour travailler avec des fichiers SVG. Elle fonctionne sur Linux, Mac et Windows. Rendez-vous sur le site Inkscape (inkscape.org) pour télécharger une copie pour votre plateforme. Les illustrations suivantes montrent l'écran d'Inkscape en cours des instructions suivantes.

![inkscape avec favicon en préparation](../../../en/images/templates/favicons-inkscape-favicon.png)

### Créer un SVG

1. Démarrez Inkscape et ajustez la fenêtre à une taille confortable : sélectionnez Affichage / Zoom / Zoom Page
2. Sélectionnez l'outil Texte, marqué avec la lettre A dans la barre d'outils de gauche
3. Sélectionnez Arial, Normal, 48 et px
4. Faites glisser pour définir la boîte n'importe où sur la page
5. Entrez le texte : J4
6. Sélectionnez Affichage / Zoom Sélection
7. Sélectionnez Chemin / Objet en chemin - aucun changement visible mais les mots ne sont plus du texte
8. Sélectionnez Fichier / Propriétés du document
9. Sélectionnez Ajuster au contenu
10. Dézoomez pour une meilleure vue - mais assurez-vous que toutes les lettres restent sélectionnées
11. Réglez la boîte de hauteur à la même valeur que la boîte de largeur. Tapez-le !
12. Fermez la boîte de dialogue Propriétés du document
13. Affichage / Zoom Page à nouveau - les caractères doivent être centrés
14. Édition / Tout sélectionner
15. Objets / Aligner et distribuer
16. Déplacez la sélection en groupe / Par rapport à la page / Centre sur l'axe horizontal - vous devriez voir J4 déplacer au point médian vertical
17. Sélectionnez Remplir et contour à droite - le panneau de droite a une liste déroulante marquée d'un chevron vers le bas
18. Dans le panneau Remplir et contour, sélectionnez Remplir et le premier carré rempli
19. Dans le panneau RVB, entrez 006400ff dans le champ RGBA en bas à droite - le code pour le style CSS *darkgreen*
20. Fichier / Enregistrer
21. Dans la boîte de dialogue Enregistrer, entrez un nom de fichier approprié, par exemple green-favicon-j4.svg
22. Sélectionnez un emplacement approprié, par exemple *~/Documents/joomla-dev/svgs*
23. Sélectionnez SVG optimisé (*.svg*) dans la liste déroulante en bas du formulaire.
24. Sélectionnez *Enregistrer*
25. Sélectionnez *OK* pour tous les Paramètres par défaut dans le formulaire de sortie SVG optimisé
26. Fermez le SVG sur lequel vous travaillez - il y a une opportunité de sauvegarder l'image au format Inkscape mais vous n'en avez pas vraiment besoin.

### Modifier le SVG avec un éditeur de texte

Démarrez votre éditeur de texte préféré pour apporter quelques modifications qui n'étaient pas possibles dans Inkscape.

1. Ouvrez votre fichier SVG nouvellement créé - remarquez que la première ligne est une spécification XML
2. Vous pouvez supprimer la deuxième ligne - un commentaire contenant Créé avec Inkscape
3. Si elle est présente, vous pouvez supprimer la ligne contenant car il n'y a pas de texte
4. Ouvrez le fichier original joomla-favicon.svg - il se trouve dans *joomla_root/media/system/images*
5. Copiez le bloc de style et collez-le dans votre SVG sur la ligne suivant la déclaration SVG
6. Fermez le fichier *joomla-favicon-svg* original pour éviter des modifications accidentelles
7. Dans le bloc de style de votre propre fichier SVG, changez path {fill: \#000;} par path {fill: \#006400;}, la valeur dans la ligne
8. Supprimez *fill="#006400"* de la ligne
9. Enregistrez
10. Ouvrez l'image dans votre navigateur. Pour Firefox, c'est Fichier / Ouvrir le fichier...

Vous devriez voir l'image dans votre navigateur. L'exemple montre J4 à 47 pixels carrés. La prochaine étape consiste à créer d'autres types d'icônes dont vous avez besoin en utilisant votre SVG nouvellement créé comme maître.

### Traitement en ligne

Rendez-vous sur le site Real Favicon Generator. D'autres sites sont disponibles, mais celui-ci semble particulièrement complet.

1. Sélectionnez le bouton étiqueté *Choisissez votre image Favicon*
2. Le site vous montrera votre image maître. Il indique également *Votre image n'est pas carrée (688x512). Nous pouvons régler cela en ajoutant des marges transparentes*
3. Sélectionnez le bouton *Continuer avec cette image* sous l'image maître.
4. Il y a des sous-formulaires avec des arrière-plans bleu pâle pour plusieurs types d'icônes - remplissez chacun d'eux en vérifiant que l'aperçu vous convient.
5. Mieux vaut s'en tenir aux paramètres par défaut des options de génération de Favicon à moins que vous ne sachiez mieux. Sauf :
6. Chemin, sélectionnez l'option Je ne peux pas... et entrez : *media/templates/cassiopeia-green/images*
7. Sélectionnez le bouton *Générez vos Favicons et code HTML*
8. Après un court délai, il y a un nouveau formulaire, sélectionnez le bouton Télécharger votre package : *package Favicon*
9. Enregistrez le téléchargement ...
10. Sélectionnez et copiez le bloc de liens pour le sauvegarder quelque part.
11. Fermez le site de traitement en ligne

Le téléchargement est un fichier *zip* contenant 10 éléments : *favicon.ico*, *safari-pinned-tab.svg*, six fichiers PNG, *browserconfig.xml* et *site.webmanifest*.

### Déploiement

Pour utiliser l'ensemble standard des favicons Joomla, vous devez renommer et déplacer les icônes vers *joomla_root/media/templates/yourtemplate/images* :

- Votre image SVG maître, *green-favicon-j4.svg*, doit être renommée en *joomla-favicon.svg*
- Le fichier *safari-pinned-tab.svg* téléchargé doit être renommé en *joomla-favicon-pinned.svg*
- Le fichier *favicon.ico* téléchargé doit simplement être déplacé

### Le bloc de liens

Le bloc de liens copié précédemment contient :

```html
<link rel="apple-touch-icon" sizes="180x180" href="media/templates/cassiopeia-green/images/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="media/templates/cassiopeia-green/images/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="media/templates/cassiopeia-green/images/favicon-16x16.png">
<link rel="manifest" href="media/templates/cassiopeia-green/images/site.webmanifest">
<link rel="mask-icon" href="media/templates/cassiopeia-green/images/safari-pinned-tab.svg" color="#5bbad5">
<link rel="shortcut icon" href="media/templates/cassiopeia-green/images/favicon.ico">
<meta name="msapplication-TileColor" content="#ffc40d">
<meta name="msapplication-config" content="media/templates/cassiopeia-green/images/browserconfig.xml">
<meta name="theme-color" content="#ffffff">
```

Vous n'avez probablement pas besoin de l'utiliser !


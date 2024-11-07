<!-- Filename: J4.x:Template_SVG_Logos / Display title: Modèles de logos SVG  -->

## Logo Cassiopeia

Le modèle de site par défaut de Joomla 4, Cassiopeia, utilise le mot CASSIOPEIA comme logo de marque. Il apparaît en haut de chaque page, sauf si vous réglez l'option Marque sur Non dans le formulaire des modèles : Modifier le style, onglet Avancé, ou si vous utilisez un mot Titre à la place d'un graphique. Ce mot est en réalité un fichier graphique vectoriel évolutif (SVG). Vous pouvez choisir un graphique alternatif, mais il est assez délicat de créer et d'utiliser un logo SVG alternatif. Ce bref ensemble d'instructions peut vous aider.

## Inkscape

Inkscape est une application de graphisme vectoriel open source et multiplateforme, ce qui signifie que vous pouvez la télécharger gratuitement et l'utiliser sur Linux, Mac ou Windows. Pour commencer, allez sur le site d'Inkscape et téléchargez la version pour votre ordinateur portable ou de bureau. Lancez Inkscape et vous êtes prêt à créer un logo de marque au format SVG. La capture d'écran ci-dessous montre Inkscape en cours de création d'un nouveau logo SVG.

![création de logo inkscape](../../../en/images/templates/templates-svg-logos-inkscape.png)

## Instructions

Pour cet article, un logo est nécessaire montrant **GREEN CASSIOPEIA** à la même taille que **CASSIOPEIA** dans le logo par défaut, qui est de 32 pixels de haut:

1. Démarrez Inkscape, redimensionnez la fenêtre à votre confort, sélectionnez Vue / Zoom / Zoom sur la page
2. Sélectionnez l'outil de texte, marqué par la lettre A dans la barre d'outils à gauche
3. Sélectionnez Arial, Gras, 40 et px
4. Faites glisser pour définir une boîte occupant la plupart de la largeur de la page
5. Tapez le texte : GREEN CASSIOPEIA
6. Sélectionnez Vue / Zoom sur la sélection
7. Sélectionnez l'outil de sélection, marqué par une flèche - en haut de la barre d'outils à gauche
8. Verrouillez les valeurs de taille horizontale et verticale - le symbole de verrouillage dans la barre supérieure
9. Réglez l'unité de mesure sur px
10. Changez la hauteur à 32 - vous verrez le logo changer de taille
11. Sélectionnez Chemin / Objet en chemin - aucun changement visible mais les mots ne sont plus du texte
12. Sélectionnez Fichier / Propriétés du document
13. Sélectionnez Redimensionner au contenu
14. Dézoomez pour une meilleure vue
15. Réglez le remplissage sur blanc - cliquez sur la boîte blanche dans la palette de couleurs en bas
16. Fichier / Enregistrer sous
    local-site-root/images/headers/green-cassiopeia-optimised.svg
    1. Si vous enregistrez ailleurs, vous devrez utiliser un gestionnaire de fichiers ou un ftp pour uploader les fichiers svg. Le composant Media peut utiliser des fichiers SVG mais actuellement il ne les téléchargera pas.
17. Sélectionnez SVG optimisé (.svg) dans la liste des types de fichiers en bas de la boîte de dialogue Enregistrer.
18. Enregistrez, OK pour tous les paramètres par défaut dans le formulaire de sortie SVG optimisé
19. Réglez quelques Options d'Administrateur Joomla pour permettre l'utilisation de fichiers SVG
20. Allez dans Contenu / Média / Options
    1. Ajoutez aux extensions autorisées : ,svg
    2. Ajoutez aux extensions d'image légales (types de fichiers) : ,svg
    3. Ajoutez aux types MIME légaux : ,image/svg+xml
21. Enregistrez & Fermez
22. Allez dans Système / Modèles de site / Options
    1. Ajoutez aux formats d'image valides : ,svg
23. Enregistrez & Fermez
24. Allez dans Système / Styles de modèle de site
25. Sélectionnez votre modèle
26. Dans l'onglet Avancé, champ Logo, utilisez Sélectionner pour trouver votre logo nouvellement créé
27. Enregistrez et rechargez la page de votre site

![résultat de la création de logo inkscape](../../../en/images/templates/templates-svg-logos-inkscape-result.png)


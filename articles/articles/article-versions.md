<!-- Filename: Help4.x:Components_Version_History / Display title: Article : Versions  -->

## Introduction

Dans le formulaire d'édition d'article de Joomla, chaque fois qu'un article est enregistré, une nouvelle version est créée automatiquement. Le nombre de versions à conserver pour chaque article peut être défini dans la page *Articles : Options*, onglet *Disposition d'édition*. La valeur par défaut est de 10. Notez que ce n'est pas l'onglet *Options* de la page *Articles : Éditer*. La version actuelle est généralement la dernière version enregistrée.

Une ou plusieurs versions peuvent être marquées pour *Conserver pour toujours*. Ces versions ne seront pas supprimées automatiquement, même si le nombre maximal de versions est dépassé.

La boîte de dialogue contextuelle *Versions* est utilisée pour gérer les versions antérieures de l'élément en cours d'édition. Des historiques de versions similaires sont disponibles pour les Articles, les Bannières et Clients, les Contacts, les Flux d'actualités, les Notes utilisateur, et toutes les Catégories.

Remarque : Les champs personnalisés ne sont pas stockés dans différentes versions.

## Comment accéder

Sélectionnez le bouton **Versions** dans la barre d'outils pendant que vous éditez l'élément.

## Capture d'écran

![Boîte de dialogue pop-up des versions](../../../en/images/articles/articles-versions.png)

## En-têtes de colonnes

- **Case à cocher** Cette case est utilisée pour sélectionner ou désélectionner toutes les versions visibles dans la liste. Si une case est cochée, les boutons de la barre d'outils sont activés et peuvent être utilisés pour effectuer une action sur les éléments sélectionnés.
- **Date** La date et l'heure auxquelles la version a été enregistrée. Cliquer sur ce lien ouvre un aperçu de cette version dans une fenêtre pop-up. Notez qu'une des dates sera suivie d'un symbole d'étoile. Cela indique que c'est la version actuellement enregistrée et en cours de modification.
- **Note de version** Lorsque vous modifiez un élément, vous avez la possibilité d'entrer une note de version. Cela peut être utilisé pour vous aider à vous rappeler quelle version contient quelles informations. Si vous avez saisi une note de version avant d'enregistrer l'élément, elle apparaîtra dans cette colonne.
- **Conserver indéfiniment** Cette colonne indique si vous avez marqué la version pour être conservée indéfiniment. Normalement, chaque version sera conservée selon les paramètres de la page des options du composant. Les paramètres par défaut sont de conserver un maximum de 10 versions antérieures pour un élément. Dans ce cas, lorsque vous enregistrez un élément qui a déjà 10 versions enregistrées, la version la plus ancienne est supprimée. Si une version est marquée pour être conservée indéfiniment, elle ne sera pas comptée parmi les versions enregistrées et ne sera pas supprimée lorsque le nombre maximum est atteint. Pour basculer l'option Conserver indéfiniment, cochez la case de la version, puis sélectionnez le bouton *Conserver On/Off* dans la barre d'outils.
- **Auteur** L'utilisateur qui a enregistré cette version.
- **Nombre de caractères** Le nombre total de caractères enregistrés dans cette version. Cela inclut les noms de colonnes de la base de données ainsi que les caractères de l'élément.

## Barre d'outils

En haut de la page, vous verrez la barre d'outils affichée dans la capture d'écran ci-dessus. Les fonctions sont :

- **Restaurer** La version actuelle de l'élément est marquée d'une étoile à droite de la date. Si vous souhaitez restaurer l'une des autres versions enregistrées, cochez la case de la version souhaitée et sélectionnez le bouton *Restaurer*. La version actuelle de l'élément sera remplacée par la version sélectionnée, et l'écran d'édition se rechargera avec la version restaurée chargée dans l'éditeur.
- **Prévisualiser** Pour prévisualiser une version, soit sélectionnez l'élément dans la colonne Date, soit cochez la case et cliquez sur le bouton Prévisualiser. Une fenêtre de navigateur distincte s'ouvrira affichant la version sélectionnée de l'élément, similaire à la capture d'écran ci-dessous. Après avoir visualisé la version, fermez la fenêtre du navigateur.
![Boîte de dialogue de prévisualisation des versions](../../../en/images/articles/articles-versions-preview.png)
- **Comparer** Pour comparer deux versions et voir ce qui a changé, cochez les cases de chacune des versions et cliquez sur le bouton Comparer. Une nouvelle fenêtre de navigateur s'ouvrira, comme montré dans la capture d'écran ci-dessous. La première colonne est le nom du champ, la deuxième est la version la plus ancienne, la troisième est la version la plus récente, et la dernière colonne met en évidence les différences entre les deux versions.
![Boîte de dialogue de comparaison des versions](../../../en/images/articles/articles-versions-compare.png)
- **Conserver Activé/Désactivé** Ce bouton vous permet d'activer ou de désactiver la fonctionnalité Conserver Pour Toujours pour une version. Normalement, la version la plus ancienne d'un élément sera supprimée automatiquement lorsque le nombre maximum de versions (défini dans les Options pour le composant) aura été dépassé. Si vous définissez la propriété Conserver Pour Toujours pour une version, elle ne sera jamais supprimée automatiquement.
- **Supprimer** Ce bouton vous permet de supprimer manuellement une ou plusieurs versions. Sélectionnez la case pour les versions que vous souhaitez supprimer et ensuite sélectionnez le bouton Supprimer. Notez que cela ne supprime *pas* l'élément en cours d'édition. Cela supprime uniquement la version sélectionnée de l'élément.


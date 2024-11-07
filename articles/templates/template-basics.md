<!-- Filename: J4.x:Template_Basics / Display title: Notions de base sur les modèles  -->

## Introduction

Dans Joomla!, un modèle (template) est un ensemble de fichiers qui, ensemble, définissent l'apparence du site web. Joomla 4 fournit deux modèles : Atum est le modèle d'administration utilisé pour la gestion du site ; et Cassiopeia est le modèle du site utilisé pour les visiteurs du site. De nombreux autres modèles de site sont disponibles auprès de fournisseurs indépendants, soit gratuitement, soit contre une somme modique. En effet, il existe toute une industrie basée sur la fourniture de modèles de site spécialisés.

Un modèle de site typique contient des fichiers PHP pour disposer le contenu et des fichiers CSS pour styliser le contenu. Il y a souvent des fichiers supplémentaires tels que des images utilisées dans la mise en page et des fichiers JavaScript utilisés pour interagir avec les fonctionnalités du site telles que les liens et les boutons. La capture d'écran suivante montre les dossiers et fichiers du modèle Cassiopeia dans une nouvelle installation de Joomla 4 :

![personnaliser la page des modèles Cassiopeia](../../../en/images/templates/templates-customise-cassiopeia.png)

Notez que les fichiers php se trouvent dans le dossier /templates du site et que les fichiers média se trouvent dans le dossier /media du site.

## Positions du modèle

Le modèle du site définit les positions du contenu principal, par exemple un article individuel ou une disposition de blog avec des articles en vedette, et tous les modules à afficher au-dessus, en dessous, à gauche ou à droite du contenu principal. L'illustration suivante montre les positions disponibles dans Cassiopeia :

![diagramme des positions du modèle](../../../en/images/templates/cassiopeia-template-positions.png)

De plus, vous pouvez voir les positions du modèle dans n'importe quel modèle en activant l'option Aperçu des positions du module dans le formulaire des options du modèle, puis en ajoutant ?tp=1 à l'URL. S'il y a déjà une chaîne de requête ajoutée à l'URL, ajoutez &tp=1 à la place.

## Style utilisateur

Cassiopeia propose certaines options que vous pouvez modifier pour changer l'apparence du site (il existe un article séparé sur la personnalisation de Cassiopeia). Cela peut ne pas suffire à vos besoins. Vous pouvez apporter vos propres modifications à l'apparence avec une feuille de style user.css. Vous devez le créer vous-même dans le formulaire Modèles : Personnaliser. Sélectionnez simplement Nouveau fichier et entrez le nom du fichier : user, sélectionnez le type de fichier : .css et choisissez css dans la liste des dossiers. Ensuite, sélectionnez le fichier user.css nouvellement créé dans le formulaire Éditer et entrez quelques styles, par exemple, pour rendre les titres vert sombre :

```css
    h1, h2, h3, h4, h5, h6 {
      color: darkgreen;
    }
```

## Substitutions de Modèles

En plus de la disposition globale définie par le modèle du site, chaque composant ou module dispose d'un modèle pour définir son apparence au sein de la disposition globale. Ces modèles se trouvent dans un dossier `tmpl` au sein du composant ou du module. Certains plugins ont également des modèles. Et il existe des dispositions qui peuvent être appelées depuis n'importe quel type d'extension.

Parfois, l'un de ces modèles d'*extension* ne vous convient pas tout à fait. Dans ce cas, vous pouvez créer une substitution de modèle. Il s'agit d'une copie du code utilisé pour générer la disposition de l'extension que vous pouvez modifier selon vos besoins. La capture d'écran suivante montre le formulaire Template : Personnaliser Créer des Substitutions :

![substitutions de modèle](../../../en/images/templates/cassiopeia-customisation-create-overrides.png)

Cassiopeia a déjà quelques substitutions installées. Cela pourrait sembler être un problème. Si vous modifiez l'un des fichiers Cassiopeia par défaut, vos modifications seront écrasées (et donc perdues) lors de la prochaine mise à jour de Joomla. La solution est les modèles enfants.

## Dispositions Alternatives

Un modèle, ou une substitution de modèle, définit l'apparence d'une extension dans un fichier spécifique, tel que default.php. Dans certains cas, vous souhaiterez peut-être choisir entre la disposition par défaut et une disposition alternative. Par exemple, un menu en position supérieure nécessite généralement une disposition différente du même menu en position latérale. Dans un module de menu, il y a un paramètre de Disposition dans l'onglet Avancé du formulaire d'édition du module qui vous permet de sélectionner parmi les dispositions alternatives disponibles. Il existe un tutoriel séparé sur les Dispositions Alternatives de Modèle.

## Modèles Enfant

Un modèle enfant utilise les fichiers de son modèle parent, sauf pour les fichiers qui se trouvent dans le modèle enfant. Par exemple, vous pourriez avoir des fichiers user.css différents dans le parent et l'enfant afin que différentes pages puissent avoir des schémas de couleurs différents. Ou vous pourriez copier le fichier index.php du parent vers l'enfant et modifier l'enfant pour produire une disposition différente de celle du parent. Il existe un tutoriel séparé sur les modèles enfant.

*Traduit par openai.com*


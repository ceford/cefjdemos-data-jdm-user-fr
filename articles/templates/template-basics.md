<!-- Filename: J4.x:Template_Basics / Display title: Les bases des templates -->

## Introduction

Dans Joomla!, un template est un ensemble de fichiers qui définissent ensemble
l'apparence du site web. Joomla 4 propose deux templates : Atum, qui est le
template Administrateur utilisé pour la gestion du site, et Cassiopeia, qui
est le template Site utilisé pour les visiteurs du site. De nombreux autres
templates de site sont disponibles auprès de fournisseurs indépendants, soit
gratuitement, soit moyennant des frais modiques. En effet, il existe toute une
industrie basée sur la fourniture de templates de site spécialisés.

Un template de site typique contient des fichiers PHP pour disposer le contenu
et des fichiers CSS pour styliser le contenu. Il y a souvent des fichiers
supplémentaires tels que des images utilisées dans la mise en page et des
fichiers JavaScript utilisés pour interagir avec les fonctionnalités du site
telles que les liens et les boutons. La capture d'écran suivante montre les
dossiers et fichiers du template Cassiopeia dans une nouvelle installation de
Joomla 4 :

<img
src="https://docs.joomla.org/images/thumb/4/45/J4x-templates-customise-cassiopeia-en.png/800px-J4x-templates-customise-cassiopeia-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/4/45/J4x-templates-customise-cassiopeia-en.png 1.5x"
data-file-width="1000" data-file-height="508" width="800" height="406"
alt="screenshot of templates customise cassiopeia page" />

Notez que les fichiers PHP se trouvent dans le dossier /templates du site, et
les fichiers médias se trouvent dans le dossier /media du site.

## Positions des templates

Le template du site définit les positions du contenu principal, par exemple un
article individuel ou une mise en page de blog pour les articles en vedette,
ainsi que les modules à afficher au-dessus, en dessous, à gauche ou à droite
du contenu principal. L'illustration suivante montre les positions disponibles
dans Cassiopeia :

<img
src="https://docs.joomla.org/images/2/28/J4x-cassiopeia_template_explained_positions.png"
class="thumbborder" decoding="async" data-file-width="786"
data-file-height="980" width="800" height="997"
alt="Template Positions" />

Vous pouvez également voir les positions des templates dans n'importe quel
template en activant l'option Aperçu des positions de module dans le formulaire
des Options du template, puis en ajoutant ?tp=1 à l'URL. S'il y a déjà une
chaîne de requête ajoutée à l'URL, ajoutez plutôt &tp=1.

## Style utilisateur

Cassiopeia propose quelques options que vous pouvez modifier pour changer
l'apparence du site (il existe un article séparé sur la personnalisation de
Cassiopeia). Cela peut ne pas suffire à répondre à vos besoins. Vous pouvez
apporter vos propres modifications à l'apparence avec une feuille de style
user.css. Vous devez la créer vous-même dans le formulaire
Templates:Personnaliser. Il suffit de sélectionner Nouveau fichier et de
saisir le nom de fichier : user, de sélectionner le type de fichier : .css,
et de choisir css dans la liste des dossiers. Ensuite, sélectionnez le fichier
user.css nouvellement créé dans le formulaire d’édition et entrez quelques
styles, par exemple, pour rendre les titres vert foncé :

```
    h1, h2, h3, h4, h5, h6 {
      color: darkgreen;
    }
```

## Substitution de template

En plus de la mise en page globale définie par le template du site, chaque
composant ou module dispose d'un template pour définir son apparence dans la
mise en page globale. Ces templates sont situés dans un dossier tmpl au sein
du composant ou du module. Certains plugins ont également des templates. De
plus, il existe des mises en page qui peuvent être appelées depuis n'importe
quel type d'extension.

Parfois, l'un de ces templates d'extension ne correspond pas tout à fait à vos
goûts. Dans ce cas, vous pouvez créer une substitution de template. Il s'agit
d'une copie du code utilisé pour générer la mise en page de l'extension, que
vous pouvez modifier selon vos propres besoins. La capture d'écran suivante
montre le formulaire de création de substitutions de template dans la section
Personnaliser du template :

<img
src="https://docs.joomla.org/images/thumb/3/3b/J4x-cassiopeia_template_overrides-en.png/800px-J4x-cassiopeia_template_overrides-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/3/3b/J4x-cassiopeia_template_overrides-en.png 1.5x"
data-file-width="1000" data-file-height="688" width="800" height="550"
alt="Template Overrides" />

Cassiopeia a déjà quelques substitutions de templates installées par défaut.
Cela peut sembler poser problème. Si vous modifiez l'un des fichiers par défaut
de Cassiopeia, vos modifications seront écrasées (et perdues) lors de la
mise à jour de Joomla. La solution consiste à utiliser des templates enfants.

## Mises en page alternatives

Un template, ou une substitution de template, définit l'apparence d'une
extension dans un fichier spécifique, tel que default.php. Dans certains cas,
vous pouvez souhaiter choisir entre la mise en page par défaut et une mise en
page alternative. Par exemple, un menu dans une position supérieure nécessite
généralement une mise en page différente du même menu dans une position
latérale. Dans un module de menu, il existe un paramètre de mise en page dans
l'onglet Avancé du formulaire de modification du module qui vous permet de
sélectionner parmi les mises en page alternatives disponibles. Il existe un
tutoriel séparé sur les Mises en page alternatives de templates.

## Templates enfants

Un template enfant utilise les fichiers de son template parent, à l'exception
de tout fichier présent dans le template enfant. Par exemple, vous pourriez
avoir différents fichiers user.css dans le template parent et dans le template
enfant, de sorte que différentes pages puissent avoir des jeux de couleurs
différents. Ou vous pourriez copier le fichier index.php du parent vers
l'enfant et modifier l'enfant pour produire une mise en page différente du
parent. Il existe un tutoriel séparé sur les templates enfants.

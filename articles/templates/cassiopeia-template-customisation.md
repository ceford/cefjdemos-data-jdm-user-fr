<!-- Filename: J4.x:Cassiopeia_Template_Customisation / Display title: Personnalisation du template Cassiopeia -->

## Introduction

Cassiopeia est le template de site fourni avec Joomla 4. C'est un excellent
modèle polyvalent, **accessible** et **réactif**. Il peut être personnalisé
via les options de modèle et le fichier user.css par les utilisateurs ayant
une certaine connaissance en HTML et CSS.

L'illustration suivante montre l'apparence d'un site Joomla 4 avec un article
et quelques liens de menu créés.

<img
src="https://docs.joomla.org/images/2/2c/J4x-cassiopeia_template_customisation_article_view.png"
class="thumbborder" decoding="async" data-file-width="720"
data-file-height="366" width="720" height="366" alt="Article View" />

## Templates : Modifier le style

Vous pouvez expérimenter avec l'apparence du site en ouvrant le formulaire de
modification de style. Allez à **Système → templates → Styles de template de site**
et sélectionnez le titre du template dans la colonne Style, Cassiopeia - Par
défaut. L'onglet Avancé contient des paramètres que vous pouvez ajuster :

<img
src="https://docs.joomla.org/images/6/64/J4x-cassiopeia_template_customisation_edit_style.png"
class="thumbborder" decoding="async" data-file-width="720"
data-file-height="733" width="720" height="733"
alt="Edit Style - Advanced Tab" />

Pour essayer les options, ouvrez une première fenêtre ou un onglet avec
l'interface d'administration et une seconde fenêtre ou onglet avec l'interface
du site, puis basculez de l'une à l'autre après chaque modification enregistrée.

### Marque

* **Oui** par défaut. La barre de logo Cassiopeia contenant un logo ou un nom
  de marque est affichée avec un fond sombre, bleu par défaut.
* **Non** La barre de logo n'est pas affichée. Les options pour sélectionner
  un logo, un titre et un slogan disparaissent.

L'image de marque par défaut est le mot Cassiopée en tant qu'image dans un
fichier SVG. C'est ce qui est affiché dans la première illustration ci-dessus.

Vous pouvez définir la Marque sur Non si vous souhaitez fournir une image de
marque dans un module HTML personnalisé.

### Logo

* **Aucun** Le logo d'image par défaut de Cassiopeia sera utilisé à moins
  qu'un Titre ne soit défini.
* **Image de logo** Le logo sélectionné apparaîtra à la place du logo
  Cassiopeia même si un Titre est défini.

### Titre (alternative au logo)

* **Mon Nom de Marque** Si présent et si vous n'avez pas sélectionné d'image
  de logo, les mots dans le champ Titre apparaîtront mais soulignés dans la
  barre supérieure bleue.

### Slogan

* **Toujours à votre service** Si présent, les mots dans le champ de slogan
  apparaîtront dans une petite taille de police sous l'image du logo ou le nom
  de marque.

<img
src="https://docs.joomla.org/images/e/e1/J4x-cassiopeia_template_customisation_brand_with_tagline.png"
class="thumbborder" decoding="async" data-file-width="570"
data-file-height="255" width="570" height="255"
alt="Brand with Tagline" />

### Schéma de polices

* **Aucun** le défaut. La famille de polices spécifiée dans la feuille de
  style du modèle est utilisée, ce qui signifie généralement que le site
  utilisera les polices disponibles sur votre propre ordinateur.
* **Autres** Une famille de polices située dans la hiérarchie de dossiers du
  modèle ou téléchargée depuis le web sera utilisée. Vous pouvez voir
  l'apparence modifiée du texte sur une page lorsque vous rechargez le site
  après avoir changé cette option.

### Thème de couleur

* **Standard** Une couleur de fond bleu foncé pour la barre de marque et
  d'autres éléments tels que le bouton de connexion.
* **Alternatif** Une couleur de fond bordeaux à la place du bleu foncé.

<img
src="https://docs.joomla.org/images/a/a9/J4x-cassiopeia_template_customisation_alt_color_scheme.png"
class="thumbborder" decoding="async" data-file-width="570"
data-file-height="243" width="570" height="243"
alt="Alternative Colour Scheme" />

### Mise en page

* **Statique** par défaut. La largeur maximale est définie sur 1320px. Sur
  des écrans plus larges, la marge devient simplement plus large.
* **Fluide** Il n'y a pas de largeur maximale.

La vue sur un appareil mobile à écran étroit :

<img
src="https://docs.joomla.org/images/a/a5/J4x-cassiopeia_template_customisation_mobile_view.png"
class="thumbborder" decoding="async" data-file-width="411"
data-file-height="731" width="411" height="731" alt="Mobile View" />

### En-tête fixe

* **Non** par défaut. Les éléments de l'en-tête et le contenu défilent vers le
  haut hors de la fenêtre d'affichage.
* **Oui** Sauf sur les écrans étroits, les éléments de l'en-tête restent fixes
  en haut de la fenêtre d'affichage tandis que les éléments de contenu défilent
  vers le haut. Cela est uniquement évident lorsque le contenu de la page est
  plus grand que la fenêtre d'affichage.

### Lien Retour en haut de page

* **Non** par défaut. Il n'y a pas de lien Retour en haut de page.
* **Oui** Lorsque le contenu est plus long que la fenêtre d'affichage, en bas
  à droite de la page se trouve un bouton marqué d'une chevron vers le haut.
  Sélectionnez-le pour remonter en haut de la page.

<img
src="https://docs.joomla.org/images/3/38/J4x-cassiopeia_template_customisation_back_to_top.png"
class="thumbborder" decoding="async" data-file-width="373"
data-file-height="337" width="373" height="337" alt="Back to Top" />

## Positions du template Cassiopeia

Lorsque vous construisez un site avec Cassiopeia, il est vraiment utile de
connaître les emplacements des positions que vous pouvez utiliser pour les
modules. Certains sont descriptifs, comme menu et bottom-a, mais il n'est pas
si évident de savoir où ils se trouvent avant de les utiliser. Cette
illustration devrait vous aider :

<img
src="https://docs.joomla.org/images/2/28/J4x-cassiopeia_template_explained_positions.png"
class="thumbborder" decoding="async" data-file-width="786"
data-file-height="980" width="786" height="980"
alt="Template Positions" />

Essayez ce qui suit :

### Déplacez le module de menu vers la position *menu*

Un site Joomla 4 nouvellement installé a un menu dans la position sidebar-right,
comme vu dans la première illustration ci-dessus. Pour ce tutoriel, quelques
éléments de menu ont été ajoutés, dont un parent avec deux éléments enfants.
Pour déplacer ce menu vers la position de menu, accédez à Contenu → Modules de
site dans le menu de l'administrateur. Dans la liste, il y a trois modules,
dont le Menu principal. Sélectionnez-le pour ouvrir le formulaire de
modification des modules : Menu.

Dans l'onglet Module, changez le champ Position à droite en Menu [menu].
Enregistrez et jetez un coup d'œil au résultat dans l'affichage du site. Le
menu semble correct, mais les éléments enfants ne sont pas là.

Dans le formulaire d'édition du menu, sélectionnez l'onglet Avancé et faites
défiler jusqu'au champ Mise en page. C'est une liste déroulante avec quatre
options. --Depuis le module-- / Par défaut est sélectionné par défaut.
Essayez les autres options et consultez le résultat. (N'oubliez pas de
Enregistrer dans le formulaire d'édition et de recharger dans la vue du Site.)
Aucune des options --Depuis le module-- ne montre les éléments de menu enfants,
mais les deux options --Depuis le template Cassiopeia-- le font.

<img
src="https://docs.joomla.org/images/b/b0/J4x-cassiopeia_template_customisation_menu_position.png"
class="thumbborder" decoding="async" data-file-width="570"
data-file-height="254" width="570" height="254" alt="Menu Position" />

Alors, quelle différence apporte l'option *Repliable* ?

* Déroulant repliable : Sur les appareils mobiles à écran étroit, le menu se
  replie en une icône Hamburger jusqu'à ce qu'il soit sélectionné. Lors de la
  sélection, il s'étend pour afficher une liste verticale.
* Déroulant : Le menu apparaît toujours sous forme de liste verticale.

### Déplacer le module de menu vers la position *topbar*

Dans l'onglet Module du formulaire d'édition, définissez la Position sur Barre
supérieure [topbar] et examinez le résultat. Il y a un problème - le menu est
positionné plus à gauche que lorsqu'il était dans la position du menu. Cela est
dû au fait que la position du menu et l'emplacement du logo ont une classe CSS
grid-child, mais pas la barre supérieure. Cela peut être corrigé avec une entrée
dans le fichier user.css, comme indiqué ci-dessous.

## Personnaliser Cassiopeia

Et si vous n'aimez pas la couleur de fond bleu foncé de l'en-tête ? Supposez
que vous préfériez un thème vert foncé. Pour résoudre cela, vous avez besoin
d'un peu de connaissance en CSS. Allez à **Système → templates de site →
Détails et fichiers de Cassiopeia** pour ouvrir le formulaire Personnaliser
le template(Cassiopeia).

L'illustration ci-dessous montre deux groupes de dossiers. Le premier groupe
se compose des dossiers et fichiers de template que vous ne devez pas modifier,
mais auxquels vous pouvez ajouter. En particulier, vous pouvez ajouter des
fichiers HTML de substitution de modèle au dossier html. Le deuxième groupe
contient les fichiers multimédias du template que vous ne devez pas modifier.
Cependant, vous pouvez ajouter un fichier user.css au dossier css et/ou un
fichier user.js au dossier js. Vous feriez cela si vous vouliez apporter
quelques changements simples à l'apparence du site.

<img
src="https://docs.joomla.org/images/3/3b/J4x-cassiopeia_template_customisation_edit_files.png"
class="thumbborder" decoding="async" data-file-width="720"
data-file-height="365" width="720" height="365" alt="Edit Files" />

Notez qu'il n'y a pas de fichier user.css présent dans le dossier css. C'est
un fichier que vous créez vous-même afin de pouvoir remplacer les styles
précédemment définis. S'il n'est pas présent, créez-le maintenant en
sélectionnant le dossier css puis le bouton Nouveau. Dans la boîte de
dialogue Nouveau fichier, sélectionnez le dossier css, sinon le nouveau
fichier apparaîtra au mauvais endroit. Entrez user (en minuscules et
sans .css) dans le champ Nom du fichier et sélectionnez .css dans le champ
Type de fichier. Sélectionnez le bouton Créer pour créer le fichier. Si
user.css est déjà présent, sélectionnez-le pour ouvrir le formulaire d'édition.

### Titres

Pour commencer simplement, changez la couleur des titres en vert foncé. Les
titres sont des balises dans la gamme *h1, h2, h3, h4, h5 et h6*. Dans le f
ichier *user.css*, entrez la définition du style :
```
    h1, h2, h3, h4, h5, h6 {
      color: darkgreen;
    }
```
Enregistrez et rechargez le site pour voir le résultat. Le titre de la page ou
de l'article devrait être en vert foncé. Sinon, vérifiez ce que vous avez tapé.
Le langage formel pour la documentation Joomla est l'anglais britannique, donc
couleur plutôt que color comme en anglais américain. Mais en CSS, cela doit
être color. La ponctuation est-elle correcte ?

Moins évident est que certaines balises autres que les titres peuvent être
stylisées pour ressembler à des titres. Ajoutez donc ceci :
```
    .h1, .h2, .h3, .h4, .h5, .h6 {
      color: darkgreen;
    }
```
Notez ici que le point (.) initial est un sélecteur de classe, par exemple
`<span class="h1">Dummy H1</span>` - donc il y a un point dans le fichier
CSS mais pas dans le nom de classe.

### Arrière-plan de l'en-tête

Dans l'onglet du navigateur contenant le Site, ouvrez les outils de
développement de votre navigateur, Firefox dans cet exemple, et sélectionnez
la balise d'en-tête.

<img
src="https://docs.joomla.org/images/3/30/J4x-cassiopeia_template_customisation_developer-tools.png"
class="thumbborder" decoding="async" data-file-width="720"
data-file-height="203" width="720" height="203" alt="Developer Tools" />

Cela montre les styles utilisés. Le style container-header est là où la couleur
d'arrière-plan et l'image d'arrière-plan sont définies. Elles doivent être
remplacées dans le fichier user.css. Essayez ceci :
```
    .container-header {
      background-color: darkgreen;
      background-image: none;
    }
```
### Style de *topbar*

Souvenez-vous de ce commentaire sur le menu étant trop à gauche dans la barre
supérieure ? Cela est dû au fait qu'il n'a pas de largeur maximale et de marges
appropriées définies. Mettez ceci dans le fichier user.css pour corriger cela :
```
    .container-topbar {
      max-width: 1320px;
      margin-left: auto;
      margin-right: auto;
    }
```
Voici le thème vert fonctionnel :

<img
src="https://docs.joomla.org/images/3/36/J4x-cassiopeia_template_customisation_green_theme.png"
class="thumbborder" decoding="async" data-file-width="720"
data-file-height="365" width="720" height="365" alt="Green Theme" />

### Accessibilité

Notez qu'il doit y avoir un contraste suffisant entre les couleurs de fond et
de premier plan pour respecter les normes d'accessibilité Web. Vous pouvez
vérifier votre contraste sur le WebAIM Contrast Checker. Le vert foncé
est \#006400.

## Substitutions

L'onglet Créer des substitutions du formulaire Personnaliser les Templates
(Cassiopeia) affiche la liste des extensions pour lesquelles vous pouvez
créer une substitution. Notez les différents symboles : sélectionnez un
symbole de dossier pour afficher une liste des dossiers et des fichiers
qu'il contient ; sélectionnez un symbole de fichier multiple pour créer
immédiatement une substitution pour cette extension ; l'élément créé
disparaît de la liste - sélectionnez l'onglet Éditeur et localisez la
substitution créée dans le dossier html. Il peut y avoir plus d'un fichier
créé - les fichiers créés sont copiés à partir de l'extension d'origine,
prêts pour que vous les éditiez. Pour cela, vous devez connaître un peu
HTML et PHP !

Voici l'onglet Créer des substitutions :

<img
src="https://docs.joomla.org/images/8/8d/J4x-cassiopeia_template_customisation-create_overrides.png"
class="thumbborder" decoding="async" data-file-width="720"
data-file-height="496" width="720" height="496"
alt="Create Overrides" />

Si vous expérimentez simplement et que vous ne voulez pas vraiment une
substitution, vous pouvez *Fermer* le formulaire d'édition, sélectionner
le bouton Gérer les dossiers dans la barre d'outils, puis sélectionner le
bouton Supprimer en bas du formulaire modal Gérer les dossiers.

Les substitutions concernent vraiment la personnalisation des extensions
plutôt que le template Cassiopeia, et c'est une autre histoire.

## Templates enfants

Si vous souhaitez apporter des modifications plus substantielles à l'apparence
du site, vous pouvez créer un template enfant. Celui-ci copie seulement une
petite sélection de dossiers et de fichiers que vous pouvez modifier ou ajouter,
mais continue par ailleurs à utiliser les dossiers et fichiers du template
parent. En utilisant des templates enfants, vous pourriez avoir certaines
pages avec une couleur de thème et d'autres pages avec une deuxième couleur
de thème. Les templates enfants sont abordés ailleurs. Ceci est une
illustration de la structure de fichiers dans un template enfant de Cassiopeia :

<img
src="https://docs.joomla.org/images/5/55/J4x-cassiopeia_template_customisation_child_template_files.png"
class="thumbborder" decoding="async" data-file-width="720"
data-file-height="264" width="720" height="264"
alt="Child Template Files" />

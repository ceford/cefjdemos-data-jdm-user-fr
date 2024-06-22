<!-- Filename: J4.x:Template_Overrides / Display title: Substitutions de template -->

## Introduction

Les extensions Joomla définissent l'apparence de leur sortie avec des fichiers
de template, qui contiennent du balisage HTML généré par PHP, et des fichiers
CSS qui définissent la mise en page, le schéma de couleurs, les polices, etc.
Cela peut parfaitement convenir à vos besoins, d'autant plus que vous pouvez
modifier l'apparence avec vos propres styles CSS. Parfois, vous souhaitez
afficher des informations supplémentaires ou peut-être moins d'informations.
Pour cela, vous devez créer un remplacement de template.

De nombreuses extensions Joomla ont des template de sortie assez complexes qui
sont difficiles à lire. Vous avez besoin d'une bonne compréhension de HTML,
PHP et CSS pour aborder certains d'entre eux. Cet article illustre donc le
processus en créant un remplacement de template pour le formulaire de
déconnexion qui se trouve en fait dans le module de connexion, mod_login. Le
propriétaire du site souhaiterait que le formulaire de déconnexion affiche
l'heure à laquelle la déconnexion automatique se produira après une période
d'inactivité.

## Exemple : Remplacement de template pour mod_login

Commencez par sélectionner **Système → Templates → Templates du site** dans le
menu Administrateur, puis sélectionnez l'élément Cassiopeia Détails et
Fichiers. Cela ouvrira le formulaire Templates : Personnaliser (Cassiopeia) :

<img
src="https://docs.joomla.org/images/thumb/4/45/J4x-templates-customise-cassiopeia-en.png/800px-J4x-templates-customise-cassiopeia-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/4/45/J4x-templates-customise-cassiopeia-en.png 1.5x"
data-file-width="1000" data-file-height="508" width="800" height="406"
alt="Cassiopeia Files" />

**Important :** n'éditer aucun des fichiers fournis dans le cadre du template
Cassiopeia. Lors de la prochaine mise à jour de Joomla, ces fichiers peuvent
être écrasés et vos modifications seront perdues.

Le dossier html est l'endroit où se trouvent les remplacements de template
d'extension. Si vous développez le dossier html, vous verrez qu'il existe
déjà des remplacements pour les mises en page, mod_custom, mod_menu et
tinymce. Développez chacun pour voir ce qu'il contient. À ce stade, il n'y
a pas de mod_login.

## Créer des substitutions

Sélectionnez l'onglet Créer des substitutions pour voir la liste des modules,
composants, plugins et affichages pour lesquels vous pouvez créer des
remplacements :

<img
src="https://docs.joomla.org/images/thumb/3/3b/J4x-cassiopeia_template_overrides-en.png/800px-J4x-cassiopeia_template_overrides-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/3/3b/J4x-cassiopeia_template_overrides-en.png 1.5x"
data-file-width="1000" data-file-height="688" width="800" height="550"
alt="Template Overrides" />

Sélectionnez l'élément mod_login. Les fichiers php du modèle mod_login seront
copiés dans le dossier html et vous serez renvoyé à l'onglet Éditeur.
Développez les dossiers html et mod_login. Vous verrez default.php et
default_logout.php.

Vous ne voulez pas le fichier default.php car c'est un remplacement pour le
formulaire de connexion. Sélectionnez-le, puis le bouton
**Supprimer le fichier** dans la barre d'outils. Dans la boîte de dialogue
d'alerte, confirmez que vous souhaitez supprimer le fichier.

Notez à quel point il est facile de supprimer des fichiers si vous changez
d'avis. Et avec le bouton Gérer les dossiers, vous pouvez également supprimer
des dossiers entiers. Faites attention à ne pas supprimer quelque chose que
vous n'avez pas créé vous-même.

## Modifier default_logout.php

Dans l'onglet Éditeur, sélectionnez le fichier default_logout.php. Remarquez
les boutons en haut à droite : Afficher le fichier original et Afficher les
différences. Ce dernier a été réglé sur Oui pour la capture d'écran suivante
afin de montrer quelques lignes de code ajoutées près du haut du fichier. Ces
lignes de code calculent quand la session de l'utilisateur expirera après le
chargement de la page contenant le formulaire de déconnexion.

<img
src="https://docs.joomla.org/images/thumb/5/55/J4x-cassiopeia-template-customisation-logout-override-en.png/800px-J4x-cassiopeia-template-customisation-logout-override-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/5/55/J4x-cassiopeia-template-customisation-logout-override-en.png 1.5x"
data-file-width="1000" data-file-height="969" width="800" height="775"
alt="Edit override file" />

La zone Diff montre les lignes ajoutées avec un fond vert et les lignes
supprimées avec un fond rouge. Il n'y a pas de lignes supprimées dans ce cas.
Le code est affiché ici si vous souhaitez le copier pour essayer vous-même.

```php
    use Joomla\CMS\Factory;

    date_default_timezone_set('Europe/London');
    $config = Factory::getContainer()->get('config');
    $lifetime = $config->get('lifetime', 0);
    $time = time() + $lifetime * 60;
    $endTime = date('H:i:s', $time); // time() returns a time in seconds already
```

Plus bas dans le fichier de remplacement, à la ligne 36, quelques lignes
supplémentaires ont été ajoutées pour afficher le message désiré :

```html
<p class="text-center">
Your session will expire at <br><?php echo $endTime; ?>
</p>
```

Enregistrez et rechargez la page du site contenant le formulaire de déconnexion.

<img
src="https://docs.joomla.org/images/c/c0/J4x-cassiopeia-template-customisation-logout-override-result-en.png"
decoding="async" data-file-width="318" data-file-height="218"
width="318" height="218" alt="Override Result" />

Vous devriez voir le formulaire de déconnexion changer à chaque fois que la
page est rechargée. Mais que se passe-t-il si vous changez d'avis? Ou si vous
avez différentes options pour différents groupes d'utilisateurs? Bienvenue
dans les mises en page, sujet d'un article distinct.

## Autres subtitutions

L'onglet Créer des substitutions du formulaire Templates: personnaliser
(Cassiopeia) est utilisé pour créer n'importe lequel des éléments de sortie
Joomla pour lesquels il est possible de créer des substitutions. Les noms de
dossier de substitutions commencent principalement par com_, mod_ ou plg_.
Notez que la deuxième partie d'un dossier de substitutions de plugin signifie
le groupe de plugin. Voici une sélection d'exemples de dossiers de
substitutions :

<img
src="https://docs.joomla.org/images/3/3d/J4x-cassiopeia-template-customisation-example-override-folder-en.png"
class="thumbborder" decoding="async" data-file-width="244"
data-file-height="403" width="244" height="403"
alt="screenshot of overrides html folder showing implemented overrides" />

## Substitutions d'Affichage

Les petits fichiers d'affichage sont souvent utilisés pour des éléments
individuels des pages Joomla! Le bouton Lire la suite des articles, l'image
d'introduction et l'image complète sont tous des exemples d'éléments générés
par leurs propres fichiers de mise en page. Ces micro-affichage se trouvent
dans le dossier /layouts. Par exemple, dans la vue Blog de catégorie, le
fichier blog_item.php contient le code pour placer le titre de l'article,
une image d'introduction, le texte d'introduction, ainsi que divers autres
éléments pertinents de la page. Il le fait en utilisant un appel à LayoutHelper
en passant la mise en page à utiliser en tant que paramètre. Voici un exemple,
l'appel pour insérer le titre de l'article dans la mise en page du blog :


```php
<?php echo LayoutHelper::render('joomla.content.blog_style_default_item_title', $this->item); ?>
```

L'emplacement du fichier pour cet élément particulier est trouvé en remplaçant
les symboles de points par des symboles de barre oblique, en ajoutant
/layouts/ et en ajoutant .php à la fin :

```php
    JOOMLAROOT/layouts/joomla/content/blog_style_default_item_title.php
```

Lorsqu'un fichier de remplacement est créé, il se trouve dans :

```php
    JOOMLAROOT/templates/cassiopeia/html/layouts/joomla/content/blog_style_default_item_title.php
```

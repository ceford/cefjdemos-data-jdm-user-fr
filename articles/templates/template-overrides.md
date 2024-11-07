<!-- Filename: J4.x:Template_Overrides / Display title: Remplacements de Modèles -->

## Introduction

Les extensions Joomla définissent l'apparence de leur sortie avec des fichiers de template, qui contiennent un balisage HTML généré par du PHP, et des fichiers CSS qui définissent la mise en page, le schéma de couleurs, les polices, etc. Cela peut parfaitement convenir à vos besoins, d'autant plus que vous pouvez modifier l'apparence avec vos propres styles CSS. Parfois, vous souhaitez afficher des informations supplémentaires ou peut-être moins d'informations. Pour cela, vous devez créer une substitution de template.

Beaucoup d'extensions Joomla ont des templates de sortie assez complexes qui sont difficiles à lire. Vous avez besoin d'une bonne compréhension du HTML, du PHP et du CSS pour en aborder certains. Cet article illustre donc le processus en créant une substitution pour le formulaire de déconnexion qui se trouve en réalité dans le module de connexion, mod_login. Le propriétaire du site aimerait que le formulaire de déconnexion affiche l'heure à laquelle la déconnexion automatique se produira après une période d'inactivité.

## Exemple : Remplacement de modèle pour mod_login

Commencez par sélectionner **Système → Templates → Templates du site** dans le menu de l'administrateur, puis sélectionnez l'élément Détails et fichiers de Cassiopeia. Cela ouvrira le formulaire Templates : Personnaliser (Cassiopeia) :

![template personnaliser cassiopeia onglet du site](../../../en/images/templates/templates-customise-cassiopeia.png)

**Important :** ne modifiez aucun des fichiers fournis dans le cadre du modèle Cassiopeia. Lors de la prochaine mise à jour de Joomla, ces fichiers peuvent être écrasés et vos modifications seront perdues.

Le dossier html est l'endroit où se trouvent les remplacements. Si vous dépliez le dossier html, vous verrez qu'il y a déjà des remplacements pour les mises en page, mod_custom, mod_menu et tinymce. Dépliez chacun d'eux pour voir ce qu'ils contiennent. Il n'y a pas de mod_login à ce stade.

## Créer des Overrides

Sélectionnez l'onglet Créer des Overrides pour voir la liste des Modules, Composants,
Plugins et Layouts pour lesquels vous pouvez créer des overrides :

![modèles personnalisation cassiopeia onglet des overrides](../../../en/images/templates/cassiopeia-customisation-create-overrides.png)

Sélectionnez l'élément mod_login. Les fichiers php du template mod_login seront
copiés dans le dossier html et vous serez renvoyé à l'onglet Éditeur.
Développez les dossiers html et mod_login. Vous verrez default.php et
default_logout.php.

Vous ne souhaitez pas le fichier default.php car il s'agit d'un override pour le
formulaire de connexion. Sélectionnez-le, puis le bouton **Supprimer le fichier** dans la
barre d'outils. Dans la boîte de dialogue d'alerte, confirmez que vous souhaitez supprimer le fichier.

Notez avec quelle facilité il est possible de supprimer des fichiers si vous changez d'avis. Et avec
le bouton Gérer les dossiers, vous pouvez également supprimer des dossiers entiers. Veillez à
ne pas supprimer quelque chose que vous n'avez pas créé vous-même.

## Modifier default_logout.php

Dans l'onglet Éditeur, sélectionnez le fichier default_logout.php. Remarquez les boutons en haut à droite : Afficher le fichier original et Afficher les différences. Ce dernier a été réglé sur Oui pour la capture d'écran suivante afin de montrer quelques lignes de code ajoutées près du haut du fichier. Ces lignes de code calculent quand la session de l'utilisateur expirera après le chargement de la page contenant le formulaire de déconnexion.

![personnalisation des modèles cassiopeia onglet des substitutions](../../../en/images/templates/cassiopeia-customisation-edit-logout-override.png)

La zone Diff montre les lignes ajoutées avec un fond vert et les lignes supprimées avec un fond rouge. Il n'y a pas de lignes supprimées dans ce cas. Le code est montré ici si vous souhaitez le copier pour essayer vous-même.

```php
    use Joomla\CMS\Factory;

    date_default_timezone_set('Europe/London');
    $config = Factory::getContainer()->get('config');
    $lifetime = $config->get('lifetime', 0);
    $time = time() + $lifetime * 60;
    $endTime = date('H:i:s', $time); // time() retourne déjà un temps en secondes
```

Plus bas dans le fichier de substitution, à la ligne 36, d'autres lignes ont été ajoutées pour afficher le message souhaité :

```html
<p class="text-center">
Votre session expirera à <br><?php echo $endTime; ?>
</p>
```

Enregistrez et rechargez la page du site contenant le formulaire de déconnexion.

![personnalisation des modèles cassiopeia onglet des substitutions](../../../en/images/templates/cassiopeia-customisation-logout-override-result.png)

Vous devriez voir le formulaire de déconnexion changer chaque fois que la page est rechargée. Mais que faire si vous changez d'avis ? Ou avez des options différentes pour différents groupes d'utilisateurs ? Bienvenue dans Layouts, le sujet d'un article séparé.

## Autres Substitutions

L'onglet Créer des Substitutions du formulaire Templates : Personnaliser (Cassiopeia) est utilisé pour créer n'importe lequel des éléments de sortie de Joomla pour lesquels il est possible de créer des substitutions. Les noms des dossiers de substitution commencent principalement par com\_, mod\_ ou plg\_. Notez que la deuxième partie d'un dossier de substitution de plugin indique le groupe de plugins. Voici une sélection d'exemples de dossiers de substitution :

![onglet des substitutions personnaliser des templates cassiopeia](../../../en/images/templates/templates-customise-example-override-folder.png)

## Substitutions de Disposition

Les petits fichiers de disposition sont souvent utilisés pour des éléments individuels des pages Joomla! Le bouton Lire la suite des articles, l'image d'introduction et l'image complète sont tous des exemples d'éléments générés par leurs propres fichiers de disposition. Ces micro-dispositions se trouvent dans le dossier /layouts. Par exemple, dans la vue Blog de Catégorie, le fichier blog_item.php contient le code pour placer le titre de l'article, une image d'introduction, le texte d'introduction, ainsi que diverses autres parties pertinentes de la page. Cela se fait en utilisant un appel à LayoutHelper en passant la disposition à utiliser comme paramètre. Voici un exemple, l'appel pour insérer le Titre de l'Article dans la disposition du blog :

```php
<?php echo LayoutHelper::render('joomla.content.blog_style_default_item_title', $this->item); ?>
```

L'emplacement du fichier pour cet élément particulier se trouve en remplaçant les points par des barres obliques, en ajoutant /layouts/ au début et .php à la fin :

```php
    JOOMLAROOT/layouts/joomla/content/blog_style_default_item_title.php
```

Lorsqu'un fichier de substitution est créé, il se trouve dans :

```php
    JOOMLAROOT/templates/cassiopeia/html/layouts/joomla/content/blog_style_default_item_title.php
```

## Informations complémentaires

- Notions de base sur le modèle
- Dossiers et fichiers du modèle Cassiopeia
- Personnalisation du modèle Cassiopeia
- Substitutions de modèles
- Dispositions des modèles
- Cassiopeia Template Simplified - Une étude de cas - un modèle simple basé
  sur Cassiopeia

*Traduit par openai.com*


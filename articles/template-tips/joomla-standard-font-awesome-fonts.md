<!-- Filename: J4.x:Joomla_Standard_Font_Awesome_Fonts / Display title: Polices Font Awesome  -->

## Comment Utiliser

Le CMS Joomla! est fourni avec son propre ensemble de polices d’icônes Font Awesome. Ces polices d'icônes sont disponibles par défaut pour une utilisation dans les modèles *Cassiopeia* et *Atum*.

Les polices d'icônes qui sont mappées dans `/media/system/scss/_icomoon.scss` peuvent être appelées avec une balise `name-of-icon">` et un {espace} `</span>`, par exemple :

```html
<span class="icon-joomla"> </span>
```

Cela affichera l'icône Joomla! : <span class="icon-joomla">&nbsp;</span>

Les polices d'icônes qui ne sont pas mappées peuvent être appelées avec une balise `<span class="far fa-name-of-icon">` et un {espace} `</span>`. Exemple :

```php
<i class="fa fa-adjust"></i>
```

Cela affichera une icône d'ajustement : <i class="fa fa-adjust"></i>

## Taille de la police

Parce que les icônes sont des polices, vous pouvez contrôler leur taille avec une classe ajoutée ou une déclaration style=. Bien sûr, vous devrez définir la classe dans votre fichier de feuille de style .css ou .less.

```html
<span class="icon-joomla large-icon"> </span>
<span class="icon-joomla" style="font-size:24px;"> </span>
```

Voici l'icône Joomla! redimensionnée : <span class="icon-joomla" style="font-size:24px;">&nbsp;</span>

## Icônes FontAwesome Disponibles

Ceci est la liste complète des bibliothèques Font Awesome incluses dans
Joomla 4

/media/vendor/fontawesome-free/webfonts/fa-brands-400

<div class="row">
<div class="small-12 large-4 columns"><span class="icon-joomla">&nbsp;</span>&nbsp; joomla</div>
</div>

L'ensemble est très détaillé et traduit mot à mot généralement, mais certaines parties, notamment les icônes, sont invariables et restent en anglais.

*Traduction par openai.com*


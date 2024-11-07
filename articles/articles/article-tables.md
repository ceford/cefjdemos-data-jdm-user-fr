<!-- Filename: J4.x:Article_Tables / Display title: Article : Modifier - Tableaux  -->

## À propos des tableaux

En HTML, les tableaux sont composés de lignes et de colonnes de cellules. Par exemple, un tableau simple peut se composer de 4 lignes et 4 colonnes, ce qui donne 16 cellules. Cependant, les cellules peuvent être combinées soit horizontalement soit verticalement pour créer des structures de tableaux assez complexes. Les tableaux ont également des fonctionnalités moins évidentes, telles qu'un en-tête, un corps, un pied de page et des légendes. Les tableaux peuvent être imbriqués !

Par défaut, les cellules de tableau s'étendent pour accueillir leur contenu. Le seul style provient du balisage du tableau : par défaut, les cellules d'en-tête (`<th>`) ont du texte en gras centré, tandis que les cellules de données (`<td>`) ont du texte normal aligné à gauche.

L'utilisation des tableaux doit être réservée à des données strictement tabulaires, telles qu'un emploi du temps ou un calendrier, où il est important de maintenir la structure des lignes et des colonnes. Les tableaux ne doivent pas être utilisés pour la mise en page, comme le placement d'images ou de textes côte à côte.

Il y a plus d'informations dans les articles suivants :

- [Notions de base sur les tableaux](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics)
- [Fonctionnalités avancées et accessibilité](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Advanced)
- [Stylisation des tableaux](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Styling_tables)

Les tableaux posent un dilemme ! Si vous insérez un tableau à l'aide des outils de tableau de TinyMCE, le tableau aura un bon rendu dans l'écran d'édition et sur le site, mais la mise en page est réalisée avec des styles CSS en ligne qui peuvent être volumineux et difficiles à éditer. Si le tableau est inséré en tant que pur HTML, le résultat n'est pas esthétique dans l'éditeur de texte TinyMCE, mais il peut tirer parti des classes Bootstrap et avoir une bien meilleure apparence sur le site. Les deux méthodes sont abordées ci-dessous.

## Insérer un tableau avec les outils TinyMCE

Pour commencer avec un tableau :

- Ouvrez l'article que vous souhaitez éditer.
- Placez le curseur sur une ligne vide où le tableau doit apparaître.
- Sélectionnez le bouton *Table* dans la première rangée des outils TinyMCE.
- Dans le menu déroulant, sélectionnez Table, puis déplacez le curseur pour définir le nombre de rangées et de colonnes. Les flèches du clavier fonctionnent aussi pour cela.
- Sélectionnez la dernière cellule dans la matrice 4x4.
- Remplissez les cellules du tableau.

Options d'édition :

- Vous pouvez insérer une rangée au-dessus ou au-dessous d'une cellule sélectionnée.
- Vous pouvez insérer une colonne avant ou après une cellule sélectionnée.
- Vous pouvez supprimer une rangée ou une colonne.
- Vous pouvez faire glisser les bordures des colonnes pour changer la largeur ou la hauteur des colonnes.
- Vous pouvez fusionner des cellules - faites glisser sur les cellules pour les sélectionner, puis utilisez Table -> Cellule -> Fusionner les cellules.
- Vous pouvez sélectionner les propriétés du tableau, y compris la largeur de bordure, le style et la couleur, et la couleur de fond.

Si vous utilisez le bouton Basculer l'éditeur, vous verrez que le format est obtenu avec des déclarations de style en ligne sur chaque rangée et chaque cellule. Voici un court extrait :

```html
<table style="border-collapse: collapse; width: 100%; height: 96px;" border="1"><colgroup><col style="width: 24.9735%;"><col style="width: 24.9735%;"><col style="width: 24.9735%;"><col style="width: 24.9735%;"></colgroup>
<tbody>
<tr style="height: 24px;">
<td style="height: 24px;">Jour</td>
<td style="height: 24px;">Matin</td>
<td style="height: 24px;">Après-midi</td>
<td style="height: 24px;">Soirée</td>
</tr>
<tr style="height: 24px;">
<td style="height: 24px;">Mardi</td>
<td style="height: 24px;">Accueil</td>
<td style="height: 24px;">Présentations</td>
<td style="height: 24px;">BBQ</td>
</tr>
...
</tbody>
</table>
```

## Insérer une Table en HTML

Si vous préférez, vous pourriez vous passer des styles en ligne et utiliser les classes Bootstrap. Vous devriez modifier la table créée par les outils de Table de TinyMCE ou la taper vous-même. Cela ressemblerait à ceci :

```html
<div class="table-responsive">
<table class="table table-striped table-bordered table-group-divider">
<thead>
<tr>
<th>Jour</th>
<th>Matin</th>
<th>Après-midi</th>
<th>Soirée</th>
</tr>
</thead>
<tbody class="table-group-divider">
<tr>
<th>Mardi</th>
<td>Accueil</td>
<td>Présentations</td>
<td>Barbecue</td>
</tr>
...
</tbody>
</table>
</div>
```

Ici, les classes Bootstrap ont les effets suivants :

- `table` - applique plusieurs styles pour donner un agencement standard et agréable à la table.
- `table-striped` - les lignes alternent entre sombres et claires.
- `table-bordered` - applique des bordures aux cellules.
- `table-group-divider` - applique une ligne épaisse au-dessus d'un élément.
- `table-responsive` - permet à une table large de défiler de droite à gauche.

La capture d'écran suivante montre une table pour un programme de conférence avec les styles en ligne par défaut de TinyMCE et une table similaire avec des styles Bootstrap :

![Exemples de tables](../../../en/images/articles/articles-site-tables.png)

Consultez la documentation Bootstrap sur les [Tables](https://getbootstrap.com/docs/5.3/content/tables/) pour plus d'options.

## Réflexion

Vous pouvez placer le code HTML d'un tableau dans un module personnalisé et inclure ce module dans l'article. Dans l'article, cela apparaît comme `{loadmoduleid xx}` où xx est l'ID du module.

*Traduit par openai.com*


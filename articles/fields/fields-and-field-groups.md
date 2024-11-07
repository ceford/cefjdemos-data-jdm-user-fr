<!-- Filename: J4.x:Fields_and_Field_Groups / Display title: Champs et Groupes de Champs -->

## Introduction

Les champs sont utilisés pour afficher des attributs supplémentaires des Articles, Contacts ou Utilisateurs. Les données sont saisies dans un formulaire de modification de l'administrateur et affichées sur le site. Un exemple :

Supposons que vous écriviez des articles sur des aspects de la nature, parfois sur les Fleurs, parfois sur les Animaux. Un champ que vous pourriez souhaiter enregistrer et afficher pour les deux est le Nom Latin, nécessitant un champ de texte. Un autre pourrait être Habitat : Forêt, Étang, Prairie, etc., nécessitant une liste déroulante. Pour les fleurs, vous pourriez souhaiter enregistrer la Saison de Floraison en utilisant 4 cases à cocher, une pour chaque saison, ou 12 cases à cocher, une pour chaque mois.

Les champs vides dans le formulaire de saisie ne sont pas affichés dans le résultat du Site, vous pourriez donc conserver tous les champs dans une liste longue. Cependant, il est généralement préférable d'utiliser des catégories pour vos Articles, par exemple Fleurs et Animaux. Les champs peuvent être attribués à plus d'une catégorie. Ainsi, les champs Nom Latin et Habitat seraient attribués aux deux, mais la Saison de Floraison ne serait attribuée qu'à la catégorie Fleurs.

Si un champ n'est pas attribué à un groupe, il apparaîtra dans le formulaire de modification sous l'onglet Champs. Si un champ est attribué à un groupe, il apparaîtra dans un onglet portant ce nom. Ainsi, pour le groupe Fleurs, il semble approprié de créer un groupe de champs nommé Données sur les Fleurs (ou simplement Fleurs, bien que l'utilisation du même nom pour des choses différentes puisse prêter à confusion). Et pour les autres champs communs, vous pourriez utiliser un groupe Nature.

## Un Exemple travaillé - Notes sur la Nature

Pour les articles sur la nature, la catégorie d'article et les sous-catégories pour chaque branche du monde vivant pourraient apparaître comme dans l'exemple suivant :

![Catégories d'articles pour la nature](../../../en/images/fields/fields-articles-categories-list.png)

Quelques caractéristiques évidentes de la nature à noter :

- La catégorie Nature est destinée aux articles qui traitent de la nature en général plutôt que de types spécifiques de plantes ou d'animaux.
- Les sous-catégories sont destinées aux articles plus spécifiques et peuvent nécessiter leurs propres sous-catégories.
- Toutes les formes de vie ont des noms communs et des noms latins.
- Les fleurs et les arbres ont une saison de floraison, une hauteur et une envergure, mais les oiseaux et les mammifères n'en ont pas.
- Les oiseaux ont une envergure et une longueur, tandis que les mammifères ont une hauteur et une longueur.
- La couleur peut être constante ou variable.

Le point ici est qu'il peut être nécessaire de mettre en place des champs ou des groupes de champs pour les caractéristiques communes, telles que le nom latin, et des groupes de champs séparés pour chaque catégorie de nature.

## Groupes de Champs

Créer des Groupes de Champs pour les Articles est très simple :

- Sélectionnez **Contenu → Groupes de Champs** dans le menu Administrateur.
- Sélectionnez le bouton **Nouveau** dans la barre d'outils.
- Entrez un **Titre** approprié.
- Entrez une **Description**. Celle-ci apparaît sous le champ dans le formulaire d'édition de l'article lorsque *Activer l'aide contextuelle* est sélectionné.
- Sélectionnez **Enregistrer et Fermer** dans la barre d'outils.

![Liste des groupes de champs de contenu](../../../en/images/fields/fields-field-groups-list.png)

### Ordonnancement

Dans l'entrée de données de l'article, les groupes de champs apparaîtront dans l'ordre vu dans cette liste. Faites glisser et déposez les éléments pour changer l'ordre.

## Champs

Pour créer un nouveau champ d'article, sélectionnez **Contenu → Champs** dans le menu de l'administrateur et remplissez le formulaire. Quelques exemples sont illustrés ci-dessous.

### Texte - Nom latin

Notez que dans la capture d'écran ci-dessous, ce champ a été attribué au groupe de champs Nature et à la catégorie Nature. Cela garantit qu'il apparaît toujours dans les articles de la catégorie Nature et toute sous-catégorie.

![Champ texte - nom latin dans le groupe nature](../../../en/images/fields/fields-latin-name.png)

### Cases à cocher - Saison de floraison

Les cases à cocher apparaissent dans le formulaire de modification d'article pour vous permettre de cocher la saison de floraison. Dans l'affichage de l'article, seules celles avec une coche seront listées. Par exemple, si vous cochez Printemps et Été, la sortie affichera Saison de floraison : Printemps, Été.

Notez que dans cette capture d'écran, le champ a été attribué au groupe Fleurs et à la catégorie Fleurs. Cela devrait garantir que le champ est uniquement présent dans les articles sur les fleurs.

![Champ case à cocher - saison de floraison](../../../en/images/fields/fields-flowering-season.png)

### Couleur - Color

Juste pour compliquer les choses, le nom du type de champ est Color (orthographe américaine) mais l'étiquette dans la documentation est Colour (orthographe britannique).

![Champ couleur](../../../en/images/fields/fields-colour.png)

Le champ Couleur est attribué au groupe de champs Nature et à la catégorie Nature, car il n'est pas unique aux fleurs.

### Entier - Rusticité

La rusticité d'une plante peut être représentée par un entier de 1 à 7. Il n'existe pas de champ pour un nombre réel, donc la longueur et la largeur pourraient être des entiers avec une échelle (cm ou m ou ft) incluse dans l'étiquette. Il existe des paramètres *Préfixe* et *Suffixe* dans l'onglet *Options*. S'il n'y a pas de limite supérieure évidente, laissez le champ *Dernier :* vide.

![Champ rusticité](../../../en/images/fields/fields-hardiness.png)

La rusticité RHS est une propriété généralement appliquée aux fleurs !

Il y a un problème avec le champ entier. Il a toujours une valeur et apparaît donc toujours dans la sortie. Vous pouvez contourner ce problème en personnalisant le modèle pour *Plugins / Integer*. Par exemple, vous pouvez utiliser une valeur au-dessus ou en dessous des limites prévues pour omettre le champ de la sortie.

## Formulaire de Modification d'Article

Lorsqu'un formulaire Articles : Nouveau est ouvert, la Catégorie par défaut est Non catégorisé, et les onglets du formulaire n'incluent pas Champs et Fleurs. Sélectionnez la catégorie Fleurs et le formulaire est rechargé avec ces onglets présents.

### Onglet Nature

![Onglet nature de l'article jacinthe des bois](../../../en/images/fields/field-article-bluebell-nature-tab.png)

- **Nom Latin** Il s'agit d'un champ de saisie de texte, donc il suffit de taper le nom latin de la forme de vie que l'article couvre. Cependant, la catégorie Nature couvre la vie en général ainsi que des animaux ou plantes spécifiques. Ce n'est donc pas un champ *obligatoire*.
- **Couleur** Le champ de sélection de couleur peut prendre soit une saisie clavier d'une valeur hexadécimale de couleur, soit une couleur sélectionnée à partir de l'outil de sélection des couleurs. Le numéro hexadécimal est xrrggbb où rr sont les valeurs de rouge, gg les valeurs de vert et bb les valeurs de bleu. En sortie, le site affiche la valeur hexadécimale, ce qui n'est pas très utile !

### Onglet Fleurs

![Onglet nature de l'article jacinthe des bois](../../../en/images/fields/field-article-bluebell-flowers-tab.png)

- **Saison de Floraison** Le champ à cases à cocher - les jacinthes des bois sont des fleurs bien connues du printemps, donc la sélection d'une case à cocher est appropriée.
- **Résistance** Le champ entier. Il y a un problème ici - il n'existe aucune méthode pour laisser ce champ vide. Il est donc toujours présent dans la sortie, même pour les articles plus généraux sur les fleurs où ce n'est pas approprié. Il existe une solution de contournement impliquant une substitution de modèle.

## Résultat du site

Jetez un coup d'œil au résultat visible sur votre site. Dans cet exemple, un élément de menu pour un seul article a été créé :

![Vue de l'article Bluebell sur le site](../../../en/images/fields/field-article-bluebell-site.png)

### La couleur hexadécimale

L'affichage par défaut des données est la valeur de la couleur hexadécimale, ce qui n'est pas très utile. La solution simple est de créer un remplacement de modèle pour le plugin fields / color, ce qui est montré dans la capture d'écran ci-dessus.

Il suffit de remplacer cette ligne :
```
echo htmlentities($value);
```
par ces lignes :
```
if (is_array($value)) {
  $list = [];
  foreach ($value as $v) {
    $x = htmlentities($v);
    $list[] = '<span class="ps-5 pe-5" style="background-color: ' . $x . ';">&nbsp</span> ' . $x;
    echo implode(', ', $list);
  }
} else {
    $x = htmlentities($value);
    echo '<span class="ps-5 pe-5" style="background-color: ' . $x . ';">&nbsp</span> ' . $x;
}
```
Et la valeur hexadécimale sera précédée d'un échantillon avec la couleur de fond de la valeur.

*Traduit par openai.com*


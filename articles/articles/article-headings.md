<!-- Filename: J4.x:Article_Headings / Display title: Article : Modifier - Titres   -->

## Sémantique des Titres

Les titres définissent une structure sémantique pour une page. Ils peuvent être utilisés pour créer une table des matières automatique et comme aides à la navigation pour les utilisateurs en situation de handicap. Les niveaux de titres vont de h1 à h6. Une page unique ne devrait contenir qu'un seul titre h1, qui est généralement le titre de la page. Un titre h1 ne doit pas être utilisé dans un article. Dans un article, les titres doivent être imbriqués pour créer une structure dans laquelle chaque niveau de titre introduit une section bien définie. Exemple, où le titre de la page h1 est Animaux :

```
    ... texte sur les animaux en général ...
    <h2>Amphibiens</h2>
    ... texte sur les amphibiens en général ...
    <h3>Grenouilles</h3>
    ... texte sur les grenouilles ...
    <h3>Tritons</h3>
    ... texte sur les tritons ...
    <h2>Reptiles</h2>
    ... texte sur les reptiles en général ...
    <h3>Crocodiles</h3>
    ... texte sur les crocodiles ...
    <h3>Tortues<h3>
    ... texte sur les tortues ...
```

Les titres facilitent la lecture. De longs blocs de texte sur les pages web sont rebutants ! Réservez-les pour les romans.

Les titres doivent être courts, plus c'est court mieux c'est. Un seul mot suffira. Des phrases complètes ne font pas de bons titres ! Les titres ne doivent pas se terminer par un point final.

Les titres sémantiques ne doivent pas sauter de niveaux, par exemple en incluant un h4 dans un bloc h2 juste pour obtenir une apparence spécifique.

## Insérer un Titre d'Article

Ouvrez l'article que vous souhaitez éditer. Remarquez que le conteneur de texte par défaut est un paragraphe, marqué par une lettre `P` dans une barre d'informations en dessous de la zone de texte en bas de la fenêtre d'édition. Le conteneur par défaut peut être modifié dans les Options de l'Éditeur, mais cela est traité ailleurs. Lorsque vous tapez un saut de ligne suivi de texte, ce texte est contenu dans un paragraphe. Pour créer un titre :

- Positionnez le curseur au début d'un paragraphe existant ou en bas du texte si vous créez une nouvelle section.
- Tapez le titre suivi d'un saut de ligne.
- Sélectionnez la ligne à transformer en titre.
- Dans les boutons de format de l'éditeur, où *Paragraphe* est affiché comme sélectionné :
  - Sélectionnez **Titres → Titre X** où X est la valeur appropriée pour votre hiérarchie.
- Le paragraphe sélectionné deviendra un titre et apparaîtra en texte gras.
- En bas de l'écran, l'indicateur de conteneur affichera HX.
- Vous pouvez double-cliquer sur n'importe quel texte sélectionné pour effectuer un changement rapide, par exemple de P à H2 (bascule) ou de H2 à H3 en utilisant une barre contextuelle comme dans la capture d'écran suivante :

![formulaire d'édition d'article avec h3 sélectionné](../../../en/images/articles/articles-edit-headings.png)

Remarque : par convention, toutes les balises HTML utilisent des lettres minuscules. Si vous sélectionnez le bouton *Basculer l'Éditeur* pour voir la source, vous verrez les paragraphes et les titres définis dans des balises en minuscules.

## Conseils

- Double-cliquez sur n'importe quelle sélection de texte pour voir une fenêtre contextuelle avec une liste d'options de formatage. Les sélections *Titre* et *Citation en bloc* sont appliquées à tout le paragraphe. Les options *Gras*, *Italique* et *Souligné* sont appliquées aux caractères sélectionnés.
*Traduit par openai.com*


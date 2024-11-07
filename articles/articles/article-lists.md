<!-- Filename: J4.x:Article_Lists / Display title: Article : Modifier - Listes  -->

## Types de listes

HTML possède trois types de listes :

- Les listes à puces sont souvent stylées avec un retrait et une puce,
  comme cette liste.
- Les listes ordonnées sont similaires mais marquées avec des numéros.
- Les listes de définitions consistent en titres et définitions.

Les points de puce et les numéros sont appliqués par le navigateur à
partir d'une sélection de styles. L'utilisateur ne doit pas entrer de texte
de puce ou de numéro car cela sera traité comme faisant partie de la liste.
L'éditeur TinyMCE a des icônes pour appliquer les styles de puces les
plus courants et les types de numérotation. Les listes de définitions
sont plus compliquées et nécessitent d'être créées manuellement.

Les listes peuvent contenir d'autres listes à n'importe quel niveau,
bien que les listes profondément indentées deviennent difficiles à lire,
il est donc préférable de se limiter à un ou deux niveaux.

## Capture d'écran

La capture d'écran suivante montre une liste non ordonnée avec deux niveaux de retrait. Elle montre également l'ensemble complet des outils, ouvert en sélectionnant le bouton points de suspension (...) à la fin de la première rangée d'icônes d'outils.

![Listes non ordonnées imbriquées](../../../en/images/articles/articles-edit-lists.png)

Cette capture d'écran sera utilisée pour expliquer comment la liste à puces a été créée en utilisant les outils *Liste à puces* et *Augmenter le retrait* ou *Diminuer le retrait* :

## Styles de Liste

### Listes à puces

Trois styles sont disponibles :

- Un cercle plein est le style par défaut.
- Un cercle vide.
- Un carré plein.

La flèche vers le bas à droite de l'icône de liste à puces ouvre un petit panneau
permettant de sélectionner le style préféré pour un élément de liste sélectionné :

![Outils de manipulation de liste à puces](../../../en/images/articles/articles-edit-list-bullets.png)

L'icône de liste fonctionne comme un bascule. Si le curseur est dans un paragraphe et qu'une puce
est sélectionnée, le paragraphe devient un élément de liste. Si la puce est sélectionnée à nouveau,
l'élément de liste redevient un paragraphe.

Si deux paragraphes ou plus sont sélectionnés et qu'une icône de liste est sélectionnée, chacun des
paragraphes devient un élément de liste. Pour créer une liste avec retrait, sélectionnez l'outil 
*Augmenter le retrait* à droite des outils de liste. Par défaut, l'élément 
de liste avec retrait adoptera le style de liste suivant.

Pour expliquer comment créer des listes avec retrait comme dans la capture d'écran :

- Tapez chacun des termes comme des paragraphes d'un seul mot.
- Sélectionnez tous les paragraphes à transformer en liste à puces.
- Sélectionnez l'icône *Liste à puces*.
- Sélectionnez le premier groupe de termes à indenter.
- Sélectionnez l'icône *Augmenter le retrait*.
- Sélectionnez le deuxième groupe de termes à indenter.
- Sélectionnez l'icône *Augmenter le retrait*.

### Listes numérotées

Six styles sont disponibles :

- Chiffres : 1, 2, 3 ...
- Lettres : a, b, c ...
- Caractères grecs : &alpha;, &beta;, &gamma; ...
- Chiffres romains en minuscules : i, ii, iii ...
- Lettres majuscules : A, B, C ...
- Chiffres romains en majuscules : I, II, III ...

![Outils de manipulation de liste numérotée](../../../en/images/articles/articles-edit-list-numbers.png)

Les listes numérotées fonctionnent un peu différemment. Lorsqu’un élément de liste est indenté, il prend
la première valeur numérique et les numéros du reste de la liste montent de sorte
que la liste soit toujours dans le bon ordre numérique.

### Listes mixtes

Le système de numérotation peut être modifié à chaque niveau. Par exemple, vous pouvez définir 
le premier niveau pour utiliser des valeurs numériques et le deuxième niveau pour utiliser des puces, ou
des caractères grecs, ou autre chose.

Il est probablement préférable d'expérimenter avec les listes pour voir comment elles peuvent être manipulées.

## Listes de définitions

Les listes de définitions se composent d'un *Titre de définition* et d'une ou plusieurs *Descriptions de définition* suivies du *Titre de définition* suivant et de sa *Description*. Elles sont utiles pour un *Glossaire* ou tout type d'ensemble de paires *Clé / Valeur*. Pour créer une liste de définitions :

- Sélectionnez le bouton *Basculer l'éditeur* pour voir le balisage de l'article HTML.
- Tapez le balisage de la liste de définitions. Voici un exemple :
```html
<dl>
<dt>Amphibie</dt>
<dd>Vertébré à sang froid qui pond des œufs dans l'eau et qui a un stade larvaire aquatique.</dd>
<dt>Reptile</dt>
<dd>Vertébré à sang froid qui pond des œufs sur terre.</dd>
</dl>
```
Enregistrez et visualisez le résultat dans l'aperçu.

*Traduit par openai.com*


<!-- Filename: J4.x:Module_and_Menu_Styles / Display title: Styles de module et de menu -->

## À propos des feuilles de style en cascade

Une page de site web générée par Joomla! se compose de balises HTML avec des attributs de style sous la forme d'instructions de classe. Par exemple, un titre dans un article pourrait être `<h3 class="special-warning">Attention !</h3>`. Ce titre pourrait apparaître dans une police plus grande, avec des couleurs différentes pour le texte et l'arrière-plan, et peut-être un bord et une icône d'avertissement. Les styles de la classe seraient définis dans le fichier user.css du modèle, comme suit :
```css
    h3.special-warning {
      color: #900;
      background-color: #fee;
      border: 1px solid #900;
      padding: 1rem;
      font-size: 2rem;
    }
```
Cela fonctionne parce que la feuille de style user.css est chargée en dernier et que tous les styles qu'elle contient prennent le pas sur les mêmes styles dans les fichiers css chargés précédemment. Le style `special-warning` ne s'applique pas aux autres balises `<h3>`, uniquement à celles ayant cette classe spécifique. Cela fonctionne dans un article car vous tapez vous-même le nom de la classe.

Mais que faire si vous voulez styliser un module ou une page entière ? Par exemple, vous pourriez appliquer des couleurs de fond différentes à différents modules ou pages. Ou vous pourriez donner un style différent à votre en-tête de page d'accueil par rapport aux en-têtes des autres pages. Tout cela peut être réalisé en ajoutant des noms de classes dans le formulaire d'édition du module ou dans le formulaire d'édition de l'élément de menu. Les classes de style sont ensuite saisies dans le fichier user.css.

## Styles de module

Cet exemple simple applique des styles personnalisés au module de connexion et à son titre. La capture d'écran suivante montre les noms de style saisis dans l'onglet Avancé du formulaire d'édition du module : Connexion. La Classe de module a été définie sur `make-me-light-green` et la Classe d'en-tête a été définie sur `make-me-dark-green`. Notez que vous pouvez inclure des tirets ou des traits de soulignement dans les noms de classe, mais les espaces séparent les différents noms de classe.

![formulaire d'édition du module de connexion, onglet avancé, montrant la classe personnalisée](../../../en/images/templates/templates-edit-module-style.png)

Les déclarations de style suivantes sont utilisées dans le fichier user.css :
```css
    .make-me-light-green {
      background-color: #efe;
      border-color: darkgreen;
    }
    .make-me-dark-green {
      color: darkgreen;
      border-color: #264f71;
    }
```
Faites attention au point (.) utilisé en CSS pour définir une classe avec ce nom. Le point ne doit pas être utilisé dans le formulaire de saisie de données du module. Le résultat dans cet exemple est le suivant :

![apparence du site du module personnalisé avec les outils de développement](../../../en/images/templates/templates-edit-module-style-result.png)

Le bas de l'image montre le panneau des outils de développement du navigateur avec la balise `<div>` entourant le module de connexion sélectionné. Vous pouvez voir que le style de la Classe de module personnalisée a été ajouté aux styles déjà définis dans le modèle de module. La ligne suivante montre la balise `<h3>` également avec la Classe d'en-tête personnalisée ajoutée aux styles déjà définis.

Vous aimerez ou n'aimerez peut-être pas ce style de module ! Mais ce n'est qu'une leçon sur la façon de le faire, pas sur ce qui fait un bon schéma de couleurs !  

## Styles de Page

Il existe plusieurs façons de personnaliser l'apparence générale d'une page. Tout fonctionne via le formulaire de l'élément de menus : Éditer l'élément :

- L'onglet Détails dispose d'une option de Style de Modèle à partir de laquelle vous pouvez sélectionner un modèle spécifique à utiliser.
- L'onglet Disposition du Blog a des champs pour la Classe de l'Article Principal et la Classe de l'Article dans lesquels vous pouvez entrer un nom de classe.
- L'onglet Options propose un champ Choisir une Disposition à partir duquel vous pouvez choisir parmi les dispositions disponibles pour tous les éléments.
- L'onglet Type de Lien dispose de champs pour une Classe de Lien, une Classe d'Icône de Lien et une Classe d'Image.
- L'onglet Affichage de la Page dispose de champs pour une Classe de Page.

C'est le dernier point de cette liste qui est traité dans cet article. Que se passe-t-il lorsque `make-me-aliceblue` est entré dans ce champ ? Et que l'on entre ce qui suit dans user.css :
```css
    .make-me-aliceblue {
      background-color: aliceblue;
    }
```
La classe est ajoutée à la balise body de la page :

![apparence du site de la page personnalisée avec les outils de développement](../../../en/images/templates/templates-edit-page-class-result.png)

CQFD !

*Traduit par openai.com*


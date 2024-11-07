<!-- Filename: Article_Images_and_Links / Display title: Article : Modifier - Images et Liens  -->

## Introduction

D'autres articles ont décrit comment intégrer des images et des liens dans le contenu d'un article. Cet article décrit l'utilisation de l'onglet *Images et Liens* pour ajouter deux types d'image et jusqu'à trois liens à utiliser dans des mises en page standardisées. En résumé :

- L’*Image d’introduction* est utilisée dans les mises en page de Blog ou Liste de catégorie comme un aperçu visuel supplémentaire du type de contenu à attendre.
- L’*Image de l'article complet* est placée en haut de l'article complet comme une introduction visuelle au contenu.
- Les liens : Lien A, Lien B et Lien C sont placés au-dessus du texte de l'article.  

## Capture d'écran

Pour cet article, à partir d'une image d'une rainette verte de 1024 pixels de large, deux images plus petites ont été créées, mesurant respectivement 128 et 256 pixels de large.  
Remarque : il est préférable de préparer les images dans votre outil de traitement d'image préféré, tel que *Gimp*. Les images de petite et moyenne taille ont été utilisées pour créer les captures d'écran suivantes.

![Formulaire de modification de l'article, onglet images et liens](../../../en/images/articles/articles-edit-images-and-links-tab.png)

## Champs de Formulaire

### Image d'Introduction

- **Image d'Intro** Sélectionnez une image appropriée à utiliser dans les mises en page du blog où elle apparaîtra normalement au-dessus du titre de l'article. Ceci est facultatif. Si laissé vide, il n'y aura pas d'image d'introduction dans la mise en page du blog.
- **Description de l'Image (Texte Alt)** Entrez une description d'image appropriée pour les lecteurs d'écran.
- **Image Décorative** Si aucune *Description de l'Image* n'est fournie et que ce bouton n'est pas coché, la page ne passera pas les tests d'accessibilité. Si ce bouton est coché, un attribut `alt` vide sera inséré. Cela peut permettre à la page de passer les tests d'accessibilité. Il est probablement préférable d'utiliser toujours une bonne description courte de l'image.
- **Classe de l'Image** La classe par défaut est *gauche*, signifiant float-left. Mais toute autre valeur de flottement ici n'aura aucun effet car elle ne peut pas être utilisée sur des éléments de grille ou flex.
- **Légende de l'Image** Les mots saisis ici apparaîtront comme une légende sous l'image. **Attention :** N'utilisez pas exactement les mêmes mots à la fois pour le texte alt et la légende. Les lecteurs d'écran annonceront l'information deux fois.
    - Le texte alt doit fournir une description concise de ce qui se trouve dans l'image.
    - La légende doit généralement fournir un contexte pour relier l'image au contenu environnant ou attirer l'attention sur une information particulière.

### Image de l'Article Complet

Les mêmes champs que pour l'image d'introduction, mais l'image est utilisée dans un contexte différent. Voir les captures d'écran du site ci-dessous.

### Lien A

- **Lien A** Collez l'URL complète de la page cible. L'URL complète doit être utilisée même si la page cible est sur ce site.
- **Texte du Lien A** Tapez le texte à utiliser pour le lien cible.
- **Fenêtre Cible de l'URL** Choisissez l'une des options cibles :
  - **Utiliser Global (Ouvrir dans la fenêtre parent)**
  - **Ouvrir dans la fenêtre parent** C'est le comportement préféré car le bouton de retour du navigateur peut être utilisé pour revenir à la page précédente.
  - **Ouvrir dans une nouvelle fenêtre** Certains utilisateurs aiment cela mais cela confond les utilisateurs mobiles car il n'est pas évident qu'une nouvelle fenêtre a été invoquée et il n'y a pas de bouton de retour.
  - **Ouvrir en popup** Une petite fenêtre popup apparaît. La fenêtre principale reste disponible. Chaque clic sur le lien ouvre une autre instance de fenêtre popup.
  - **Ouvrir en modal** Une boîte de dialogue modale s'ouvre au centre de l'écran qui est inactive jusqu'à ce que la boîte de dialogue soit fermée.

### Liens B et C

Exactement la même saisie de données que le Lien A.  

## Captures d'écran du site

La capture d'écran ci-dessous montre une mise en page de blog de catégorie avec l'*Image d'Intro*. Il aurait peut-être été préférable d'utiliser une image panoramique de la même hauteur mais beaucoup plus large pour occuper l'espace blanc vacant.

![Page de blog de la catégorie Amphibiens](../../../en/images/articles/articles-site-amphibians-blog.png)

La capture d'écran ci-dessous montre la page d'un article individuel avec l'*Image de l'Article Complet* et le Lien A. L'image a été alignée à droite et la légende visible dit quelque chose pour compléter ce que la Description dit, afin que cela semble logique pour les lecteurs d'écran.

![Page d'un article individuel sur les grenouilles](../../../en/images/articles/articles-site-amphibians-frogs.png)

*Traduit par openai.com*


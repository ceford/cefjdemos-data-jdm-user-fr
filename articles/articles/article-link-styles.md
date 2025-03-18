<!-- Filename: J5.x:Add_a_class_selector_to_the_create_link_dialog / Display title: Article : Modifier - Styles de lien -->

## Description

Des classes de lien personnalisées ajoutées aux options de l'éditeur TinyMCE vous permettent de transformer rapidement un lien d'article en bouton ou d'ajouter d'autres effets visuels sans avoir à modifier directement le code HTML.

### Étapes pour utiliser le sélecteur de classe

1. Depuis le tableau de bord d'accueil, allez à la liste des plugins et trouvez le plugin TinyMCE.
2. Ouvrez le plugin TinyMCE et avec l'onglet Plugin sélectionné, faites défiler jusqu'en bas.
3. Ajoutez des classes à la *Liste de classes de liens* Par exemple, des classes Bootstrap pour créer des boutons élégants. Vous devrez peut-être faire défiler la liste de gauche à droite ou changer le grossissement de l'écran pour voir les boutons ajouter, supprimer et ordonner à la fin.
4. Enregistrez & Fermez.

![Set link classes in tinymce](../../../en/images/articles/article-edit-link-style-tinymce.png)

Vous pouvez trouver des exemples de modèles qui utilisent Bootstrap nativement dans la [documentation officielle de Bootstrap](https://getbootstrap.com/docs/5.3/components/buttons/).

Voici quelques classes que vous pouvez utiliser pour les variantes de boutons Bootstrap :

- `btn btn-primary` pour un bouton principal
- `btn btn-secondary` pour un bouton secondaire
- `btn btn-success` pour un bouton de réussite
- `btn btn-danger` pour un bouton de danger
- `btn btn-warning` pour un bouton d'avertissement
- `btn btn-info` pour un bouton d'information
- `btn btn-light` pour un bouton clair
- `btn btn-dark` pour un bouton sombre
- `btn btn-link` pour un bouton lien

#### Alternatives au bouton contour

Vous pouvez également utiliser les variantes de bouton de contour :

- `btn btn-outline-primary` pour un bouton principal avec contour
- `btn btn-outline-secondary` pour un bouton secondaire avec contour
- … (etc.)

#### Pour les tailles de bouton, ajoutez ces classes

- `btn-lg` pour un grand bouton
- `btn-sm` pour un petit bouton

**Exemple :** `btn btn-dark btn-lg` (un grand bouton sombre)

## Créer un lien dans un article

1. Ouvrez un article et sélectionnez du texte, un mot ou une phrase, pour créer un lien.
2. Sélectionnez l'icône Lien qui apparaît lorsque vous sélectionnez du texte.
3. Entrez l'URL pour le lien.
4. En bas de la boîte de dialogue de création de lien, sélectionnez l'une des classes configurées.
5. Enregistrez le lien.
6. Enregistrez l'article.
7. Prévisualisez l'article.

![Apply link style in an article](../../../en/images/articles/article-edit-link-style-apply.png)

Et voici un exemple où la classe du bouton de lien a été définie sur `btn btn-sm btn-outline-info` et le texte lié est *Bootstrap* :

![Preview of a custom Link Button](../../../en/images/articles/article-edit-link-style-preview.png)

## Utilisation avancée : Application de classes personnalisées

Cette fonctionnalité n’est pas limitée aux classes Bootstrap. Vous pouvez également appliquer vos propres classes CSS personnalisées pour des besoins spécifiques. Par exemple, vous pouvez ajouter une icône avant le lien avec un effet au survol. Cela facilite le style des liens sans avoir besoin de modifier le code source de l'article.  
*Traduit par openai.com*


<!-- Filename: J4.x:Article_Pagination / Display title: Article : Modifier - Pagination  -->

## Articles Longs

La seule limite à la longueur d'un article dans Joomla est la taille du champ de la base de données utilisé pour contenir le texte de l'article. Cette taille est très grande ! Les articles longs peuvent contenir de nombreuses images et prendre du temps à traiter, ce qui peut être gênant pour le lecteur et le site web. Il existe donc un mécanisme simple pour diviser les articles longs en pages distinctes avec une table des matières.

## Insérer un saut de page

Pour ajouter des sauts de page, ouvrez d'abord un article dans l'éditeur de texte, TinyMCE est l'éditeur par défaut, et procédez comme suit :

- Positionnez le curseur à l'endroit où un saut de page doit se produire.
- Dans la liste déroulante **Contenu du CMS**, sélectionnez l'élément *Saut de page*.
- Dans la boîte de dialogue Saut de page, entrez :
  - *Titre de la page* - cela sera ajouté au titre de la page existante.
    Exemple : Page 2
  - *Alias du Table des Matières* - cela sera utilisé comme texte dans la Table
    des Matières. Exemple : Chapitre 2
- Sélectionnez le bouton **Insérer un saut de page**.

![Formulaire de dialogue saut de page](../../../en/images/articles/articles-edit-pagination.png)

- Répétez l'opération pour chaque saut de page que vous souhaitez créer.
- Enregistrez l'article et jetez un œil à l'Aperçu ou à l'affichage du site.

![Affichage du site avec pagination de l'article](../../../en/images/articles/articles-site-pagination.png)

## Modifier ou Déplacer un Saut de Page

Vous pouvez sélectionner un saut de page et le supprimer. Cependant, vous ne pouvez pas le couper et le coller, et vous ne pouvez pas ouvrir un saut de page existant dans le formulaire de Saut de Page. Pour déplacer ou modifier un saut de page, utilisez l'éditeur de code source comme suit :

- Sélectionnez l'élément **Outils -> Code source+** de l'éditeur de texte.
- L'éditeur de code source affiche le HTML source avec une coloration syntaxique.
- Faites défiler jusqu'au saut de page que vous souhaitez modifier ou déplacer.
- Pour déplacer un saut de page :
  - Sélectionnez et coupez la ligne contenant le saut de page.
  - Placez le curseur à la nouvelle position et collez la ligne coupée.
- Pour modifier :
  - Changez le texte du titre et/ou le texte alternatif comme vous le souhaitez.
- Sélectionnez **Enregistrer**.
- Enregistrez l'article et vérifiez l'Aperçu ou la vue du Site.

L'éditeur de code source se trouve dans une boîte de dialogue contextuelle :

![Éditeur de code source](../../../en/images/articles/articles-edit-pagination-source-code.png)


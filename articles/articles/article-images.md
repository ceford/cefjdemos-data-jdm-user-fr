<!-- Filename: Adding_an_image_to_an_article / Display title: Article : Édition - Images -->

## Introduction

Il est important de comprendre que les images pour les documents web sont stockées séparément du texte HTML. Lorsqu'une page web est demandée, le navigateur récupère d'abord le texte et des fichiers de support séparés comme les feuilles de style et les scripts JavaScript. Les images sont récupérées plus tard. Souvent, le navigateur et le serveur web négocient quelle version d'une image récupérer pour convenir à la taille et à la résolution de l'écran du navigateur. Il existe même une extension Joomla disponible qui crée plusieurs versions d'une image parente dans différentes tailles et formats pour améliorer la vitesse de livraison et de rendu.

Les images sont intégrées dans les pages web par l'inclusion de liens formatés de manière appropriée. Il existe deux mécanismes différents pour inclure des images dans les articles :

- L'onglet *Contenu* du formulaire d'édition permet l'insertion d'un ou plusieurs liens vers des images directement dans le texte de l'article. C'est le sujet de cet article.
- L'onglet *Images et Liens* du formulaire d'édition permet l'inclusion d'une image en tant qu'*Image d'introduction* ou d'*Image de l'article complet* ou les deux. Cela est couvert dans un article séparé sur [Images et Liens](jdocmanual?article=user/articles/article-images-and-links).

Il convient de faire une distinction entre les images locales et les images distantes :

- **Images Locales** sont situées sur le même site que l'installation Joomla, généralement dans le dossier *images*. Les liens vers les images ne nécessitent pas d'inclure le protocole et le nom de domaine, car ils sont pris à partir des paramètres du site.
- **Images Distantes** sont situées ailleurs sur Internet. Elles doivent inclure le protocole et le nom de domaine dans le lien. L'utilisation d'images distantes par un tel *hot-linking* peut être permise aujourd'hui mais pas demain. L'utilisation d'images distantes sans autorisation est considérée comme une mauvaise étiquette ou même du vol.

## Ajouter une image locale

La meilleure façon d'insérer des images locales est d'utiliser le bouton **CMS Contenu → Médias** dans la barre d'outils d'édition TinyMCE. Cela ouvre une boîte de dialogue Média qui permet de sélectionner n'importe quelle image dans le dossier d'images du site.

**Important :** Placez d'abord le curseur à l'endroit où vous souhaitez que l'image apparaisse. Cela peut être au début ou à la fin d'un paragraphe ou dans un paragraphe vide.

![La boîte de dialogue à fenêtres contextuelles média](../../../en/images/articles/articles-edit-images-media.png)

Dans la boîte de dialogue, naviguez vers l'image que vous souhaitez utiliser et sélectionnez-la. Une fois sélectionnée, un formulaire apparaîtra pour demander des informations supplémentaires.

- **Description de l'image (Texte alternatif)** Ceci est important pour des raisons d'accessibilité et de conformité avec les normes web.
- **Classe d'image** Si une image est utilisée sans légende, certaines classes personnalisées peuvent être appliquées ici. Par exemple, *float-end ms-2 mb-1* alignera l'image à droite et fera flotter le texte autour avec des marges à gauche et en dessous pour éviter que le texte ne touche l'image.
- **Classe de figure** Si une légende est définie, une classe d'alignement, le cas échéant, peut être appliquée à la figure. Notez que dans Cassiopeia, les marges sont appliquées à la figure par la feuille de style du modèle, donc *float-start* ou *float-end* suffisent.
- **Légende de la figure** Active la légende qui affiche le contenu de ce champ comme une légende sous l'image.

**Important :** Si le champ *Légende de la figure* est vide, l'image sera insérée dans une balise `<img...>` et le champ *Classe de figure* ne sera pas utilisé. Si le champ *Légende de la figure* contient du texte, la balise `<img...>` sera enveloppée dans des balises `<figure>...</figure>`. Les classes les plus utiles à ajouter sont *float-start* et *float-end* pour placer l'image à gauche ou à droite de la page avec le texte se déroulant autour.

Sélectionnez le bouton *Insérer média* pour insérer l'image. L'écran Insérer une image se fermera et l'image sera affichée dans l'éditeur. Ou sélectionnez le bouton *Annuler* pour quitter l'écran Insérer une image.

**Astuce** sélectionnez le bouton Basculer l'éditeur pour voir les styles d'image et de figure appliqués. Vous devrez peut-être couper et coller une figure ou une image pour la déplacer.

### Utiliser le glisser-déposer pour les images locales

Vous pouvez faire glisser une image depuis le bureau ou un navigateur de fichiers directement dans le texte de l'article, et l'image sera téléchargée dans le dossier média et placée dans l'article. Le seul inconvénient est que toutes les images téléchargées de cette manière seront placées dans le même dossier média.

L'emplacement du *Répertoire des images* utilisé pour le téléchargement et si cette fonctionnalité est activée (par défaut) sont définis dans les options de configuration de TinyMCE.

## Ajout d'un lien vers une image distante

Si l'image que vous souhaitez utiliser n'est pas dans le dossier des images de votre installation Joomla, une procédure légèrement différente est nécessaire.

- Sélectionnez **Insérer → Image** dans la barre d'outils de TinyMCE pour ouvrir une boîte de dialogue.
- Dans le champ **Source**, insérez l'URL de l'image.
- Complétez les autres champs selon vos besoins.
- L'onglet **Avancé** offre quelques options de formatage appliquées sous forme de styles en ligne. Expérimentez avec 1rem, 2, groove.

![La boîte de dialogue contextuelle d'insertion d'image](../../../en/images/articles/articles-edit-images-external-image.png)

### Utiliser le glisser-déposer pour insérer des liens vers des images distantes

Vous pouvez glisser-déposer un lien d'image d'un site web distant directement dans le texte de votre article. Mais soyez conscient que cela peut également copier le conteneur HTML de l'image avec des déclarations de classe non valides pour votre site.

## Téléchargement d’images à l’aide de la boîte de dialogue Médias

Vous pouvez télécharger de nouvelles images dans votre dossier d'images depuis la page *CMS Content -> Media*.

- Ouvrez la boîte de dialogue Médias et naviguez jusqu’au dossier où vous souhaitez enregistrer de nouvelles images pour l’article actuel.
- Sélectionnez le bouton Télécharger en haut à gauche de l’écran des Médias pour ouvrir un explorateur de fichiers.
- Sélectionnez les fichiers d'image que vous souhaitez télécharger. Cliquez sur Ouvrir dans l’explorateur de fichiers pour confirmer la sélection. Remarque : Le style et la disposition de l’explorateur de fichiers dépendent du navigateur et du système d’exploitation que vous utilisez.
- Les fichiers sélectionnés apparaissent par ordre alphabétique dans l'écran Médias/Image.
- Lorsque le téléchargement est terminé, un avis de confirmation vert apparaîtra en haut de l’écran.

Vous pouvez désormais sélectionner et insérer l'image téléchargée comme avant.

*Traduit par openai.com*


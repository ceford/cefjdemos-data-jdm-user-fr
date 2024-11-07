<!-- Filename: J4.x:Article_Preview / Display title: Article : Aperçu -->

## Introduction

Il peut être utile de prévisualiser un article avant de le publier. Il y a un bouton de *Prévisualisation* dans la barre d'outils du formulaire de modification de l'*Article* en backend à cet effet. Cependant, cette fonctionnalité utilise l'article enregistré et non le contenu du formulaire de l'éditeur. La fonctionnalité de prévisualisation n'est pas disponible dans le formulaire de modification d'article en frontend.

Vous pourriez ne pas vouloir rendre un article visible avant qu'il ne soit terminé. À cet effet, différentes stratégies sont nécessaires pour les éditeurs en frontend et en backend.

## Aperçu du Frontend

La seule façon de garder un article semi-privé depuis le frontend est de définir son accès sur *Enregistré* afin que seuls les utilisateurs connectés puissent le voir.

- Connectez-vous à l'interface frontend du site.
- Sélectionnez le lien *Modifier* pour un article à mettre à jour. Ou bien...
- Sélectionnez le bouton *Nouvel Article* sous les mises en page du blog.
  - Définissez le niveau d'accès de l'article sur *Enregistré* jusqu'à ce qu'il soit prêt pour la publication.
  - Vous pouvez ajouter un avis *Alerte* indiquant que l'article est en cours de construction : `<div class="alert alert-warning">En Construction</div>`.
- *Enregistrer & Fermer* pour voir l'article.

## Aperçu du Backend

Après vous être connecté à l'interface Administrateur :

- Sélectionnez un article à modifier ou créez-en un nouveau et enregistrez-le.
- Pour garder un nouvel article privé pour l'instant, définissez le Statut sur *Non publié* ou laissez-le *Publié* et ajustez la date de *Début de publication*.
- Apportez des modifications et *Enregistrez* l'article.
- Sélectionnez le bouton *Aperçu* dans la barre d'outils. Une fenêtre contextuelle d'aperçu devrait apparaître.
- Si vous recevez un message *La page demandée est introuvable*, connectez-vous à l'interface Frontend et réessayez.
- Pour fermer la fenêtre d'aperçu, sélectionnez le bouton *X* dans le coin supérieur droit.

![La fenêtre d'aperçu](../../../en/images/getting-started/article-edit-preview.png)

*Traduit par openai.com*


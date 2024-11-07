<!-- Filename: J4.x:Deleting_an_Article / Display title: Articles : Supprimer -->

## Introduction

Dans Joomla, la suppression d'un article se fait en deux étapes. La première étape l'envoie à la *Corbeille* d'où il peut être restauré. La deuxième étape le supprime de la Corbeille, après quoi l'article est supprimé définitivement.

## Considérations

Réfléchissez aux raisons pour lesquelles vous souhaitez supprimer l'article :

- N'est-il plus nécessaire ? Si c'est le cas, la suppression est très probablement la bonne décision.
- Est-ce un article qui pourrait être réutilisé à l'avenir ? Il peut être très frustrant de savoir que vous aviez un article qui aurait été une bonne base pour un autre, mais que vous l'avez supprimé - envisagez de l'archiver à la place.

## Déplacer l'article à la corbeille

- Sélectionnez **Contenu -> Articles** dans le menu de l'administrateur.
- Cochez la case pour sélectionner l'article que vous souhaitez supprimer. Un article 
  **doit** être sélectionné pour activer le bouton **Actions** dans la barre d'outils.
- Sélectionnez le bouton **Actions** dans la barre d'outils.
- Sélectionnez **Corbeille** dans le menu déroulant.

![Article sélectionné pour la mise à la corbeille](../../../en/images/articles/articles-selected-to-trash.png)

Un message de confirmation apparaîtra et l'article aura disparu de 
la liste actuelle d'articles car elle n'inclut normalement pas les éléments mis à la corbeille.

## Filtrer pour Restaurer ou Supprimer

À cette étape du processus, l'article n'a pas été complètement supprimé. C'est une fonctionnalité utile au cas où vous auriez supprimé l'article par erreur.

Pour voir la liste des articles mis à la corbeille :

- Sélectionnez le bouton **Options de Filtre** pour ouvrir la liste des filtres.
- Sélectionnez **Mise à la corbeille** dans la liste *-- Sélectionner le Statut --*.

![Vue de la corbeille des articles](../../../en/images/articles/articles-trash-list.png)

### Pour Restaurer

Si vous avez changé d'avis, vous pouvez sélectionner le symbole **Mise à la corbeille** dans la colonne *Statut*. L'article reviendra à l'état *Publié* et disparaîtra de la liste des articles mis à la corbeille.

### Pour Supprimer

Cochez la case dans la colonne de gauche des données de l'article. Cela activera les boutons *Actions* et *Supprimer* dans la barre d'outils. Le bouton *Actions* vous permet d'appliquer la même action à tous les articles sélectionnés. Si vous êtes vraiment sûr :

1. Sélectionnez le bouton *Supprimer* dans la barre d'outils. Une boîte de message apparaîtra :<br>
   <div class="alert alert-light">
   Êtes-vous sûr de vouloir supprimer ? Confirmer entraînera la suppression définitive des éléments sélectionnés !</div>
2. Sélectionnez **OK** pour confirmer et l'article sera supprimé de la Corbeille. L'article sera supprimé de la base de données. C'est fait, définitivement !
3. Sélectionnez le bouton **Effacer** à côté des **Options de Filtre** pour revenir à la liste des **Articles** non filtrée.

## Conseils

- N'oubliez pas que supprimer un article n'est pas la même chose qu'archiver un article. Une fois qu'il a été supprimé de la corbeille, il est définitivement perdu.
- Si vous supprimez un article par erreur mais que vous ne l'avez pas supprimé de la corbeille, vous pouvez changer son statut. Vous avez la possibilité de le définir comme *Archivé*, *Publié* ou *Non publié*.
- Joomla ne vous permettra pas de sauvegarder plus d'un article avec le même alias. Si un article est supprimé mais laissé dans la corbeille, il existe encore. Si vous essayez de sauvegarder un article et que vous obtenez une erreur indiquant que l'alias existe déjà, il peut être dans la corbeille ! Vous devriez donc soit le vider de la corbeille, soit entrer un alias différent pour votre nouvel article.
- Joomla conserve les versions précédentes d'un article à moins que les versions soient désactivées. Si vous supprimez un article parce qu'il est d'une manière ou d'une autre "cassé", essayez de revenir à une version précédente.

*Traduit par openai.com*


<!-- Filename: J4.x:Workflow / Display title: Flux de travail -->

Joomla!  4.x

## Introduction

Le composant de Flux de travail (Workflow) de publication est utilisé
pour remplacer les états statiques (non publiés, publiés, mis à la
corbeille et archivés) par une approche plus générique. De cette façon,
vous pouvez facilement créer un flux de travail personnalisé pour gérer
vos articles dans un composant.

- Vue d'article en backend avec Joomla 3.x :

<img
src="https://docs.joomla.org/images/thumb/a/a4/Article_view_3-en.png/800px-Article_view_3-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/a/a4/Article_view_3-en.png/1200px-Article_view_3-en.png 1.5x, https://docs.joomla.org/images/thumb/a/a4/Article_view_3-en.png/1600px-Article_view_3-en.png 2x"
data-file-width="2538" data-file-height="766" width="800" height="241"
alt="Article view 3-en.png" />

- Vue d'article en backend avec Joomla 4.x :

<img
src="https://docs.joomla.org/images/thumb/9/94/J4_Articles_Backend-en.png/800px-J4_Articles_Backend-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/9/94/J4_Articles_Backend-en.png 1.5x"
data-file-width="1200" data-file-height="332" width="800" height="221"
alt="J4 Articles Backend-en.png" />

La gamme d'outils de l'article est maintenant plus petite et la vue
généralement plus claire. Vous pouvez créer des états personnalisés pour
les articles et les regrouper en catégories.

Il existe une page de tutoriel contenant les étapes pour la création de
votre premier flux de travail:
Scenarios.
Vous trouverez plus d'informations sur l'implémentation du composant
dans d'autres zones de la page du projet Google Summer of Code DOC:
Vous pouvez désactiver les flux de travail à tout moment en visitant
"articles" ou "flux de travail" et en cliquant sur "options" en haut à
droite. Passez à l'onglet "Intégration" et faites défiler la page
jusqu'à "Activer le flux de travail".

### Termes et définitions

- *Flux de travail :* Vous pouvez créer plusieurs Flux de travail.
  Chaque Flux de travail contient des états, des transitions possibles
  et des conditions d'élément.
- «États:» Les États peuvent être considérés comme des étapes d’un flux
  de travail.
- *Conditions:* La condition d'un article peut être non publiée,
  publiée, mise à la poubelle ou archivée.
- *Transitions:* Les transitions définissent la séquence d'états qu'un
  article doit passer.
- *Catégories:* Les articles peuvent être affectés à des catégories.

## Flux de travail

Le Flux de travail ressemble à une séquence d'étapes. On peut y accéder
via le menu principal sous "Contenu". Vous serez dirigé vers la "Liste
des flux de travail", un aperçu de tous vos flux de travail existants.
Un Flux de travail contient plusieurs états de conditions différentes.
Les éléments (par exemple les articles) peuvent transiter par ces états.

<img
src="https://docs.joomla.org/images/thumb/e/e2/Workflows-en.png/800px-Workflows-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/e/e2/Workflows-en.png/1200px-Workflows-en.png 1.5x, https://docs.joomla.org/images/thumb/e/e2/Workflows-en.png/1600px-Workflows-en.png 2x"
data-file-width="1906" data-file-height="455" width="800" height="191"
alt="Workflows List" />

- Vous voyez le statut du Flux de travail (publié / non publié)
- À côté du statut est le titre. En cliquant sur le titre, vous pouvez
  "éditer le Flux de travail"
  - *Editable* : Titre \| Description \| Statut \| Option par défaut \|
    Autorisations (gestion des droits)
- À côté du titre, vous trouvez l'option de "Gérer" les états du Flux de
  travail (pour plus d'informations, voir
  States
- À côté de "États" est l'option par défaut
- Vous trouvez une icône de cercle jaune, à côté de "défaut",
  représentant le nombre d'états existants dans ce Flux de travail
- À côté du cercle jaune se trouve une icône représentant une flèche
  bleue représentant le nombre de transitions existantes dans ce flux de
  travail (pour plus d'informations, voir
  Transitions
- De plus, vous voyez la date de création du Flux de travail, l'auteur
  et un identifiant.

## Etats

Les états sont accessibles via le conteneur "Liste des flux de travail"
en cliquant sur les états "Gérer". Vous pouvez définir un état par
défaut (qui doit être à la condition "publié"). En cliquant sur le
titre, vous pouvez "modifier" l'état.


<img
src="https://docs.joomla.org/images/thumb/a/ac/Stages-en.png/800px-Stages-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/a/ac/Stages-en.png 1.5x"
data-file-width="1200" data-file-height="251" width="800" height="167"
alt="Stages View" />

<img
src="https://docs.joomla.org/images/thumb/7/7f/Stages--edit-en.png/800px-Stages--edit-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/7/7f/Stages--edit-en.png 1.5x"
data-file-width="1200" data-file-height="404" width="800" height="269"
alt="The Edit Stage view" />

- Dans la deuxième image, vous trouvez une option de statut à droite.
  C'est la condition de l'état.

## Transitions

Les articles peuvent transiter d'un état à un autre. Les transitions
peuvent être gérées via le conteneur "List des Flux de travail" en
cliquant sur la flèche bleue ou via le menu de gauche, après avoir
cliqué sur "Gérer". Vous pouvez définir plusieurs transitions que les
éléments peuvent traverser. Les états possibles sont basés sur ceux que
vous avez créés pour ce flux de travail spécifique.

The *current stage* will define where this transition is applied. You
can choose all stages, or a specific stage.

The *target stage* is the stage the workflow will end up at after the
transition has taken place.

<img
src="https://docs.joomla.org/images/thumb/4/45/Transitions--edit--description-en.png/800px-Transitions--edit--description-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/4/45/Transitions--edit--description-en.png 1.5x"
data-file-width="1200" data-file-height="456" width="800" height="304"
alt="Edit Transitions View" />

The *transition actions* tab allows you to define what state the item
will be in after the transition is complete. For example if the item is
an article it could become unpublished, which is exactly what happens in
the *unpublish* transition. You can also define whether the item is
featured or not by the end of the state.

<img
src="https://docs.joomla.org/images/thumb/2/27/Transitions--edit--transition-actions-en.png/800px-Transitions--edit--transition-actions-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/2/27/Transitions--edit--transition-actions-en.png 1.5x"
data-file-width="1200" data-file-height="429" width="800" height="286"
alt="Edit Transition Actions" />

The *transition notifications* tab allows you to define whether a
notification is sent during that state. For example if an article has
been written but needs to be proofread, you could send an email
notification to the editor.

You can also add additional message text. This will also allow you to
use a  language
string
which would make the message text translatable.

The Usergroups option will allow you to define who will receive the
notification. In the example we have chosen we would choose *editor* as
the usergroup. In that example all users within that usergroup would get
a notification.

Finally there is the "more receivers" option. This allows you to choose
individual users to receive this notification.

<img
src="https://docs.joomla.org/images/thumb/5/57/Transitions--edit--notification-en.png/800px-Transitions--edit--notification-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/5/57/Transitions--edit--notification-en.png 1.5x"
data-file-width="1200" data-file-height="481" width="800" height="321"
alt="Edit Transition Notification" />

The final tab is the permissions tab. This allows you to set who can use
this transition.

- *Example:* In the transition "Next Step: Publishing" items are
  originally of the state "unpublished". They are, for example, in need
  of a review. After they have been reviewed, they can transit to the
  state "published".
- All the workflow transition actions are Joomla! workflow plugins. If
  you go to System **→** Plugins. Then change the "type" dropdown to
  "workflow" you will see the plugins. These can be disabled like any
  other plugin.

<img
src="https://docs.joomla.org/images/thumb/9/96/Workflows--plugins--workflows-en.png/800px-Workflows--plugins--workflows-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/9/96/Workflows--plugins--workflows-en.png 1.5x"
data-file-width="1200" data-file-height="358" width="800" height="239"
alt="Workflows Plugins" />

## Categories

Les articles peuvent être affectés à des catégories. Ils correspondent à
un certain flux de travail et peuvent être personnalisés de diverses
manières. Vous pouvez définir un statut, une catégorie parente et
également restreindre l'accès ainsi que les permissions. Cette option ne
figure pas dans l'écran des flux de travail. Pour cette option, vous
devez aller dans Contenu **→** Catégories. Une fois là, ouvrez n'importe
quelle catégorie et vous verrez un onglet "flux de travail".

- *Exemple :* Vous avez certains articles que vous voulez rendre
  disponibles uniquement pour les administrateurs ou les utilisateurs
  d'un niveau supérieur. Vous pouvez appeler votre catégorie "Restreint"
  et définir toutes les permissions sur "Autorisé" pour les
  administrateurs ou les utilisateurs de niveau supérieur. De cette
  façon, vous ne devez pas définir ces autorisations pour chaque article
  concerné mais vous pouvez les déplacer dans cette catégorie spéciale
  et gagner du temps.

<img
src="https://docs.joomla.org/images/thumb/d/dd/Workflow-categories-en.png/800px-Workflow-categories-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/d/dd/Workflow-categories-en.png 1.5x"
data-file-width="1200" data-file-height="431" width="800" height="287"
alt="Workflow-categories-en.png" />

## Gestion des versions

Lorsque le flux de travail est activé, les champs gérés par le flux de
travail sont exclus de la gestion de version (comme "state" et
"épinglé") pour éviter les conflits de permission.

## Informations connexes

Voir également :

-  Publishing Workflow
  Implementation
- Scenarios

<!-- Filename: J4.x:Access_Control / Display title: Contrôle d'accès -->

## Introduction

Joomla dispose d'un mécanisme sophistiqué pour contrôler qui peut voir et manipuler le contenu sur un site Joomla. La partie **qui** est configurée dans les options du composant Utilisateurs avec les Groupes d'utilisateurs et les Niveaux d'accès. La partie **manipuler** est configurée dans les Permissions d'action, soit dans les paramètres de Configuration globale, soit dans les paramètres de Composant ou dans les paramètres d'Élément. Par exemple, les valeurs par défaut configurées dans les Permissions globales peuvent être remplacées dans les Permissions des articles (tous les articles) et les Permissions des articles peuvent être remplacées dans les Permissions d'article individuel.

## Groupes d'utilisateurs

Les groupes d'utilisateurs sont utilisés pour diviser les utilisateurs du site en groupes ayant des responsabilités différentes. Par exemple, les membres du groupe d'utilisateurs Auteur ont la permission de se connecter au site, de créer des articles et de modifier leurs propres articles. Rien de plus ! Les membres du groupe Super Users sont responsables de tous les aspects de la gestion et du fonctionnement du site. Joomla propose neuf groupes d'utilisateurs par défaut et vous pouvez en créer davantage si nécessaire.

<img
src="https://docs.joomla.org/images/thumb/b/bf/J4x-user-groups-en.png/800px-J4x-user-groups-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/b/bf/J4x-user-groups-en.png 1.5x"
data-file-width="1000" data-file-height="556" width="800" height="445"
alt="Screenshot of users groups" />

Les groupes d'utilisateurs par défaut sont configurés avec des relations parent-enfant pour minimiser la duplication des permissions. Exemples d'héritage :

* Un membre du groupe Enregistré n'a pas la permission de se connecter en tant qu'administrateur. Il en est de même pour les groupes Rédacteur et Editeur.
* Un membre du groupe Auteur a la permission de créer et de modifier ses propres articles. Il en est de même pour les groupes Rédacteur et Editeur, mais ils disposent de permissions supplémentaires.

Vous pouvez créer de nouveaux groupes d'utilisateurs pour des besoins spécifiques selon vos besoins. Par exemple, vous pouvez souhaiter créer un groupe qui a la permission de se connecter en tant qu'administrateur mais avec un accès restreint à un seul composant. Il y a un exemple d'un tel groupe d'utilisateurs personnalisé vers la fin de ce tutoriel.

## Niveaux d'accès

Chaque fois que vous créez un objet, tel qu'un article, un module ou un élément de menu, vous verrez un champ Accès, généralement dans la colonne de droite du formulaire de saisie de données. Il s'agit d'une liste déroulante offrant un choix parmi Public, Invité, Enregistré, Spécial et Super Utilisateurs. La valeur par défaut est Public. Les niveaux d'accès par défaut sont illustrés dans la capture d'écran suivante :

<img
src="https://docs.joomla.org/images/thumb/9/99/J4x-user-access-levels-en.png/800px-J4x-user-access-levels-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/9/99/J4x-user-access-levels-en.png 1.5x"
data-file-width="1000" data-file-height="386" width="800" height="309"
alt="Screenshot of users viewing access levels" />

Exemples :

* Si vous créez un module de site et définissez l'accès sur Enregistré, il ne sera visible que par les utilisateurs connectés au site.
* Si vous créez un lien de menu de site et définissez l'accès sur Super Utilisateurs, il ne sera visible que par les Super Utilisateurs connectés au site.

## Permissions

Les Permissions de la Configuration Globale sont le point de départ à partir duquel les paramètres de permission dans les composants ou les éléments individuels peuvent hériter ou être remplacés. Capture d'écran :

<img
src="https://docs.joomla.org/images/thumb/9/92/J4x-permissions-global-en.png/800px-J4x-permissions-global-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/9/92/J4x-permissions-global-en.png 1.5x"
data-file-width="1000" data-file-height="1016" width="800" height="813"
alt="Screenshot of global configuration permissions page" />

La capture d'écran montre que les membres du groupe Public n'ont pas la permission d'effectuer des actions. Si vous sélectionnez chaque groupe à tour de rôle, vous verrez comment les permissions changent de groupe à groupe. Notez que Gestionnaire et Administrateur sont autorisés à se connecter en tant qu'administrateur, mais pas Auteur, Rédacteur et Editeur. Ces derniers sont en effet des rôles de site plutôt que des rôles d'administrateur.

Toutes les permissions de groupe héritent du groupe Public. Ce dernier n'a pas la permission d'effectuer des actions. Cependant, par défaut, les éléments du groupe Public peuvent être consultés, donc attribuer la permission Public à un élément permettra à tous les visiteurs du site, connectés ou non, de le voir.

### Permissions des articles

Les actions des Permissions des articles diffèrent des actions des Permissions de Configuration globale. Les éléments liés à la connexion ne sont pas présents, tandis que les éléments liés aux flux de travail sont présents. C'est un schéma assez typique : un composant aura des permissions pertinentes pour le composant lui-même ; un élément de composant (tel qu'un article) aura des permissions pertinentes pour cet élément spécifique.

<img
src="https://docs.joomla.org/images/thumb/7/7f/J4x-permissions-articles-en.png/800px-J4x-permissions-articles-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/7/7f/J4x-permissions-articles-en.png 1.5x"
data-file-width="1000" data-file-height="1037" width="800" height="830"
alt="Screenshot of articles options permissions page" />

### Permissions d'article individuel

Les permissions d'article individuel comprennent seulement trois éléments : Supprimer, Modifier et Modifier l'état :

<img
src="https://docs.joomla.org/images/thumb/1/18/J4x-permissions-article-en.png/800px-J4x-permissions-article-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/1/18/J4x-permissions-article-en.png 1.5x"
data-file-width="1000" data-file-height="711" width="800" height="569"
alt="Screenshot of permissions page for a single article" />

## Exemple de contrôle d'accès : Utilisateur à des fins spéciales

Supposons que vous ayez besoin de créer un groupe d'utilisateurs pour des utilisateurs qui n'ont qu'une seule responsabilité, dans cet exemple un Administrateur d'articles. Les utilisateurs de ce groupe devraient avoir la permission de se connecter en tant qu'administrateur mais ne devraient rien voir d'autre que les éléments de contenu. Procédure :

### Créer un nouveau groupe d'utilisateurs

* Sélectionnez **Utilisateurs → Groupes** dans le menu Administrateur.
* Sélectionnez le bouton Nouveau dans la barre d'outils.
* Remplissez le champ Titre du groupe : Administrateur d'articles
* Le groupe Parent doit être Public - il n'a aucune permission pour quoi que ce soit.

<img
src="https://docs.joomla.org/images/thumb/c/c6/J4x-permissions-article-administrator-en.png/800px-J4x-permissions-article-administrator-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/c/c6/J4x-permissions-article-administrator-en.png 1.5x"
data-file-width="1000" data-file-height="249" width="800" height="199"
alt="Screenshot of users new group form" />

### Attribution à Spécial

* Sélectionnez **Utilisateurs → Niveaux d'accès** dans le menu Administrateur.
* Sélectionnez l'élément **Spécial**.
* Cochez la case Article Administrateur dans le formulaire **Utilisateurs : Modifier le niveau d'accès à la vue**.
* **Enregistrez & Fermez**.

<img
src="https://docs.joomla.org/images/thumb/5/59/J4x-permissions-article-administrator-special-en.png/800px-J4x-permissions-article-administrator-special-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/5/59/J4x-permissions-article-administrator-special-en.png 1.5x"
data-file-width="1000" data-file-height="470" width="800" height="376"
alt="Screenshot of user groups with viewing access levels page" />

### Permissions de Configuration globale

* Sélectionnez **Tableau de bord d'accueil → Configuration globale** dans le menu Administrateur.
* Sélectionnez l'onglet **Permissions**.
* Sélectionnez le groupe **Administrateur d'articles**.
* Définissez **Connexion administrateur** sur Autorisé.
* **Enregistrez & Fermez**.

<img
src="https://docs.joomla.org/images/thumb/6/66/J4x-permissions-article-administrator-global-en.png/800px-J4x-permissions-article-administrator-global-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/6/66/J4x-permissions-article-administrator-global-en.png 1.5x"
data-file-width="1000" data-file-height="940" width="800" height="752"
alt="Screenshot of global permissions page" />

### Permissions des Options des Articles

* Sélectionnez **Contenu → Articles** dans le menu Administrateur.
* Sélectionnez le bouton **Options** dans la barre d'outils.
* Sélectionnez l'onglet **Permissions**.
* Sélectionnez le groupe **Administrateur d'articles**.
* Autorisez tous les éléments sauf les deux premiers (Configurer les ACL et options et Configurer uniquement les options).
* **Enregistrez & Fermez**.

<img
src="https://docs.joomla.org/images/thumb/e/ef/J4x-permissions-article-administrator-articles-en.png/800px-J4x-permissions-article-administrator-articles-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/e/ef/J4x-permissions-article-administrator-articles-en.png 1.5x"
data-file-width="1000" data-file-height="930" width="800" height="744"
alt="Screenshot of articles options permissions page" />

### Créer ou Modifier un utilisateur

* Créez un nouvel utilisateur ou modifiez un utilisateur existant qui n'est assigné à aucun groupe.
* Sélectionnez **Administrateur d'articles** dans l'onglet **Groupes d'utilisateurs assignés** du formulaire de modification de l'utilisateur.
* **Enregistrez & Fermez**.
* Connectez-vous en tant qu'utilisateur dans le groupe Administrateur d'articles uniquement. Le menu ne devrait afficher que les éléments liés aux articles :

<img
src="https://docs.joomla.org/images/thumb/4/40/J4x-permissions-article-administrator-menu-en.png/800px-J4x-permissions-article-administrator-menu-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/4/40/J4x-permissions-article-administrator-menu-en.png 1.5x"
data-file-width="1000" data-file-height="451" width="800" height="361"
alt="Screenshot of Home Dashboard for user with restricted access" />

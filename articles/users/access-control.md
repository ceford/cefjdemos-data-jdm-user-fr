<!-- Filename: J4.x:Access_Control / Display title: Contrôle d'accès  -->

## Introduction

Joomla dispose d’un mécanisme sophistiqué pour contrôler qui peut voir et manipuler le contenu sur un site Joomla. La partie **qui** est configurée dans les options du composant Utilisateurs avec des Groupes d'Utilisateurs et des Niveaux d'Accès. La partie **manipulation** est configurée dans les Permissions d'Action, soit dans les paramètres de Configuration Globale, soit dans les paramètres du Composant, soit dans les paramètres de l'Élément. Par exemple, les valeurs par défaut configurées dans les Permissions Globales peuvent être remplacées dans les Permissions des Articles (tous les articles) et les Permissions des Articles peuvent être remplacées dans les Permissions d'un Article individuel.

## Groupes d'Utilisateurs

Les groupes d'utilisateurs sont utilisés pour diviser les utilisateurs du site en groupes avec des responsabilités différentes. Par exemple, les membres du groupe d'utilisateurs Auteur ont la permission de se connecter au site, de créer des articles et de modifier leurs propres articles. Rien d'autre ! Les membres du groupe Super Utilisateurs sont responsables de tous les aspects de la gestion et du fonctionnement du site. Joomla fournit neuf groupes d'utilisateurs par défaut et vous pouvez en créer d'autres si nécessaire.

![Liste des groupes d'utilisateurs](../../../en/images/users/access-control-users-groups-list.png)

Les groupes d'utilisateurs par défaut sont configurés avec des relations parent-enfant pour minimiser la duplication des autorisations. Exemples d'héritage :

- Un membre du groupe Enregistré n'a pas la permission de connexion Administrateur. L'Éditeur et le Publieur non plus.
- Un membre du groupe Auteur a la permission de créer et de modifier ses propres contenus. L'Éditeur et le Publieur ont ces permissions ainsi que d'autres permissions supplémentaires.

Vous pouvez créer de nouveaux groupes d'utilisateurs à des fins spéciales selon vos besoins. Par exemple, vous pourriez souhaiter créer un groupe ayant la permission de connexion Administrateur mais avec un accès restreint à un seul composant. Il y a un exemple d'un tel groupe d'utilisateurs personnalisé vers la fin de ce didacticiel.

## Niveaux d'accès

Chaque fois que vous créez un objet, tel qu'un article, un module ou un élément de menu, vous verrez un champ Accès, généralement dans la colonne de droite du formulaire de saisie de données. Il s'agit d'une liste déroulante offrant un choix entre Public, Invité, Enregistré, Spécial et Super Utilisateurs. Par défaut, c'est Public. Les niveaux d'accès par défaut sont affichés dans la capture d'écran suivante :

![Niveaux d'accès des utilisateurs](../../../en/images/users/access-control-users-access-levels.png)

Exemples :

- Si vous créez un module de site et définissez Accès sur Enregistré, il ne sera visible que par les utilisateurs qui sont connectés au site.
- Si vous créez un élément de menu de site et définissez Accès sur Super Utilisateurs, il ne sera visible que par les Super Utilisateurs qui sont connectés au site.

## Permissions

Les Permissions de Configuration Globale sont le point de départ à partir duquel les paramètres de permission dans les composants ou les éléments individuels peuvent hériter ou remplacer. Capture d'écran :

![permissions de configuration globale](../../../en/images/users/access-control-global-configuration-permissions.png)

La capture d'écran montre que les membres du groupe Public n'ont pas la permission d'effectuer des actions. Si vous sélectionnez chaque groupe à tour de rôle, vous verrez comment les permissions changent d'un groupe à l'autre. Notez que le Gestionnaire et l'Administrateur sont autorisés à se connecter en tant qu'Administrateur, mais l'Auteur, l'Éditeur et l'Éditeur ne le sont pas. Ces derniers sont effectivement des rôles de Site plutôt que des rôles d'Administrateur.

Toutes les permissions de groupe héritent du groupe Public. Il n'a pas la permission pour aucune action. Cependant, par défaut, les éléments dans le groupe Public peuvent être visualisés, donc attribuer la permission Public à un élément permettra à tous les visiteurs du site de le voir, qu'ils soient connectés ou non.

### Permissions des Articles

Les actions de Permissions des Articles diffèrent des actions de Permissions de Configuration Globale. Ne sont pas présentes les actions liées à la connexion et sont présentes les actions liées aux flux de travail. Il s'agit d'un modèle assez typique : un composant aura des permissions pertinentes pour le composant ; un élément de composant (tel qu'un article) aura des permissions pertinentes pour cet élément unique.

![permissions de contenu](../../../en/images/users/access-control-global-content-permissions.png)

### Permissions d'un Article Unique

Les permissions d'un article unique comportent seulement trois actions : Supprimer, Modifier et Modifier l'État :

![permissions d'un article unique](../../../en/images/users/access-control-article-permissions.png)

## Exemple de Contrôle d'Accès : Utilisateur à But Spécial

Supposons que vous devez créer un Groupe d'Utilisateurs pour les utilisateurs ayant une seule responsabilité, dans cet exemple un Administrateur d'Articles. Les utilisateurs de ce groupe doivent avoir l'autorisation de Connexion Administrateur mais ne doivent rien voir d'autre que les éléments de Contenu. Procédure :

### Créer un nouveau Groupe d'Utilisateurs

- Sélectionnez **Utilisateurs → Groupes** dans le menu Administrateur.
- Sélectionnez le bouton `Nouveau` dans la Barre d'outils.
- Remplissez le champ Titre du Groupe : Administrateur d'Articles
- Le Parent du Groupe doit être Public - il n'a aucune permission pour quoi que ce soit.

![Formulaire de nouveau groupe d'utilisateurs](../../../en/images/users/access-control-new-group.png)

### Affecter à Spécial

- Sélectionnez **Utilisateurs → Niveaux d'Accès** dans le menu Administrateur.
- Sélectionnez l'élément **Spécial**.
- Cochez la case Administrateur d'Articles dans le formulaire **Utilisateurs : Modifier le Niveau d'Accès de Visualisation**.
- Enregistrez & Fermez.

![Sélectionner l'accès pour le groupe](../../../en/images/users/access-control-select-access-for-group.png)

### Permissions de Configuration Globale

- Sélectionnez **Tableau de Bord Accueil → Configuration Globale** dans le menu Administrateur.
- Sélectionnez l'onglet **Permissions**.
- Sélectionnez le groupe **Administrateur d'Articles**.
- Réglez la **Connexion Administrateur** sur Autorisé.
- Enregistrez & Fermez

![Sélectionner l'accès pour le groupe](../../../en/images/users/access-control-article-administrator-global-permissions.png)

### Permissions des Options des Articles

- Sélectionnez **Contenu → Articles** dans le menu Administrateur.
- Sélectionnez le bouton `Options` dans la Barre d'outils.
- Sélectionnez l'onglet **Permissions**.
- Sélectionnez le groupe **Administrateur d'Articles**.
- Réglez tous les éléments sauf les deux premiers (Configurer ACL & Options et Configurer Options Seulement) sur Autorisé.
- Enregistrez & Fermez

![Sélectionner l'accès pour le groupe](../../../en/images/users/access-control-article-administrator-content-permissions.png)

### Créer ou Modifier un Utilisateur

- Créez un nouvel utilisateur ou modifiez un utilisateur existant qui n'est affecté à aucun groupe
- Sélectionnez **Administrateur d'Articles** dans l'onglet **Groupes d'Utilisateurs Assignés** du formulaire d'édition de l'utilisateur.
- Enregistrez & Fermez.
- Connectez-vous en tant qu'utilisateur appartenant uniquement au Groupe Administrateur d'Articles. Le menu ne devrait afficher que les éléments liés aux articles :

![Sélectionner l'accès pour le groupe](../../../en/images/users/access-control-article-administrator-home-dashboard.png)

*Traduit par openai.com*


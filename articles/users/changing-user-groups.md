<!-- Filename: Changing_user_groups / Display title: Changer les groupes d'un utilisateur  -->

## Héritage des Groupes

Les listes de groupes utilisent un modèle d'héritage. Par exemple, un utilisateur du groupe Auteur hérite de tous les privilèges du groupe Enregistré et obtient quelques privilèges supplémentaires. De même, un utilisateur du groupe Éditeur hérite de tous les privilèges du groupe Auteur et obtient encore plus de privilèges supplémentaires. Les groupes du backend héritent du niveau de privilège le plus élevé du frontend.

Pour cette raison, vous n'avez besoin de sélectionner qu'un seul groupe pour un utilisateur individuel - le groupe avec le plus de privilèges.

## Étapes

Vous pouvez changer le groupe d'un utilisateur en suivant ces étapes. Vous devez vous connecter en tant qu'Administrateur ou Super Utilisateur pour pouvoir changer les groupes d'un utilisateur. De plus, un Administrateur ne peut se nommer lui-même ou nommer d'autres personnes Super Utilisateur.

1. Depuis le *Tableau de bord d'accueil*, sélectionnez l'élément **Utilisateurs**. Ou...
2. Depuis l'élément de menu *Utilisateur*, sélectionnez **Utilisateurs** puis **Gérer**.
3. Trouvez l'utilisateur requis dans la liste d'utilisateurs. Vous pouvez rechercher par nom, nom d'utilisateur, e-mail ou id : préfixe.
4. Sélectionnez le nom de l'utilisateur à modifier.
5. Sélectionnez l'onglet *Groupes d'utilisateurs attribués*.
6. Sélectionnez le groupe auquel un utilisateur doit appartenir.
7. Sélectionnez *Enregistrer*.

## Liste de contrôle d'accès (ACL) pour Joomla

La liste suivante est la liste de contrôle d'accès (ACL) pour Joomla. Le groupe d'utilisateurs est listé, et les puces ci-dessous décrivent les permissions associées à ce groupe.

### Groupes du front-end

#### Invité

- Voir le site public et les articles publics

#### Enregistré

- Privilèges du groupe Invité
- Voir les articles enregistrés
- Pas d'accès aux éléments restreints au groupe Invité

#### Auteur

- Privilèges du groupe Enregistré
- Créer de nouveaux articles
- Modifier les articles qu'ils possèdent
- Voir du contenu spécial

#### Éditeur

- Privilèges du groupe Auteur
- Modifier tous les articles, y compris ceux non publiés

#### Éditeur de publication

- Privilèges du groupe Éditeur
- Publier des articles

### Groupes du back-end

Ces groupes vous permettent de vous connecter à l'administrateur via l'URL */administrator*.

#### Gestionnaire

- Privilèges du groupe Éditeur de publication
- Accéder au back-end de l'administrateur

#### Administrateur

- Privilèges du groupe Gestionnaire
- Créer de nouveaux utilisateurs
- Installer des extensions

#### Super Utilisateur

- Privilèges de l'administrateur
- Changer le modèle du site
- Modifier la configuration globale

*Traduit par openai.com*


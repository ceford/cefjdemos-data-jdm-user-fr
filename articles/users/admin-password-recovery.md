<!-- Filename: How_do_you_recover_or_reset_your_admin_password%3F / Display title: Récupération du mot de passe administrateur  -->

## Introduction

Normalement, un Super Utilisateur peut ajouter, modifier et supprimer des utilisateurs et des mots de passe de la liste des utilisateurs. Dans certaines situations, cela peut ne pas être possible. Par exemple, la personne qui connaissait le mot de passe d'un Super Utilisateur n'est plus disponible. Ou peut-être que le Super Utilisateur a oublié le mot de passe qui était utilisé.

Dans de tels cas, deux méthodes sont disponibles pour permettre à un administrateur du site de se connecter en tant que Super Utilisateur.

## Méthode 1 : Modifier le fichier configuration.php

Si vous avez accès au fichier `configuration.php` de l'installation de Joomla
sur votre serveur, vous pouvez alors réinitialiser un mot de passe Super Utilisateur ou créer un nouveau Super Utilisateur si vous pouvez vous connecter en tant que Manager ou Administrateur.

Vous devez ouvrir le fichier `configuration.php` dans un éditeur de texte. Modifiez d'abord les autorisations du fichier en 644. Vos outils de gestion de site, tels que cPanel ou Plesk (il y en a d'autres), vous permettent généralement de le faire en ligne. Si ce n'est pas le cas, vous devrez peut-être utiliser le FTP pour télécharger le fichier, le modifier localement et le télécharger à nouveau.

Ajoutez cette ligne à la fin du fichier, mais avant l'accolade fermante :
```
    public $root_user='monnom';
```
où **monnom** est un nom d'utilisateur avec accès au groupe *Manager* ou *Administrateur* dont vous connaissez le mot de passe. Un nom d'utilisateur appartenant aux groupes *Auteur*, *Éditeur* ou *Éditeur-en-chef* ne fonctionnera pas car ces groupes n'ont pas accès au backend.

Cet utilisateur sera maintenant un Super Utilisateur temporaire.

Connectez-vous à l'interface d'administration et modifiez le mot de passe de Super Utilisateur pour lequel vous n'avez pas le mot de passe ou créez un nouveau compte Super Utilisateur. Si vous créez un nouvel utilisateur, vous pourriez vouloir bloquer ou supprimer l'ancien utilisateur en fonction de votre situation.

Une fois terminé, assurez-vous d'utiliser le lien *Sélectionnez ici pour essayer de le faire automatiquement* qui apparaît dans la boîte d'alerte pour supprimer la ligne qui a été ajoutée au fichier configuration.php. Si l'utilisation du lien n'a pas réussi, retournez et supprimez la ligne ajoutée de votre fichier configuration.php à l'aide d'un éditeur de texte.

Si vous n'avez aucun utilisateur qui connaît ses mots de passe, vous devrez peut-être effectuer un changement dans votre base de données.

## Méthode 2 : Modifier la base de données

Si les méthodes ci-dessus n'ont pas fonctionné, vous avez deux autres options, toutes deux nécessitant de travailler directement avec la base de données MySQL.

### Changer un mot de passe dans la base de données

L'option la plus simple est de modifier le mot de passe du Super Utilisateur dans la base de données pour une valeur connue. Cela nécessite que vous ayez accès à la base de données MySQL en utilisant phpMyAdmin ou un autre client. Ces instructions montrent comment changer un mot de passe en **secret**.

Cette méthode fonctionnera uniquement si l'utilisateur sélectionné est dans les groupes *Manager* ou *Administrateur*.

**Assurez-vous de changer le mot de passe du Super Utilisateur dès que vous regagnez l'accès !**

1.  Ouvrez phpMyAdmin et sélectionnez la base de données du site Joomla! Cela affichera les tables de la base de données sur le côté gauche de l'écran.
2.  Trouvez et sélectionnez la table *#__users* où *#_* est le préfixe de la table pour votre site.
3.  Dans la vue *Parcourir*, trouvez l'utilisateur dont vous voulez changer le mot de passe et sélectionnez l'icône Modifier pour cette ligne.
    - si la liste est longue, sélectionnez le bouton SQL en haut et utilisez cette requête :<br>
    `SELECT * FROM `xxxxx_users` WHERE `username` = 'username'`<br>
    où vous utilisez votre préfixe de base de données pour remplacer `xxxxx` et le nom d'utilisateur que vous devez trouver à la place de `username`.
4.  Dans le formulaire de modification, changez le mot de passe par<br>
    `d2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199`<br>
    et sélectionnez le bouton *Exécuter* en bas du formulaire. phpMyAdmin devrait afficher le message *Lignes affectées : 1*. À ce stade, le mot de passe devrait être **secret**.
5.  Connectez-vous avec cet utilisateur et ce mot de passe et changez le mot de passe de cet utilisateur pour une valeur sécurisée. Vérifiez tous les utilisateurs pour vous assurer qu'ils sont légitimes. Si vous avez été piraté, vous pourriez vouloir changer tous les mots de passe du site.

### Ajouter un nouveau Super Utilisateur

Si changer le mot de passe ne fonctionne pas, ou si vous n'êtes pas sûr quel utilisateur est membre du groupe Super Utilisateur, vous pouvez utiliser cette méthode pour créer un nouveau Super Utilisateur.
1.  Ouvrez phpMyAdmin et sélectionnez la base de données du site Joomla!.
2.  Sélectionnez le bouton *SQL* dans la barre d'outils pour exécuter une requête SQL sur la base de données sélectionnée. Cela affichera un champ appelé "Exécuter une ou des requêtes SQL sur la base de données xxxxx".
3.  Supprimez tout texte dans ce champ et copiez et collez la requête suivante. N'oubliez pas de remplacer `xxxxx` par votre propre préfixe de base de données.
    ```
    INSERT INTO `xxxxx_users`
       (`name`, `username`, `password`, `params`, `registerDate`, `lastvisitDate`, `lastResetTime`)
    VALUES ('Administrator2', 'admin2',
        'd2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199', '', NOW(), NOW(), NOW());
    INSERT INTO `xxxxx_user_usergroup_map` (`user_id`,`group_id`)
    VALUES (LAST_INSERT_ID(),'8');
    ```
    Sélectionnez le bouton *Exécuter* pour exécuter la requête et ajouter le nouveau Super Utilisateur à la table.

À ce stade, vous devriez être en mesure de vous connecter à l'interface d'administration de Joomla! avec le nom d'utilisateur *admin2* et le mot de passe *secret*.

Après vous être connecté, allez à la liste des utilisateurs et changez le mot de passe pour une nouvelle valeur sécurisée et ajoutez une adresse e-mail valide au compte.

Si vous pensez avoir été *piraté*, assurez-vous de vérifier que tous les utilisateurs sont légitimes, en particulier les membres du groupe Super Utilisateur.

## Mots de passe temporaires alternatifs

**Avertissement:** Les valeurs des mots de passe affichées sur cette page sont de notoriété publique et
ne sont destinées qu'à la récupération. Pour éviter les piratages, assurez-vous de changer un mot de passe temporaire pour une valeur sécurisée après vous être connecté.

    mot_de_passe = "c'est le mot de passe haché en MD5 et salé"
    ---------------------------------------------------------
    admin  = 433903e0a9d6a712e00251e44d29bf87:UJ0b9J5fufL3FKfCc0TLsYJBh2PFULvT
    secret = d2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199
    OU812  = 5e3128b27a2c1f8eb53689f511c4ca9e:J584KAEv9d8VKwRGhb8ve7GdKoG7isMm

*Traduit par openai.com*  


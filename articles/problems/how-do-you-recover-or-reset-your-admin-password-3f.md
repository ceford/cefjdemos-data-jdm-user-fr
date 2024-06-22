<!-- Filename: How_do_you_recover_or_reset_your_admin_password%3F / Display title: Comment récupérer ou réinitialiser votre mot de passe d'administration ? -->

Récupération d'un mot de passe pour Joomla! 1.5

Cette page ne concerne que les versions 2.5 de Joomla! et supérieures.
Si vous utilisez toujours Joomla! 1.5   vous trouverez des instructions
ici.

Habituellement, vous pouvez ajouter, modifier et supprimer des
utilisateurs et des mots de passe depuis le gestionnaire des
utilisateurs dans l'administration du site. Pour ce faire, vous devez
être connecté en qualité de membre du groupe des Super-Administrateurs.

Dans certaines situations, cette opération n'est pas possible. Par
exemple, votre site peut avoir été "piraté" et les mots de passe ou
utilisateurs modifiés. Peut-être que la personne ayant connaissance des
mots de passe n'est plus disponible. Ou vous avez tout simplement oublié
le mot de passe utilisé.

Dans ces cas, il reste possible de modifier la base de données de
Joomla! afin de pouvoir vous connecter en tant de Super-Administrateur.
Vous trouverez ci-après les méthodes disponibles pour les
administrateurs Joomla.

## Méthode 1 : le fichier configuration.php

Si vous pouvez accéder au fichier `configuration.php` de votre
installation Joomla! sur votre serveur, vous pouvez alors retrouver le
mot de passe en utilisant la méthode ci-après.

1\. Utilisez un logiciel FTP afin de vous connecter à votre site.
Trouvez le fichier configuration.php et regardez les droits du fichiers.
Si les droits sont sur 444 ou sur une autre valeur, alors modifiez les
droits du fichier configuration.php en 644. Cela vous permettra d'éviter
des erreurs lors du chargement ultérieur du fichier modifié
configuration.php.

2\. Téléchargez le fichier configuration.

3\. Ouvrez le fichier configuration.php que vous venez de télécharger
avec un éditeur de texte tel que notepad++ et ajoutez cette ligne

    public $root_user='myname';

en bas de la liste, myname correspond au nom d'utilisateur ayant un
accès administrateur et dont vous connaissez le mot de passe. Un nom
d'utilisateur ayant des droits d'Auteur ou supérieurs peut également
être utilisé à la place du nom d'utilisateur ayant un accès en tant
qu'administrateur.

4\. Enregistrez le fichier configuration.php file et renvoyez-le sur le
site. Conservez les droits du fichier configuration.php sur 644.

Ainsi, cet utilisateur sera un super administrateur temporaire.

5\. Connectez-vous au back-end et modifiez le mot de passe de
l'administrateur dont vous n'avez pas le mot de passe ou créer un
nouveau super administrateur. Si vous créez un nouvel utilisateur, vous
devriez bloquer ou supprimer l'ancien utilisateur, selon les
circonstances.

6\. Lorsque vous avez terminé, assurez-vous de cliquer sur le lien
"Cliquez ici pour essayer de le faire automatiquement" qui s'affiche
dans l'encart d'alerte afin de supprimer la ligne précédemment ajoutée
au fichier configuration.php. Si l'utilisation du lien est inefficace,
alors supprimez manuellement la ligne ajoutée dans votre fichier
configuration.php, via un éditeur de texte. Renvoyez le fichier
configuration.php sur votre site.

7\. Utilisez votre logiciel FTP pour vérifier les droits du fichier
configuration.php, ils doivent être sur 444. Si vous avez supprimé
manuellement la ligne ajoutée, alors changez les droits du fichier
configuration.php en 444.

Si aucun des utilisateurs n'a connaissance de son mot de passe et s'il
n'est pas possible de s'inscrire sur le front-end, alors il vous faudra
effectuer une modification dans votre base de données, comme décrit
ci-après.

## Méthode 2: Modifier la base de données

Si les méthodes ci-dessus n'ont pas fonctionnées, deux options se
présentent à vous, requérant toutes deux d'intervenir directement sur la
base de données MySQL.

### Modifier le mot de passe dans la base de données

Si l'administrateur existe, l'option la plus simple est de changer le
mot de passe dans la base de données par une valeur connue. Cela
implique vous ayez accès à la base de données MySQL via phpMyAdmin ou
similaire.

<img
src="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/25px-Stop_hand_nuvola.svg.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/38px-Stop_hand_nuvola.svg.png 1.5x, https://docs.joomla.org/images/4/41/Stop_hand_nuvola.svg.png 2x"
data-file-width="40" data-file-height="40" width="25" height="25"
alt="Stop hand nuvola.svg.png" />Assurez-vous de changer votre mot de
passe une fois que vous avez à nouveau un accès

Les instructions ci-dessous vous indiquent comment remplacer
manuellement un mot de passe par le terme - "secret"

1.  Allez dans phpMyAdmin et sélectionnez, dans la liste située à
    gauche, la base de données du site Joomla!. Les tables de la base de
    données vont alors s'afficher sur la colonne gauche de votre écran.

2.  Recherchez et cliquez sur la table contenant "\_users" (note : le
    préfixe de table peut être différent de jos\_, allez tout simplement
    dans la table \_users de votre préfixe).

3.  Cliquez sur le bouton "Parcourir" dans la barre d'outils située en
    haut. Cela permettra d'afficher tous les utilisateurs configurés
    pour ce site.

4.  Cherchez l'utilisateur dont vous souhaitez modifier le mot de passe
    et cliquez sur l'icône modifier située sur cette même ligne.

5.  Un formulaire va s'afficher vous permettant de modifier le champ
    password. Copiez la valeur :

        d2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199

    dans le champ password et cliquez sur le bouton *Exécuter*.
    phpMyadmin devrait alors afficher le message "1 ligne affectée". A
    ce stade, le mot de passe devrait être modifié en **"secret"**.

6.  Connectez-vous avec cet utilisateur et ce mot de passe et modifiez
    le mot de passe de cet utilisateur en une valeur sécurisée. Vérifiez
    tous les utilisateurs via le Gestionnaire des utilisateurs pour vous
    assurer qu'ils sont tous légitimes. Si vous avez été piraté, vous
    devriez modifier tous les mots de passe du site.

### Ajouter un nouveau super administrateur

Si le changement de mot de passe n'a pas fonctionné, ou si vous n'êtes
pas sûr de savoir quel utilisateur est membre du groupe des
Supers-Administrateurs, vous pouvez utiliser la méthode suivante pour
créer un nouvel utilisateur.

1.  Allez dans phpMyAdmin et sélectionnez, dans la liste située à
    gauche, la base de données du site Joomla!. Les tables de la base de
    données vont alors s'afficher sur la colonne gauche de votre écran.
2.  Cliquez sur le bouton "SQL" de la barre d'outils afin de lancer une
    requête SQL sur la base de données sélectionnée. Un champ nommé
    "Exécuter une ou des requêtes SQL sur la base " va s'afficher.
3.  Supprimez tout texte contenu dans ce champ et copiez / collez la
    requête suivante puis cliquez sur le bouton *Exécuter* pour exécuter
    la requête et ajouter un nouvel administrateur à cette table.
4.  Utilisez la requête SQL ci-dessous pour ajouter un nouveau compte
    administrateur.

<img
src="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/25px-Stop_hand_nuvola.svg.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/38px-Stop_hand_nuvola.svg.png 1.5x, https://docs.joomla.org/images/4/41/Stop_hand_nuvola.svg.png 2x"
data-file-width="40" data-file-height="40" width="25" height="25"
alt="Stop hand nuvola.svg.png" />Assurez-vous que le préfixe de table de
la base de données correspond !

Le code ci-dessous utilise jos31\_ comme nom de préfixe de table, ce
n'est qu'un exemple de préfixe de table. Le préfixe lors de la première
installation de Joomla! est **ALEATOIRE** ou est celui que vous avez
spécifié. Il vous faudra alors remplacer toutes les occurrences
**jos31\_** (votre préfixe d'installation) du code ci-dessous par le
préfixe de votre installation.

**Le code SQL à utiliser avec Joomla!
 <img src="https://docs.joomla.org/images/5/53/Compat_icon_2_5.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 2.5" /> <img src="https://docs.joomla.org/images/4/4d/Compat_icon_3_x.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 3.x" /> <img src="https://docs.joomla.org/images/b/bd/Compat_icon_4_x.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 4.x" />**

    INSERT INTO `jos31_users`
       (`name`, `username`, `password`, `params`, `registerDate`, `lastvisitDate`, `lastResetTime`)
    VALUES ('Administrator2', 'admin2',
        'd2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199', '', NOW(), NOW(), NOW());
    INSERT INTO `jos31_user_usergroup_map` (`user_id`,`group_id`)
    VALUES (LAST_INSERT_ID(),'8');

A ce stade, vous devriez être en mesure de vous connecter au back-end de
Joomla! avec le nom d'utilisateur "admin2" et le mot de passe "secret".
Après vous être connecté, allez dans le gestionnaire des utilisateurs et
remplacer le mot de passe par une valeur plus sécurisée et ajoutez une
adresse e-mail valide pour ce compte. S'il existe une possibilité que
vous ayez été "piraté", assurez-vous de vérifier que tous les
utilisateurs sont légitimes, en particulier les membres du groupe des
supers administrateurs.

<img
src="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/25px-Stop_hand_nuvola.svg.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/38px-Stop_hand_nuvola.svg.png 1.5x, https://docs.joomla.org/images/4/41/Stop_hand_nuvola.svg.png 2x"
data-file-width="40" data-file-height="40" width="25" height="25"
alt="Stop hand nuvola.svg.png" />Warning!

Attention : les valeurs de mot de passe indiquées sur cette page sont de
notoriété publique et ne sont destinées qu'à la récupération de mot de
passe. Votre site peut être piraté si vous ne changez pas le mot de
passe en une valeur plus sécurisée après connexion. Alors, assurez-vous
de changer votre mot de passe en une valeur sécurisée après connexion.


Les exemples ci-dessus permettent de remplacer le mot de passe par
"secret". Deux autres valeurs possibles sont indiquées ci-dessous :

    - password = "this is the MD5 and salted hashed password"
    ------------------------------------------------------
    - admin  = 433903e0a9d6a712e00251e44d29bf87:UJ0b9J5fufL3FKfCc0TLsYJBh2PFULvT
    - secret = d2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199
    - OU812  = 5e3128b27a2c1f8eb53689f511c4ca9e:J584KAEv9d8VKwRGhb8ve7GdKoG7isMm

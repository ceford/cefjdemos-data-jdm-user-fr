<!-- Filename: J4.x:User_Registration / Display title: Inscription de l'utilisateur  -->

## Politique d'inscription

Sur un site Joomla, les utilisateurs enregistrés sont autorisés à se connecter pour voir ou interagir avec du contenu auquel les utilisateurs non enregistrés n'ont pas accès. La connexion au site et la connexion à l'administration sont traitées séparément, bien qu'il existe un paramètre de configuration globale permettant de les combiner. Certains sites ont de petits nombres d'utilisateurs créés par un administrateur. D'autres sites ont tellement d'utilisateurs qu'ils doivent s'auto-enregistrer et s'auto-activer leurs comptes. La manière dont les utilisateurs s'inscrivent sur votre site se configure dans le formulaire *Utilisateurs : Options*.

## Autoriser l'Auto-enregistrement

L'auto-enregistrement des utilisateurs est désactivé par défaut. Tout nouvel utilisateur doit être créé par un Gestionnaire ou un Administrateur. L'auto-enregistrement peut être autorisé avec quelques modifications simples du formulaire *Utilisateurs : Options*.

- Sélectionnez **Utilisateurs → Gérer** dans le menu Administrateur.
- Sélectionnez le bouton *Options* de la Barre d'outils.
- Réglez **Autoriser l'enregistrement des utilisateurs** sur **Oui**.
- Le **Groupe d'enregistrement des nouveaux utilisateurs** devrait être **- Enregistré -** sauf s'il y a une bonne raison pour qu'il soit autre chose.
- L'**Activation du compte du nouvel utilisateur** devrait être **Soi-même** ou **Administrateur**.
  - Soi-même : L'utilisateur recevra un e-mail avec un lien d'activation. Le compte sera activé lorsque l'utilisateur cliquera sur le lien d'activation.
  - Administrateur : L'utilisateur recevra un e-mail avec un lien d'activation. Lorsque l'utilisateur clique sur ce lien, l'administrateur du site sera averti par e-mail. L'administrateur du site doit ensuite activer le compte de l'utilisateur.

![Onglet des options de configuration de l'utilisateur](../../../en/images/users/users-configuration-user-options.png)

- **Enregistrer & Fermer**
- Ajouter un module *Connexion*. Ou
- Ajouter un élément de menu *Utilisateurs : Formulaire de connexion* et un élément de menu *Utilisateurs : Déconnexion*.

## Interdire l'auto-inscription

- Réglez **Autoriser l'inscription des utilisateurs** sur **Non**.

## Ajout d'un Nouvel Utilisateur

Si l'auto-inscription n'est pas autorisée, tout nouvel utilisateur doit être créé par un administrateur. Procédez comme suit :

- Sélectionnez l'icône **Utilisateurs +** dans le panneau de tableau de bord du site d'accueil. Ou
- Sélectionnez **Utilisateurs** → **Gérer +** dans le menu Administrateur.
- Remplissez le formulaire **Détails du Nouvel Utilisateur**. La plupart des champs ont des valeurs par défaut appropriées.

![Page de saisie des données du nouvel utilisateur](../../../en/images/users/users-new-user.png)

- Sélectionnez l'onglet **Groupes d'Utilisateurs Assignés** et cochez la case correspondant au groupe d'utilisateurs souhaité. Inscrits est coché par défaut.
- **Enregistrer & Fermer**.
- Dans la liste des utilisateurs, vérifiez que le nouveau compte utilisateur est activé (cocher verte dans les colonnes Activé).

## Bloquer un utilisateur

La meilleure méthode pour gérer un utilisateur problématique est de désactiver le compte utilisateur plutôt que de le supprimer. Cette mesure peut être utilisée pour suspendre l'utilisateur et être révoquée si l'utilisateur promet de se comporter correctement. Supprimer un compte romprait tout lien vers le contenu apporté par l'utilisateur, tel que la paternité d'articles, et pourrait permettre à l'utilisateur de s'inscrire à nouveau avec la même adresse e-mail.

Pour bloquer un utilisateur :

- Sélectionnez **Utilisateurs → Gérer** dans le menu Administrateur.
- Trouvez l'utilisateur dans la liste des *Utilisateurs*. Utilisez le filtre texte si nécessaire.
- Sélectionnez l'icône Activée apparaissant sous la forme d'une coche verte à côté du nom de l'utilisateur. Un libellé **Bloquer** apparaît au survol.

![Page de saisie de données d'utilisateur nouveau](../../../en/images/users/users-hover-block.png)

- Sélectionnez l'icône *Activée*. La page se recharge avec l'icône Activée apparaissant sous la forme d'une croix grise.

## Débloquer un utilisateur

Simple :

- Basculez l'icône *Activé* pour qu'elle redevienne une coche verte.

*Traduit par openai.com*


<!-- Filename: J4.x:User_Password_Reset / Display title: Réinitialisation du mot de passe utilisateur -->

## Réinitialisation de l'utilisateur

Si vos utilisateurs ont accès à la connexion au site et qu'un utilisateur ne peut pas se souvenir soit de son identifiant, soit de son mot de passe, il est préférable d'exiger que l'individu réinitialise lui-même ses identifiants en utilisant les liens dans le formulaire de connexion :

![module de connexion utilisateur du site](../../../en/images/users/user-site-login-module.png)

Dans chaque cas, la sélection d'un lien mène à un formulaire pour saisir l'adresse électronique associée au compte :

![formulaire de réinitialisation de mot de passe oublié du site](../../../en/images/users/user-forgot-password-reset.png)

L'ensemble du processus est accompli par l'utilisateur sans intervention requise de la part d'un administrateur. Il s'agit du formulaire de vérification du mot de passe perdu :

![formulaire de confirmation de mot de passe oublié du site](../../../en/images/users/user-forgot-password-confirm.png)

Et enfin, l'utilisateur doit entrer un nouveau mot de passe :

![formulaire de réinitialisation de mot de passe complète du site](../../../en/images/users/user-forgot-password-complete.png)  

## Réinitialisation de l'administrateur

S'il n'y a qu'une connexion Administrateur, la réinitialisation d'un mot de passe utilisateur doit être effectuée par un Super Utilisateur ou un Administrateur. Si c’est le seul Super Utilisateur qui ne connaît pas les identifiants de connexion, consultez l'article distinct sur la Récupération du Mot de Passe de l'Administrateur. Sinon :

- Sélectionnez **Utilisateurs → Gérer** dans le menu Administrateur ou sélectionnez *Utilisateurs* depuis le panneau du Tableau de Bord de la page d'accueil.
- Trouvez l'utilisateur dont le mot de passe doit être réinitialisé.
- Sélectionnez le **Nom** lié pour ouvrir le formulaire *Utilisateur : Éditer*.
- Saisissez un nouveau mot de passe dans les champs Mot de passe et Répéter le mot de passe.
- Réglez le champ **Exiger la Réinitialisation du Mot de Passe** sur *Oui*.
- **Enregistrer & Fermer**

![formulaire d'édition d'utilisateur administrateurs](../../../en/images/users/users-edit-user-john-doe.png)

Vous devrez ensuite envoyer un email à l'utilisateur avec le nouveau mot de passe provisoire en texte clair. Après la connexion, l'utilisateur pourra voir la page d'accueil du site mais toute tentative de navigation vers une autre page l'amènera au formulaire de nouveau mot de passe.

*Traduit par openai.com*


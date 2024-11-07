<!-- Filename: J4.x:Login_and_Logout_Redirects / Display title: Redirections de connexion et déconnexion   -->

## Paramètres par défaut

Les options de connexion et de déconnexion permettent de sélectionner une page vers laquelle rediriger en cas de succès. Il existe des paramètres par défaut, mais ils peuvent ne pas convenir à votre site. Par exemple, le formulaire de connexion mène par défaut à la page du profil utilisateur. Cela devient ennuyeux s'il n'y a aucune raison valable de voir la page de profil à chaque connexion.

Cet article couvre les options de redirection disponibles après une connexion ou une déconnexion réussie.

## Module de connexion

Le comportement par défaut d'un module de connexion est de rester sur la même page après la connexion et la déconnexion. Le seul inconvénient de ce comportement est qu'un utilisateur se déconnectant d'une page restreinte sera invité à se reconnecter. Si cela pose problème, une solution facile est de sélectionner la page d'accueil pour rediriger dans le champ de paramètres du module de la page de redirection de déconnexion.

![formulaire de menu de déconnexion restreint à l'accès enregistré](../../../en/images/users/login-redirects-login-form.png)

Conseil : Vous pourriez utiliser deux modules de connexion. L'un avec l'accès **Invité** intitulé **Connexion**. Le second avec l'accès **Enregistré** intitulé **Déconnexion**.

## Élément de menu de connexion

Le type d'élément de menu de connexion peut être utilisé pour la connexion et la déconnexion. S'il est utilisé pour les deux, il devrait avoir un titre tel que Connexion/Déconnexion. Si vous trouvez cela maladroit, vous pouvez utiliser des éléments de menu distincts pour Connexion et Déconnexion.

Le type d'élément de menu de connexion permet de choisir le type de redirection de connexion : par élément de menu ou par URL interne. Par défaut, Élément de menu est sélectionné mais non défini, et la connexion mène à la page de profil utilisateur. Vous pouvez sélectionner un élément de menu ou donner l'URL d'une page. Par exemple, vous pourriez avoir une page d'état du système avec un message du jour personnalisé.

![formulaire de menu de déconnexion restreint à l'accès enregistré](../../../en/images/users/login-redirects-login-menu-options.png)

Le comportement de déconnexion par défaut est de rediriger vers la page d'accueil du site. Vous pourriez rediriger vers autre chose, comme un message d'au revoir lié par un élément de menu ou une URL interne.  

## Élément de menu Déconnexion

L'élément de menu Déconnexion est simple. Par défaut, vous restez sur la même page après la déconnexion. Si cela s'avère peu pratique, sélectionnez la page d'accueil du site.

![formulaire du menu de déconnexion réservé à l'accès enregistré](../../../en/images/users/login-redirects-logout-menu-options.png)

*Traduit par openai.com*


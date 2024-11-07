<!-- Filename: J4.x:Guest_Access / Display title: Accès Invité -->

## Niveaux d'accès

Les visiteurs du site peuvent voir des éléments tels que des articles, des modules et des éléments de menu, car ces éléments sont attribués au niveau d'accès Public par défaut. Ce niveau d'accès permet également aux utilisateurs connectés de voir les mêmes contenus. Cependant, il y a des occasions où il n'est pas approprié pour un utilisateur connecté de voir un élément de contenu. Par exemple, un élément de menu Connexion devrait être visible par les utilisateurs qui ne sont pas connectés, mais ne devrait pas être visible par les utilisateurs qui sont connectés. C'est à cela que sert le niveau d'accès Invité. Les utilisateurs connectés devraient voir un élément de menu Déconnexion à la place. Ces éléments doivent être attribués au niveau d'accès Enregistré.

Dans certains cas, il est également approprié de restreindre l'accès à un article ou à un module aux utilisateurs qui ne sont pas connectés ou aux utilisateurs qui sont connectés.

## Accès Invité

L'utilisation du niveau d'accès Invité peut être illustrée avec un élément de menu Connexion :

- Sélectionnez **Menus → Menu Principal → +** dans le menu Administrateur. Utilisez le menu que vous préférez pour les nouveaux éléments.
- Dans le formulaire **Menus : Nouvel Élément**, entrez un titre approprié dans le champ **Titre**, par exemple **Connexion**.
- Dans le champ **Type d'Élément de Menu**, utilisez le bouton **Sélectionner** pour ouvrir la boîte de dialogue contextuelle Type d'Élément de Menu.
- Dans la liste **Type d'Élément de Menu**, sélectionnez la section Utilisateurs et choisissez l'élément **Formulaire de Connexion**.
- De retour dans le formulaire **Menus : Nouvel Élément**, définissez le champ **Accès** sur **Invité**.
- Enregistrez
- Facultativement, sélectionnez la liste Ordre et choisissez l'élément **après** lequel vous souhaitez que l'élément de menu Connexion apparaisse.

![formulaire de menu de connexion restreint à l'accès invité](../../../en/images/users/guest-access-menu-login.png)

- Enregistrer et Fermer.
- Visualisez le site. Vérifiez que l'élément de menu Connexion fonctionne. Vérifiez qu'il disparaît après la connexion.

## Accès Enregistré

L'utilisation du niveau d'accès Enregistré peut être illustrée avec un élément de menu Déconnexion :

- Sélectionnez **Menus → Menu Principal → +** dans le menu de l'Administrateur. Utilisez le menu de votre choix pour les nouveaux éléments.
- Dans le formulaire **Menus : Nouvel Élément**, entrez un titre approprié dans le champ **Titre**, par exemple **Déconnexion**.
- Dans le champ **Type d'Élément de Menu**, utilisez le bouton **Sélectionner** pour ouvrir la boîte de dialogue contextuelle Type d'Élément de Menu.
- Dans la liste **Type d'Élément de Menu**, sélectionnez la section Utilisateurs et choisissez l'élément **Déconnexion**.
- De retour dans le formulaire **Menus : Nouvel Élément**, réglez le champ **Accès** sur **Enregistré**.
- Enregistrez.
- Optionnellement, sélectionnez le menu déroulant de Classement et choisissez l'élément **après** lequel vous souhaitez que l'élément de connexion apparaisse.

![formulaire de menu déconnexion restreint à l'accès enregistré](../../../en/images/users/guest-access-menu-logout.png)

- Enregistrez et Fermez.
- Visualisez le site. Vérifiez que l'élément de menu Déconnexion fonctionne. Vérifiez qu'il disparaît après la déconnexion.

*Traduit par openai.com*


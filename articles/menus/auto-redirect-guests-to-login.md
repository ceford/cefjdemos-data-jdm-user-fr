<!-- Filename: Auto_redirect_guests_to_login / Display title: Rediriger automatiquement les invités vers la connexion -->

## Fonctionnalité souhaitée

Supposons que vous ayez des choix de menu nécessitant qu'un utilisateur soit connecté, comme *Soumettre un article*. Vous souhaitez que tous les utilisateurs puissent voir l'élément de menu restreint, qu'ils soient connectés ou non. Le comportement souhaité est le suivant :

* Si l'utilisateur est connecté, il accède directement à l'élément de menu restreint.
* Si l'utilisateur n'est pas connecté, il est présenté avec le formulaire de connexion et, après une connexion réussie, continue vers la page restreinte.
* Si l'utilisateur n'est pas enregistré, il a la possibilité de s'enregistrer ou de naviguer vers une autre page.

## Solution

Voici comment procéder dans Joomla!.

1. Créez un nouveau menu dans la liste **Menus**, nommé par exemple **Menu Caché**.
2. Ajoutez des éléments de menu qui seront accessibles uniquement aux utilisateurs enregistrés (par exemple, *Soumettre un article*). Définissez les niveaux d'accès requis de ces éléments de menu sur **Enregistré**.
3. Ne créez PAS de module pour le *Menu Caché*. Il ne sera pas affiché sur aucune page, donc il n'a pas besoin de module.
4. Créez votre menu *réel*, nommé par exemple **Menu du Site**, et l'élément de menu qui sera affiché pour tous les utilisateurs, comme *Soumettre un article*.
    - L'élément de menu aura un type d'élément de menu de type **Alias d'Élément de Menu** trouvé dans le type d'élément de menu **Liens Système**.
    - Son paramètre *Élément de Menu* sera l'élément de menu *Soumettre un article* dans le **Menu Caché**.
    - Le niveau d'accès pour cet élément de menu sera **Public**, car tout le monde doit pouvoir le voir et l'utiliser.
5. Créez un module pour le *Menu du Site* comme vous le faites pour tout menu.
6. Si vous souhaitez des sous-menus, assurez-vous d'avoir ajouté les éléments du sous-menu dans le **Menu du Site** et non dans le **Menu Caché**.

Maintenant, lorsqu'un invité (utilisateur non connecté) accède à l'option de menu *Soumettre un article*, cela le redirige vers la page de connexion. Si la connexion est réussie, l'utilisateur est redirigé vers la page **Soumettre un article** restreinte. Si l'utilisateur est déjà connecté, la redirection est immédiate.

## Exemple

Pour les éléments de menu suivants :

1. Accueil
2. Blog
3. Wiki
4. Annuaire
5. Petites annonces
6. FAQ
7. Boutique
8. Contactez-nous

Tous les éléments de menu doivent être visibles par tout le monde en front-end, mais les éléments 3, 4, 5, 6 et 7 doivent être accessibles uniquement aux utilisateurs **Enregistrés**.

Dans ce cas, les éléments de menu 3 à 7 se trouvent dans le menu *caché* avec leur paramètre **Accès** défini sur **Enregistré**. Les éléments 3 à 7 ont des éléments de menu *alias* dans le menu *réel* avec leurs paramètres **Accès** définis sur **Public**.


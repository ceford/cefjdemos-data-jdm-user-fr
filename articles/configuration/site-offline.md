<!-- Filename: J4.x:Site_Offline / Display title: Site hors ligne -->

## Uniquement pour les utilisateurs du site

Il peut arriver que vous ayez besoin de rendre votre site Joomla! indisponible pour les visiteurs pendant une courte période. Il existe un simple commutateur de configuration **Site hors ligne** à cet effet, qui peut être modifié de **Non** à **Oui** selon les besoins. Lorsque réglé sur *Oui*, tous les visiteurs du site voient une page de message hors ligne avec un formulaire de connexion. Le formulaire hors ligne par défaut peut être personnalisé avec une image :

![Écran site hors ligne](../../../en/images/configuration/site-offline.png)

Le commutateur Site hors ligne ne s'applique pas à l'interface administrateur, et les utilisateurs qui peuvent se connecter à l'arrière-plan peuvent continuer à se connecter au front-end. La connexion au front-end est refusée uniquement aux utilisateurs des groupes d'utilisateurs Enregistré, Auteur, Éditeur et Éditeur en chef.

## Pour basculer hors ligne

- Sélectionnez **Tableau de bord principal → Configuration globale** dans le menu Administrateur.
- Dans l'onglet **Site**, réglez l'interrupteur **Site hors ligne** sur **Oui**.
- Vous pouvez alors choisir d'utiliser soit
  - **Utiliser un message personnalisé** qui est le texte dans la case Message personnalisé. Ou...
  - **Le message par défaut de la langue du site**, qui est **Ce site est en maintenance. Veuillez revenir bientôt.** en anglais ou l'équivalent dans la langue sélectionnée du site. Cela permet également de sélectionner une image. Ou...
  - **Masquer** pour ne montrer aucun message.
- Sélectionnez **Enregistrer & Fermer** dans la barre d'outils.
- Effectuez les opérations de maintenance nécessaires.
- Retournez au formulaire de configuration globale.
- Réglez l'interrupteur Site hors ligne sur **Non**.
- Sélectionnez **Enregistrer & Fermer** dans la barre d'outils.

## Tous les utilisateurs

Vous pouvez limiter l'accès à votre site web en protégeant par mot de passe le répertoire Joomla. Seuls les utilisateurs qui connaissent le nom d'utilisateur et le mot de passe d'accès au répertoire pourront accéder au site. Vous pouvez configurer plusieurs utilisateurs de ce type. Avec le panneau de contrôle d'hébergement cPanel :

- Connectez-vous à votre compte cPanel.
- Dans la section Fichiers, sélectionnez **Confidentialité des répertoires**.
- Si la racine de votre site se trouve dans un sous-répertoire de public_html
  - Sélectionnez le répertoire public_html
- Sélectionnez le bouton Modifier pour le répertoire contenant votre site (public_html si votre site est à la racine du web).
- Cochez la case **Protéger par mot de passe ce répertoire.**.
- Entrez un nom pour le répertoire protégé : le nom par défaut peut être suffisant.
- Sélectionnez le bouton **Enregistrer**.
- Une page de message de succès avec un lien Retour apparaît, sélectionnez-le.
- Créez un utilisateur pour accéder au répertoire protégé.
- Entrez un nom d'utilisateur.
- Entrez un mot de passe et répétez (retenez-le ou écrivez-le).
- Sélectionnez **Enregistrer**.

Maintenant, vérifiez que le répertoire nécessite un mot de passe pour accéder via le web. Lorsque vous visitez votre site, il vous sera demandé votre nom d'utilisateur et votre mot de passe d'accès au répertoire. Ils peuvent être complètement différents de votre nom d'utilisateur et mot de passe Joomla.

Pour supprimer la protection par mot de passe du répertoire :

- Connectez-vous à votre compte cPanel.
- Dans la section Fichiers, sélectionnez **Confidentialité des répertoires**.
- Si la racine de votre site se trouve dans un sous-répertoire de public_html
  - Sélectionnez le répertoire public_html
- Sélectionnez le bouton **Modifier** pour le répertoire contenant votre site (public_html si votre site est à la racine du web). Il affichera maintenant un symbole de verrouillage et Oui sous l'en-tête Privé.
- **Décochez** la case **Protéger par mot de passe ce répertoire.**.
- Sélectionnez le bouton **Enregistrer**.

Pour vérifier que la protection par mot de passe a été supprimée, utilisez un autre navigateur pour accéder à votre site ou fermez et rouvrez votre navigateur actuel, puis accédez à votre site à nouveau.


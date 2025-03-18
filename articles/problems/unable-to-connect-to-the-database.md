<!-- Filename: Unable_to_connect_to_the_database / Display title: Connexion à la base de données  -->

## Erreur de Connexion Impossible

Si vous recevez une erreur "**Impossible de se connecter à la base de données**" lors de l'installation, vérifiez que vous avez correctement saisi les détails de votre base de données MySQL/MariaDB. Le script d'**installation** ne vous permettra pas de continuer à moins que les détails soient corrects.

Notez qu'il n'est pas nécessaire de créer un utilisateur de base de données et un mot de passe lors de l'installation. Ils doivent être créés au préalable.

Si l'erreur se produit après avoir déplacé votre site vers un autre hôte, vérifiez les éléments suivants de votre fichier *configuration.php*. Les paramètres de base de données habituels sont les suivants :

    public $dbtype = 'mysqli';
    public $host = 'localhost';
    public $user = 'yourdbuser';
    public $password = 'yourdbpassword';
    public $db = 'yourdbname';
    public $dbprefix = 't6q6i_';

Si l'erreur survient sur un site qui fonctionnait auparavant, il y a plusieurs raisons possibles, parfois temporaires et parfois accidentelles.

## Les pannes les plus courantes

1. Parfois, vous verrez ce message si MySQL/MariaDB a cessé de fonctionner sur votre serveur. L'administrateur de votre serveur peut temporairement arrêter MySQL/MariaDB pour effectuer une maintenance. Dans de telles circonstances, votre site reviendra probablement bientôt.
2. Votre utilisateur de base de données a été supprimé. Si tel est le cas, vous devrez recréer votre utilisateur de base de données avec le même nom d'utilisateur et mot de passe qui existaient lors de l'installation initiale de Joomla. Utilisez le panneau de contrôle de votre domaine pour gérer cela ou contactez votre administrateur de serveur.
3. Votre nom d'utilisateur ou mot de passe de base de données a changé.

*Traduit par openai.com*

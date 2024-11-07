<!-- Filename: Moving_the_site_among_directories/sub-directories / Display title: Déplacement du Répertoire d'Installation -->

Il arrive souvent que vous installiez Joomla dans un sous-répertoire et que vous souhaitiez ensuite le déplacer vers un répertoire de niveau supérieur. Voici un court tutoriel sur la manière de procéder.

Supposons que vous ayez installé Joomla dans le dossier suivant : public_html/tryjoomla. Maintenant que vous êtes satisfait du site, vous voudrez le déplacer vers public_html.

1. Déplacez tous les fichiers du sous-répertoire (c'est-à-dire, public_html/tryjoomla) vers le répertoire de niveau supérieur (c'est-à-dire, public_html). Vous pouvez utiliser votre client FTP préféré ou le panneau de contrôle fourni par votre service d'hébergement.
2. Téléchargez et ouvrez le fichier configuration.php dans un éditeur de texte.
3. Supprimez simplement le nom du dossier tryjoomla du chemin. Recherchez les lignes suivantes :
    ```
    var $live_site = '';
    var $log_path = '/home/username/public_html/tryjoomla/administrator/logs';
    var $tmp_path = '/home/username/public_html/tryjoomla/tmp';
    var $ftp_root = 'public_html/tryjoomla';
    ```
    Modifiez comme suit :
    ```
    var $live_site = '';
    var $log_path = '/home/username/public_html/administrator/logs';
    var $tmp_path = '/home/username/public_html/tmp';
    var $ftp_root = 'public_html';
    ```
    N.B. La variable \$live_site a rarement besoin de recevoir une valeur. Mais si une valeur lui a été attribuée lors de l'installation, modifiez également ce chemin.
    ```
    var $live_site = 'http://www.example.com/tryjoomla';
    ```
    Modifiez comme suit :
    ```
    var $live_site = 'http://www.example.com';
    ```
4. Vérifiez le fichier .htaccess de votre site. Le sous-dossier devrait y être supprimé également. La directive RewriteBase devrait être commentée. Vérifiez s'il existe une RewriteRule contenant l'ancien sous-répertoire.
5. Assurez-vous qu'aucun ordre de redirection vers l'ancien sous-répertoire n'est en place dans le panneau de contrôle de votre hébergement.
6. Si vous avez activé le cache, connectez-vous à l'interface d'administration (qui se trouve maintenant à `http://www.example.com/administrator` et non `http://www.example.com/tryjoomla/administrator`). Allez dans Système / Cache et supprimez tous les fichiers de cache.

*Traduit par openai.com*

<!-- Filename: How_do_you_block_directory_scans_using_htaccess%3F / Display title: Comment bloquer les analyses de répertoires à l'aide du htaccess ? -->

**Instructions**

Add Apache rewrite rules to your `.htaccess` file. For example, the
following will redirect all attempts to access files with names starting
with, "phpMyAdmin" to `index.php`.

  
**Exemple de règle de réécriture Apache**

    RewriteRule ^/phpMyAdmin.*$ /index.php

  
**Quelques conseils d'expressions régulières**

    ^ Signifie le début de nom de fichier
    . Signifie n'importe quel caractère autre que les retours à la ligne
    * Désigne une ou plusieurs des caractères précédents
    $ Signifie la fin de la ligne

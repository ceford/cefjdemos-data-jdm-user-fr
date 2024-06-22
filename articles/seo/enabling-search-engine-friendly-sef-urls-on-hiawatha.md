<!-- Filename: Enabling_Search_Engine_Friendly_(SEF)_URLs_on_Hiawatha / Display title: Autoriser les réécriture d'URL en clair  (SEF) dans Hiawatha -->

Utilisez les règles UrlToolkit suivantes pour activer les URLs propres
sur un serveur Hiawatha :

    UrlToolkit {
        ToolkitID = joomla
        Match base64_encode.*\(.*\) DenyAccess
        Match (<|%3C).*script.*(>|%3E) DenyAccess
        Match GLOBALS(=|\[|\%[0-9A-Z]{0,2}) DenyAccess
        Match _REQUEST(=|\[|\%[0-9A-Z]{0,2}) DenyAccess
        RequestURI exists Return
        Match /index.php Return
        Match ^/component/ Skip 2
        Match ^(/|\.php|\.html|\.htm|\.feed|\.pdf|\.raw|/[^.]*)$ Skip 1
        Skip 1
        Match .* Rewrite /index.php
    }

Utilisez une règle UrlToolkit pour un hébergeur virtuel (virtual host)
grâce au paramétrage UseToolkit :

    VirtualHost {
        ...
        UseToolkit = joomla
    }

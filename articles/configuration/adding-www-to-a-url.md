<!-- Filename: Adding_www_to_a_url / Display title: Ajouter www à une URL  -->

## Expressions régulières Apache .htaccess

Pour une solution simple, ajoutez ce qui suit à votre fichier `.htaccess` :

```bash
    RewriteEngine On
    RewriteCond %{HTTP_HOST} !^(www\.example\.com)?$ [NC]
    RewriteRule (.*) https://www.example.com/$1 [R=301,L]
```

Dans ce cas, une URL de la forme `https://example.com/index.php?item=1` sera redirigée vers `https://www.example.com/index.php?item=1`.

Dans l'exemple ci-dessus :

* `RewriteCond` définit une condition de test.
* `%{HTTP_HOST}` utilise la variable d'hôte de la requête (example.com).
* `!` signifie PAS et `^` signifie DÉBUT - donc, ne commence pas par www.example.com
* `(` et `)` capturent ce qui se trouve entre les parenthèses pour une utilisation de référence ultérieure.
* `\` transforme le caractère suivant d'un caractère de contrôle en un caractère réel.
* `.` signifie habituellement n'importe quel caractère mais précédé par \ il signifie un point.
* `?` rend la correspondance optionnelle.
* `$` signifie FIN (de la correspondance optionnelle).
* `[NC]` signifie Sans Casse, donc insensible à la casse.
* `RewriteRule` est valide si l'URL ne commence pas par www.
* `(.*)` est un modèle, dans ce cas un seul caractère répété 0 ou plus de fois, représentant la partie chemin de l'URL. Il est capturé comme $1.
* `https://www.example.com/` est le remplacement pour la partie hôte de l'URL.
* `$1` est le chemin capturé.
* `[]` contient des indicateurs - instructions sur ce qu'il faut faire.
* `R=301` est une instruction pour envoyer un en-tête Déplacé de manière Permanente.
* `L` signifie Dernier dans l'ensemble - dès qu'une correspondance est trouvée, ignorer toute règle subséquente.

Une solution plus complète résolvant plusieurs autres problèmes de canonisation en même temps :

    RewriteEngine On
    #
    RewriteCond %{THE_REQUEST} ^[A-Z]{3,9}\ /([^/]+/)*index\.html?\ HTTP/
    RewriteRule ^(([^/]+/)*)index\.html?$ http://www.example.com/$1 [R=301,L]
    #
    RewriteCond %{THE_REQUEST} !^POST
    RewriteCond %{THE_REQUEST} ^[A-Z]{3,9}\ /([^/]+/)*index\.php\ HTTP/
    RewriteCond %{SERVER_PORT}>s ^(443>(s)|[0-9]+>s)$
    RewriteRule ^(([^/]+/)*)index\.php$ http%2://www.example.com/$1 [R=301,L]
    #
    RewriteCond %{HTTP_HOST} !^(www\.example\.com)?$
    RewriteRule (.*) http://www.example.com/$1 [R=301,L]

Si vous souhaitez comprendre ce que tout cela signifie, vous pouvez lire ces articles :

* [Introduction à Apache mod_rewrite](https://httpd.apache.org/docs/2.4/rewrite/intro.html)
* [Introduction aux redirections .htaccess](https://www.danielmorell.com/guides/htaccess-seo/redirects/introduction-to-redirects)

*Traduit par openai.com*


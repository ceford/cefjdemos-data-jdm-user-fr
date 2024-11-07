<!-- Filename: Nginx / Display title: Nginx -->

<a href="http://nginx.org/" rel="nofollow noreferrer noopener">Nginx</a> est un serveur Web léger qui alimente <a href="https://en.wikipedia.org/wiki/Nginx" rel="nofollow noreferrer noopener">environ 33%</a> des serveurs Web dans tous les domaines. À moins que vous n'ayez des exigences spécifiques nécessitant un serveur Web lourd comme Apache, il est préférable d'utiliser Nginx.

Vous trouverez ci-dessous des instructions sur la façon de faire fonctionner Joomla! avec <a href="https://www.nginx.com/resources/wiki/start/topics/examples/phpfcgi/" rel="nofollow noreferrer noopener">l'exemple PHP FastCGI</a>.
## Installer Nginx

Pour Ubuntu, exécutez *aptitude install Nginx*. Pour d'autres distributions, utilisez le gestionnaire de paquets correspondant ou consultez la <a href="https://www.nginx.com/resources/wiki/start/topics/tutorials/install/" rel="nofollow noreferrer noopener">page d'installation de Nginx</a>.

## Installer PHP FastCGI

Pour Ubuntu, lisez l'<a href="https://www.nginx.com/resources/wiki/start/topics/examples/phpfcgi/" rel="nofollow noreferrer noopener">exemple PHP FastCGI</a>.

Pour Gentoo, PHP fonctionnera en tant que service FastCGI (FPM), donc le serveur Nginx exécutera PHP comme un processus séparé :

```shell
# echo "dev-lang/php gd gd2 curl simplexml tokenizer dom tidy sqlite xml fpm cgi" >> /etc/portage/package.use
# emerge php
```

Les paramètres par défaut de PHP-FPM conviennent à la plupart des serveurs. Pour des configurations spéciales, visitez le
<a href="http://php.net/manual/en/install.fpm.php" rel="nofollow noreferrer noopener">site PHP FPM</a>.

## Configurer Nginx

Les fichiers de configuration de Nginx se trouvent dans :

- `/etc/nginx/sites-available/` sur Ubuntu (pour les sites fonctionnant
  sur cette instance Nginx)
- `/etc/nginx/nginx.conf` sur Gentoo et Raspbian (Debian optimisé pour
  Raspberry Pi)

Voici un exemple de fichier de configuration Nginx, *joomla.conf*, que vous pouvez
réutiliser sur tous vos sites activés par Nginx.

    server {
      listen 80;
        server_name VOTRE_DOMAINE;
        server_name_in_redirect off;

        access_log /var/log/nginx/localhost.access_log;
        error_log /var/log/nginx/localhost.error_log info;

        root CHEMIN_SUR_SERVEUR;
        index index.php index.html index.htm default.html default.htm;
        # Support des URLs propres (alias URL conviviales pour les moteurs de recherche)
        location / {
            try_files $uri $uri/ /index.php?$args;
        }

        # Ajouter un en-tête global x-content-type-options
        add_header X-Content-Type-Options nosniff;

        # Refuser l'exécution de scripts dans les répertoires accessibles en écriture
        location ~* /(images|cache|media|logs|tmp)/.*\.(php|pl|py|jsp|asp|sh|cgi)$ {
            return 403;
            error_page 403 /403_error.html;
        }

        location ~ \.php$ {
          fastcgi_pass  127.0.0.1:9000;
          fastcgi_index index.php;
          include fastcgi_params;
          fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
          include /etc/nginx/fastcgi.conf;
        }

        # mise en cache des fichiers
        location ~* \.(ico|pdf|flv)$ {
            expires 1y;
        }

        location ~* \.(js|css|png|jpg|jpeg|gif|swf|xml|txt)$ {
            expires 14d;
        }

    }

Prêtez attention à quelques éléments :

1.  Le paramètre *fastcgi_pass* est défini sur *127.0.0.1:9000*,
    correspondant au port auquel FPM est configuré pour écouter. Cela
    signifie que vous pouvez exécuter les processus PHP sur des serveurs séparés. Sur Gentoo,
    vous pouvez trouver cette configuration dans le fichier
    */etc/php/fpm-php5.3/php-fpm.conf/*.
2.  N'oubliez pas de remplacer VOTRE_DOMAINE et CHEMIN_SUR_SERVEUR ci-dessus en fonction
    de votre domaine et du chemin de Joomla sur votre serveur.

## Support GZip

Si vous avez besoin du support de la compression GZip, ajoutez la section suivante à la section *http* du fichier de configuration principal de Nginx :

    gzip on;
    gzip_http_version 1.1;
    gzip_comp_level 6;
    gzip_min_length 1100;
    gzip_buffers 4 8k;
    gzip_types text/plain application/xhtml+xml text/css application/xml application/xml+rss text/javascript application/javascript application/x-javascript;
    gzip_proxied any;
    gzip_disable "MSIE [1-6]\.";

## Sources

- <a href="https://wiki.gentoo.org/wiki/Nginx"
rel="nofollow noreferrer noopener">Nginx dans Gentoo</a>
- <a href="https://kevinworthington.com/nginx-for-windows/"
  rel="nofollow noreferrer noopener">Nginx pour Windows</a>
- <a
  href="https://ubuntu.com/tutorials/install-and-configure-nginx#1-overview"
  rel="nofollow noreferrer noopener">Nginx dans Ubuntu</a>
- <a
  href="https://www.debianadmin.com/howto-install-nginx-webserver-in-debian.html"
  rel="nofollow noreferrer noopener">Nginx dans Debian</a>
- <a href="https://www.php.net/manual/en/install.fpm.php"
  rel="nofollow noreferrer noopener">Installation et configuration de PHP-FPM</a>
- <a
  href="https://docs.nginx.com/nginx/admin-guide/web-server/compression/"
  rel="nofollow noreferrer noopener">Compression et Décompression</a>
- <a href="https://www.nginx.com/blog/creating-nginx-rewrite-rules/"
  rel="nofollow noreferrer noopener">Création de Règles de Réécriture NGINX</a>
- <a href="http://nginx.org/en/docs/http/request_processing.html"
  rel="nofollow noreferrer noopener">Comment Nginx traite une requête</a>

*Traduit par openai.com*


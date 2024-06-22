<!-- Filename: Enabling_Search_Engine_Friendly_(SEF)_URLs_on_Nginx / Display title: Autoriser les réécritures d'URL en clair  (SEF) dans Nginx. -->

**Search engine friendly (SEF)**, **human-readable** or
<a href="https://en.wikipedia.org/wiki/Clean_URL" class="extiw"
title="wikipedia:Clean URL">clean URLs</a> are URLs that make sense to
both humans and search engines because they explain the path to the
particular page they point to. Since version 1.5, Joomla! is capable of
creating and parsing URLs in any format, including SEF URLs. This does
not depend on URL rewriting executed by the web server, so it works even
if Joomla! runs a server other than Apache with the mod_rewrite module.
The SEF URLs follow a certain fixed pattern, but the user can define a
short descriptive text (alias)
for each segment of the URL.

Internally, the local part of a SEF URL (the part after the domain name)
is called a *route*. Creating and processing SEF URLs is therefore
referred to as *routing*, and the relevant code is called a *router*.

Cet article concerne la fonctionnalité de réécriture d'URL en clair
(SEF) avec le serveur libre de droit fréquemment utilisé
<a href="http://nginx.net" class="external text" target="_blank"
rel="nofollow noreferrer noopener">Nginx</a>.

Depuis la version Joomla!
<img src="https://docs.joomla.org/images/5/53/Compat_icon_2_5.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 2.5" />, la réécriture simple d'URL en clair est
disponible par défaut.
<img src="https://docs.joomla.org/images/c/c8/Compat_icon_1_5.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 1.5" /> Dans les versions antérieures, il
fallait utiliser la configuration globale pour l'activer. Les
instructions ci-dessous s'appliquent toujours si vous voulez mettre en
oeuvre la réécriture d'URL Apache mod_rewrite.

- Ajoutez le code suivant dans la configuration de votre serveur (vhost)
  dans le fichier *nginx.conf* 
       # Support Clean (aka Search Engine Friendly) URLs
       location / {
          try_files $uri $uri/ /index.php?$args;
       }

- Si cela ne fonctionne pas, ajoutez le code suivant dans le fichier de
  configuration *nginx.conf* : (Ceci fonctionnait avec nginx 1.4.6 sur
  Ubuntu.)
    server {
      ....
      location / {
         expires 1d;

         # Enable joomla SEF URL's inside Nginx
         try_files $uri $uri/ /index.php?$args;
      }
      ....
    }

- Connectez-vous à l'interface d'administration et accédez à la
  configuration globale du site.
- Activez le paramètre **Réécriture d'URL en clair (SEF)** et
  *Enregistrer*. Ce paramètre convertit les URLs depuis le format natif
  de Joomla! vers le format SEF.
  Vérifiez que votre site fonctionne correctement. Vos URLs devraient
  maintenant ressembler à
  `http://www.exemple.fr/index.php/les-­nouveautes/1-­dernieres-actualites/1­-bienvenue-dans-joomla`.
  Si votre site ne fonctionne pas correctement, reportez-vous à
  [Problèmes courants lors de l'activation de la réécriture d'URL en
  clair
  (SEF)](https://docs.joomla.org/Common_problems_when_enabling_Search_Engine_Friendly_(SEF)_URLs/fr "Common problems when enabling Search Engine Friendly (SEF) URLs/fr")
- Activez le paramètre **Réécriture au 'vol' des URL (Use Apache
  mod_rewrite/URL rewriting)** et *Enregistrer*. Ce paramètre utilise la
  fonction *mod_rewrite* Apache pour supprimer la portion "index.php" de
  l'URL.
  Vérifiez que votre site fonctionne correctement. Vos URLs devraient
  maintenant ressembler à
  `http://www.exemple.fr/les-­nouveautes/1-­dernieres-actualites/1­-bienvenue-dans-joomla`.
  Si ce paramètre provoque des erreurs, reportez-vous à [Comment
  vérifier si mod_rewrite est activé sur votre
  serveur](https://docs.joomla.org/How_to_check_if_mod_rewrite_is_enabled_on_your_server/fr "How to check if mod rewrite is enabled on your server/fr").
  Si cette option n'est pas activée mais que vous avez accès au fichier
  `apache/conf/httpd.conf`, ouvrez ce fichier et vérifiez si la ligne
  `LoadModule rewrite_module modules/mod_rewrite.so` n'est pas
  commentée. Si nécessaire, ne commentez plus cette ligne et redémarrez
  le serveur web Apache.
  Si *mod_rewrite* ne peut pas être activé, laissez cette option ainsi.
  Ce n'est pas important si vous laissez le fichier `.htaccess` renommé.
  *Si vous estimez cela nécessaire*, activez **Ajouter un suffixe aux
  URL** et *Enregistrer*. Cette option ajoute `.html` à la fin des URLs.
  Il y a différentes opinions si cela est nécessaire ou bien même utile.
  Cela ne semble pas important pour les moteurs de recherche d'avoir ou
  non `.html` à la fin des URLs.
- Ouvrez le gestionnaire de plugins et activez le plugin **Système -
  SEF**. Ce plugin ajoute le support SEF aux liens dans les articles
  Joomla. Il agit directement sur le code HTML et ne nécessite pas de
  tag particulier.

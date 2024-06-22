<!-- Filename: Enabling_Search_Engine_Friendly_(SEF)_URLs / Display title: Autoriser les réécriture d'URL en clair  (SEF). -->

La **réécriture d'URL en clair (SEF Search Engine Friendly)**, **lisible
par l'utilisateur** ou
<a href="https://en.wikipedia.org/wiki/Clean_URL" class="extiw"
title="wikipedia:Clean URL">URL propres</a> sont des URLs
compréhensibles aussi bien par les utilisateurs que par les moteurs de
recherche car elles expliquent le chemin d'accès de la page vers
laquelle elles pointent. Depuis la version Joomla! 1.5, Joomla! est
capable de créer et d'analyser tout format d'URL, y compris les URL SEF.
Cela ne dépend pas de la réécriture d'URL exécutée par le serveur, de
sorte que cela fonctionne également si Joomla! n'est pas exécuté sur un
serveur Apache utilisant le module mod_rewrite. Les URL SEF répondent à
une certaine forme fixe, mais l'utilisateur peut définir un [court texte
descriptif
(alias)](https://docs.joomla.org/Alias "Special:MyLanguage/Alias") pour
chaque segment de l'URL.

En interne, la partie d'une URL SEF (la partie située après le nom de
domaine) est appelée **route**. La création et le traitement des URLs
SEF sont donc appelés le **routage**, et le code correspondant, un
**routeur**.

La méthode pour autoriser les réécritures d'URL en clair est différente
suivant le serveur web utilisé. Si vous utilisez de l'hébergement
partagé, vous utilisez probablement Apache. Demandez confirmation à
votre hébergeur si vous n'êtes pas certain.

Seuls les serveurs web les plus utilisés ont été inclus dans cette page.
Rendez-vous sur  Autoiser les réécritures d'URL pour
IIS
et  Optimisation des URLs pour les moteurs de
recherche
pour accéder à plus d'articles.

## Apache

## Vérifiez que .htaccess est en place

Vérifiez que votre configuration Apache autorise l'accès au fichier
.htaccess en écriture. Vous devez vous assurez que l'écriture est
possible ou le fichier dans le répertoire à la racine de Joomla! sera
ignoré ou provoquera une erreur. Dans la section du fichier de
configuration du virtual host ou dans le fichier de configuration
principal (`httpd.conf`), vous devez avoir quelque chose de similaire à
l'exemple ci-dessous autorisant la réécriture :

```bash
<Directory "/home/user/public_html">
  AllowOverride All
</Directory>

<Directory "/path/to/htdocs">
  AllowOverride All Options=[an option],[an option],...
</Directory>
```

Il y a d'autres moyens de tester si `.htaccess` est autorisé si vous
n'avez pas accès aux fichiers de configuration de votre site.
Référez-vous au
<a href="http://httpd.apache.org/docs/current/howto/htaccess.html"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Tutoriel du serveur HTTP Apache :
fichiers .htaccess</a> disponible sur le site
<a href="http://www.apache.org/" class="external text" target="_blank"
rel="nofollow noreferrer noopener">The Apache Software Foundation</a>
pour de plus amples informations.

## Procédure à suivre

Voici les instructions étape par étape. Veuillez les suivre dans l'ordre
de présentation ci-dessous. Si une étape échoue, **ne pas** continuer
tant que le problème n'a pas été résolu.

1.  Renommer le fichier `"htaccess.txt"` du répertoire racine de Joomla!
    en `".htaccess"`.

2.  *Cette étape peut ne pas être nécessaire.* Ouvrir le fichier
    `.htaccess` dans un éditeur de texte. Enlever le commentaire sur la
    ligne `RewriteBase /` (enlever le premier caractère, \#). Si Joomlaǃ
    est installé dans son propre répertoire, saisissez le nom du
    répertoire Joomlaǃ après le slash. i.e.
    `RewriteBase /yourjoomlafolder`.

3.  Connectez-vous au site d'administration et accédez à la
    configuration globale du site.

4.  Activez l'option **Réécriture au 'vol' des URL (Use Apache
    mod_rewrite/URL rewriting)** et *Enregistrer*. Cette option utilises
    la fonction *mod_rewrite* Apache pour supprimer la portion
    "index.php" de l'URL.

    Vérifiez que votre site fonctionne correctement. Vos URLs devraient
    maintenant ressembler à :

        http://www.example.com/les-­nouveautes/1­-dernieres-­actualites/1-­bienvenue-­dans-joomla

    Si cette option produit des erreurs, reportez-vous à [Comment
    vérifier si mod rewrite est activé sur votre
    serveur](https://docs.joomla.org/How_to_check_if_mod_rewrite_is_enabled_on_your_server "Special:MyLanguage/How to check if mod rewrite is enabled on your server").

    - Si cette option n'est pas activée mais que vous avez accès au
      fichier `apache/conf/httpd.conf`, ouvrez ce fichier et vérifiez si
      la ligne `LoadModule rewrite_module modules/mod_rewrite.so` n'est
      pas commentée. Si nécessaire, ne commentez plus cette ligne et
      redémarrez le serveur web Apache.
    - Si *mod_rewrite* ne peut pas être activé, laissez cette option
      ainsi. Ce n'est pas important si vous laissez le fichier
      `.htaccess` renommé.

5.  *Si vous estimez cela nécessaire*, activez **Ajouter un suffixe aux
    URL** et *Enregistrer*. Cette option ajoute `.html` à la fin des
    URLs. Il y a différentes opinions si cela est nécessaire ou bien
    même utile. Cela ne semble pas important pour les moteurs de
    recherche d'avoir ou non `.html` à la fin des URLs.

6.  Ouvrez le gestionnaire de plugins et activez le plugin **Système -
    SEF**. Ce plugin ajoute le support SEF aux liens dans les articles
    Joomla. Il agit directement sur le code HTML et ne nécessite pas de
    tag particulier.

## Hiawatha

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

## IIS 7

Si votre serveur utilise IIS 7 et PHP, vous pouvez bénéficier de la
réécriture d'URL propre à IIS en utilisant un fichier web.config
similaire à celui décrit ci-dessous.

Vous pouvez soit créer le fichier vous-même ou bien à travers l'IHM du
gestionnaire IIS7. Vous pouvez importer les règles .htaccess en
utilisant le GUI/wizard.

L'utilisation de cette fonctionnalité dépend de la présence du module
**IIS URL Rewrite Module**, qui n'est pas installé par défaut avec
Windows. C'est un téléchargement gratuit d'un produit Microsoft.

### IHM

Si le module IIS "URL Rewrite module" est installé, votre gestionnaire
de site mettra à disposition un outil "URL Rewrite", visible dans
l'interface du gestionnaire d'IIS dans les modules IIS de la
configuration de votre site. L'interface est largement intiutive. Les
expressions régulières, les caractères spéciaux et les correspondances
exactes sont tous supportés.

Dans la configuration de Joomla, activez à la fois SEF et Apache
mod_rewrite. Ensuite, créer une règle dans IIS URL Rewrite :

Pattern field: **^(\[^/\]+)/?\$**

Ignore case **ON**

Action type: **Rewrite**

Rewrite URL: **index.php/**

### web.config

Ceci a été testé avec Joomla 1.5 et IIS 7 sous Windows Server 2008 sans
rencontrer de problèmes. Pour plus d'information sur la conversion de
.htaccess en web.config, reportez-vous à <a
href="http://learn.iis.net/page.aspx/557/translate-htaccess-content-to-iis-webconfig/"
class="external free" target="_blank"
rel="nofollow noreferrer noopener">http://learn.iis.net/page.aspx/557/translate-htaccess-content-to-iis-webconfig/</a>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <rewrite>
            <rules>
                <clear />
                <rule name="Common Exploit Blocking" stopProcessing="true">
                    <match url="^(.*)$" />
                    <conditions logicalGrouping="MatchAny">
                        <add input="{QUERY_STRING}" pattern="mosConfig_[a-zA-Z_]{1,21}(=|\%3D)" />
                        <add input="{QUERY_STRING}" pattern="base64_encode.*\(.*\)" />
                        <add input="{QUERY_STRING}" pattern="(\&lt;|%3C).*script.*(\>|%3E)" />
                        <add input="{QUERY_STRING}" pattern="GLOBALS(=|\[|\%[0-9A-Z]{0,2})" />
                        <add input="{QUERY_STRING}" pattern="_REQUEST(=|\[|\%[0-9A-Z]{0,2})" />
                    </conditions>
                    <action type="Redirect" url="index.php" appendQueryString="false" redirectType="SeeOther" />
                </rule>
                <rule name="Joomla Search Rule" stopProcessing="true">
                    <match url="(.*)" ignoreCase="true" />
                    <conditions logicalGrouping="MatchAll">
                        <add input="{URL}" pattern="^/search.php" ignoreCase="true" />
                    </conditions>
                    <action type="Rewrite" url="/index.php?option=com_content&amp;view=article&amp;id=4" />
                </rule>
                <rule name="Joomla Main Rewrite Rule" stopProcessing="true">
                    <match url="(.*)" ignoreCase="true" />
                    <conditions logicalGrouping="MatchAll">
                        <add input="{URL}" pattern="(/[^.]*|\.(php|html?|feed|pdf|raw))$" />
                        <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
                        <add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" />
                    </conditions>
                    <action type="Rewrite" url="index.php/" />
                </rule>
            </rules>
        </rewrite>
        <caching>
            <profiles>
                <add extension=".php" policy="DisableCache" kernelCachePolicy="DisableCache" />
            </profiles>
        </caching>
    </system.webServer>
</configuration>
```

## Nginx

- Ajoutez le code suivant dans la configuration de votre serveur (vhost)
  dans le fichier *nginx.conf*

```
       # Support Clean (aka Search Engine Friendly) URLs
       location / {
          try_files $uri $uri/ /index.php?$args;
       }
```

- Si cela ne fonctionne pas, ajoutez le code suivant dans le fichier de
  configuration *nginx.conf* : (Ceci fonctionnait avec nginx 1.4.6 sur
  Ubuntu.)

```
    server {
      ....
      location / {
         expires 1d;

         # Enable joomla SEF URL's inside Nginx
         try_files $uri $uri/ /index.php?$args;
      }
      ....
    }
```

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

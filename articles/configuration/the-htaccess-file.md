<!-- Filename: Preconfigured_htaccess / Display title: Le fichier htaccess.txt -->

## Introduction

Un serveur web Apache utilise un fichier .htaccess pour la configuration spécifique du site. Un fichier htaccess préconfiguré (`htaccess.txt`) est livré avec Joomla. Il se trouve dans le répertoire racine de Joomla et contient des instructions pour éviter les failles de sécurité courantes et mettre en œuvre des URL SEF. Si Joomla est installé dans un sous-répertoire, il peut y avoir un fichier `.htaccess` supplémentaire dans le répertoire parent. Apache les traite chacun à leur tour.

La pratique habituelle est de renommer le `htaccess.txt` fourni par Joomla en `.htaccess`, en conjonction avec la sélection des paramètres SEO dans le panneau de configuration globale. Votre service d'hébergement peut ajouter d'autres paramètres à .htaccess, il peut donc être préférable de fusionner votre fichier .htaccess avec tout fichier .htaccess fourni par le système existant.

### Configuration de la plateforme

Le fichier actif est défini dans l'un des fichiers httpd.conf avec :
```
    AccessFileName .htaccess
```
Il est par défaut à .htaccess (ce qui le rend caché sur les systèmes de fichiers de type Unix). Pas besoin de changer cela.

Sur la plateforme Windows, vous pouvez le modifier en :

    AccessFileName htaccess.ini

pour pouvoir le modifier plus facilement.

Ne faites pas de modifications à `htaccess.txt` car il pourrait être écrasé par une mise à jour de Joomla et toutes les modifications seraient perdues.

## Mises à jour Joomla

Le fichier htaccess.txt peut changer d'une version de Joomla à une autre. En cas de doute, ou si des problèmes étranges surviennent après la mise à jour, assurez-vous que votre fichier .htaccess est à jour. Voici le contenu du fichier `htaccess.txt` inclus avec Joomla 5.1 :

```bash
##
# @package    Joomla
# @copyright  (C) 2005 Open Source Matters, Inc. <https://www.joomla.org>
# @license    GNU General Public License version 2 or later; see LICENSE.txt
##

##
# LISEZ CECI EN ENTIER SI VOUS CHOISISSEZ D'UTILISER CE FICHIER !
#
# La ligne 'Options +FollowSymLinks' peut causer des problèmes avec certaines configurations de serveur.
# Elle est requise pour l'utilisation d'Apache mod_rewrite, mais elle a peut-être déjà été définie par
# votre administrateur serveur de manière à interdire sa modification dans ce fichier .htaccess.
# Si son utilisation provoque une erreur sur votre site, commentez-la (ajoutez # au début de la ligne),
# rechargez votre site dans votre navigateur et testez vos URL sef. Si elles fonctionnent, cela signifie
# qu'elle a été définie par votre administrateur serveur et vous n'avez pas besoin de la définir ici.
##

## ERREURS LIÉES AU CSS OU AU JAVASCRIPT MANQUANT

# Si votre site a un aspect étrange après avoir activé ce fichier, alors votre serveur
# compresse probablement déjà les fichiers css et js et vous devriez commenter la section
# GZIP de ce fichier.
##

## OPENLITESPEED

# Si vous utilisez un serveur web OpenLiteSpeed, toute modification apportée à ce fichier
# ne prendra effet qu'après le redémarrage du serveur web.
##

## Peut être commenté si cela provoque des erreurs, voir les notes ci-dessus.
Options +FollowSymlinks
Options -Indexes

## Pas de liste de répertoires
<IfModule mod_autoindex.c>
    IndexIgnore *
</IfModule>

## Supprimer la détection du type MIME dans les navigateurs pour les types inconnus
<IfModule mod_headers.c>
    Header always set X-Content-Type-Options "nosniff"
</IfModule>

## Protégez-vous contre certaines requêtes inter-origines. Plus d'informations peuvent être trouvées ici :

It seems like you provided a URL that points to a document about Cross-Origin Resource Policy (CORP) on the Mozilla Developer Network. Since URLs and related document titles often don't require translation, if you're in need of a translation for any specific text or section within that document, please provide the English text that you would like to have translated into French.

## https://web.dev/why-coop-coep/
#<IfModule mod_headers.c>
#    Header always set Cross-Origin-Resource-Policy "same-origin"
#    Header always set Cross-Origin-Embedder-Policy "require-corp"
#</IfModule>

## Désactiver le JavaScript en ligne lors de l'ouverture directe des fichiers SVG ou de leur intégration avec la balise object
<FilesMatch "\.svg$">
  <IfModule mod_headers.c>
    Header always set Content-Security-Policy "script-src 'none'"
  </IfModule>
</FilesMatch>

## Ces directives sont activées uniquement si le module mod_rewrite d'Apache est activé
<IfModule mod_rewrite.c>
    RewriteEngine On

    ## Début - Règles de réécriture pour bloquer certaines exploitations courantes.
    # Si vous rencontrez des problèmes sur votre site, commentez les opérations listées
    # ci-dessous en ajoutant un # au début de la ligne.
    # Cela tente de bloquer les types d'exploitations les plus courantes `tentatives` sur Joomla!
    #
    # Bloquer tout script essayant d'utiliser base64_encode dans l'URL.
    RewriteCond %{QUERY_STRING} base64_encode[^(]*\([^)]*\) [OR]
    # Bloquer tout script incluant une balise <script> dans l'URL.
    RewriteCond %{QUERY_STRING} (<|%3C)([^s]*s)+cript.*(>|%3E) [NC,OR]
    # Bloquer tout script essayant de définir une variable PHP GLOBALS via l'URL.
    RewriteCond %{QUERY_STRING} GLOBALS(=|\[|\%[0-9A-Z]{0,2}) [OR]
    # Bloquer tout script essayant de modifier une variable _REQUEST via l'URL.
    RewriteCond %{QUERY_STRING} _REQUEST(=|\[|\%[0-9A-Z]{0,2})
    # Retourner un en-tête 403 Interdit et afficher le contenu de la page d'accueil racine
    RewriteRule .* index.php [F]
    #
    ## Fin - Règles de réécriture pour bloquer certaines exploitations courantes.

    ## Début - Redirections personnalisées
    #
    # Si vous avez besoin de rediriger certaines pages, ou d'installer une redirection canonique
    # non-www vers www (ou vice versa), placez ce code ici. Assurez-vous que ces
    # redirections utilisent la syntaxe correcte RewriteRule et les drapeaux [R=301,L].
    #
    ## Fin - Redirections personnalisées

    ##
    # Décommentez la ligne suivante si l'URL de votre serveur web
    # n'est pas directement liée aux chemins de fichiers physiques.
    # Mettez à jour votre répertoire Joomla! (juste / pour la racine).
    ##

    # RewriteBase /

    ## Début - Section SEF Joomla! core
    #
    # Correction PHP FastCGI pour l'autorisation HTTP, nécessaire pour l'application API
    RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
    # -- URLs SEF pour l'application API
    # Si le chemin demandé commence par /api, le fichier n'est pas /api/index.php
    # et la demande n'a pas déjà été réécrite en interne vers le
    # script api/index.php
    RewriteCond %{REQUEST_URI} ^/api/
    RewriteCond %{REQUEST_URI} !^/api/index\.php
    # et le chemin et fichier demandés ne correspondent pas directement à un fichier physique
    RewriteCond %{REQUEST_FILENAME} !-f
    # et le chemin et fichier demandés ne correspondent pas directement à un dossier physique
    RewriteCond %{REQUEST_FILENAME} !-d
    # réécrire en interne la demande vers le script /api/index.php
    RewriteRule .* api/index.php [L]
    # -- URLs SEF pour l'application frontend publique
    # Si le chemin et fichier demandés ne sont pas /index.php et que la demande
    # n'a pas déjà été réécrite en interne vers le script index.php
    RewriteCond %{REQUEST_URI} !^/index\.php
    # et le chemin et fichier demandés ne correspondent pas directement à un fichier physique
    RewriteCond %{REQUEST_FILENAME} !-f
    # et le chemin et fichier demandés ne correspondent pas directement à un dossier physique
    RewriteCond %{REQUEST_FILENAME} !-d
    # réécrire en interne la demande vers le script index.php
    RewriteRule .* index.php [L]
    #
    ## Fin - Section SEF Joomla! core.
</IfModule>

## Ces directives sont activées uniquement si le module mod_rewrite d'Apache est désactivé
<IfModule !mod_rewrite.c>
    <IfModule mod_alias.c>
        # Lorsque le module mod_rewrite d'Apache n'est pas disponible, nous demandons
        # une redirection temporaire de la page de démarrage vers le contrôleur frontal
        # explicitement afin que le site Web et les liens générés puissent toujours être utilisés.
        RedirectMatch 302 ^/$ /index.php/
        # RedirectTemp ne peut pas être utilisé à la place
    </IfModule>
</IfModule>

## GZIP & BROTLI
## Ces directives ne sont activées que si le module mod_headers d'Apache est activé.
## Cette section vérifiera si un fichier .gz existe et, le cas échéant, le diffusera en continu
## directement ou utiliser gzip comme solution de secours pour tout actif à la volée
## Si votre site commence à avoir un aspect étrange après avoir activé ce fichier, et que vous voyez
## ERR_CONTENT_DECODING_FAILED dans l'onglet réseau de la console de votre navigateur
## alors votre serveur compresse déjà les fichiers CSS et JS et vous n'avez pas besoin de cela
## block activé dans votre .htaccess
<IfModule mod_headers.c>
    # Servir des fichiers CSS compressés en gzip s'ils existent
    # et que le client accepte le gzip.
    RewriteCond "%{HTTP:Accept-encoding}" "gzip"
    RewriteCond "%{REQUEST_FILENAME}\.gz" -s
    RewriteRule "^(.*)\.css" "$1\.css\.gz" [QSA]

    # Servir des fichiers JS compressés en gzip s'ils existent
    # et que le client accepte le gzip.
    RewriteCond "%{HTTP:Accept-encoding}" "gzip"
    RewriteCond "%{REQUEST_FILENAME}\.gz" -s
    RewriteRule "^(.*)\.js" "$1\.js\.gz" [QSA]

    # Servir les types de contenu corrects et empêcher la double compression par mod_deflate.
    RewriteRule "\.css\.gz$" "-" [T=text/css,E=no-gzip:1,E=no-brotli:1]
    RewriteRule "\.js\.gz$" "-" [T=text/javascript,E=no-gzip:1,E=no-brotli:1]

    <FilesMatch "(\.js\.gz|\.css\.gz)$">
        # Servir le type d'encodage correct.
        Header set Content-Encoding gzip

        # Forcer les proxys à mettre en cache séparément les fichiers css/js gzippés &
        # non-gzippés.
        Header append Vary Accept-Encoding
    </FilesMatch>
</IfModule>
```

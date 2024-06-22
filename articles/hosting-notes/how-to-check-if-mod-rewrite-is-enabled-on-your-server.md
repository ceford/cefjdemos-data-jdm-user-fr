<!-- Filename: How_to_check_if_mod_rewrite_is_enabled_on_your_server / Display title: Comment vérifier si mod rewrite est activé sur votre serveur -->

De nombreux problèmes SEO se produisent du fait que l'hébergeur n'a pas
activé mod_rewrite (pour la configuration Apache) sur ses serveurs.
Souvent il vous indique que c'est le cas (alors que ce n'est pas le
cas). Vous pouvez vérifier si cela est correct ou non et si cette
réécriture provoque une erreur HTTP 500 sur le serveur.

Voici comment vérifier si mod_rewrite est activé !

**1. Activez le SEO dans votre site d'administration :**

Site -\> Configuration -\> Paramètres SEO : "Réécriture d'URL en clair
(SEF)" activé, "Réécriture au 'vol' des URL" activé. ("Ajouter un
suffixe aux URL" à votre libre arbitre).

  
**2. Renommez le fichier htaccess.txt en .htaccess :**

Ensuite ne mettre QUE les lignes suivantes dans le fichier .htaccess :

    RewriteEngine On
    Options +FollowSymLinks
    RewriteRule ^joomla\.html http://www.joomla.org/? [R=303,L]

  
**3. Puis ouvrez dans votre navigateur :**
<a href="https://www.example.com/joomla.html" class="external free"
target="_blank"
rel="nofollow noreferrer noopener">https://www.example.com/joomla.html</a>

(Remplacez www.example.com par votre propre nom de domaine dans l'URL
ci-dessus.)

Si cela vous redirige vers joomla.org alors le mod_rewrite est
fonctionnel. Si cela produit une erreur, cela signifie que mod_rewrite
n'est pas fonctionnel.

A noter : si votre site est positionné dans un répertoire tel que
"/test/" vous devez insérer les lignes suivantes dans le fichier
.htaccess à la racine :

    RewriteEngine On
    Options +FollowSymLinks
    RewriteRule ^test/joomla\.html http://www.joomla.org/? [R=303,L]

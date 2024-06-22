<!-- Filename: Enabling_Search_Engine_Friendly_(SEF)_URLs_on_Apache / Display title: Autoriser les réécriture d'URL en clair  (SEF) dans Apache. -->

  
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

Cet article concerne la réécriture d'URL en clair pour Apache, le
serveur web open-source fréquemment utilisé. La mise en oeuvre de la
réécriture d'URL en clair est également possible pour le serveur web
Microsoft IIS ː référez-vous à [Autoriser la réécriture des URL en clair
pour
IIS](https://docs.joomla.org/Enabling_Search_Engine_Friendly_(SEF)_URLs_on_IIS "Special:MyLanguage/Enabling Search Engine Friendly (SEF) URLs on IIS").

Depuis la version Joomla!
<img src="https://docs.joomla.org/images/d/da/Compat_icon_1_6.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 1.6" />, la réécriture simple d'URL en clair est
disponible par défaut. Dans les versions antérieures, il fallait
utiliser la configuration globale pour l'activer. Les instructions
ci-dessous s'appliquent toujours si vous voulez mettre en oeuvre la
réécriture d'URL Apache mod_rewrite.

## Vérifiez que .htaccess est en place

Vérifiez que votre configuration Apache autorise l'accès au fichier
.htaccess en écriture. Vous devez vous assurez que l'écriture est
possible ou le fichier dans le répertoire à la racine de Joomla! sera
ignoré ou provoquera une erreur. Dans la section du fichier de
configuration du virtual host ou dans le fichier de configuration
principal (`httpd.conf`), vous devez avoir quelque chose de similaire à
l'exemple ci-dessous autorisant la réécriture :

      AllowOverride All



      AllowOverride All Options=[an option],[an option],...

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

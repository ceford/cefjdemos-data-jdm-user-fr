<!-- Filename: Enabling_Search_Engine_Friendly_(SEF)_URLs_on_Apache / Display title: Les URL SEF sur Apache -->

## Vérifiez si .htaccess est activé

Vérifiez que votre fichier de configuration Apache autorise les overrides avec .htaccess. Vous devez vous assurer que les overrides sont activés, sinon le fichier .htaccess dans le répertoire racine de votre Joomla! sera ignoré ou provoquera une erreur. Dans la section de votre fichier de configuration de l'hôte virtuel ou dans le fichier de configuration principal (`httpd.conf`), vous devez avoir quelque chose de similaire à l'exemple ci-dessous pour activer les overrides :

```bash
<Directory "/home/user/public_html">
  AllowOverride All
</Directory>

<Directory "/path/to/htdocs">
  AllowOverride All Options=[une option],[une option],...
</Directory>
```

Il existe d'autres moyens de tester si `.htaccess` est activé si vous n'avez pas accès aux fichiers de configuration de votre site. Veuillez vous référer au [tutoriel .htaccess](http://httpd.apache.org/docs/current/howto/htaccess.html) disponible sur le site de *The Apache Software Foundation* pour plus d'informations.  

## Étape par Étape

Voici des instructions étape par étape. Veuillez les suivre dans l'ordre où elles sont présentées ici. Si une étape échoue, **ne continuez pas** jusqu'à ce que vous ayez résolu le problème.

1. Renommez le fichier `htaccess.txt` dans le dossier de base de votre Joomla! en `.htaccess`.
2. *Cette étape peut ne pas être nécessaire.* Ouvrez `.htaccess` dans un éditeur de texte. Décommentez `RewriteBase /` (supprimez le premier caractère, \#). Si Joomla est installé dans son propre dossier, entrez le nom du dossier Joomla après la barre oblique. par exemple, `RewriteBase /yourjoomlafolder`.
3. Connectez-vous à votre administration et ouvrez la Configuration globale.
4. Activez l'option **Utiliser la réécriture d'URL/mod_rewrite d'Apache** et *Enregistrez*. Cette option utilise la fonction Apache *mod_rewrite* pour éliminer la partie "index.php" de l'URL.

   Vérifiez si votre site fonctionne correctement. Vos URL devraient désormais ressembler à :

        `http://www.example.com/les-nouvelles/1-dernieres-nouvelles/1-bienvenue-a-joomla`

   Si cette option cause des erreurs, veuillez consulter [Comment vérifier si mod rewrite est activé sur votre serveur](https://docs.joomla.org/How_to_check_if_mod_rewrite_is_enabled_on_your_server).

   - S'il n'est pas activé et que vous avez accès au fichier
     `apache/conf/httpd.conf`, ouvrez ce fichier et vérifiez si la ligne
     `LoadModule rewrite_module modules/mod_rewrite.so` est décommentée.
     Si nécessaire, décommentez la ligne et redémarrez le serveur web Apache.
   - Si *mod_rewrite* ne peut pas être activé, laissez cette option désactivée. Cela n'a pas d'importance si vous laissez le fichier `.htaccess` renommé.
5. *Si vous estimez cela nécessaire*, activez **Ajouter un suffixe aux URLs** et *Enregistrez*. Cette option ajoute `.html` à la fin des URLs. Les avis divergent quant à savoir si c'est nécessaire ou même utile. Les moteurs de recherche ne semblent pas se soucier si vos URLs se terminent par `.html` ou non.
6. Ouvrez le Gestionnaire des plugins et activez le plugin **Système - SEF**. Ce plugin ajoute le support SEF aux liens dans vos articles Joomla. Il fonctionne directement sur le HTML et ne nécessite pas de balise spéciale.


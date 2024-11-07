<!-- Filename: Enabling_Search_Engine_Friendly_(SEF)_URLs_on_Nginx / Display title: URL SEF sur Nginx  -->

## Introduction

Les URLs conviviales pour les moteurs de recherche (SEF), lisibles ou propres sont des URLs qui ont du sens aussi bien pour les humains que pour les moteurs de recherche, car elles indiquent le chemin vers la page spécifique à laquelle elles renvoient. Joomla! est capable de créer et d'analyser des URLs dans n'importe quel format, y compris les URLs SEF. Cela ne dépend pas de la réécriture d'URL effectuée par le serveur web, de sorte que cela fonctionne même si Joomla! fonctionne sur un serveur autre qu'Apache avec le module mod_rewrite. Les URLs SEF suivent un certain modèle fixe, mais l'utilisateur peut définir un texte descriptif court (alias) pour chaque segment de l'URL.

En interne, la partie locale d'une URL SEF (la partie après le nom de domaine) est appelée une route. La création et le traitement des URLs SEF sont donc appelés routage, et le code correspondant est appelé un routeur.

Cet article traite des URLs SEF avec le serveur web open source populaire Nginx.

## Étapes pour les serveurs NginX¶

- Ajoutez le code suivant à la configuration de votre serveur (vhost) dans le fichier nginx.conf :

```
    # Support des URLs propres (alias URLs conviviales pour les moteurs de recherche)
    location / {
       try_files $uri $uri/ /index.php?$args;
    }
```
- Si cela ne fonctionne pas, ajoutez le code suivant à la configuration de votre serveur dans le fichier nginx.conf : (Cela a fonctionné avec nginx 1.4.6 sur Ubuntu.)
```
    server {
      ....
      location / {
      expires 1d;

      # Activer les URLs SEF de Joomla dans Nginx
      try_files $uri $uri/ /index.php?$args;
      }
      ....
    }
```
- Connectez-vous à votre interface d'administration et ouvrez la Configuration Globale
- Activez l'option **URLs conviviales pour les moteurs de recherche** et enregistrez. Cette option convertit les URLs du format natif de Joomla! au format SEF. Vérifiez que votre site fonctionne correctement. Vos URLs devraient maintenant ressembler à `http://www.example.com/index.php/the-news/1-latest-news/1-welcome-to-joomla`. Si votre site ne fonctionne pas correctement, veuillez consulter [Pourquoi votre site devient-il désordonné lorsque vous activez les URLs SEF (Search Engine Friendly)?](https://docs.joomla.org/Why_does_your_site_get_messed_up_when_you_turn_on_SEF_(Search_Engine_Friendly_URLs)%3F)
- Activez l'option **Utiliser la réécriture d'URL/mod_rewrite d'Apache** et enregistrez. Cette option utilise la fonction mod_rewrite d'Apache pour éliminer la partie *index.php* de l'URL. Vérifiez que votre site fonctionne correctement. Vos URLs devraient maintenant ressembler à `http://www.example.com/the-news/1-latest-news/1-welcome-to-joomla`. Si cette option provoque des erreurs, veuillez consulter [Comment vérifier si mod_rewrite est activé sur votre serveur](https://docs.joomla.org/How_to_check_if_mod_rewrite_is_enabled_on_your_server). S'il n'est pas activé et que vous avez accès au fichier `apache/conf/httpd.conf`, ouvrez ce fichier et vérifiez que la ligne `LoadModule rewrite_module modules/mod_rewrite.so` n'est pas commentée. Si nécessaire, décommentez la ligne et redémarrez le serveur web Apache. Si *mod_rewrite* ne peut pas être activé, laissez cette option désactivée. Peu importe si vous laissez le fichier `.htaccess` renommé.
- *Si vous jugez cela nécessaire*, activez **Ajouter un suffixe aux URLs** et *enregistrez*. Cette option ajoute `.html` à la fin des URLs. Les avis divergent quant à savoir si cela est nécessaire ou même utile. Les moteurs de recherche ne semblent pas se soucier si vos URLs se terminent par `.html` ou non.
- Ouvrez le gestionnaire de plugins et activez le plugin **System - SEF**. Ce plugin ajoute le support SEF aux liens de vos articles Joomla. Il agit directement sur le HTML et ne nécessite pas de balise spéciale.

*Traduit par openai.com*


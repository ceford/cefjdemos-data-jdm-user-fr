<!-- Filename: Robots.txt_file / Display title: Le fichier robots.txt -->

## À propos des robots

Les robots web, également connus sous les noms de crawlers, web wanderers ou spiders, sont des programmes qui parcourent le web automatiquement. Parmi de nombreuses utilisations, les moteurs de recherche les utilisent pour indexer le contenu du web.

Le fichier robots.txt met en œuvre le [protocole d'exclusion des robots](https://fr.wikipedia.org/wiki/Protocole_d%27exclusion_des_robots), ce qui permet à un administrateur de site web de définir quelles parties du site ne doivent pas être inspectées par des agents utilisateurs de robots spécifiques. Par exemple, l'accès au contenu des pages publiques est normalement autorisé, mais l'accès aux répertoires cgi, privés et temporaires qui ne doivent pas avoir de pages indexées est souvent refusé.  

## Où placer le fichier *robots.txt*

Un fichier standard *robots.txt* est inclus dans la racine de votre Joomla. Le fichier *robots.txt* doit se trouver à la racine du domaine ou du sous-domaine et doit être nommé `robots.txt`.

### Joomla dans un sous-répertoire

Un fichier robots.txt situé dans un sous-répertoire n'est pas valide. Les robots vérifient uniquement ce fichier à la racine du domaine. Si le site Joomla est installé dans un sous-répertoire tel que *example.com/joomla/*, le fichier *robots.txt* **doit** être déplacé à la racine du site à *example.com/robots.txt*.

**Remarque :** Dans le fichier robots.txt, le nom du sous-répertoire **doit** préfixer tous les chemins Joomla interdits. Par exemple, la règle d'interdiction pour le répertoire `/administrator/` **doit** être modifiée pour s'écrire `Disallow: /joomla/administrator/`.

## Contenu du *robots.txt* de Joomla

Voici le contenu d'un [fichier robots.txt standard de Joomla](https://raw.githubusercontent.com/joomla/joomla-cms/refs/heads/5.2-dev/robots.txt.dist) :

```
# Si le site Joomla est installé dans un dossier
# par exemple www.example.com/joomla/ alors le fichier robots.txt
# DOIT être déplacé à la racine du site
# par exemple www.example.com/robots.txt
# ET le nom du dossier joomla DOIT être préfixé à tous les
# chemins.
# par exemple, la règle Disallow pour le dossier /administrator/ DOIT
# être modifiée pour lire
# Disallow: /joomla/administrator/
#
# Pour plus d'informations sur la norme robots.txt, voir :
# https://www.robotstxt.org/orig.html

User-agent: *
Disallow: /administrator/
Disallow: /api/
Disallow: /bin/
Disallow: /cache/
Disallow: /cli/
Disallow: /components/
Disallow: /includes/
Disallow: /installation/
Disallow: /language/
Disallow: /layouts/
Disallow: /libraries/
Disallow: /logs/
Disallow: /modules/
Disallow: /plugins/
Disallow: /tmp/
```

## Exclusion des robots

Vous pouvez exclure des répertoires ou bloquer des robots sur votre site en ajoutant une règle **Disallow** au fichier *robots.txt*. Par exemple, pour empêcher tout robot de visiter le répertoire */tmp*, ajoutez cette règle :

    Disallow: /tmp/

Voir aussi :

- [Bloquer l'accès à votre contenu](https://support.google.com/webmasters/topic/4598466?hl=fr&amp;ref_topic=9427949) au Centre d'aide de Google.

## Vérification de la syntaxe

Pour la vérification de la syntaxe, vous pouvez utiliser un validateur pour les fichiers *robots.txt*. Essayez l'un de ceux-ci :

- [Testez votre <em>robots.txt</em> avec le testeur robots.txt](https://support.google.com/webmasters/answer/6062598) chez Google.
- [<em>robots.txt</em> Checker](http://www.searchenginepromotionhelp.com/m/robots-text-tester/robots-checker.php) par Search Engine Promotion Help.

### Informations générales

- [The Web Robots Pages](http://www.robotstxt.org/) est le site principal pour *robots.txt*.
- [A Standard for Robot Exclusion](http://www.robotstxt.org/orig.html) est la norme originale.
- [Spécifications de la balise meta robots, data-nosnippet, et X-Robots-Tag](https://developers.google.com/search/docs/advanced/robots/robots_meta_tag)

*Traduit par openai.com*


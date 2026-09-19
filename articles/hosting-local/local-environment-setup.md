<!--
{
    "source": "https://docs.joomla.org/J4.x:Setting_Up_Your_Local_Environment",
    "title": "Configuration de l\u2019environnement local",
    "description": "",
    "author": ""
}
-->

Depuis Joomla! 4, nous avons modifié le processus de développement. Il n’est plus
possible de cloner le dépôt et d’obtenir une installation Joomla utilisable.
Nous suivons les bonnes pratiques et mettons en œuvre un processus de compilation
pour le CMS.

## Guide de démarrage rapide

Les étapes de configuration de votre environnement de développement dépendent de votre
système d’exploitation. Nous ne pouvons pas rédiger de documentation pour chaque système
d’exploitation (SE) ; veuillez utiliser votre moteur de recherche préféré pour trouver un tutoriel.

### Outils nécessaires

1.  PHP - essentiellement la même version que celle nécessaire pour faire fonctionner un site Joomla, mais
    vous avez besoin de la version CLI de PHP (interface de ligne de commande). (Voir
    la page [Configuration d’un serveur LAMPP pour le développement PHP](https://docs.joomla.org/Special:MyLanguage/Configuring_a_LAMPP_server_for_PHP_development "Special:MyLanguage/Configuring a LAMPP server for PHP development").)
2.  Composer - pour gérer les dépendances PHP de Joomla. Pour obtenir de l’aide
    sur l’installation de Composer, consultez la documentation
    à <a href="https://getcomposer.org/doc/00-intro.md" class="external free"
    target="_blank"
    rel="nofollow noreferrer noopener">https://getcomposer.org/doc/00-intro.md</a>.
3.  Node.js - pour compiler les fichiers JavaScript et SASS de Joomla. Pour obtenir de l’aide
    sur l’installation de Node.js, veuillez suivre les instructions disponibles
    sur <a href="https://nodejs.org/en/" class="external free" target="_blank"
    rel="nofollow noreferrer noopener">https://nodejs.org/en/</a>. Remarque,
    vous aurez besoin de NodeJS 12 ou d’une version ultérieure pour installer Joomla.
4.  Git - pour la gestion des versions.

### Étapes de configuration de l’environnement local

1.  Cloner le dépôt
2.  Extraire la branche correspondant à la dernière version.
3.  Exécuter `composer install` (composer = gestionnaire de paquets pour PHP) depuis la racine du dépôt git. (Vous pouvez ajouter *--ignore-platform-reqs* si PHP-LDAP n’est pas installé localement et que vous n’en avez pas besoin.)
4.  Exécuter `npm ci` (npm = gestionnaire de paquets pour JavaScript, le paramètre « ci » signifie « clean install ») depuis la racine du dépôt git. (Remarque : vous devez utiliser npm 10.1.0 ou une version ultérieure pour cela. Exécutez `npm install -g npm@lts` pour mettre à niveau votre version de npm vers la version LTS.)

Les utilisateurs de Linux et d’OSX peuvent configurer l’alias bash suivant en plaçant ce qui suit dans le fichier *~/.bashrc* :

```
    alias jclean="rm -rf administrator/templates/atum/css; \
    rm -rf templates/cassiopeia/css; \
    rm -rf administrator/templates/system/css; \
    rm -rf templates/system/css; \
    rm -rf media/; \
    rm -rf node_modules/; \
    rm -rf libraries/vendor/; \
    rm -f administrator/cache/autoload_psr4.php; \
    rm -rf installation/template/css"
    alias jinstall="jclean; composer install; npm ci"
```

Cela supprimera tous les fichiers compilés de votre système et effectuera une nouvelle installation en une seule commande en appelant `jinstall` dans votre installation Joomla.

## Guide de démarrage un peu plus détaillé

Joomla est similaire à de nombreux autres outils web de nos jours. Il comporte
une grande partie en PHP et de plus en plus de code JavaScript. Bien que le
développement en PHP ne nécessite pas autant de préparation, JavaScript requiert
beaucoup d'outils autour de lui. La raison principale est que personne n'écrit
du code d'une manière comprise par tous les navigateurs, le code doit donc être
transpilé, par exemple d'ES6 vers une version compatible de JavaScript. Il en va
de même pour le CSS. Pour Joomla, nous utilisons SASS, qui sera converti en CSS
natif afin que tous les navigateurs puissent le comprendre. En contrepartie, la
mise en place d'un environnement de développement est un peu plus complexe,
mais les outils rendent le codage plus pratique. Grâce aux outils de
surveillance et au rechargement automatique du navigateur, vous pouvez voir vos
modifications en temps réel.

### PHP

Il devrait suffire d’exécuter `composer install`, car cette commande installera les
dépendances PHP enregistrées dans le fichier *composer.lock*. Vous pouvez exécuter
cette commande autant de fois que vous le souhaitez. Elle n’installera de nouveaux
paquets que lorsque le fichier *composer.lock* sera modifié. N’exécutez pas
`composer update`, car cette commande mettra à jour tous les paquets vers des
versions plus récentes et modifiera le fichier *composer.lock*.

**Remarque :** Vous devrez peut-être exécuter `composer install` avec
l’option `--ignore-platform-reqs` afin d’ignorer les exigences de plateforme
spécifiées dans Composer, par exemple si l’extension LDAP de PHP
n’est pas installée.

### Scripts Node/npm

Node.js est fourni avec un gestionnaire de paquets appelé NPM (qui fonctionne
à certains égards comme Composer). NPM possède une commande `run` et nous avons
préparé quelques scripts pour vous faciliter la tâche. Vous devez exécuter les
commandes à la racine du dépôt lorsque vous avez modifié des fichiers JS ou SASS.
Auparavant, vous deviez exécuter `npm ci` une fois pour installer les dépendances.

#### npm run build:css (jusqu’à Joomla 6.1)

Cette commande compile les fichiers SASS en fichiers CSS et crée également les fichiers minifiés.

#### npm run build:js (jusqu’à Joomla 6.1)

Cette commande compile et transpile les fichiers JavaScript au format approprié
et crée les fichiers minifiés.

#### À partir de Joomla 6.2, utilisez les commandes suivantes :

- npm run build -- -n <extension> pour reconstruire une extension spécifique
- exécutez npm run builders-list pour trouver le nom de l’extension
- npm run build -- --all pour tout reconstruire

## Problèmes possibles

Lorsque vous exécutez composer install, vous pouvez rencontrer ces erreurs

```
    Problem 1
        - Installation request for joomla/ldap 2.0.0-beta -> satisfiable by joomla/ldap[2.0.0-beta].
        - joomla/ldap 2.0.0-beta requires ext-ldap * -> the requested PHP extension ldap is missing from your system.
    Problem 2
        - Installation request for symfony/ldap v5.1.5 -> satisfiable by symfony/ldap[v5.1.5].
        - symfony/ldap v5.1.5 requires ext-ldap * -> the requested PHP extension ldap is missing from your system.
```

La solution consiste à exécuter composer install avec
l’option `--ignore-platform-reqs` afin d’ignorer les exigences de la plateforme
spécifiées dans Composer. Cela se produit notamment si l’extension LDAP de PHP
n’est pas installée.

```
    composer install --ignore-platform-reqs
```

Si vous recevez une erreur de connexion telle que celle présentée ci-dessous, supprimez
le fichier `administrator/cache/autoload_psr4.php`.

![écran d’erreur de connexion de Joomla 4](../../../en/images/hosting-local/local-environment-setup/01-joomla-4-login-error-screen.png)

*Traduit par openai.com*
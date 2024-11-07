<!-- Filename: Cache / Display title: Cache -->

## Pour les administrateurs

En tant qu'administrateur, Joomla vous offre la possibilité de mettre en cache des parties de votre site. Vous pouvez choisir de mettre en cache des pages web entières ou juste des parties de ces pages. Ce guide explique comment procéder.

Sur une page web d'un site Joomla, il y a 3 éléments qui peuvent être mis en cache :

1. La page entière elle-même – le cache de la page
2. Le rendu du composant Joomla pour cette page web – connu sous le nom de cache de la vue
3. Le rendu des modules affichés sur cette page – connu sous le nom de cache du module

Vous disposez de plusieurs paramètres de cache qui vous permettent de contrôler ce qui est mis en cache :

1. Le plugin système "Système – Cache de page"
2. La Configuration globale, onglet Système, Paramètres de cache. Ici, l'option de cache système peut être réglée sur
   - ARRÊT – Mise en cache désactivée
   - ACTIVÉ – Mise en cache conservatrice
   - ACTIVÉ – Mise en cache progressive
3. De nombreux modules disposent d'un onglet Avancé dans leurs options, où la mise en cache peut être réglée sur *Utiliser global* ou *Pas de mise en cache*

Comme décrit ci-dessous, il existe également des règles de mise en cache implémentées dans le code de Joomla, sur lesquelles vous n'avez aucun contrôle.

Vous pouvez effacer le cache via le menu Administrateur → Système → Vider le cache. En général, vous pouvez considérer que Joomla possède 3 niveaux de cache, augmentant en agressivité :

1. Mise en cache conservatrice
2. Mise en cache progressive
3. Mise en cache de la page

De plus, les développeurs Joomla peuvent utiliser des fonctionnalités de mise en cache pour stocker le résultat des requêtes de base de données, par exemple, pour augmenter la réactivité du site, mais cela est en dehors du champ des capacités de l'administrateur.

## Mise en cache des pages

Pour activer cette option, allez dans Administrateur → Extensions → Plugins. Ensuite, trouvez le plugin Système – Cache de page, et activez-le. Cela signifie que les pages du site seront désormais mises en cache et chaque fois qu'elles seront à nouveau demandées, la page mise en cache sera servie, plutôt que d'être générée par Joomla à partir des informations de la base de données. La page mise en cache continuera d'être servie jusqu'à son expiration – telle que définie par le paramètre *Durée du cache* dans Administrateur → Configuration globale → onglet Système → Paramètres de cache.

Si vous lisez cette page en guise de tutoriel et souhaitez tester la mise en cache des pages, il est préférable de définir les paramètres de cache de la Configuration globale sur :

- Gestionnaire de cache – Fichier
- Chemin vers le dossier de cache – laisser vide
- Durée du cache – 15 (la valeur par défaut de 15 minutes)
- Mise en cache spécifique à la plateforme - Non
- Cache système – OFF – Mise en cache désactivée

Pour vérifier que la mise en cache des pages est fonctionnelle, allez sur une page du site qui affiche un article. Après avoir affiché cette page, vous devriez trouver dans le système de fichiers un répertoire `cache/page` contenant un fichier avec un nom tel que `xxx-cache-page-yyy.php` où xxx et yyy sont de longues chaînes de hachage. Joomla doit stocker des pages de cache distinctes pour des URL distinctes, donc la deuxième chaîne de chiffres hexadécimaux est un hachage de l'URL de la page web du site, afin de rendre le nom de fichier unique à cette page.

Ensuite, utilisez les fonctionnalités de l'administrateur pour modifier le texte de cet article et réaffichez la page web du site. Vous devriez trouver la version mise en cache, pas votre texte modifié.

Modifier un article (ou un autre élément Joomla) n'efface pas le cache de page pour les pages web où cet article est affiché. Pour effacer le cache de la page, allez dans Administrateur → Système → Vider le cache. Cochez la case à côté du *Groupe de cache* appelé "page", et appuyez sur le bouton Supprimer. Lorsque vous réaffichez votre page web, elle devrait maintenant afficher votre texte modifié.

Si votre site a une fonction comme un panier d'achat, appliquer la mise en cache des pages posera des problèmes, car les pages doivent montrer ce que le client a déjà sélectionné, plutôt que d'afficher une page en cache qui est commune à tout le monde. Cependant, vous pouvez configurer le plugin Système - Cache de page pour exclure la mise en cache d'éléments de menu spécifiés ou d'URL et de plages d'URL spécifiées (dans l'onglet Avancé), de sorte que seules les pages réellement statiques soient mises en cache.  

## Mise en cache conservative

Avec la mise en cache conservative, vous pouvez mettre en cache le rendu de la vue des composants et le rendu de ces modules qui permettent la mise en cache. Mais notez que cela ne fonctionnera que sur les pages qui ne sont pas mises en cache en utilisant la mise en cache de page. Pour ces pages, l'ensemble de la page web est mis en cache et la mise en cache conservative n'est même pas envisagée.

Pour activer la mise en cache conservative :

1. Allez dans Administrateur → Système → Configuration globale → Onglet Système et, dans les Paramètres de cache, réglez le Cache système sur ON – mise en cache conservative.
2. Allez dans Administrateur → Extensions → Modules et sélectionnez les modules que vous souhaitez mettre en cache. Si ce module permet la mise en cache, vous devriez pouvoir le régler sous l'onglet Avancé sur

- Utiliser Global – ce module sera mis en cache (avec l'option Global maintenant réglée sur la mise en cache conservative)
- Pas de mise en cache – ce module ne sera pas mis en cache.

(Notez que le temps de cache dans la Configuration globale est en minutes mais que le temps de cache dans les paramètres du Module est en secondes.)

Pour vérifier son bon fonctionnement, allez sur votre site, **assurez-vous d'être déconnecté**, et naviguez vers une page web qui affiche un article. Vérifiez votre système de fichiers et vous devriez trouver un dossier `cache/com_content` contenant un fichier de cache.

Vous trouverez également d'autres répertoires tels que `cache/com_languages` (car l'affichage de la page implique le chargement de la langue actuelle, qui sera également mise en cache) et des répertoires relatifs à la mise en cache des modules, par exemple `cache/com_modules`. Ceux-ci résultent de l'utilisation du cache que les développeurs ont codé dans l'application Joomla.

Si vous modifiez et enregistrez cet article, puis actualisez la page du site, vous constaterez que le site affiche le texte mis à jour cette fois-ci. En effet, chaque fois que la modification est enregistrée, Joomla efface le cache pour cet article.

Cependant, vous pouvez démontrer que le cache fonctionne si vous modifiez le fichier de cache dans le répertoire `cache/com_content` en utilisant un éditeur de texte de base. Avec l'éditeur, changez une lettre dans le texte de l'article dans le fichier de cache et enregistrez le fichier. Ensuite, lorsque vous actualisez la page web, vous devriez voir le changement que vous avez apporté au fichier de cache.

Comment pouvez-vous sélectionner quelles vues de composant sont mises en cache et dans quelles circonstances ? Malheureusement, vous ne pouvez pas faire cela. Cela est déterminé par les développeurs de composants de base de Joomla et codé dans le code PHP du composant. Les critères sont différents pour chaque composant. Cependant, vous pouvez facilement découvrir quels critères sont utilisés car pour chacun des composants du site, ils sont codés dans le fichier `DisplayController.php` du site. Par exemple, au moment de cette révision (version 5 de Joomla) pour le composant Contacts, on trouve dans `components/com_contact/src/Controller/DisplayController.php`

```php
    public function display($cachable = false, $urlparams = [])
    {
        if ($this->app->getUserState('com_contact.contact.data') === null) {
            $cachable = true;
        }
```

Cela signifie que les vues associées aux contacts seront mises en cache sauf s'il y a des données de session identifiées par com_contact.contact.data – ce qui sera le cas si, dans la session utilisateur, l'utilisateur a affiché un formulaire de contact (par exemple sur une page pointée par un élément de menu de type Contacts → Contact unique).

Le fichier équivalent pour les articles `components/com_content/src/Controller/DisplayController.php` contient :

```php
    public function display($cachable = false, $urlparams = false)
    {
        $cachable = true;

        /**
         * Définir le nom et le format de vue par défaut à partir de la requête.
         * Notez que nous utilisons a_id pour éviter les collisions avec le routeur et la page de retour.
         * Le frontal est un peu plus désordonné que le backend.
         */
        $id    = $this->input->getInt('a_id');
        $vName = $this->input->getCmd('view', 'categories');
        $this->input->set('view', $vName);

        $user = $this->app->getIdentity();

        if (
            $user->get('id')
            || ($this->input->getMethod() === 'POST'
            && (($vName === 'category' && $this->input->get('layout') !== 'blog') || $vName === 'archive'))
        ) {
            $cachable = false;
        }
```

L'expression `$user->get('id')` est vraie si c'est un utilisateur connecté. Cela signifie que les articles ne sont jamais mis en cache pour les utilisateurs connectés. Les expressions suivantes concernent d'autres conditions lorsque la mise en cache n'est pas effectuée, même si l'utilisateur n'est pas connecté.

Donc, de cette façon, vous pouvez découvrir les circonstances dans lesquelles la mise en cache est effectuée, mais modifier celles-ci n'est pas conseillé. Vous pouvez également démontrer que les modules sont mis en cache en utilisant le module Joomla Breadcrumbs, en vous assurant qu'il est affiché dans une certaine position de module sur la page web, en réglant son option de mise en cache et en éditant manuellement le fichier de cache dans cache/mod_breadcrumbs.

## Mise en cache progressive

Tout comme la mise en cache conservative, la mise en cache progressive met également en cache la sortie des vues de composants et des modules. La différence fonctionnelle entre les deux est qu'avec la mise en cache progressive, **pour les utilisateurs déconnectés, tous les modules sont toujours mis en cache**. Dans ce cas, définir l'option *Pas de mise en cache* pour un module n'a aucun effet. Si l'option de stockage en cache est réglée sur *Fichier*, vous pouvez trouver le fichier de cache des modules (la sortie de tous les modules est stockée dans le même fichier) dans le répertoire `cache/com_modules`.

Pour activer la mise en cache progressive, rendez-vous sur Administrateur → Système → Configuration globale → onglet Système et dans *Paramètres de cache*, réglez *Cache Système* sur *ACTIVÉ – Mise en cache progressive*.

En ce qui concerne les conditions de mise en cache des vues des composants du noyau de Joomla, **il n'y a aucune différence entre la mise en cache conservative et progressive**. Malgré ce que vous pourriez lire sur certains sites web et les réponses aux questions sur Stack Overflow, il n'est pas vrai que la mise en cache conservative concerne lorsque l'utilisateur n'est pas connecté et la mise en cache progressive lorsque l'utilisateur est connecté.

## Résumé

Un résumé des types de mise en cache est présenté ci-dessous.

### Mise en cache de la page entière

- **Configuration** : Plugin intégré (Administrateur → Extensions → Gestionnaire de plugins → Système - Mise en cache des pages)
- **Met en cache** : chaque page entière de votre site
- **Basé sur** : URL
- **Plus d'informations** :
  - Cache optionnel par navigateur : Met également en cache sur le navigateur/ordinateur de vos visiteurs
  - Ne met en cache que les pages pour les visiteurs invités (pas pour les visiteurs connectés). Soyez prudent lors de l'utilisation de ce plugin si vous avez un site interactif où vous souhaitez servir du contenu basé sur des informations de session/cookies plutôt que sur l'URL simple. Des fonctionnalités comme un panier d'achat ne fonctionneront pas.

### Mise en cache de la vue

- **Configuration** : Configuration globale → Cache
- **Met en cache** : chaque vue d'un composant
- **Basé sur** : URL, vue, paramètres, ...
- **Plus d'informations** : Les développeurs de composants doivent inclure cela dans leur code pour que cela fonctionne. Cela n'est généralement pas fait. Le composant de contenu principal de Joomla utilise cela, mais uniquement pour les visiteurs invités de votre site, bien que cela ne soit pas obligatoire pour chaque composant.

### Mise en cache du module

- **Configuration** : Configuration globale → Cache
- **Met en cache** : chaque module (personnalisé individuellement via les paramètres avancés de chaque module)
- **Basé sur** : l'identifiant du module, les niveaux de vue de l'utilisateur et le paramètre *Itemid* dans la requête HTTP
- **Plus d'informations** : Vous devez le désactiver sur certains modules pour éviter les problèmes

### Autres systèmes de mise en cache

Si vous souhaitez explorer d'autres systèmes et possibilités de mise en cache, vous pouvez consulter les extensions tierces autour de la mise en cache.

### Moteurs ou stockages de mise en cache

- **Configuration** : Configuration globale → Cache

Ici, vous pouvez choisir quel système vous souhaitez que votre site utilise pour toute la mise en cache. Certaines options sont : APC, Eaccelorator, File, Memcache, Redis, XCache.

APC, par exemple, met également en cache votre opcode PHP.

## Pour les développeurs

<div class="alert alert-warning">
Cette section nécessite une révision pour Joomla! 4/5.
</div>

La classe **JCache** permet de réaliser de nombreux types et niveaux de cache différents. Les sous-classes suivantes sont spécifiquement conçues, mais vous pouvez ajouter les vôtres, ou utiliser la classe principale de nombreuses manières différentes.

N'oubliez pas que le premier niveau de cache rencontré remplacera tout cache plus profond. Je suppose que trop de niveaux est également contre-productif (*à vérifier toutefois*).

- **JCacheView** met en cache et retourne la sortie d'une vue donnée (en MVC). Un identifiant de cache est automatiquement généré à partir de l'URI, de la vue spécifique et de sa méthode spécifique, ou vous pouvez donner le vôtre.

Ceci peut être automatiquement effectué via la fonction d'affichage du contrôleur de base. Par exemple, dans le contrôleur de votre composant :

    class DeliciousController extends JController {
        function display() {
            parent::display(true); //true demande la mise en cache.
        }
    }

Il y a aussi quelques paramètres d'URL à prendre en compte. Consultez cette [Joomla StackExchange](http://joomla.stackexchange.com/questions/5781/how-can-i-use-joomlas-cache-with-my-components-view/7000#7000 "")

De plus, sachez que les mises à jour (comme les hits ou les comptes de visites) ne seront PAS mises à jour (sauf si vous ajoutez cela en dehors de cette méthode et donc de toute partie MVC plus profonde).

- **JCachePage** met en cache et retourne le corps de la page.
- **JCacheCallback** met en cache et retourne la sortie et les résultats des fonctions ou méthodes.

Si vous souhaitez mettre en cache des requêtes, c'est une bonne classe pour cela, comme illustré ici : Utiliser le cache pour accélérer votre code

- **JCacheOutput** met en cache et retourne la sortie.

Ceci est plutôt destiné à mettre en cache une partie spécifique du code PHP. Il fonctionne comme un tampon de sortie, mais mis en cache.

*Traduit par openai.com*


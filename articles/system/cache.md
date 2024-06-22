<!-- Filename: Cache / Display title: Cache -->

Joomla! propose différentes options de "mise en cache". Voici un aperçu
destiné aux administrateurs et développeurs du quoi, où et quand...

# Pour les administrateurs

En tant qu'administrateur, Joomlaǃ vous fournit la capacité de mettre en
cache des parties de votre site. Vous pouvez choisir de mettre en cache
des pages web entières ou juste certaines parties de ces pages. Ce guide
explique comment procéder.

Sur une page du site web Joomlaǃ, 3 choses peuvent être mises en cache :

1.  La page dans son intégralité – le cache de page
2.  Le résultat du composant Joomlaǃ affiché sur cette page web – connu
    sous le nom de cache de la vue
3.  Le résultat des modules affiché sur cette page – connu sous le nom
    de cache des modules

Vous avez plusieurs paramètres de cache qui vous permettent de contrôler
ce qui est mis en cache :

1.  Le plugin "Système - Cache de page"
2.  Dans la configuration, onglet Système, Paramètres de Cache. Voici
    les paramètres "Cache système" qui peuvent être modifiés ː
    - Cache désactivé
    - Cache conservateur
    - Cache progressif
3.  De nombreux modules proposent, dans leurs paramètres, un onglet
    Paramètres avancés dans lequel la mise en cache peut être placée à
    "Paramètres globaux" ou "Pas de cache".

Comme décrit ci-dessous, il y a des règles pour la mise en cache qui
sont implémentées dans le code Joomlaǃ et sur lesquelles vous n'avez pas
la main.

Il est possible de vider le cache à travers l'élément du menu
d'administration Système / Purger le cache.

En règle générale, vous pouvez considérer que Joomlaǃ a 3 niveaux de
cache qui augmentent en agressivité ː

1.  Cache conservateur ;
2.  Cache progressif ;
3.  Cache de la page ;

Nous allons détailler les trois en détail plus bas.

De plus, les développeurs Joomlaǃ peuvent utiliser les fonctions de
cache pour sauvegarder le résultat de requêtes depuis la base de donnée
par exemple, pour améliorer le temps de réponse du site, mais ceci est
en dehors du périmètre de ce sur quoi l'administrateur peut agir.

## Cache de la page

Pour démarrer le cache par page, allez sur le site d'administration dans
Extensions / Plug-ins et activez le plugin Système - Cache de page. Ceci
implique que les pages du site vont maintenant être mises en cache et
que, si elles sont redemandées, la page en cache sera servie plutôt
qu'elle ne soit à nouveau générée par Joomlaǃ à partir des informations
en base de donnée. Cette page en cache continuera à être servie jusqu'à
expiration - valeur définie par le paramètre Durée du cache dans
Configuration / Système / Paramètres du cache.

Si vous lisez cette page en tant que didacticiel et que vous voulez
tester le fonctionnement du cache, alors il est préférable de mettre les
paramètres de cache de la Configuration à

- Gestion du cache – Fichier
- Chemin du répertoire de cache – ne pas renseigner
- Durée du cache – 15 (par défaut 15 minutes)
- Cache système – cache désactivé

Pour vérifier que la mise en cache fonctionne, allez sur une page du
site qui affiche un article. Après avoir affiché cette page, vous devez
trouver dans le système de fichiers un répertoire `cache/page` contenant
un fichier avec un nom tel que `-cache-page-.php`. (Joomla génère des
fichiers de cache pour les différentes URLs et la seconde chaîne de
chiffres hexadécimaux est un hachage de l'URL de la page web du site,
afin de créer un nom de fichier unique à cette page).

Utilisez ensuite la fonctionnalité d'administration pour changer le
texte de cet article, et affichez à nouveau la page. Vous devez voir la
version mise en cache, et pas le texte modifié.

Modifier un article (ou tout autre élément Joomlaǃ) n'efface pas le
cache pour les pages web où l'article est affiché. Pour vider le cache,
utilisez dans l'administration du site Système / Purger le cache. Cochez
la case à côté du groupe de cache appelé "page", et appuyez sur le
bouton Supprimer. Si vous affichez à nouveau la page web, elle
s'affichera dorénavant avec le texte modifié.

Si votre site dispose d'une fonctionnalité de panier d'achat,
l'application d'un système de cache posera soucis étant donné que ces
pages doivent montrer ce que le client a déjà sélectionné plutôt que
d'afficher une page mise en cache commune à tout le monde. Cependant,
vous pouvez configurer le plugin "Système - Cache de page" pour exclure
la mise en cache des éléments de menus spécifiés ou spécifier des URLs
et des séries d'URLs (dans l'onglet Paramètres avancés), afin que seules
les pages entièrement statiques soient mises en cache.

## Cache conservateur

Grâce au Cache conservateur, vous pouvez mettre en cache la Vue des
composants et également l'affichage des modules qui autorisent la mise
en cache. Notez cependant que cela ne fonctionnera que sur les pages qui
n'utilisent pas le cache de page, car pour des pages, la page entière
sera mise en cache et du coup le cache conservateur ne sera, par
conséquent, même pas mis en œuvre.

Pour activer le Cache conservateur :

1.  Dans l'administration du site, allez à Configuration / Système et
    dans les Paramètres du cache, Mettez le paramètre Cache système à
    "Cache conservateur"
2.  Allez dans Extensions / Modules et sélectionnez les modules que vous
    souhaitez mettre en cache. Si ce module autorise la mise en cache,
    alors sous l'onglet Paramètres avancés vous pourrez mettre Mise en
    cache à

- Paramètres Globaux – ce module sera mis en cache (puisque le paramètre
  global a été mis à Cache conservateur) ;
- Pas de cache – ce module ne sera pas mis en cache ;

(Notez que la durée de mise en cache dans la configuration globale est
en minutes alors que la durée de cache dans les paramètres des modules
est en secondes.)

Pour vérifier que cela fonctionne, allez sur votre site public,
**assurez-vous que vous n'êtes pas connecté**, et naviguez sur une page
web qui affiche un article. Vérifiez votre système de fichier et vous
devriez trouver un répertoire `cache/com_content` contenant un fichier
de cache.

Vous devriez également trouver d'autres répertoires tels que
`cache/com_languages` (l'affichage d'une page implique effectivement le
chargement de la langue courante, et ceci sera également mis en cache)
et également des répertoires relatifs au cache des modules, i.e.
`cache/com_modules`. Ceci provient de l'utilisation du cache que les
développeurs ont codé au sein de l'application Joomlaǃ.

Si vous éditez, modifiez et enregistrez cet article, puis rafraîchissez
la page de cet article sur le site, vous verrez que le site affichera le
texte mis à jour cette fois. Ceci se produit car, lors de
l'enregistrement de la modification, Joomlaǃ efface le cache de cet
article.

Cependant, vous pouvez vérifiez que le cache fonctionne en éditant le
fichier de cache dans le répertoire `cache/com_content` avec un simple
éditeur de texte. Avec l'éditeur, changez une lettre dans le texte de
l'article du fichier cache et enregistrez le. En rafraîchissant la page
de l'article sur le site, vous verrez la modification que vous avez
faite dans le fichier de cache.

Comment sélectionnez les vues de composants qui vont être mises en cache
et dans quelles circonstances ? Malheureusement, ceci ne peut pas être
fait. Ceci a été défini par les développeurs des composants du noyau de
Joomlaǃ et écrit dans le code php du composant. Les critères sont
différents pour chaque composant. Cependant, vous pouvez aisément savoir
quels critères ont été utilisés car, pour chaque composant du site, ils
sont codés dans le fichier du site `controller.php`. Par exemple, au
moment ou j'écris (version Joomlaǃ 3.9.2), nous trouvons trouver pour le
composant des contacts `components/com_contact/controller.php`

    if (JFactory::getApplication()->getUserState('com_contact.contact.data') === null)
    {
        $cachable = true;
    }

Ceci signifie que les vues associées aux contacts seront mises en cache
à moins qu'il y ait une donnée de session saisie dans
com_contact.contact.data – ce qui sera le cas si dans la session
utilisateur, l'utilisateur a affiché un formulaire de contact (i.e. dans
une page pointée par un élément de menu de type Fiches de contact /
Contact).

Le fichier équivalent pour les articles
`components/com_content/controller.php` contient :

    $cachable = true;
    if ($user->get('id') || ($this->input->getMethod() === 'POST' && (($vName === 'category' && $this->input->get('layout') !== 'blog') || $vName === 'archive' )))
    {
        $cachable = false;
    }

L'expression `$user->get('id')` est vraie si l'utilisateur est connecté,
donc ceci signifie que les articles ne sont jamais mis en cache pour les
utilisateurs connectés. Les expressions suivantes se rapportent à
d'autres conditions où la mise en cache ne sera pas effectuée, même si
l'utilisateur n'est pas connecté.

Ainsi, de cette manière, vous pouvez connaître les circonstances dans
lesquelles la mise en case est effectuée, mais il n'est pas conseillé de
modifier cela.

Vous pouvez aussi savoir que les modules sont mis en cache en utilisant
les modules du fil d’Ariane de Joomlaǃ, en s'assurant qu'ils sont
affichés dans des positions de module sur la page du site et en
paramétrant les options de mise en cache puis en éditant manuellement le
fichier de cache cache/mod_breadcrumbs.

## Cache progressif

Comme pour le cache conservateur, le cache progressif met également en
cache l'affichage des vues composants et des modules. La différence
fonctionnelle entre les deux est qu'avec le cache progressif, **tous les
modules sont toujours mis en cache pour les utilisateurs déconnectés**.
Dans le cas de ce paramétrage, la valeur "Pas de cache" pour les modules
n'a pas d'effet. Si l'option de stockage de la mise en cache est
Fichier, alors vous pouvez trouver les fichiers de mise en cache des
modules dans le répertoire `cache/com_modules` (la mise en cache de tous
les modules se fait dans un seul fichier commun à tous).

Pour activer le cache progressif, allez dans l'administration dans
Configuration / Système et mettez le paramètre Cache système à "Cache
progressif".

Concernant les conditions de mise en cache des vues des composants du
noyau de Joomlaǃ **il n'y a pas de différence entre le cache
conservateur et progressif**. Malgré ce que vous pouvez lire sur
certains sites et des réponses aux questions sur le débordement de pile,
il n'est pas vrai que le cache conservateur s'applique aux utilisateurs
non connectés et le cache progressif aux utilisateurs connectés.

## Résumé

Un résumé des types de mises en cache est donné ci-dessous.

### Cache de page

- **Configuration** : Plugin intégré (Extensions -\> Gestionnaire de
  plug-in -\> Système - Cache de page)
- **Mise en cache** : chaque page complète du site
- **Basé sur** : URL
- **Information complémentaire** :
  - Cache facultatif du navigateur : Met également en cache le
    navigateur/ordinateur du visiteur du site.
  - Met uniquement en cache les pages des invités (pas les pages des
    utilisateurs connectés). Attention à l'utilisation de ce plugin si
    vous avez un site interactif où vous souhaitez délivrer un contenu
    basé sur la session ou les cookies plutôt que sur l'URL seulement.
    Les fonctionnalités telles que le panier d'achat ne vont pas
    fonctionner.

### Cache de vue

- **Configuration** : Configuration-\>Cache
- **Mise en cache** : chaque vue d'un composant
- **Basé sur** : URL, vue, paramètres...
- **Plus d'infos** : les développeurs de composants doivent l'inclure
  dans leur code pour qu'il fonctionne. La plupart du temps, ce n'est
  pas le cas. Le composant principal de contenu pour Joomla! l'utilise,
  mais uniquement pour les visiteurs de votre site car il n'est pas
  obligatoire pour chacun des composants.

### Mise en cache de modules

- **Configuration** : Configuration-\>Cache
- **Mise en cache** : chaque module (individuellement personnalisé via
  les paramètres avancés de modules)
- **Basé sur** : l'id du module, les niveaux de vue de l'utilisateur et
  le paramètres itemid dans la requête HTTP
- **Plus d'infos** : vous devez le désactiver sur certains modules afin
  d'éviter certains problèmes.

### Plus de cache

Si vous souhaitez voir d'autres systèmes et possibilités de cache,
consultez les extensions tierces traitant de la mise en cache.

### Mise en cache des moteurs ou stockages

- **Configuration**: Configuration-\>Cache

Vous pouvez choisir le système que vous souhaitez utiliser sur votre
site pour tous les caches. Les options actuelles sont : APC,
Eaccelorator, File, Memcache, Redis, XCache.

APC par exemple met également en cache votre opcode php.

# Pour les développeurs

La classe **JCache** permet différentes sortes et niveaux de cache. Les
sous-classes suivantes ont été créées spécifiquement, mais vous pouvez
ajouter la votre, ou utiliser la classe principale de différentes
façons.

N'oubliez pas que le premier niveau de cache rencontré va remplacé toute
mise en cache plus profonde. Je suppose qu'un trop grand nombre de
niveaux est également contre-productif.

- **JCacheView** met en cache et retourne la sortie d'une vue donnée (en
  MVC). Un identifiant de cache est automatiquement généré à partir de
  l'URI, une vue spécifique et sa méthode spécifique, ou vous pouvez
  donner le votre.

Cela peut être réalisé automatiquement via la fonction d'affichage de
base du contrôleur. Par exemple, dans le contrôleur de votre composant :

    class DeliciousController extends JController {
        function display() {
            parent::display(true); //true asks for caching.
        }
    }

Il existe également des paramètres d'url (urlparams) à considérer.
Consultez <a
href="http://joomla.stackexchange.com/questions/5781/how-can-i-use-joomlas-cache-with-my-components-view/7000#7000"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">"joomla stack"</a>.

Egalement, soyez conscient que toute mise à jour (comme les hits ou
visites) ne sera PAS mise à jour (sauf si vous ajoutez cela à
l'extérieur de cette méthode et donc plus en profondeur dans la partie
MVC.)

- **JCachePage** met en cache et retourne le corps de la page.
- **JCacheCallback** met en cache et retourne la sortie et les résultats
  des fonctions ou des méthodes.

Si vous souhaitez mettre en cache des requêtes, c'est la classe pour le
faire comme illustré ici : [Utiliser la mise en cache pour accélérer
votre
code](https://docs.joomla.org/Using_caching_to_speed_up_your_code "Special:MyLanguage/Using caching to speed up your code").

- **JCacheOutput** met en cache et retourne la sortie.

Plutôt utilisé pour la mise en cache d'une partie spécifique du code
php. Il agit comme un tampon de sortie, mais mis en cache.

## Références

- <a
  href="http://forum.joomla.org/viewtopic.php?f=428&amp;t=326990&amp;start=0"
  class="external text" target="_blank" rel="noreferrer noopener">Better
  performance with joomla System Cache plugin (Joomla! Forum)</a> (en
  anglais).
- <a href="https://api.joomla.org/cms-3/classes/JCache.html"
  class="external text" target="_blank"
  rel="noreferrer noopener">JCache</a>
- <a
  href="http://joomla.stackexchange.com/questions/5781/how-can-i-use-joomlas-cache-with-my-components-view/7000#7000"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">How can I use Joomla's Cache with my
  components view? (joomla stackexchange beta)</a> (en anglais).

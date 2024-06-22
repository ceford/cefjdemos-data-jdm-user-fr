<!-- Filename: Potential_backward_compatibility_issues_in_Joomla_4 / Display title: Éventuelles anomalies  de rétro-compatibilité dans Joomla! 4 -->

<img
src="https://docs.joomla.org/images/thumb/e/e5/Quill_icon.png/30px-Quill_icon.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/e/e5/Quill_icon.png/45px-Quill_icon.png 1.5x, https://docs.joomla.org/images/thumb/e/e5/Quill_icon.png/60px-Quill_icon.png 2x"
data-file-width="71" data-file-height="59" width="30" height="25"
alt="Quill icon.png" />Content is Incomplete

This article or section **is incomplete, which means it may be lacking
information.** You are welcome to assist in its completion by editing it
as well. If this article or section <a
href="https://docs.joomla.org//docs.joomla.org/index.php?title=Potential_backward_compatibility_issues_in_Joomla_4/fr&amp;action=history"
class="external text" target="_blank" rel="noreferrer noopener"></a> <a
href="https://docs.joomla.org//docs.joomla.org/index.php?title=Potential_backward_compatibility_issues_in_Joomla_4/fr&amp;action=history"
class="external text" target="_blank" rel="noreferrer noopener">has not
been edited in several days</a>, please consider helping complete the
content.
<span class="small">This article was <a
href="https://docs.joomla.org//docs.joomla.org/index.php?title=Potential_backward_compatibility_issues_in_Joomla_4/fr&amp;diff=cur"
class="external text" target="_blank" rel="noreferrer noopener">last
edited</a> by
FuzzyBot
(talk\|
contribs
5 months ago. *(<a
href="https://docs.joomla.org//docs.joomla.org/index.php?title=Potential_backward_compatibility_issues_in_Joomla_4/fr&amp;action=purge"
class="external text" target="_blank"
rel="noreferrer noopener">Purge</a>)*</span>

Ce document suit les problèmes potentiels de rétrocompatibilité pour
Joomla! 4. Sont listés des problèmes qui peuvent potentiellement briser
des extensions.

La base de cette comparaison est Joomla! 3.10.

## Évolution des configurations minimales du système

Les configurations minimales du système doivent être mises à jour
ainsi :

- PHP 7.2.5
- MySQL 5.6
- PostgreSQL 11.0
- le support de SQL Server ne fait plus partie de la configuration.

### Extension PHP MySQL

- Joomla! ne supporte plus l'utilisation des pilotes PHP ext/mysql (qui
  ont été retirés de la version PHP 7.0). Joomla! va automatiquement
  essayer d'utiliser l'extension mysqli (disponible depuis PHP 5.3) ou
  le pilote mysql PDO (disponible depuis PHP 5.3 également) sinon
  Joomla! échouera à créer la connexion à la base de données.
- Le mode strict a été activé. Les indicateurs suivants sont maintenant
  actifs par défaut dans Joomla 4 et vous devrez peut-être mettre à jour
  vos requêtes de base de données en conséquence. Cela nous aidera pour
  les futures mises à jour de la version de MySQL et s'aligne également
  plus étroitement avec Postgres pour permettre une compatibilité plus
  facile avec les requêtes dans les deux langues.
    'STRICT_TRANS_TABLES',
    'ERROR_FOR_DIVISION_BY_ZERO',
    'NO_AUTO_CREATE_USER',
    'NO_ENGINE_SUBSTITUTION',

En conséquence, Joomla 4 n'utilisera que des dates **NULL** par défaut.
L'utilisation de la *date par défaut non valide* de 0000-00-00 00:00:00
dans Joomla 4 est déconseillée.

### Extension PHP Postgres

- Joomla! ne supporte plus l'utilisation des pilotes PHP ext/pgsql.
  Joomla! va automatiquement essayer d'utiliser le pilote PostgreSQL PDO
  (disponible depuis PHP 5.3 et Joomla! 3.9). Sinon, Joomla! échouera à
  créer une connexion à la base de données en cas de base de données
  Postgres.

### Extension PHP GMP

Ceci est nécessaire pour utiliser la fonction  WebAuthn Passwordless
Login.
Notez que l'extension PHP GMP est installée par défaut sur la majorité
des sites d'hébergement. La fonction  WebAuthn Passwordless
Login.
Le plugin système est activé par défaut dans Joomla 4 sur les sites
https.

### Extension PHP mcrypt

Ceci est nécessaire pour utiliser la classe
Joomla\CMS\Crypt\Cipher\CrytoCipher et son alias JCryptCipherCrypto.

## Librairies du CMS

Les changements suivant ont été faits dans les librairies CMS de Joomla!
(ceci est essentiellement du code qui a été trouvé dans le répertoire
\`libraries/cms\` de Joomla! 3.7 et antérieur).

### Installeur

- La recherche d'installations de plugins ne se fera plus pour les
  fichiers xml dans le répertoire des plugins de mises en page de
  Joomla! 1.5 ;
- Dans la version 3.x, seuls les scripts des plugins avaient la méthode
  avant lancement de la désinstallation appelée et aucun ne mettaient à
  disposition une méthode après désinstallation. Tous ces branchements
  sont disponibles en version 4.0 lors de la désinstallation d'une
  extension. Si actuellement vous pensiez que les méthodes pré et post
  étaient uniquement appelées dans le contexte de l'installation ou de
  la mise à jour, cette logique est maintenant incorrecte et vous devez
  utiliser le chemin d'installation (transmis en tant que paramètre de
  la méthode).
- Lors de la désinstallation du plugin, la fonction de désinstallation
  dans le script de l'extension et maintenant activé avant l'activation
  des requêtes SQL (ce qui est maintenant cohérent avec les autres types
  d'extensions).

#### Classes supprimées

Les classes suivantes ont été retirées de Joomla! 4.0 :

- JInstallerComponent (utilisez plutôt JInstallerAdapterComponent)
- JInstallerFile (utilisez plutôt JInstallerAdapterFile)
- JInstallerLanguage (utilisez plutôt JInstallerAdapterLanguage)
- JInstallerLibrary (utilisez plutôt JInstallerAdapterLibrary)
- JInstallerModule (utilisez plutôt JInstallerAdapterModule)
- JInstallerPackage (utilisez plutôt JInstallerAdapterPackage)
- JInstallerPlugin (utilisez plutôt JInstallerAdapterPlugin)
- JInstallerTemplate (utilisez plutôt JInstallerAdapterTemplate)
- JSubMenuHelper (utilisez plutôt JHtmlSidebar ; à noter que
  contrairement à JSubMenuHelper, ceci demande l'ajout d'un emplacement
  dans le modèle de votre vue)

#### Héritage de JInstallerAdapter

JInstallerAdapter n'hérite plus de JAdapterInstance et par conséquent
plus de JObject.

Les adaptateurs d'installeur personnalisés doivent maintenant être auto
chargeables.

### Menu

#### JMenu devient une classe abstraite

JMenu devient une classe abstraite. Les sous-classes de JMenu doivent
maintenant implémenter une méthode de chargement.

#### Suppression de la possibilité d'une inclusion manuelle

La possibilité dans JMenu::getInstance() d'inclure manuellement un
fichier depuis le chemin de l'application includes/menu.php a été
supprimée. La sous-classe JMenu doit maintenant s'auto-charger.

#### JMenuItem

- Vous ne pouvez plus récupérer la propriété des paramètres directement
  depuis JMenuItem. Utilisez plutôt la méthode getParams() (disponible
  depuis Joomla 3.7)
- JMenuItem::set et JMenuItem::get ont été supprimés. Les propriétés
  doivent être explicitement nommées
- Il existe maintenant une classe AdministratorMenuItem qui s'étend à
  partir de MenuItem et qui contient des propriétés publiques
  supplémentaires utilisées pour l'élément de menu Administrator.

### Pagination

- Les fonctions de pagination magique *pagination_item_active*,
  *pagination_item_inactive* ont été supprimées. Utilisez plutôt
  joomla.pagination.link du JLayout
- La fonction de pagination magique *pagination_list_render* est
  obsolète. Utilisez plutôt la fonction JLayout joomla.pagination.list

### Chemin

#### Suppression de la possibilité d'une inclusion manuelle

La possibilité dans JPathway::getInstance() d'inclure manuellement un
fichier depuis le chemin de l'application includes/pathway.php a été
supprimée. La sous-classe JPathway doit maintenant s'auto-charger.

### Routeur

#### Suppression de la possibilité d'une inclusion manuelle

La possibilité dans JRouter::getInstance() d'inclure manuellement un
fichier depuis le chemin de l'application includes/router.php a été
supprimée. La sous-classe JRouter doit maintenant s'auto-charger.

#### Modification des méthodes de signature

attachBuildRule et attachParseRule sont maintenant typés (typehint) pour
être appelables.

### JVersion

L'accès aux constantes de classe de JVersion en tant que propriétés de
classe n'est plus supporté. Les constantes avaient été introduites avec
Joomla! 3.5 pour éviter l'édition des paramètres des anciennes classes.

Les constantes obsolètes suivantes ont été supprimées :

- JVersion::RELEASE
- JVersion::DEV_LEVEL
- JVersion::BUILD

### JHtml

- La fonction de déclaration dans JHtml est maintenant typée (typehint)
  pour être appelable. Les sous-classes de JHtml vont devoir maintenant
  correspondre à cette signature (à noter que ceci était déjà requis au
  niveau du code des fonctions).
- JHtml::\_ n'autorise plus l'appel de méthodes non publiques de JHtml ;
- JHtml::\_ est maintenant une méthode finale (il n'est plus possible de
  la surcharger en faisant une sous-classe de JHtml) et sa signature a
  évolué pour bénéficier des avantages des fonctionnalités modernes de
  PHP (éléments typés scalaires et variadiques) ;
- JHtmlBootstrap::modal a été supprimé. Utilisez
  JHtmlBootstrap::renderModal
- JHtmlSortablelist::sortable a été déprécié en faveur de
  JHtmlDraggablelist::draggable - l'ancienne méthode agit comme un proxy
  de la nouvelle méthode actuellement pour faciliter la suppression de
  jQuery UI de Joomla Core. Tous les actifs media relatifs à la mise en
  œuvre originale de jQuery UI ont été supprimés.
- JHtmlBatch a été supprimé car tout le code avait été déplacé vers les
  mises en page pour les modifications de templates. Utilisez les
  JLayouts directement dans votre code.

### Mise à jour

- Nous avons supprimé la gestion des clients entiers dépréciés de la
  classe d'adaptateur d'extension de mise à jour. Veuillez utiliser
  **site** et **administrateur** maintenant et non les valeurs entières
  **0** / **1**.

## Plateforme

Les changements suivant ont été effectués sur les librairies de la
plateforme Joomla! (ceci concerne essentiellement du code des
répertoires \`libraries/joomla\` ou \`libraries/legacy\` de Joomla! 3).

### Accès

- JAccess::\$assetPermissionsById and JAccess::\$assetPermissionsByName
  et JAccess::\$assetPermissionsByName et
  JAccess::preloadPermissionsParentIdMapping ont été supprimées sans
  être remplacées. Depuis la version 3.6, nous utilisons d'autres
  méthodes et propriétés de classe pour optimiser le chargement des
  actifs. Consultez le
  <a href="https://github.com/joomla/joomla-cms/pull/12850"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Demande d'extraction de corrections
  de bogues et d'optimisations de JAccess</a> pour connaître les raisons
  de cette dégradation.
- JAccess::getActions a été supprimé. Utilisez plutôt
  JAccess::getActionsFromFile ou JAccess::getActionsFromData.

### Application

#### Classes supprimées

Les classes suivantes ont été supprimées de Joomla! 4.0 :

- JApplicationWebRouter (utilisez plutôt le paquet \`joomla/router\`)
- JApplicationWebRouterBase (utilisez plutôt le paquet
  \`joomla/router\`)
- JApplicationWebRouterRest (utilisez plutôt le paquet
  \`joomla/router\`)

Toutes les références à JSite et JAdministrator ont été supprimées (ce
n'étaient que des "alias de classe" depuis Joomla 3.2)

#### Classes obsolètes

Les classes suivantes ont été dépréciées et seront retirées dans la
version Joomla! 5.0 :

- JApplicationBase (utilisez plutôt
  Joomla\Application\AbstractApplication)

#### Modifications des classes CLI/Web

Les classes JApplicationCli et JApplicationWeb ont été recomposées pour
être étendues depuis le paquet de la structure de l'application. Ceci
casse les vérifications de types pour un objet JApplicationBase. Pour la
compatibilité future, il est recommandé de vérifier si les classes de
l'application sont une instance de
Joomla\Application\AbstractApplication (JApplicationBase a étendu cette
classe depuis Joomla! 3.4).

De plus, ces deux classes sont maintenant abstraites. Les développeurs
implémentant ces classes doivent fournir une méthode \`doExecute\` avec
leur logique d'application.

La méthode registerEvent est maintenant typée (typehint) pour être
appelable pour le paramètre \$handler.

Les applications qui veulent à la fois supporter les applications Web et
CLI doivent maintenant être typées (typehint) avec
\Joomla\CMS\Application\\ CMSApplicationInterface - ceci inclut les
méthodes communes (certaines d'entre elles dans Joomla 3.x étaient
seulement présentes dans la classe JApplicationCms) qui peuvent être
utilisées pour tout code. Il est fortement recommandé dans les
applications personnalisées (en particulier les applications CLI)
d'implémenter cette interface pour faciliter les vérifications de
compatibilité ; simultanément, tout typehint doit utiliser l'interface
plutôt qu'une classe réelle.

##### JApplicationCli

- Ancien : JApplicationCli **→** JApplicationBase **→** 
  Joomla\Application\AbstractApplication
- Nouveau :
  JApplicationCli **→** Joomla\Application\AbstractCliApplication **→** 
  Joomla\Application\AbstractApplication

##### JApplicationWeb

- Ancien : JApplicationWeb **→** JApplicationBase **→** 
  Joomla\Application\AbstractApplication
- Nouveau :
  JApplicationWeb **→** Joomla\Application\AbstractWebApplication **→** 
  Joomla\Application\AbstractApplication
- Les manières obsolètes d'appeler JApplicationWeb::redirect ont été
  supprimées :
  - avec un message et des paramètres messageType (appel de
    enqueueMessage séparément) ;
  - passer une valeur true/false en tant que 2ème/3ème paramètres au
    lieu du code de redirection va générer un InvalidArgumentException
    au lieu de l'état par défaut 303 ;
- JApplicationWeb::\$singleValueResponseHeaders a été supprimé parce que
  le Framework de l'application va utiliser en interne les objets PSR-7
  Response et la version 2.0. Ceci modifie la manière dont les données
  headers sont stockées bien que ce soit toujours un tableau
  multi-dimensionnel avec chaque clé de niveau supérieur comme noms de
  header et la valeur étant un tableau contenant toutes les valeurs de
  ce header.

##### CMSApplication

- Les propriétés de classe \$\_clientId, \$\_messageQueue et \$\_name
  ont été renommées pour supprimer le tiret bas.
- Implémente dorénavant CMSApplicationInterface ;
- Si il y a une erreur en récupérant l'objet de chemin, routage ou menu
  en utilisant les méthodes respectives, l'exception va dorénavant se
  manifester plutôt que la méthode génère l'exception en silence et
  retourne null ;
- CMSApplication::getInstance va de plus dorénavant essayer de charger
  l'objet utilisateur (en utilisant la fonction loadidentity) ;
- CMSApplication::isSite et CMSApplication::isAdmin ont été retirés car
  avec l'ajout de ConsoleApplication et ApiApplication cela pouvait
  conduire à des résultats trompeurs. Utilisez, s'il vous plaît,
  CMSApplication::isClient (disponible depuis la version
  <img src="https://docs.joomla.org/images/a/a7/Compat_icon_3_7.png"
  decoding="async" data-file-width="40" data-file-height="17" width="40"
  height="17" alt="Joomla 3.7" />). Pour plus d'informations, lisez,
  s'il vous plaît, Découvrez sur quel client le code de votre extension
  s'exécute.

##### JApplicationSite

Les propriétés de classe \$\_language_filter et \$\_detect_browser ont
été renommées pour supprimer le tiret bas.

La méthode obsolète JApplicationSite::getPageParameters a été supprimée
au profit de son alias JApplicationSite::getParams.

##### JApplicationHelper

JApplicationHelper::parseXMLLangMetaFile a été supprimée sans
remplacement.

### Archive

- Le paquet d'archive à été supprimé au profit de paquet d'archive du
  framework. A noter que l'API devrait rester inchangée ;
- Le gestion des erreurs utilise dorénavant les Exceptions plutôt que
  JError ;

### Client

\Joomla\CMS\Client\ClientWrapper a été supprimé. Utilisez les méthodes
statiques dans \Joomla\CMS\Client\ClientHelper

### Crypt

- JCrypt::hasStrongPasswordSupport a été supprimé sans remplacement car
  toutes les versions de PHP correspondant à Joomla 4 supportent le
  hachage de mot de passe fort.

#### Classes supprimées

Les chiffrages suivants ont été retirés de Joomla! 4.0 ;:

- JCryptCipher3Des
- JCryptCipherBlowfish
- JCryptCipherMcrypt
- JCryptCipherRijndael256
- JCryptCipherSimple

Ils ont été retirés sans remplaçant. Utilisez JCryptCipherCrypto.

#### Méthodes supprimées

- JCrypt::hasStrongPasswordSupport a été retiré sans remplaçant (ceci
  tentait de détecter les 'bcrypt polyfills' de l'hôte linux mais
  retournait toujours true depuis l'utilisation de PHP 5.3.10 dans
  Joomla! 3.3) ;

### Cache

- JCacheController::get requiert maintenant un call. De ce fait,
  JCacheControllerCallback::call a été supprimé.
- JCacheStorage::test a été supprimé. Utilisez
  JCacheStorage::isSupported dorénavant
- Les moteurs de stockage ne sont plus chargés manuellement et sont
  maintenant chargés automatiquement
- JCacheControllerOutput::start et JCacheControllerOutput::end ont été
  retirés sans remplaçant
- Suppression du stockage CacheLite étant donné qu'il n'est pas
  compatible avec PHP7 (qui est la version minimale requise)
- Le gestion des erreurs utilise dorénavant les Exceptions plutôt que
  JError ;

### Composant

- \Joomla\CMS\Component\ComponentRecord n'est plus une extension de
  JObject

### Document

#### Changement d'héritage

Les classes suivantes ont changé d'héritage :

- JDocumentError (qui hérite maintenant de
  \Joomla\Cms\Document\HtmlDocument au lieu de
  \Joomla\Cms\Document\Document)

A noter que, comme résultat de ce changement, le rendu d'une page
d'erreur réinitialise l'objet document Joomla\CMS\Factory::\$document,
la raison étant que nous voulons partir d'un rendu vierge du document
pour travailler; si la page d'erreur est déclenchée, nous ne sommes par
intéressés par les métadonnées que votre document a initialisées, ou les
médias ajouté par un module défaillant, ou n'importe quel plugin
s'affichant à l'écran. Nous voulons un environnement propre pour
afficher la page d'erreur en affichant uniquement les données chargées
par la page d'erreur.

#### Rendus

- Afin d'être conforme avec les spécifications des fils RSS,
  JDocumentRendererFeedRss autorise maintenant l'élément lastBuildDate à
  être configuré en utilisant la propriété de classe
  JDocumentFeed::\$lastBuildDate lorsqu'un fil d'actualité est affiché.
  La valeur par défaut est l'heure courante, comme c'est le cas avec
  Joomla! 3.x et antérieur, cependant l'heure peut être modifiée en
  changeant la propriété de classe avec un objet JDate configuré avec le
  timestamp souhaité.
- Il y a dorénavant un RendererInterface que tous les Renderers doivent
  implémenter.
- JDocumentRenderer est dorénavant une classe abstraite qui implémente
  RendererInterface.
- En alternative à , vous pouvez dorénavant charger individuellement
  pour les metadata, pour le CSS et pour le javascript. Le but de cela
  est de permettre optionnellement aux utilisateurs de placer tous les
  javascript en fin du document HTML dans leur modèle de site.

#### JDocumentFeed

Le type de propriété de JDocumentFeed::\$lastBuildDate a été modifié
d'un format de string à un objet JDate. La propriété était par le passé
inutilisée dans le noyau API Joomla mais des extensions peuvent l'avoir
utilisée.

### Base de données

- Ce paquet à été remplacé par le paquet Joomla Framework Database.
- Le mode debug a été retravaillé (voyez les documents du framework pour
  plus d'information
  <a href="https://github.com/joomla-framework/database"
  class="external autonumber" target="_blank"
  rel="nofollow noreferrer noopener">[1]</a>)

### Factory

- Factory::getApplication ne prend plus d'arguments. Ceci était trompeur
  vu qu'elle retournait systématiquement l'application active après le
  premier appel dans le bootstrap, quels que soient les arguments qui
  étaient passés à la fonction.
- Factory::getXml a été retiré avec JXMLElement. Utilisez dorénavant
  SimpleXMLElement directement.
- Factory::getEditor a été retiré. Utilisez dorénavant
  JEditor::getInstance.
- Factory:: getUri a été retiré. Utilisez dorénavant Uri::getInstance().

### Environnement

- JBrowser::isSSLConnection has been removed. Use
  JApplicationCms::isSSLConnection (available since Joomla 3.2)

### Système de fichiers

- Les classes surchargeant le système de fichiers ont été retirées.
  Continuez à utiliser les méthodes statiques d'origine.

### Filter

- JFilterInput::\_remove a été supprimé en faveur de
  JFilterInput::remove
- JFilterInput::\_cleanTags a été supprimé en faveur de
  JFilterInput::cleanTags
- JFilterInput::\_cleanAttributes a été supprimé en faveur de
  JFilterInput::cleanAttributes
- JFilterInput::\_decode a été supprimé en faveur de
  JFilterInput::decode
- JFilterInput::\_escapeAttributeValues a été supprimé en faveur de
  JFilterInput::escapeAttributeValues
- JFilterInput::\_stripCSSExpressions a été supprimé en faveur de
  JFilterInput::stripCSSExpressions

Toutes les dépréciations et les suppressions susmentionnées doivent
permettre le regroupement de la classe avec la classe parente du
framework.

### Form

- Les répertoires libraries/joomla/form/fields et
  libraries/joomla/form/rules ne sont plus enregistrés pour trouver les
  formulaires de classes ; Les formulaires de classes doivent dorénavant
  être auto-chargés.
- Deux nouvelles propriétés ajoutent addfieldprefix qui déclarent un
  préfixe d'espace-nom (namespace) pour les extensions (dont le but est
  d'être utilisé pour remplacer addfieldpath). Pour un exemple d'usage,
  voyez, s'il vous plaît,
  <a href="https://github.com/joomla/joomla-cms/pull/16419"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">ce Github PR</a>
- JForm::getControlGroup a été retiré. Utilisez l'alias
  JForm::renderField (disponible depuis Joomlaǃ 3.2.3)
- JForm::getControlGroups a été retiré. Utilisez l'alias
  JForm::renderFieldset (disonible depuis Joomlaǃ 3.2.3)
- Lors du rendu d'un champ en utilisant l'option étiquette cachée dans
  JForm - elle ne cache désormais que l'étiquette de l'interface
  utilisateur - le html est toujours rendu avec la classe sr uniquement
  à des fins d'accessibilité pour les lecteurs d'écran.
- JFormFieldUsergroup a été retiré. Utilisez dorénavant
  Joomla\CMS\Form\Field\UsergrouplistField (disponible depuis la version
  Joomlaǃ 3.2).
- La classe Form a supprimé les méthodes protégées filterField() et
  validateField(). Cela brisera toute classe de formulaire personnalisée
  qui étend le formulaire de base et utilisera ces méthodes. Elle a été
  remplacée par un filtrage au niveau du champ (voir
  <a href="https://github.com/joomla/joomla-cms/pull/12414"
  class="external free" target="_blank"
  rel="nofollow noreferrer noopener">https://github.com/joomla/joomla-cms/pull/12414</a>
  pour plus d'informations)

#### Fields

- Les propriétés des filtres JFormFieldFilelist et JFormFieldFolderList
  ont été renommées respectivement en `fileFilter` et `folderFilter`
  (afin de permettre l'utilisation de l'attribut de filtre Joomla
  habituel sur les valeurs de retour)
- JFormPredefinedlistField voit ses propriétés de filtrage renommées en
- JFormFieldEditor::save a été retiré sans être remplacé
- JFormFieldText::getSuggestions a été supprimé en faveur de
  JFormFieldText::getOptions

#### Media Field

The Media field type now encodes image metadata into the internal value.
This is a sample value:

images/banners/osmbanner1.png#joomlaImage://local-images/banners/osmbanner1.png?width=468&height=60

To produce the final Image URL or the relative image file path, you can
use the new helper:

echo \Joomla\CMS\HTML\HTMLHelper::cleanImageURL(\$oldValue);

To get the clean value (without adapter information and metadata) from
the value which is stored in media form field:

echo
\Joomla\CMS\Helper\MediaHelper::getCleanMediaFieldValue(\$oldValue);

Function cleanImageURL does not clean the image URL but returns object
where one part of the object is cleaned URL. Using echo throws an error.
For more information visit <a
href="https://github.com/joomla/joomla-cms/issues/35871#issuecomment-968107241"
class="external autonumber" target="_blank"
rel="nofollow noreferrer noopener">[2]</a>

### Wrapper

- Les classes d'enveloppes de formulaires ont été supprimées. Continuez
  à utiliser les méthodes statiques d'origine.

### HTTP

#### Classes et Interfaces obsolètes

Les classes et interfaces suivantes sont obsolètes et planifiées pour
suppression dans la version Joomla! 5.0 :

- JHttpResponse (utilisez dorénavant Joomla\Http\Response)
- JHttpTransport (implémentez dorénavant Joomla\Http\TransportInterface)

#### Modifications de classe

Le paquet HTTP du Framework est dorénavant inclus dans Joomla! 4.0 et
JHttp et les sous-classes JHttpTransport ont été remaniées pour utiliser
le paquet en amont.

##### JHttp

- JHttp n'est plus fourni avec un package cacerts.pem dans le répertoire
  transports, utilisez plutôt le package composer/ca qui est livré avec
  les fichiers core.

Le constructeur de classe JHttp a été allégé avec les changements
suivant :

- Le paramètre d'options n'est plus typehinted en tant qu'objet
  Joomla\Registry\Registry, un tableau ou un objet implémentant
  l'interface
  <a href="https://secure.php.net/manual/en/class.arrayaccess.php"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">ArrayAccess</a> peut être utilisée
  en lieu et place ;
- Le paramètre de transport &accepte dorénavant tout objet
  Joomla\Http\TransportInterface ;

##### JHttpTransport

L'interface dorénavant obsolète JHttpTransport étend maintenant
Joomla\Http\TransportInterface et a provoqué des changements dans
l'interface qui causent des problèmes de compatibilité aval. Le
constructeur ne fait plus partie de l'interface, et la méthode
\`request()\` de l'interface a changé de signature. Plus spécifiquement,
le second paramètre qui typait (typehint) la classe JUri, type
(typehint) dorénavant Joomla\Uri\UriInterface.

##### JHttpResponse

En remaniant l'objet de réponse pour hériter du paquet HTTP du
Framework, qui utilise maintenant l'API ResponseInterface PSR-7, la
compatibilité a été cassée dans la structure des entêtes de réponses. A
partir de 4.0, ceci sera dorénavant un tableau multi-dimensionnel où la
clé est nom de l'entête et la valeur est un tableau de valeurs pour cet
entête (par le passé, c'était une chaîne de caractères).

### Image

#### Classes et Interfaces obsolètes

Les classes et interfaces suivantes sont obsolètes et seront retirées
dans la version Joomla! 5.0 :

- JImageFilter (utilisez dorénavant Joomla\CMS\Image\ImageFilter)
- JImageFilterBackgroundfill (utilisez dorénavant
  Joomla\CMS\Image\Filter\Backgroundfill )
- JImageFilterBrightness (utilisez dorénavant
  Joomla\CMS\Image\Filter\Brightness)
- JImageFilterContrast (utilisez dorénavant
  Joomla\CMS\Image\Filter\Contrast)
- JImageFilterEdgedetect (utilisez dorénavant
  Joomla\CMS\Image\Filter\Edgedetect)
- JImageFilterEmboss (utilisez dorénavant
  Joomla\CMS\Image\Filter\Emboss)
- JImageFilterGrayscale (utilisez dorénavant
  Joomla\CMS\Image\Filter\Grayscale)
- JImageFilterNegate (utilisez dorénavant
  Joomla\CMS\Image\Filter\Negate)
- JImageFilterSketchy (utilisez dorénavant
  Joomla\CMS\Image\Filter\Sketchy)
- JImageFilterSmooth (utilisez dorénavant
  Joomla\CMS\Image\Filter\Smooth)

#### Modifications de classe

Les classes du package Image du Framework ont été intégrées dans CMS et
JImage et les sous-classes de JImageFilter ont été refaites pour les
utiliser. C'est-à-dire que toutes les classes sous l'espace de noms
Joomla\Image ont été déplacées vers l'espace de nommage
Joomla\CMS\Image.

### Menu

- Le tiret bas de JMenu::\$\_items, JMenu::\$\_default et
  JMenu::\$\_active a été retiré (notez que ces propriétés étaient
  protégées et donc cela n'impacte que les sous-classes personnalisées
  de JMenu) ;

### New MVC Layer

- Ceci a été supprimé dans Joomla 4. Nous avons décidé que cet effort
  n'a pas abouti et avons donc poursuivi le travail de développement sur
  la couche MVC originale (voir la section "MVC héritée"). Il y a un
  plugin situé <a href="https://github.com/joomla-extensions/legacy-mvc"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">sur GitHub</a> que vous pouvez
  utiliser avec vos extensions pendant que vous les migrez à nouveau
  vers l'ancien MVC (notez que ce n'est pas livré par défaut dans Joomla
  4).

### Keychain

Retirer le keychain de la version 4.0 implique la suppression des
classes suivantes :

- JKeychain

### Pathway

- Le tiret bas de JPathway::\$\_pathway et JPathway::\$\_count a été
  supprimé (notez que ces propriétés étaient protégées et donc cela
  n'impacte que les sous-classes personnalisées de JPathway) ;
- JPathway::\_makeItem a été retiré à la faveur de JPathway::makeItem
  (notez que cette méthode était protégée et donc cela n'impacte que les
  sous-classes personnalisées de JPathway) ;

### Profiler

- JProfiler::getmicrotime et JProfiler::getMemory ont été supprimés au
  profit des méthodes PHP natives qu'ils enveloppaient (`microtime(1)`
  et `memory_get_usage()` respectivement

### Table

- l'objet de base de données JTable::\_\_construct est dorénavant typé
  (typehint) pour être un JDatabaseDriver ;
  - Les sous-classes de JTable devront s'assurer qu'elles passent un
    objet JDatabaseDriver au constructeur parent ;
  - Les sous-classes de JTable devront changer la signature de la
    méthode de setDbo() si elles veulent avoir une version étendue de
    cette méthode pour inclure le typehint ;
- Il existe une nouvelle méthode JTable::hasField - toutes les instances
  de property_exists sur les instances de JTable devront dorénavant de
  préférence utiliser cette méthode de proxy afin de permettre une
  meilleure interopérabilité des instances de Table  ;
- Le modèle JTableObserver (et des classes correspondantes) a été retiré
  de JTable. Dorénavant les déclenchements d'événements, les Tags et
  Content History de JTable (et toute autre utilisation personnalisée de
  ce modèle) doivent être déplacées vers les plugins standards ;

### E-mail

Les méthodes suivantes ont été retirées de Joomla! 4.0 :

- JMail::sendAdminMail a été supprimée ;

#### Exceptions

JMail ne prend plus en compte les exceptions de PHPMailer. C'est
maintenant à JMail qu'il incombe de gérer ces exceptions comme il se
doit. En outre, si l'envoi de courrier est désactivé dans la
configuration globale, l'appel de `\Joomla\CMS\Mail::send()` lancera une
`\Joomla\CMS\Mail\Exception\MailDisabledException`.

### Langues

- Les fonctions setTransliterator, setPluralSuffixesCallback,
  setIgnoredSearchWordsCallback, setLowerLimitSearchWordCallback,
  setUpperLimitSearchWordCallback et
  setSearchDisplayedCharactersNumberCallback sont maintenant typées
  (typehint) pour être appelables.
- `"_QQ_"` pour positionner les guillemets doubles a été retiré (ceci
  existait uniquement pour éviter un ancien bogue de PHP qui a été
  résolu depuis). Mettre un caractère d'échappement devant le guillemet
  double si nécessaire (i.e. `\"`).
- Le format des noms de fichiers linguistiques a été modifié pour
  faciliter le travail dans les outils de traduction tiers (tels que
  crowdin). Les fichiers de langue INI ne doivent plus contenir le code
  de langue (c'est-à-dire en-GB.com_contact.ini =\> com_contact.ini),
  dans ce cas le cas particulier de en-GB.ini a été renommé joomla.ini
  dans le paquet de langue de base. en-GB.xml a été nommé
  langmetadata.xml. Il existe une couche b/c qui continuera à lire les
  anciens noms de fichiers Joomla 3 dans tout Joomla 4.
- \Joomla\CMS\Language\Multilanguage::getSiteLangs a été supprimé.
  Utilisez plutôt
  \Joomla\CMS\Language\LanguageHelper::getInstalledLanguages(0)
- JLanguage::exists a été supprimé. Utilisez plutôt
  Joomla\CMS\Language\LanguageHelper::exists.
- Les classes de wrapper JTextWrapper, LanguageHelperWrapper et
  TransliterateWrapper ont été supprimées. Continuez à utiliser les
  méthodes statiques qu'elles englobaient.
- The pdf_fonts handling/support for language packs
  (`language/pdf_fonts`) has been removed from the language installer
  (<a href="https://github.com/joomla/joomla-cms/pull/31288"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">see GitHub PR #31288</a>).

### Compatibilité des couches MVC

#### JControllerLegacy

- JControllerLegacy a été retiré de la couche de compatibilité, et nous
  n'avons plus l'intention de la retirer (ni ses sous-classes) dans le
  futur proche.
- JControllerLegacy n'étend plus JObject. Les contrôleurs ne devraient
  appeler aucune méthode contenues dans la classe JObject.
- JControllerLegacy implémente une interface pour les contrôleurs
  multi-tâches.
- JControllerLegacy::\_construct prend dorénavant des arguments
  supplémentaires. Si par le passé vous obteniez un objet de type
  Controller en utilisant JControllerLegacy::getInstance, vous devrez
  modifier votre code.
  - Paramètre 2: Une instance facultative de MVCFactoryInterface
  - Paramètre 3: Une instance facultative de CMSApplicationInterface
  - Paramètre 4: Une instance facultative de Input
  - Paramètre 5: Une instance facultative de FormFactoryInterface
- JControllerForm utilise dorénavant le paquet StringInflector pour
  déterminer la vue en liste. Ceci devrait améliorer sa capacité à
  déterminer la vue en liste avec plus de noms de vues. Si les
  développeurs d'extensions trouvent que la vue en liste n'est plus
  trouvée, ils devront mettre à la main la propriété de classe
  \`view_list\` dans leur contrôleur.

#### LegacyView

- JViewLegacy a été retiré de la couche de compatibilité, et nous
  n'avons plus l'intention de la retirer (ni ses sous-classes) dans le
  futur proche.
- JViewHtml a été divisé en deux classes - AbstractView et HtmlView. La
  vue abstraite contient la logique pour accéder au modèle et récupérer
  le nom de la vue et est sensée être la classe de base pour les vues
  non-Html. La vue HTML contient la même logique que par le passé.
- Il y a deux sous-classes de JViewHtml - \Joomla\CMS\MVC\View\ListView
  et \Joomla\CMS\MVC\View\FormView conçues pour accélérer le
  développement des vues de liste et de formulaire et réduire la
  duplication de code.

### Library

- JLibraryHelper::\_load a été supprimé. Utilisez
  \Joomla\CMS\Helper\LibraryHelper::loadLibrary à la place.

### Session

Le paquet de session a subi un remaniement majeur pour utiliser le
paquet de Framework de Session. Ce changement affecte en premier le
contenu du paquet ; les changements de l'API publique principale à
travers la classe JSession sont faibles.

### String

L'ancien alias de classe JString a été retiré. Utilisez dorénavant
\Joomla\String\StringHelper

#### Classes et Interfaces retirées

Les classes et interfaces suivantes ont été retirées de Joomla! 5.0 :

- JSessionExceptionUnsupported
- JSessionHandlerInterface
- JSessionHandlerJoomla
- JSessionHandlerNative
- JSessionStorage
- JSessionStorageApc
- JSessionStorageDatabase
- JSessionStorageMemcache
- JSessionStorageMemcached
- JSessionStorageNone
- JSessionStorageWincache
- JSessionStorageXcache

#### JSession

JSession étend dorénavant la classe Joomla\Session\Session du Framework.
Beaucoup de méthodes ont une signature modifiée et une couche de
compatibilité existe pour aider à la transition.

##### Paramètres Namespace obsolètes

Les méthodes get, set, has, et clear supportaient pas le passé un
paramètre espace-nom (namespace). Ce paramètre est maintenant obsolète,
l'espace-nom doit être ajouté au début du nom avant d'appeler ces
méthodes.

##### JSession::clear() redéfini

Dans la classe Joomla\Session\Session, la méthode clear est utilisée
pour effacer toutes les données du magasin de session. Dans JSession,
cette méthode est utilisée pour supprimer une seule entrée. Lorsque
cette méthode est appelée avec des paramètres, elle appellera la
nouvelle méthode Joomla\Session\Session::remove().

##### JSession::getInstance() obsolète

Le méthode singleton getInstance() devient obsolète. L'objet session
doit maintenant être récupéré depuis l'application active ou bien depuis
le conteneur d'injection de dépendances.

##### Gestionnaires de Session

Dans la version Joomla! 3.x et antérieures, les gestionnaires de
sessions étaient représentés par la classe JSessionStorage et ses
sous-classes. Dans Joomla! 4.0, les gestionnaires de sessions sont
dorénavant implémentés depuis Joomla\Session\HandlerInterface (qui est
une extension <a
href="https://secure.php.net/manual/en/class.sessionhandlerinterface.php"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">SessionHandlerInterface</a> de PHP).
Tous les gestionnaires qui étaient supportés dans Joomla! 3.x restent
disponibles dans 4.0 en plus de l'ajout de deux gestionnaires
supplémentaires ; l'un implémentant nativement l'extension APCu et
l'autre supportant Redis.

### Librairies de réseaux sociaux

Les paquets facebook, github, google, linkedin, openstreetmap, mediawiki
et twitter ont tous été supprimés du CMS.

### User

- JUser::getParameters a été supprimé. Vous ne pouvez plus récupérer
  tous les paramètres d'un utilisateur, mais vous pouvez utiliser
  JUser::getParam pour obtenir des paramètres individuels selon vos
  besoins.

#### Helper

- JUserHelper::getCryptedPassword a été supprimé. Joomla 4 ne supporte
  que le hachage avec la fonction native PHP password_hash (via
  JUserHelper::hashPassword (disponible depuis Joomla 3.2.1))
- JUserHelper::getSalt a été supprimé sans être remplacé (il générait le
  JUserHelper::getCryptedPassword du hash qui est maintenant supprimé
  comme ci-dessus)
- JUserHelper::invalidateCookie, JUserHelper::clearExpiredTokens et
  JUserHelper::getRememberCookieData ont été supprimés sans être
  remplacés. Ils étaient inutilisés dans le noyau depuis Joomla 3.2
  lorsque leur logique a été déplacée dans le plugin d'authentification
  des cookies
- Le JUserWrapperHelper a été retiré. Continuez à utiliser les méthodes
  statiques originales dans JUserHelper.

### Classes supprimées sans remplaçant

- JNode
- JTree
- JGrid
- JError (utilisez des exceptions natives lorsque la gestion d'erreur
  est requise)

#### Services

#### Classes et Interfaces retirées

Les classes et interfaces suivantes ont été retirées de Joomla! 4.0:

- JArrayHelper

utilisez dorénavant Joomla\Utilities\ArrayHelper.

## Librairies externes

Les changements suivant ont été faits dans les librairies externes
incluses dans les paquets Joomla!.

### PHPMailer

Joomla! 4.0 embarque PHPMailer 6.0. Lisez, s'il vous plaît,
<a href="https://github.com/PHPMailer/PHPMailer/blob/6.0/UPGRADING.md"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">le guide de mise à jour</a> pour en
savoir plus sur les changements.

### PHPUTF8

Depuis Joomla! 3.4, la librairie PHPUTF8 étaient présente à deux
endroits dans la paquet Joomla! : \`libraries/phputf8\` et
\`libraries/vendor/joomla/string/src/phputf8\`. Dans Joomla! 4.0, la
copie de la librairie dans \`libraries/phputf8\` a été retirée. La
classe Joomla\String\StringHelper expose de nombreuses fonctions de la
librairie et la définition de l'autoloader Composer importe l'essentiel
de la librairie également ; Cependant, si vous avez besoin d'une
fonctionnalité qui n'est pas déjà incluse, vous devrez importer la
fonction requise depuis le chemin
\`libraries/vendor/joomla/string/src/phputf8\`.

### SimplePie

La librairie SimplePie n'est plus incluse dans Joomla! 4.0.

### jQuery

Joomla! 4.0 embarque jQuery 3. Lisez, s'il vous plaît,
<a href="https://jquery.com/upgrade-guide/3.0/" class="external text"
target="_blank" rel="nofollow noreferrer noopener">le guide de mise à
jour</a> pour prendre connaissance des principaux changements. Notez que
nous n'incluons plus jQuery Migrate également. Nous recommandons de
l'utiliser localement pour aider au débogage du code pour trouver les
problèmes résiduels.

### jQuery UI

jQuery UI a été retiré de Joomla 4. Bien qu'il n'ait pas été
officiellement annoncé comme terminé, il n'y a pas eu de version de
jQuery UI depuis 2016.

### Bootstrap

Joomla! 4.0 embarque Bootstrap 4. Bootstrap 2.3.2 a été retiré ;
cependant, nous avons maintenu certaines classes BS2 pour faciliter la
migration (i.e. l'ancien element-invisible de BS2 existe toujours pour
les lecteurs d'écrans).

### FOF

FOF 2.x a été retiré.

## Templates

Les modèles de site Joomla! 3 - ISIS et Hathor pour le site
d'administration, et Protostar et Beez pour le site public - ne sont
plus maintenus. Le nouveau modèle 4.0 pour le site d'administration
s'appelle Atum et pour le site public Cassiopeia.

En conséquence, toutes les extensions doivent migrer vers les nouveaux
styles Bootstrap 4, en s'éloignant de l'implémentation actuelle de
Bootstrap 2.3.2. Pour plus d'information, lisez
l'<a href="http://getbootstrap.com/docs/4.0/getting-started/introduction/"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">introduction à Bootstrap 4.0</a>.
Pour plus d'information sur Bootstrap 2.3.2, lisez
<a href="http://getbootstrap.com/2.3.2/" class="external text"
target="_blank" rel="nofollow noreferrer noopener">Bootstrap 2.3.2</a>.

- Joomla 4 chargera d'abord la favicon du template plutôt que celle de
  la racine de Joomla, conformément au concept selon lequel le template
  est le référentiel unique de contenus
- Les composants frontaux et les vues de module utilisent désormais le
  balisage de classe Block Element Modifier (BEM) pour permettre aux
  templates de supporter plus facilement des frameworks autres que le
  bootstrap. Voir le
  <a href="http://getbem.com/" class="external text" target="_blank"
  rel="nofollow noreferrer noopener">site web BEM</a> pour plus
  d'informations sur la façon de construire des classes similaires.

Vous y trouverez également des modifications des options des éléments de
base que vous devez examiner lorsque votre template doit prendre en
charge 3.x et 4.x en même temps : <a
href="https://docs.joomla.org/J4.x:Changed_parameters_for_template_providers"
class="external free" target="_blank"
rel="noreferrer noopener">https://docs.joomla.org/J4.x:Changed_parameters_for_template_providers</a>

## Autre

- La variable globale *\$\_PROFILER* a été supprimée. Utilisez plutôt
  *\Joomla\CMS\Profiler::getInstance*.

### Médias dans les librairies

Les médias ne sont pas autorisés dans le répertoire racine des
librairies du CMS - la bonne pratique veut que tous les éléments
associés avec les librairies Joomla! soient placés dans le répertoire
'media'. L'accès direct est bloqué par des fichiers .htaccess et
web.config à la racine du répertoire des librairies.

### Bin

La suppression de 'keychain.php' dans la version 4.0 entraine la
suppression du répertoire 'bin' à la racine qui ne contenait plus que ce
fichier.

### Composants

- Tous les composants ont été mis dans l'espace de nom et les
  répertoires retravaillés en accord. Pour plus d'information à ce
  propos, lisez le didacticiel pour savoir comment créer un composant
  pour Joomlaǃ 4.
- La vue profil de com_admin a été retirée (cela avait été créé
  historiquement du fait de problèmes d'accès à com_users ; ce n'est
  plus le cas et du coup toutes les modifications d'utilisateurs passent
  dorénavant par l'édition d'utilisateurs dans la vue com_users du site
  d'administration).
- Le code php 5.5 de remblai (backfill) dans com_actionlogs a été retiré
  et en accord avec `ActionlogsHelper::getCsvData()` est dorénavant type
  hinté pour retourner un objet `Generator`.
- Les en-têtes d'exportation de com_actionlogs CSV ont été modifiés pour
  correspondre aux chaînes de caractères affichées dans l'interface
  utilisateur.
- Le mode de routage des URL 'Legacy' des composants du noyau a été
  retiré en Joomlaǃ 3.7. Vous devez soit utiliser votre fichier
  .htaccess ou bien le composant de redirection pour positionner toute
  URL interne qui change. Vous pouvez essayer le mode 'Modern' de Joomla
  3 en suivant les instructions du  Nouveau système de
  routage.
- Le composant MailTo a été retiré sans être remplacé. Si vous avez
  utilisé cette fonctionnalité, vous devrez trouver un autre composant
  sur JED.
- Dans la vue frontale des contacts de com_contact - la propriété du
  contact a été supprimée car elle était un double de la propriété de
  l'objet. Nous avons choisi de conserver \$this-\>item car il était
  cohérent avec celui des vues de l'article et des balises. Les modèles
  de remplacement devront être mis à jour en conséquence.
- Le champ répétable dans com_fields a été supprimé au profit du nouveau
  champ de sous-formulaire. Les données des champs répétables sont
  automatiquement transférées vers le nouveau champ de sous-formulaire
  mais sont stockées dans un format différent.
- Les champs xreference ont été supprimés de *\#\_\_contact_details*,
  *\#\_\_content* et *\#\_\_newsfeeds* car ils étaient inutilisés.

### Plugins

- Le plugin d'authentification gmail a été retiré. Pour plus
  d'information, lisez s'il vous plaît <a
  href="https://developer.joomla.org/news/724-removal-of-the-gmail-authentication-plugin-as-of-joomla-4-0.html"
  class="external text" target="_blank"
  rel="noreferrer noopener">l'article de ce blog</a>.
- Le support de Recaptcha v1 a été entièrement retiré du plugin de
  captcha - cela ne fonctionnait plus depuis Q2 2018 du fait de
  l'abandon de son support par Google.
- Le plugin Recaptcha utilise dorénavant la librairie php officielle clé
  en main du captcha de Google.
- Pour les plugins utilisant la couche de compatibilité 3.x, le nom du
  résultat est une propriété privée autant pour les paramètres d'entrée
  que pour les valeurs de résultat. Pour plus d'information sur
  l'approche recommandée pour créer des plugins, lisez, s'il vous plaît,
   Créer un plugin pour
  Joomla!.
- Pour les plugins utilisant la couche de compatibilité 3.x, pour tout
  type d'indices pour des événements qui nécessitent une classe, cette
  classe *doit* être autochargée avant que le plugin ne soit instancié.
- L'événement onContentBeforeSave requiert maintenant le paramètre
  'data' (ceci a été passé dans \Joomla\CMS\MVC\Model\LegacyModel depuis
  la version 3.7 mais est dorénavant passé en cohérence avec les
  extensions du noyau et utilisé par le plugin de contenu du noyau de
  Joomla).
- Le retour avant d'appeler `parent::__construct()` dans le constructeur
  d'un plugin n'est plus pris en charge pour éviter de mettre le plugin
  en file d'attente dans le répartiteur d'événements.
- *onUserBeforeDataValidation* est déprécié comme un événement en faveur
  de "onContentBeforeValidateData" (L'événement était utilisable par
  tous les types de contenu et n'était pas spécifique aux utilisateurs.
  Notez que les deux événements seront appelés pour la durée de
  Joomla 4. Vous devriez migrer votre code vers le nouvel événement
  lorsque vous n'aurez plus besoin de supporter Joomla 3.

### Plugins (Events)

- In Joomla 4, events whose name does not start with "on" no longer
  work. They don't even produce any error, so it's very hard to figure
  out why they don't work. This means that you need to overwrite both
  the names of functions in plugins and the names of their calls. For
  more information please read
  <a href="https://github.com/joomla/joomla-cms/issues/36062"
  class="external autonumber" target="_blank"
  rel="nofollow noreferrer noopener">[3]</a>

### Assistants de l'administration

- JAdministratorHelper a été retiré sans remplaçant (il a été mergé dans
  JApplicationAdministrator) ;
- JSubMenuHelper a été retiré sans remplaçant (utilisez dorénavant
  JHtmlSidebar - disponible depuis la version 3.0) ;
- JToolbarHelper a été déplacé dans le répertoire des librairies
  principales ;

### Modules

- Le module du site d'administration "submenu" a été supprimé.
- La logique des *Module Chromes* (styles de module) dans les fichiers
  de template `html/modules.php` a été déplacée vers les fichiers
  `JLayout`. Les fonctions de `modChrome_x` dans `modules.php` ne sont
  plus supportées. Voir
  <a href="https://github.com/joomla/joomla-cms/pull/23570"
  class="external free" target="_blank"
  rel="nofollow noreferrer noopener">https://github.com/joomla/joomla-cms/pull/23570</a>
  pour plus de détails.
- Les *Module Chromes* (styles de module) `modChrome_horz`,
  `modChrome_xhtml`, `modChrome_rounded` ont été supprimés du modèle
  `system` sans remplacement.
- Les suffixes des classes de modules ont été renommés et normalisés.
  Ils s'appellent désormais Module Class et sont ajoutés à la liste des
  classes dans le Module Chrome. (Ils ne sont plus rendus dans la sortie
  du module lui-même).

### Gestion des erreurs

- Joomla! gérera dorénavant les erreurs PHP E_USER_DEPRECATED et les
  acheminera dans JLog - ceci est utile pour gérer les obsolescences
  dans les nombreuses librairies PHP tierces (notez que cela va bloquer
  le chargement de la page lorsque le mode de débogage sera activé) ;
- Joomla\CMS\Exception\ExceptionHandler n'opère maintenant que sur les
  Exceptions levées dans JApplication::execute. Nous utilisons
  maintenant Symfony ErrorHandler lorsque cela échoue ou que des
  exceptions sont levées en dehors de cela. Nous espérons que ceci aura
  un impact minimal sur la plupart des utilisateurs et devrait remonter,
  dans de nombreux cas, plus de messages utiles que la traditionnelle
  erreur "Error displaying the error page"/"Erreur lors de l'affichage
  de la page d'erreur" pour les utilisateurs lorsque les choses tournent
  très mal.
- Joomla\CMS\Exception\ExceptionHandler est maintenant sensible au
  format et devrait remonter des erreurs dans les formats html, json,
  xml, feed ou cli ;
- La signature Joomla\CMS\Exception\ExceptionHandler::render() est
  modifiée pour inclure the type (typehint) Throwable. Avant la version
  3.5 lorsque le support de PHP 7 a été ajouté ceci est typehint en tant
  qu'Exception, et depuis la version 3.5 a été typechecked dans le code
  lui même.

### Base Tag

Les versions précédentes de Joomla définissent une balise d'en-tête de
l'URL actuelle dans le frontend. Cette balise a été supprimée car elle
n'avait pas d'utilité précise.

### JavaScript

Le fichier *caption.js* a été supprimé de Joomla. Utilisez les éléments
HTML natifs *figure* et *figcaption*. (Vous pouvez consulter JLayout
dans *layouts/joomla/content/intro_image.php* pour un exemple).

saveOrderAjax does not send complete form data (like it did in Joomla
3), only cid and order variable. This may be insufficient because some
extensions need more data for proper sorting - see:
<a href="https://github.com/joomla/joomla-cms/issues/36346"
class="external free" target="_blank"
rel="nofollow noreferrer noopener">https://github.com/joomla/joomla-cms/issues/36346</a>

### Namespacing

L'utilisation de classes comme *\$msg = JText::\_('Hello man!');* peut
maintenant utiliser l'espacement des noms. Cela se transformerait en
*\$msg = Text::\_( 'Hello man!' );*. Pour utiliser l'espace de noms,
vous devez ajouter la déclaration d'espace de noms appropriée. Celle-ci
doit être ajoutée après le *defined('\_JEXEC') or die ;*.

Pour connaître l'espace de noms approprié, vous pouvez soit suivre les
instructions ici : <a
href="https://groups.google.com/forum/#!topic/joomla-dev-general/1ua9zIqlcVc"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">si confus au sujet de l'espace de
noms et de la demande de renseignements...</a> ou utiliser le fichier
généré fichier de référence pdf :  File:J! namespace
reference.pdf

#### Namespace mapping and manifest file name

Automatic namespace mapping won't work with extension manifest files
named `manifest.xml`. See:
<a href="https://github.com/joomla/joomla-cms/issues/37750"
class="external free" target="_blank"
rel="nofollow noreferrer noopener">https://github.com/joomla/joomla-cms/issues/37750</a>

<!-- Filename: jdocmanual?manual=user&heading=help&filename=administrator-help.md / Display title: Aide de l'administrateur  -->

## Introduction

Presque toutes les pages d'administration de Joomla ont une barre d'outils contenant un bouton **Aide** près du coin supérieur droit de la page. Seuls les tableaux de bord n'ont pas de barre d'outils et donc pas de bouton d'aide.

De nombreuses pages ont également un bouton intitulé **Activer/Désactiver l'aide en ligne**. Cela affiche ou masque simplement une description du champ si elle est disponible. Son objectif est de réduire l'encombrement mais de fournir un mécanisme de rappel là où cela serait utile. Il n'est pas traité plus en détail ici.

Le bouton **Aide** déclenche l'ouverture d'une nouvelle fenêtre en utilisant une URL intégrée dans le bouton. Un exemple :
```
data-url="https://help.joomla.org/proxy/index.php?keyref=Help51:Articles&lang=en"
```
Dans ce cas, le contenu de la page d'aide provient d'une source externe.  

## La Source d'Aide - un site MediaWiki

MediaWiki est le logiciel utilisé par WikiPedia. C'est un logiciel libre open source (FOSS) qui utilise PHP et MySQL, tout comme Joomla. Vous pouvez le télécharger et l'installer vous-même. En théorie, vous pourriez créer votre propre serveur d'aide et l'utiliser à la place du serveur d'aide communautaire de Joomla. En pratique, vous devez savoir que les pages MediaWiki nécessitent un certain traitement pour les rendre adaptées à l'affichage en tant que pages d'aide.

C'est là qu'intervient le **proxy**. Il récupère la page nécessaire de l'installation MediaWiki et la prépare pour l'affichage en tant que page d'aide. Vous pouvez voir une page MediaWiki originale dans cet exemple à l'adresse https://docs.joomla.org/Help5.x:Articles et vous pouvez la modifier si vous remarquez quelque chose qui ne va pas.  

## L'URL d'Aide Globale

Le fichier **configuration.php** à la racine d'une installation Joomla contient une
variable `$helpurl` :

```
$helpurl = 'https://help.joomla.org/proxy/index.php?keyref=Help{major}{minor}:{keyref}&lang={langcode}';
```

Lorsqu'un bouton Aide est sélectionné, chacun des éléments entre accolades est remplacé.
Les valeurs {major} et {minor} sont les paramètres de version de votre installation.
Le {langcode} est le code de langue de votre Administrateur actuellement sélectionné,
qui peut être en, de ou fr.

La variable {keyref} est le nom de fichier d'une page sur le serveur d'aide, moins son
espace de noms. Ainsi, pour la page Articles, le nom de fichier pertinent se trouve être
*Articles*.

**Note :** `https://docs.joomla.org/` est le site pour éditer les pages d'aide. Mais
`https://help.joomla.org/proxy` est le site pour récupérer les pages d'aide.

Il n'existe pas de disposition pour changer l'URL du serveur d'aide par défaut depuis les
formulaires de Configuration Globale de l'Administrateur, mais vous pouvez la changer avec
un éditeur de texte.

La liste complète des codes de substitution disponibles est :

| Code          | Sera remplacé par                                                             |
|---------------|--------------------------------------------------------------------------------|
| {app}         | Nom de l'application (par exemple "Administrator" dans l'interface administrative de Joomla CMS)|
| {component}   | Nom du composant (par exemple "com_content" dans le Gestionnaire d'Articles)  |
| {keyref}      | Référence de la clé de l'écran d'aide (après passage par le système de traduction) |
| {major}       | Numéro de révision majeure de Joomla (par exemple "5" dans Joomla 5.6).       |
| {minor}       | Numéro de révision mineure de Joomla (par exemple "1" dans Joomla 5.1)        |
| {maintenance} | Numéro de révision de maintenance de Joomla (par exemple "3" dans Joomla 5.1.1).|
| {language}    | Code de langue complet (par exemple "en-GB")                                  |
| {langcode}    | Partie du code de langue correspondant à l'étiquette de langue (par exemple "en" si le code complet est "en-GB") |
| {langregion}  | Partie du code de langue correspondant à l'étiquette de région (par exemple "GB" si le code complet est "en-GB") |

## Aide Mondiale à l'Avenir

L'utilisation d'un site MediaWiki pour la diffusion des pages d'aide est quelque peu contraignante pour ceux qui maintiennent la documentation et la procédure pourrait changer à l'avenir. En cas de changement, il est probable que la source se compose de fichiers HTML précompilés accessibles avec un simple changement de domaine source $helpurl.

## Aide locale pour le composant personnalisé

Si vous avez un composant personnalisé et que vous êtes à l'aise avec l'édition de code source PHP et la création de contenu, vous pouvez créer vos propres pages d'aide individuelles. Prenons le composant Jdocmanual comme exemple. En tant que composant personnalisé, il n'y a pas de pages d'aide sur le site MediaWiki docs.joomla.org. Les composants tiers ne sont pas autorisés à y servir des pages d'aide.

Examinez ce fragment de code provenant de administrator/components/com_jdocmanual/src/View/Manual/ViewHtml.php :
```
        $tmpl = $app->input->getCmd('tmpl');
        if ($tmpl !== 'component') {
            ToolbarHelper::help('jdocmanual', true);
        }
```
La spécification de l'appel ToolbarHelper::help est la suivante :
```
@param $ref : Le nom du fichier cible (sans l'extension du fichier).
@param $useComponent : Utiliser le fichier d'aide dans le répertoire du composant.
@param $url : Utiliser cette URL au lieu de toute autre.
@param $component : Nom du composant pour obtenir de l'aide (null pour le composant actuel)
function Toolbar::help(
    string $ref,
    bool $useComponent = false,
    string $url = null,
    string $component = null
): HelpButton
Écrit un bouton d'aide pour une option donnée (ouvre une fenêtre popup).
```
Dans cet exemple, **$ref** est un nom de fichier à utiliser, dans ce cas `'jdocmanual'` (il doit correspondre à la casse du fichier cible) et **$useComponent** est `true`, ce qui signifie que la page d'aide à utiliser se trouvera dans les fichiers du composant à l'adresse administrator/component/com_jdocmanual/help/en-GB/jdocmanual.html

Utiliser un fichier d'aide au sein du composant devrait signifier que l'aide n'est jamais manquante et peut-être toujours à jour.

## Aide à distance pour composant personnalisé

Lors de la création du bouton d'aide, vous pouvez définir $useComponent = false et configurer l'URL pour pointer vers un emplacement spécifique sur votre propre site ou un site distant.

```
    ToolbarHelper::help('jdocmanual', false, 'http://example.com/help/en-GB/jdocmanual.html');
```

Tout ce qui est nécessaire est donc une page HTML avec le bon nom au bon endroit.

*Traduit par openai.com*


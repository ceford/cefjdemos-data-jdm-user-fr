<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Garder les sous-menus ouverts",
    "description": " ",
    "author": ""
}
-->

Un module de menu peut être utilisé pour afficher un menu horizontal (généralement en haut de la page) ou un menu vertical (généralement dans une barre latérale, à gauche ou à droite). Dans un menu horizontal (en haut), il n'est généralement pas souhaitable de garder le sous-menu ouvert. C'est pourquoi le comportement par défaut d'un module de menu consiste à fermer les sous-menus au chargement de la page.

## Comportement de basculement de l'état *ouvert*

Cependant, dans un menu vertical (barre latérale), il est souvent souhaitable de laisser un sous-menu ouvert lorsqu'il contient l'élément de menu actif. Dans Joomla 6.0, une nouvelle classe CSS, `nav-active-open`, a été introduite spécifiquement pour permettre de contrôler si les sous-menus sont automatiquement ouverts au chargement de la page pour l'élément de menu actif. La définition de cette classe permet désormais d'obtenir ce comportement. La classe est définie dans le module via l'administration.

![paramètre de classe de menu dans l'administration pour nav-active-open afin que le menu reste ouvert sur l'élément actif](../../../en/images/menus/keep-submenus-open/01-menu-class-setting.png)

## Comment créer un menu de barre latérale sans basculement de menu déroulant

Si vous souhaitez garder tous les sous-menus ouverts, vous n'avez pas besoin d'un bouton de basculement de menu déroulant. Utilisez plutôt une [surcharge de modèle](jdocmanual?article=user/templates/template-overrides).

Voici comment cette surcharge particulière du modèle est réalisée :

1. Commencez par sélectionner Système → Templates → Templates de site dans le menu d'administration, puis sélectionnez l'élément Détails et fichiers de Cassiopeia. Cela ouvre le formulaire Templates : Personnaliser (Cassiopeia).

2. Passez à l'onglet Créer des surcharges et sélectionnez mod_menu :

![sélection de la surcharge du modèle de menu de module](../../../en/images/menus/keep-submenus-open/02-create-override-select-mod-menu.png)

Cela copiera tous les fichiers de mise en page du menu depuis le module de menu dans la surcharge. L'onglet Éditeur s'affiche ensuite.

3. Dans l'onglet Éditeur, développez les entrées sous HTML → mod_menu. Vous trouverez ici le fichier `default.php`. Ouvrez le fichier et copiez son contenu dans un emplacement sûr. Fermez le fichier.

4. Créez un nouveau fichier dans le dossier html → mod_menu. Son nom ne doit pas contenir de caractère de soulignement. Dans cet exemple, le nouveau fichier est nommé `treedefault.php`. Cela vous permet de sélectionner soit la mise en page de menu par défaut, soit cette autre mise en page dans n'importe lequel de vos modules de menu. Dans la liste suivante des fichiers de surcharge, l'original est encadré en rouge et la nouvelle alternative est encadrée en vert.

![onglet de modification de la surcharge mod_menu - ouverture de default.php](../../../en/images/menus/keep-submenus-open/03-edit-mod-menu.png)

4. Modifiez le nouveau fichier de mise en page. Les étapes suivantes sont répertoriées dans l'ordre inverse afin de
préserver les numéros de ligne pendant le processus de modification :

Modifiez la ligne 104 afin qu'elle contienne ce qui suit :

```
        echo '<ul class="list-unstyled ps-3" aria-hidden="false">';
```

Cela maintient le menu ouvert et ajoute une indentation aux sous-menus.

Remplacez les lignes 98 à 101 par `break`

```php
                    echo '<button class="mod-menu__toggle-sub" aria-expanded="false">' .
                 break;
                    '<span class="icon-chevron-down" aria-hidden="true"></span>' .
                    '<span class="visually-hidden">' . Text::sprintf('MOD_MENU_TOGGLE_SUBMENU_LABEL', $item->title) . '</span>' .
                    '</button>';
```

Supprimez les lignes 93 à 94

```php
                    echo '<span class="icon-chevron-down" aria-hidden="true">' .
                        '</span></button>';
```

Supprimez les lignes 66 à 71

```php
    // The next item is deeper - add toggle only here it is a heading or separator
    if ($item->deeper && (int) $item->level === $startLevel && in_array($item->type, ['separator', 'heading'])) {
        // Add a toggle button.
        echo '<button class="mod-menu__toggle-sub" aria-expanded="false">';
    }
```

Supprimez les lignes 15 à 20

```php
/** @var Joomla\CMS\WebAsset\WebAssetManager $wa */
$wa = $app->getDocument()->getWebAssetManager();
$wa->getRegistry()->addExtensionRegistryFile('mod_menu');
$wa->usePreset('mod_menu.menu');
```

Voici le fichier de surcharge `treedefault.php` complet :

```
<?php

/**
 * @package     Joomla.Site
 * @subpackage  mod_menu
 *
 * @copyright   (C) 2009 Open Source Matters, Inc. <https://www.joomla.org>
 * @license     GNU General Public License version 2 or later; see LICENSE.txt
 */

defined('_JEXEC') or die;

use Joomla\CMS\Helper\ModuleHelper;
use Joomla\CMS\Language\Text;

$tagId      = $params->get('tag_id', '') ?: 'mod-menu' . $module->id;
$id         = ' id="' . htmlspecialchars($tagId, ENT_QUOTES, 'UTF-8') . '"';
$startLevel = (int) $params->get('startLevel', 1);

// The menu class is deprecated. Use mod-menu instead
?>
<ul<?php echo $id; ?> class="mod-menu mod-list nav <?php echo $class_sfx; ?>">
<?php foreach ($list as $i => &$item) {
    $itemParams = $item->getParams();
    $class      = 'nav-item item-' . $item->id;

    if ($item->id == $default_id) {
        $class .= ' default';
    }

    if ($item->id == $active_id || ($item->type === 'alias' && $itemParams->get('aliasoptions') == $active_id)) {
        $class .= ' current';
    }

    if (in_array($item->id, $path)) {
        $class .= ' active';
    } elseif ($item->type === 'alias') {
        $aliasToId = $itemParams->get('aliasoptions');

        if (count($path) > 0 && $aliasToId == $path[count($path) - 1]) {
            $class .= ' active';
        } elseif (in_array($aliasToId, $path)) {
            $class .= ' alias-parent-active';
        }
    }

    if ($item->type === 'separator') {
        $class .= ' divider';
    }

    if ($item->deeper) {
        $class .= ' deeper';
    }

    if ($item->parent) {
        $class .= ' parent';
    }

    echo '<li class="' . $class . '">';

    switch ($item->type) :
        case 'separator':
        case 'component':
        case 'heading':
            require ModuleHelper::getLayoutPath('mod_menu', 'default_' . $item->type);
            break;
        default:
            require ModuleHelper::getLayoutPath('mod_menu', 'default_url');
            break;
    endswitch;

    // The next item is deeper.
    if ($item->deeper) {
        // Check type - add only on first level
        // @todo aria-label - set in menu item ???
        if ((int) $item->level === $startLevel) {
            switch ($item->type) {
                case 'heading':
                case 'separator':
                    break;

                default:
                    break;
            }
        }
        echo '<ul class="list-unstyled ps-3" aria-hidden="false">';
    } elseif ($item->shallower) {
        // The next item is shallower.
        echo '</li>';
        echo str_repeat('</ul></li>', $item->level_diff);
    } else {
        // The next item is on the same level.
        echo '</li>';
    }
}
?></ul>
```

## Résultat

Le résultat est une simple liste, sans fonctionnalité de basculement pour le module de menu latéral, illustrée ici à gauche :

![résultat avec surcharge de modèle - simple liste sans boutons ni fonctionnalité de basculement](../../../en/images/menus/keep-submenus-open/05-site-result.png)

*Traduit par openai.com*

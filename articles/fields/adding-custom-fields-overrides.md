<!-- Filename: J3.x:Adding_custom_fields/Overrides / Display title: Substitution de Modèles  -->

## Affichage Automatique du Champ

Chacun des champs disponibles possède une option intitulée *Affichage Automatique* qui peut être définie sur l'une des options suivantes :

* Après le Titre
* Avant le Contenu Affiché
* Après le Contenu Affiché
* Ne pas afficher automatiquement

Si le dernier de ces éléments est sélectionné, alors le champ n'est pas affiché à moins que vous ne créiez un remplacement de modèle pour gérer l'affichage vous-même. Vous pouvez également ajouter `{field ID}` dans un article pour placer le champ où vous le souhaitez. Mais vous devez vous souvenir de le faire dans chaque article.

Cet exemple montre comment créer un remplacement de modèle pour un Contact. Les méthodes s'appliquent également aux composants Contenu et Utilisateur.

## Créer une Surcharge de Modèle

Depuis le menu Administrateur :

* Sélectionnez **Système / Modèles de Site / Détails et Fichiers de Cassiopeia**
* Sélectionnez l'onglet **Créer des Surcharges**.
* Sélectionnez **com_contact** dans le panneau *Composants*.
* Sélectionnez **Contact** dans la liste des vues disponibles. Il s'agit de la mise en page pour un seul contact.

Dans le panneau **Éditeur** :
* Sélectionnez **html / com_contact / contact / default.php**, qui est le fichier
  qui définit la mise en page générale de la page de contact unique.
* Faites défiler ce fichier et remarquez une série de blocs `<php if (...) : ?>`.
  Chacun affichera ou masquera une section de texte en fonction des paramètres du contact.
* Remarquez les lignes contenant
  ```
  <?php echo $this->item->event->afterDisplayTitle; ?> (ligne 73)
  <?php echo $this->item->event->beforeDisplayContent; ?> (ligne 98)
  <?php echo $this->item->event->afterDisplayContent; ?> (ligne 189)
  ```
  L'une de ces variables, ou aucune d'entre elles, est peuplée en fonction de la valeur du champ
  Affichage Automatique.

## Utilisation des champs dans votre remplacement

Vous avez tous les champs correspondant à l'élément actuel accessibles via une
propriété `$this->item->jcfields`, qui est un tableau contenant les données suivantes pour chaque champ (cet exemple est pour un champ Éditeur) :

```php
    Array
    (
        [4] => stdClass Object
            (
                [id] => 4
                [title] => article-editor
                [name] => article-editor
                [checked_out] => 0
                [checked_out_time] => 0000-00-00 00:00:00
                [note] =>
                [state] => 1
                [access] => 1
                [created_time] => 2017-04-07 12:08:59
                [created_user_id] => 856
                [ordering] => 0
                [language] => *
                [fieldparams] => Joomla\Registry\Registry Object
                    (
                        [data:protected] => stdClass Object
                            (
                                [buttons] =>
                                [width] =>
                                [height] =>
                                [filter] =>
                            )

                        [initialized:protected] => 1
                        [separator] => .
                    )

                [params] => Joomla\Registry\Registry Object
                    (
                        [data:protected] => stdClass Object
                            (
                                [hint] =>
                                [render_class] =>
                                [class] =>
                                [showlabel] => 1
                                [disabled] => 0
                                [readonly] => 0
                                [show_on] =>
                                [display] => 2
                            )

                        [initialized:protected] => 1
                        [separator] => .
                    )

                [type] => editor
                [default_value] =>
                [context] => com_content.article
                [group_id] => 0
                [label] => article-editor
                [description] =>
                [required] => 0
                [language_title] =>
                [language_image] =>
                [editor] =>
                [access_level] => Public
                [author_name] => Super Utilisateur
                [group_title] =>
                [group_access] =>
                [group_state] =>
                [value] => Bar
                [rawvalue] => Bar
            )
    )
```

## Rendre le champ

La fonction `FieldsHelper::render()` est utilisée pour rendre chaque champ. Ajoutez d'abord une
instruction `use Joomla\Component\Fields\Administrator\Helper\FieldsHelper;` à
la liste des instructions `use` en haut du fichier de remplacement :

```php
defined('_JEXEC') or die;

use Joomla\CMS\Helper\ContentHelper;
use Joomla\CMS\HTML\HTMLHelper;
use Joomla\CMS\Language\Text;
use Joomla\CMS\Layout\FileLayout;
use Joomla\CMS\Layout\LayoutHelper;
use Joomla\CMS\Plugin\PluginHelper;
use Joomla\CMS\Router\Route;
use Joomla\Component\Contact\Site\Helper\RouteHelper;
use Joomla\Component\Fields\Administrator\Helper\FieldsHelper;
```

Ensuite, partout où vous souhaitez placer les champs dans votre modèle, utilisez le code suivant :
```php
<?php foreach ($this->item->jcfields as $field) : ?>
    <?php echo FieldsHelper::render($field->context, 'field.render', array('field' => $field)); ?><br>
<?php endforeach ?>
```

Ou pour un remplacement brut, qui ne traduit pas l'étiquette :

```php
<?php foreach ($this->item->jcfields as $field) : ?>
    <?php echo $field->label . ':' . $field->value; ?><br>
<?php endforeach ?>
```

## Chargement des champs individuels

Pour ajouter des champs individuels à votre contenu, commencez par choisir des noms spécifiques pour vos champs personnalisés, en utilisant le champ **Nom**, qui sera utilisé pour référencer votre champ directement dans le code de surcharge. Dans l'onglet `Options`, sélectionnez **Non** dans le champ `Affichage Automatique` pour éviter qu'il ne soit affiché automatiquement dans l'une des positions standard.

Ensuite, pour permettre un accès direct par nom aux champs personnalisés dans une surcharge, placez le code ci-dessous au début de votre fichier. Vous devriez faire cela pour chaque fichier PHP de surcharge sur lequel vous souhaitez placer des champs personnalisés individuels.

```php
<?php foreach($this->item->jcfields as $jcfield) {
    $this->item->jcFields[$jcfield->name] = $jcfield;
} ?>
```

Et enfin, vous devriez ajouter le code de placement du champ à l'endroit où vous souhaitez que l'étiquette ou la valeur du champ soit affichée.

Pour ajouter l'**étiquette** du champ à votre surcharge, insérez le code ci-dessous, en remplaçant `name-of-field` par le nom du champ.

```php
<?php echo $this->item->jcFields['name-of-field']->label; ?>:&nbsp;
```

Pour ajouter la **valeur** du champ à votre surcharge, insérez le code ci-dessous, en remplaçant `name-of-field` par le nom du champ.

```php
<?php echo $this->item->jcFields['name-of-field']->rawvalue; ?>
```

Vous pouvez ajouter ce code à n'importe quelle partie de votre surcharge. Exemples : Le contenu d'un div, le src dans une balise `img`, dans un attribut de classe CSS, etc.

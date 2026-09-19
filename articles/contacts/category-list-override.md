<!--
{
    "source": "https://docs.joomla.org/category-list-override.md",
    "title": "Remplacement de la liste des cat\u00e9gories",
    "description": "D\u00e9couvrez comment cr\u00e9er une surcharge de mod\u00e8le pour am\u00e9liorer la mise en page d\u2019une liste de contacts dans une cat\u00e9gorie ",
    "author": ""
}
-->

## La liste des contacts d’une catégorie

La mise en page par défaut des contacts d’une catégorie est contrôlée par un modèle dans le code du composant 
com_contacts. La mise en page par défaut ressemble à ceci :

![comité culturel utilisant la mise en page et le style par défaut](../../../en/images/contacts/category-list-override/01-contacts-culture-committee.png)

C’est peut-être une opinion personnelle, mais la mise en page par défaut des contacts ne me 
convient pas vraiment. Voici ce qui me pose problème :

* Les images de portrait originales faisaient 500 pixels de large et étaient beaucoup trop imposantes.
* Le nom du contact n’est pas suffisamment mis en évidence.
* La liste à puces des informations personnelles n’a pas de titre et semble isolée.
* La fonction de la personne n’a pas de titre.
* Les champs d’adresse et de code postal sont absents.
* Les données de localisation sont incomplètes.
* Les données de chaque contact sont présentées dans un tableau et sont assez serrées sur les écrans étroits.

Alors, comment faire pour l’adapter à mes préférences ? Ma solution consiste à créer une surcharge de modèle 
et à ajouter quelques styles personnalisés. Voici le résultat :
![comité d’entreprise utilisant une surcharge de modèle et des styles personnalisés](../../../en/images/contacts/category-list-override/02-contacts-business-committee.png)

## Surcharge de la mise en page du modèle

Le dossier com_contact/tmpl/category contient trois fichiers PHP : default.php,
default_children.php et default_items.php. Le dernier de cette liste contient
la mise en page du tableau pour la liste.

Les fichiers de surcharge sont créés via Système / Modèles de site / Cassiopeia
Détails et fichiers / Créer des substitutions. Sélectionnez com_contact, puis category.
Le dossier html contient alors com_contact/category avec les trois fichiers de modèle
mentionnés ci-dessus.

### Modifier le fichier default.php en mydefault.php

Le fichier `default.php` contient une ligne qui spécifie la mise en page à utiliser pour 
chaque enregistrement individuel. Sélectionnez ce fichier pour le modifier et **renommez**-le 
en `mydefault.php` (ou utilisez le préfixe de votre choix à la place de `my`). N’utilisez pas 
de caractère de soulignement dans le nom de fichier !

Lorsque vous accéderez ensuite au formulaire Contacts / Catégorie / Modifier, le champ
Mise en page de l’onglet Options vous permettra de choisir entre la mise en page du composant et votre
mise en page personnalisée. Il se présente ainsi :

```
---From Global Options---
  Use Global
---From Component---
  Default
---From cassiopeia Template---
  mydefault

```

### Modifier le fichier mydefault.php

La ligne 20 de `mydefault.php` contient `$this->subtemplatename = 'items';`.
Remplacez `items` par `myitems` afin que les lignes 18 à 23 soient les suivantes :

```html
<div class="com-contact-category">
    <?php
        $this->subtemplatename = 'myitems';
        echo LayoutHelper::render('joomla.content.category_default', $this);
    ?>
</div>
```

### Modifier le fichier default_items.php en mydefault_myitems.php

Le fichier `default_items.php` contient la mise en page de chaque contact. Il doit être
renommé afin de conserver la possibilité d’utiliser la mise en page d’origine. La première partie
du nom n’a pas d’importance. C’est la partie `myitems`, mentionnée dans le fichier
`mydefault.php`, qui est utilisée pour la mise en page.

### Modifier le fichier mydefault_myitems.php

La section `<table>...</table>` de ce fichier s’étend des lignes 85 à 204. Pour
la surcharge de mise en page, j’ai remplacé le balisage du tableau par le balisage de grille
Bootstrap suivant. Sur les écrans étroits, les trois colonnes sont empilées. Sur les écrans de plus de
768 pixels de large, les colonnes sont côte à côte. Le balisage révisé a déplacé les
champs personnalisés sous le nom du contact.

```
<div class="container-fluid text-center border border-2">
<?php $nrows = 0; foreach ($this->items as $i => $item) : ?>
    <?php if ($item->published !== 1 ||
        (!empty($item->publish_up) && strtotime($item->publish_up) > strtotime(Factory::getDate())) ||
        (!empty($item->publish_down) && strtotime($item->publish_down) < strtotime(Factory::getDate()))) { continue; } ?>
        <div class="row cat-list-row<?php echo $nrows % 2; $nrows += 1; ?> align-items-center">
            <div class="col-12 col-md-3">
                <?php if ($this->params->get('show_image_heading')) : ?>
                    <?php if ($item->image) : ?>
                        <?php echo LayoutHelper::render(
                            'joomla.html.image',
                            [
                                'src'   => $item->image,
                                'alt'   => 'official image of ' . $item->name,
                                'class' => 'contact-thumbnail img-thumbnail',
                            ]
                        ); ?>
                    <?php endif; ?>
                <?php endif; ?>
            </div>
            <div class="col-12 col-md-3">
                <div class="parliament-committee-fields">
                <a href="<?php echo Route::_(RouteHelper::getContactRoute($item->slug, $item->catid, $item->language)); ?>">
                    <span class="fs-2"><?php echo $this->escape($item->name); ?></span>
                </a>
                    <?php echo $item->event->beforeDisplayContent; ?>
                </div>
            </div>
            <div class="col-12 col-md-6 text-start">
                <?php if ($this->params->get('show_position_headings') && !empty($item->con_position)) : ?>
                    <strong><?php echo Text::_('COM_CONTACT_FIELD_INFORMATION_POSITION_LABEL'); ?></strong><br>
                    <?php echo $item->con_position; ?><br>
                <?php endif; ?>
                <?php if ($this->params->get('show_suburb_headings')) : ?>
                    <?php $location = []; ?>
                    <?php if (!empty($item->address)) : ?>
                        <?php $location[] = $item->address; ?>
                    <?php endif; ?>
                    <?php if (!empty($item->suburb)) : ?>
                        <?php $location[] = $item->suburb; ?>
                    <?php endif; ?>
                    <?php if (!empty($item->state)) : ?>
                        <?php $location[] = $item->state; ?>
                    <?php endif; ?>
                    <?php if (!empty($item->postcode)) : ?>
                        <?php $location[] = $item->postcode; ?>
                    <?php endif; ?>
                        <strong><?php echo Text::_('COM_CONTACT_FIELD_INFORMATION_ADDRESS_LABEL'); ?></strong><br>
                    <?php echo implode("<br>\n", $location); ?><br>
                <?php endif; ?>
                <?php if (!empty($item->misc)) : ?>
                    <?php echo $item->misc; ?>
                <?php endif; ?>
            </div>
        </div>
    <?php endforeach; ?>
</div>
```

## Mise en forme

Les classes de style Bootstrap peuvent être définies dans le fichier `mydefault_myitems.php`.
Par exemple, `<span class="fs-2">...</span>` est utilisé pour augmenter la taille de la police
du nom du contact. D’autres styles peuvent être ajoutés dans le fichier `user.css`, par
exemple, la personnalisation des listes à puces apparaissant uniquement au sein d’une balise
ayant une classe `contactList`.

Voici les styles saisis dans le fichier user.css pour obtenir la mise en page
du comité d’entreprise illustré ci-dessus.

```
.contact-thumbnail {
  max-width: 200px;
  margin-right: 1rem;
}
a:has(.contact-thumbnail) {
  font-weight: 700;
  font-size: larger;
}
#contactList ul {
  list-style-type: none;
  padding-left: 0;
}
.cat-list-row0 {
  background-color: #efefef;
}
.cat-list-row0:hover, .cat-list-row1:hover  {
  background-color: #ddd;
}
div.parliament-committee-fields {
  text-align: left;
  margin-top: 1rem;
}
div.parliament-committee-fields ul.fields-container {
  list-style-type: none;
  padding-left: 0;
}
div.parliament-committee-fields ul.fields-container span.field-label {
  font-weight: 700;
}
```

*Traduit par openai.com*